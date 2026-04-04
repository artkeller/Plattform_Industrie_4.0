# 1. Vorbemerkung: „Token Fatigue“ ist kein definierter Fachbegriff

Der Ausdruck *Token Fatigue* ist kein etablierter Begriff in der Mathematik oder im Machine Learning. 
Was damit gemeint ist, lässt sich jedoch präzise auf Eigenschaften von **Transformer-Modellen** 
(vgl. Transformer Architecture) zurückführen.

*Token Fatigue* ist eine **informelle** Beschreibung für:

* die **Begrenzung des Kontextfensters**
* die **Skalierungsprobleme von Self-Attention**
* die **Instabilität autoregressiver Generierung über lange Sequenzen**

---

# 2. Formales Modell

Ein Sprachmodell approximiert die Wahrscheinlichkeit einer Token-Sequenz:

$$
P(x_1, x_2, \dots, x_n) = \prod_{t=1}^{n} P(x_t \mid x_1, \dots, x_{t-1})
$$

Das ist ein **autoregressives Modell**.

---

# 3. Self-Attention als Kernmechanismus

In einem Transformer wird für jedes Token (i) eine gewichtete Summe über alle Tokens (j) gebildet:

$$
\text{Attention}(Q,K,V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

Das ist die bekannte **Scaled Dot-Product Attention** (Attention Mechanism).

Für ein einzelnes Token (i):

$$
y_i = \sum_{j=1}^{n} \alpha_{ij} v_j
$$

mit

$$
\alpha_{ij} = \frac{\exp(q_i \cdot k_j / \sqrt{d_k})}{\sum_{l=1}^{n} \exp(q_i \cdot k_l / \sqrt{d_k})}
$$

---

# 4. Problem 1: Skalierung mit Sequenzlänge

Die Attention-Gewichte erfüllen:

$$
\sum_{j=1}^{n} \alpha_{ij} = 1
$$

Wenn (n) wächst, verteilt sich die Aufmerksamkeit auf mehr Tokens.

### Konsequenz:

Im Erwartungswert gilt (vereinfacht):

$$
\mathbb{E}[\alpha_{ij}] \approx \frac{1}{n}
$$

→ **Signalverdünnung**

Wichtige Tokens müssen sich gegen viele irrelevante durchsetzen.

---

# 5. Problem 2: Informationsverlust durch Projektion

Die Repräsentation eines Tokens ist:

$$
y_i = \sum_{j} \alpha_{ij} v_j
$$

Das ist eine **lineare Kombination** im Vektorraum.

Mit wachsendem (n):

* steigt die Anzahl der summierten Terme
* aber die Dimension (d) bleibt konstant

→ Projektion vieler Informationen in einen festen Raum

### Interpretation:

Das ist eine Form von **Kompressionsverlust**.

---

# 6. Problem 3: Begrenztes Kontextfenster

Modelle haben eine maximale Länge (L):

$$
n \leq L
$$

Für (n > L) wird typischerweise:

$$
(x_1, \dots, x_{n-L}) \text{ verworfen}
$$

Das ist ein harter Informationsverlust.

---

# 7. Problem 4: Fehlerfortpflanzung

Da das Modell autoregressiv ist:

$$
\hat{x}_t \sim P(x_t \mid \hat{x}*1, \dots, \hat{x}*{t-1})
$$

Fehler wirken rekursiv:

$$
\epsilon_t = f(\epsilon_{t-1})
$$

Unter milden Annahmen kann sich der Fehler aufschaukeln:

$$
\epsilon_t \approx \sum_{k=1}^{t} \delta_k
$$

→ Drift im Kontext

---

# 8. Kombination der Effekte

Das, was informell „Token Fatigue“ genannt wird, ist die Überlagerung von:

1. **Attention-Diffusion**

$$
\alpha_{ij} \to \frac{1}{n}
$$

3. **Informationskompression**

$$
\text{many } v_j \rightarrow \text{fixed-dimensional } y_i
$$

5. **Kontextabschneiden**

$$
n > L \Rightarrow \text{Truncation}
$$

7. **Fehlerakkumulation**

$$
\epsilon_t \uparrow
$$

---

# 9. Präzise Interpretation

Der Marketingbegriff „Token Fatigue“ beschreibt kein eigenständiges Phänomen, sondern:

> die Abnahme der effektiven Informationsnutzung eines Transformers mit wachsender Sequenzlänge.

Formal kann man das als sinkendes Signal-Rausch-Verhältnis interpretieren:

$$
\text{SNR} \propto \frac{\text{relevante Attention-Masse}}{\text{irrelevante Tokens}}
$$

Mit wachsendem (n):

$$
\text{SNR} \downarrow
$$

---

