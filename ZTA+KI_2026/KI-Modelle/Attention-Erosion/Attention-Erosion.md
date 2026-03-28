# Die Kaskade der Aufmerksamkeitserosion

## Wissenschaftliche Grundlage

Bevor die Kaskade erklärt werden kann, braucht es ein präzises Modell dessen, was Attention eigentlich berechnet.

Für jeden Token $q$ (Query) und alle Kontext-Tokens $K$ (Keys) gilt:

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

Entscheidend ist die **Softmax-Normalisierung**: Die Gewichte summieren sich zu 1. Das bedeutet — Attention ist ein **Nullsummenspiel**. Jeder neue Token, der in den Kontext kommt, verdrängt anteilig alle anderen.

---

## Stufe 1: Lost-in-the-Middle

**Mechanismus: Positionelle Aufmerksamkeitsverzerrung**

Liu et al. (2023) zeigten empirisch, dass die Modellperformance einer U-Kurve folgt:

$$\text{Performance}(p) \propto \frac{1}{1 + \lambda \cdot \min(p,\, N-p)}$$

wobei $p$ die Position der relevanten Information und $N$ die Gesamtlänge des Kontexts ist.

Die strukturellen Ursachen:

**a) Positionskodierung und Attention-Bias**
In RoPE (Rotary Position Embedding) und ähnlichen Systemen wird die Attention-Stärke zwischen zwei Tokens durch ihre relative Distanz moduliert. Tokens mit großer gegenseitiger Distanz erhalten systematisch niedrigere Attention-Scores — ein impliziter *recency bias* ist in die Geometrie eingebaut.

**b) [Softmax-Sättigung](Softmax-Funktion.md)**
Bei langen Sequenzen tendiert Softmax dazu, Gewichte auf wenige dominante Positionen zu konzentrieren (*attention sink*-Phänomen, Xiao et al. 2023). Mittlere Tokens fallen unter die Wahrnehmungsschwelle.

**c) Residualstream-Propagation**
Information aus mittleren Positionen muss durch mehr Attention-Hops propagiert werden, um die finale Ausgabeschicht zu erreichen. Jeder Hop ist verlustbehaftet — die effektive Informationsdichte sinkt mit der Distanz.

**Ergebnis:** Ein Token bei Position $N/2$ in einem 10.000-Token-Kontext hat eine messbar niedrigere Wahrscheinlichkeit, die Ausgabe zu beeinflussen, als ein semantisch identischer Token bei Position 100 oder Position 9.900.

---

## Stufe 2: Silent Truncation

**Mechanismus: Schwellenbasierter Informationsverlust ohne Metasignal**

Silent Truncation ist die **direkte Konsequenz** aus Stufe 1 — aber sie wird durch zwei weitere Eigenschaften des Systems erst *still*:

**a) Keine interne Verlustbuchhaltung**
Transformer-Architekturen haben keine dedizierte Komponente, die überwacht, ob alle Input-Informationen in die Ausgabe eingeflossen sind. Es gibt kein Äquivalent zu einem `NULL`-Pointer oder einem `KeyError` — der Forward Pass läuft durch, unabhängig davon, ob relevante Tokens effektiv ignoriert wurden.

**b) Fluente Completion trotz Informationslücke**
Das Modell generiert den nächsten Token basierend auf der Verteilung:

$$P(x_t \mid x_{<t}) = \text{softmax}(W_o \cdot h_t)$$

Diese Verteilung ist immer definiert — sie kollabiert nie auf ein "Ich weiß es nicht"-Signal, weil kein solcher Zustand im Output-Vokabular existiert. Das Modell **muss** einen Token generieren, auch wenn die zugrundeliegende Information effektiv absent ist.

**c) Konfabulationsdruck**
Wenn relevante Kontext-Information niedrig gewichtet wurde, füllt das Modell die Lücke mit der statistisch wahrscheinlichsten Fortsetzung aus dem Training — nicht aus dem Kontext. Das ist der Übergang von *Retrieval* zu *Generation*, und er ist von außen nicht sichtbar.

**Ergebnis:** Der Output ist syntaktisch kohärent und semantisch plausibel. Das Modell meldet nicht, dass es auf Trainingsdaten statt auf Kontextinformation zurückgegriffen hat. Die Truncation ist silent, weil das Ausgabesystem keine Verlustanzeige kennt.

---

## Stufe 3: Instruction Drift

**Mechanismus: Kumulative Kontextverschiebung durch lokale Kohärenzoptimierung**

Instruction Drift entsteht, wenn Silent Truncation **wiederholt** auf regeltragende Tokens wirkt — also auf jene Tokens, die Verhaltensvorgaben kodieren.

