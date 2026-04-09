# 1. Ausgangspunkt: Was ein Sprachmodell formal tut

Es approximiert:

$$
P(x_t \mid x_1, \dots, x_{t-1})
$$

Das ist eine **statistische Vorhersagefunktion** über Token-Sequenzen – keine semantische Operation im logischen Sinn.

---

# 2. Was „Verstehen“ in der Mathematik bedeuten würde

Wenn man „Verstehen“ formalisiert, landet man typischerweise bei:

* **Semantikfunktion**

$$
\lbrack\!\lbrack \cdot \rbrack\!\rbrack : \text{Syntax} \to \text{Bedeutung}
$$

* **Wahrheitsbewertung** (Logik)

$$
\lbrack\!\lbrack \varphi \rbrack\!\rbrack \in \{\text{wahr}, \text{falsch}\}
$$

* **Ableitbarkeit**

$$
\Gamma \vdash \varphi
$$

Ein System „versteht“ eine Ableitung, wenn es:

1. die Semantik kennt
2. die Inferenzregeln korrekt anwendet
3. die Gültigkeit unabhängig von Formulierungen erkennt

Das ist klassische Logik (vgl. Mathematical Logic).

---

# 3. Was ein Transformer stattdessen macht

Ein Transformer (Transformer Architecture) bildet:

$$
f_\theta : \text{Token-Sequenzen} \to \mathbb{R}^d
$$

und nutzt dann:

$$
P(x_t \mid \cdot) = \text{softmax}(g(f_\theta(\cdot)))
$$

Wichtig:

* Die Repräsentationen sind **Vektoren**, keine Wahrheitswerte
* Es gibt **keine explizite Semantikfunktion**
* Es existiert **kein internes Modell der Welt oder Logiksystem**

---

# 4. Der zentrale Punkt: Syntax ≠ Semantik

Das Modell lernt:

$$
\text{Korrelationen in } P(\text{Text})
$$

aber nicht:

$$
\text{Bedeutung im Sinne von } \lbrack\!\lbrack \cdot \rbrack\!\rbrack
$$

Das ist genau die Trennung, die auch in der Philosophie diskutiert wird (vgl. Chinese Room):

> Korrekte Symbolmanipulation ≠ Verstehen

---

# 5. Warum logische Ableitung nicht „verstanden“ wird

## 5.1 Beispiel: Modus Ponens

Formal:

$$
(p \rightarrow q),; p ;\vdash; q
$$

Ein logisches System:

* kennt die Regel
* garantiert Korrektheit

Ein Sprachmodell:

* hat viele Beispiele gesehen, in denen solche Muster vorkommen
* approximiert:

$$
P(q \mid p \rightarrow q,, p)
$$

Das Ergebnis kann korrekt sein – aber:

> Es basiert auf statistischer Ähnlichkeit, nicht auf Regelanwendung.

---

## 5.2 Fehlende Invarianz

Ein echtes logisches System ist **invariant unter Umformulierung**:

$$
(p \rightarrow q), p \vdash q \quad \equiv \quad (\neg p \lor q), p \vdash q
$$

Ein Modell hingegen ist sensitiv gegenüber:

* Formulierung
* Reihenfolge
* Tokenisierung

→ Hinweis auf fehlende abstrakte Repräsentation

---

## 5.3 Kein Wahrheitsbegriff

Das Modell optimiert:

$$
\min_\theta ; \mathbb{E}[-\log P_\theta(x_t \mid \cdot)]
$$

Nicht:

$$
\text{Korrektheit von Aussagen}
$$

Es gibt intern keinen Operator wie:

$$
\text{Truth}(\varphi)
$$

---

# 6. Informations-theoretische Sicht

Das Modell lernt:

$$
I(\text{Token}; \text{Kontext})
$$

also **Mutual Information** zwischen Textteilen.

Nicht gelernt wird:

$$
I(\text{Aussage}; \text{Weltzustand})
$$

→ keine Erdung (Grounding)

---

# 7. Fehlende Semantische Abstraktion

Semantische Abstraktion würde bedeuten:

$$
\text{verschiedene syntaktische Formen} \rightarrow \text{gleiche Bedeutung}
$$

z. B.:

* „Alle Menschen sind sterblich“
* „Für alle x gilt: Mensch(x) → sterblich(x)“

Ein Modell approximiert nur:

$$
\text{Ähnlichkeit im Embedding-Raum}
$$

Das ist:

* kontinuierlich
* unscharf
* kontextabhängig

Nicht:

* diskret
* regelbasiert
* beweisbar korrekt

---

# 8. Konsequenz: Simulation von Verstehen

Das Modell kann:

* logische Schritte oft korrekt reproduzieren
* Argumentationen generieren
* scheinbar „verstehen“

Aber formal gilt:

> Es simuliert die Form von Verstehen, ohne eine semantische Theorie oder Inferenzmaschine zu besitzen.

---

# 9. Präzise Formulierung des „Mangels“

Das „Manko“ ist kein Fehler, sondern eine Eigenschaft:

Ein Sprachmodell ist:

$$
\text{ein probabilistischer Approximationoperator über Symbolsequenzen}
$$

aber nicht:

$$
\text{ein semantisches oder logisches System}
$$

---

# 10. Kurzfazit

Was oft als „fehlendes Verständnis“ beschrieben wird, ist präzise:

* keine explizite Semantik (\llbracket \cdot \rrbracket)
* keine garantierten Inferenzregeln (\vdash)
* kein Wahrheitsbegriff
* keine Weltverankerung

Stattdessen:

$$
\text{Optimierung von } P(\text{Text})
$$

---

# 11. Nächster Schritt: Hybride Modelle

[Hybride Modelle](Hybride-Modelle.md)

---



