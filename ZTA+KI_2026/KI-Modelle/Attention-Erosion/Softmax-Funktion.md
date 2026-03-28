# Softmax-Effekt

### Softmax-Funktion

**Softmax** ist eine mathematische Funktion, die in neuronalen Netzen (vor allem in der letzten Schicht bei Klassifikationsaufgaben) verwendet wird, um **Rohwerte (Logits)** in **Wahrscheinlichkeiten** umzuwandeln.

### Formel

Gegeben sind Logits $$\( z_1, z_2, \dots, z_K \)$$:

$$
\text{softmax}(z_i) = \frac{e^{z_i}}{\sum_{j=1}^{K} e^{z_j}}
$$

Das Ergebnis ist ein Vektor, bei dem:
- Alle Werte zwischen **0 und 1** liegen
- Die Summe aller Werte **genau 1** ergibt → echte Wahrscheinlichkeitsverteilung

### Der „Softmax-Effekt“

Der Softmax hat drei charakteristische Eigenschaften:

1. **Exponentieller Effekt (das Wichtigste!)**
   - Große positive Logits werden stark verstärkt (exponentiell)
   - Negative Logits werden stark abgeschwächt
   - Beispiel:
     - Logits: [2.0, 1.0, 0.0]
     - Nach Softmax ≈ [0.665, 0.245, 0.090]
     - Der größte Wert (2.0) bekommt deutlich mehr Gewicht als bei einer linearen Skalierung.

2. **„Winner-takes-most“-Verhalten**
   - Je größer der Unterschied zwischen den Logits ist, desto stärker dominiert die höchste Klasse.
   - Bei sehr großen Unterschieden verhält sich Softmax fast wie eine harte argmax-Funktion (nur eine Klasse hat fast 100 %).

3. **Temperatur-Effekt (wichtig in der Praxis)**
   Oft wird Softmax mit einer Temperatur $$\( \tau \)$$ verwendet:

$$
\text{softmax}(z_i, \tau) = \frac{e^{z_i / \tau}}{\sum_{j} e^{z_j / \tau}}
$$

   - $$\( \tau > 1 \)$$: Verteilung wird weicher (mehr Zufall, kreativere Antworten)
   - $$\( \tau < 1 \)$$: Verteilung wird schärfer (stärkere Konzentration auf die beste Klasse)
   - $$\( \tau = 1 \)$$: normales Softmax

### Warum ist das in LLMs so wichtig?

- Beim nächsten Token Prediction wandelt das Modell die Roh-Logits aller möglichen Tokens in eine Wahrscheinlichkeitsverteilung um.
- Der **Softmax-Effekt** entscheidet, wie „entschieden“ oder wie „unsicher“ das Modell ist.
- Bei niedriger Temperatur (z. B. 0.7) wirkt das Modell selbstbewusst und fokussiert.
- Bei hoher Temperatur (z. B. 1.3) wird es kreativer und vielfältiger.

### Zahlenbeispiel

| Logit | e^Logit | Softmax (τ=1) | Softmax (τ=0.5) | Softmax (τ=2.0) |
|-------|---------|---------------|-----------------|-----------------|
| 4.0   | 54.60   | **0.88**      | **0.98**        | 0.73            |
| 2.0   | 7.39    | 0.12          | 0.02            | **0.22**        |
| 0.0   | 1.00    | 0.016         | 0.0003          | 0.05            |

→ Der größte Logit dominiert bei kleiner Temperatur

**Zusammengefasst:**
Der Softmax-Effekt ist der Mechanismus, der aus „rohen Bewertungen“ eines Modells eine Wahrscheinlichkeitsverteilung macht – mit starker Betonung der besten Optionen durch die Exponentialfunktion. Er bestimmt maßgeblich, wie sicher oder wie kreativ eine KI antwortet.