**a) Lokale vs. globale Kohärenz**
Das Modell optimiert bei der Generierung primär auf lokale Kohärenz — der nächste Token soll gut zum unmittelbaren Kontext passen. Frühe Instruktionen sind *global* relevant, aber *lokal* weit entfernt. Mit wachsendem Gesprächsverlauf sinkt ihr Einfluss auf die lokale Generierungsentscheidung.

**b) In-context Learning als Driftverstärker**
Transformer-Modelle betreiben implizit *in-context learning* (Brown et al. 2020): Sie passen ihr Verhalten an Muster im Kontext an. Das bedeutet — die eigenen früheren Outputs werden zu impliziten Beispielen, die das Modell "lernt". Wenn das Modell in Turn 5 leicht von einer Regel abweicht, erhöht dieser Output die statistische Wahrscheinlichkeit einer ähnlichen Abweichung in Turn 6.

Formalisiert:

$$P(\text{Output}_t) \propto P(\text{Instruktion}) \cdot P(\text{lokaler Kontext}_{t-k:t})$$

Mit wachsendem $t$ sinkt der relative Einfluss von $P(\text{Instruktion})$ gegenüber $P(\text{lokaler Kontext})$.

**c) Fehlende Rekalibrierung**
Ein System ohne expliziten Mechanismus zur Instruktionsprüfung hat keine Möglichkeit, die aktuelle Ausgabe gegen die Ausgangsvorgabe zu evaluieren. Der Drift ist selbstverstärkend, weil jede neue Ausgabe den Kontext weiter in die Drift-Richtung verschiebt.

**Ergebnis:** Die Verhaltensabweichung ist keine Entscheidung — sie ist das emergente Ergebnis lokaler Optimierung unter degradierter globaler Information.

---

## Stufe 4: Silent Arbitration

**Mechanismus: Implizite Konfliktauflösung ohne Metakommunikation**

Silent Arbitration ist der **Auflösungsmechanismus** der durch Drift entstandenen Inkonsistenz — und gleichzeitig der Punkt, an dem die Kaskade für den Benutzer am wenigsten sichtbar wird.

**a) Konfliktstruktur**
Am Ende der Kaskade stehen zwei konkurrierende Signale im Kontext:

```
Signal A: Ursprungsinstruktion (positionell weit, Attention-Gewicht niedrig)
Signal B: Lokaler Kontext + eigene Drift-Outputs (positionell nah, Gewicht hoch)
```

Das Modell muss einen Token generieren, der beiden Signalen Rechnung trägt — oder eines implizit priorisiert.

**b) Keine explizite Konfliktrepräsentation**
Transformer haben keine dedizierte Komponente für *Konfliktdetektion*. Es gibt keinen Mechanismus, der zwei Instruktionen vergleicht und einen Widerspruch als solchen repräsentiert. Die Auflösung geschieht implizit durch die Gewichtungsverhältnisse in der Attention-Matrix — nicht durch eine explizite Entscheidungslogik.

**c) Fluenz als Verschleierung**
Die Sprachmodellierung ist darauf trainiert, flüente, kohärente Outputs zu erzeugen. Metakommunikation über interne Zustände — "Ich bemerke einen Widerspruch zwischen X und Y" — ist kein natürlicher Output-Typ, der im Training systematisch verstärkt wurde. Das Modell hat eine *strukturelle Tendenz zur Fluenz über Transparenz*.

**Ergebnis:** Der Konflikt wird aufgelöst, ohne dass eine Auflösung stattgefunden zu haben scheint. Der Output wirkt konsistent — und genau das macht Silent Arbitration zur gefährlichsten Stufe der Kaskade.

---

## Die Kaskade als Gesamtsystem
<br>

$$\underbrace{\text{Attention-Geometrie}}_{\text{physikalische Ursache}} \xrightarrow{\text{erzeugt}} \underbrace{\text{Silent Truncation}}_{\text{Informationsverlust}} \xrightarrow{\text{akkumuliert}} \underbrace{\text{Instruction Drift}}_{\text{Verhaltensverschiebung}} \xrightarrow{\text{wird maskiert}} \underbrace{\text{Silent Arbitration}}_{\text{Transparenzverlust}}$$

<br>

Die Kaskade ist kein Bug — sie ist das **emergente Verhalten eines Systems**, das für Fluenz und lokale Kohärenz optimiert wurde, ohne explizite Mechanismen für globale Konsistenzprüfung, Verlustanzeige oder Konflikttransparenz.

---

**Die eigentliche wissenschaftliche Aussage:** Diese vier Phänomene sind nicht vier separate Fehler. Sie sind **eine einzige Konsequenz** der Softmax-Normalisierung in langen Sequenzen — beobachtet auf vier verschiedenen Abstraktionsebenen.
