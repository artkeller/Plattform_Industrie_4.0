# Lost-in-the-Middle-Effekt

Das Modell liest die Mitte — aber es *erinnert* sich schlechter daran. Und es sagt dir nicht, was es vergessen hat.

Der **Lost-in-the-Middle-Effekt** ist ein empirisch belegtes Phänomen: Sprachmodelle verarbeiten Informationen am **Anfang und Ende** eines langen Kontexts deutlich besser als Informationen in der **Mitte**.

---

## Die Grundform

```
[Kontext-Fenster]

Pos 0        Pos N/2        Pos N
  ↓             ↓              ↓
 stark        schwach         stark
erinnert     erinnert        erinnert

  ←————————————————————————————→
         "U-Kurve" der Aufmerksamkeit
```

Das ist keine Metapher — es wurde 2023 in kontrollierten Experimenten gemessen, indem relevante Dokumente systematisch an verschiedenen Positionen in langen Prompts platziert wurden. Die Modellperformance fiel konsistent ab, wenn die relevante Information in der Mitte lag.

---

## Warum passiert das

**1. Primacy-Effekt (Anfang)**
Die ersten Tokens setzen den initialen Attention-Zustand. Sie beeinflussen alle nachfolgenden Attention-Berechnungen — ihr Signal propagiert durch alle Schichten.

**2. Recency-Effekt (Ende)**
Tokens nah am Generierungspunkt haben kurze Attention-Distanz. Der Gradient des Einflusses ist steil und direkt.

**3. Mittlere Tokens**
Sie sind weit genug vom Anfang entfernt, um keinen starken Primacy-Effekt zu haben — und weit genug vom Ende, um keinen Recency-Effekt zu haben. Sie konkurrieren mit dem gesamten restlichen Kontext um ein begrenztes Attention-Budget.

```
Attention-Kosten ∝ Sequenzlänge²  (bei Standard-Attention)
                                    ↑
               je länger der Kontext, desto teurer wird
               das "Erreichen" mittlerer Positionen
```

---

## Konkrete Konsequenzen

| Szenario | Risiko |
|---|---|
| Wichtige Bedingung steht in Absatz 4 von 10 | Wird möglicherweise ignoriert |
| Relevantes Dokument in der Mitte von 20 | Schlechtere Extraktion als bei Pos. 1 oder 20 |
| Langer System-Prompt, kritische Regel in der Mitte | Regelkonformität sinkt |
| RAG-System mit vielen Chunks | Mittlere Chunks systematisch benachteiligt |

---

## Verhältnis zu den anderen Konzepten

```
Lost-in-the-Middle
        ↓ erzeugt
Silent Truncation       ← Information nominell vorhanden, aber effektiv ignoriert
        ↓ akkumuliert zu
Instruction Drift       ← Regelabweichung, weil Regel in der Mitte versank
        ↓ wird aufgelöst durch
Silent Arbitration      ← Modell füllt Lücke ohne zu melden, dass eine existiert
```

Die vier Konzepte sind keine unabhängigen Fehler — sie sind **Stufen einer Kausalkette**.

---

## Gegenmaßnahmen

```
1. Kritische Information ans Ende     →  Recency-Effekt nutzen
2. Kritische Information wiederholen  →  An Anfang UND Ende platzieren
3. Explizite Referenz erzwingen       →  "Beziehe dich auf Abschnitt X"
4. Kontext komprimieren               →  Weniger Konkurrenz um Attention
5. Chunking-Strategie in RAG          →  Relevanteste Chunks an Randpositionen
```

---
