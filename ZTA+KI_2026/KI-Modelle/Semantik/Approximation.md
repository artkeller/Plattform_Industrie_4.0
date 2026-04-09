# **Approximation logikähnlichen Verhaltens**

---

# 1. Problemstellung

Gegeben ist ein autoregressives Sprachmodell:

$$
P_\theta(x_t \mid x_1,\dots,x_{t-1})
$$

Gesucht ist eine Erklärung dafür, warum ein solches System **logikähnliches Verhalten** zeigt, obwohl es:

* keine explizite Semantik besitzt
* keine Inferenzregeln implementiert
* keine Wahrheitswerte berechnet

---

# 2. Trainingsziel als Ausgangspunkt

Das Modell minimiert:

$$
\mathcal{L}(\theta) = \mathbb{E}*{(x_1,\dots,x_n)\sim D} \left[-\sum*{t=1}^n \log P_\theta(x_t \mid x_{<t}) \right]
$$

Das ist Maximum-Likelihood-Schätzung auf einer Textverteilung (D).

**Wichtig:**
Wenn das Trainingskorpus viele korrekte logische Argumente enthält, dann gilt implizit:

$$
P_D(\text{korrekte Ableitung}) \gg P_D(\text{inkorrekte Ableitung})
$$

---

# 3. Logik als statistische Regularität

Betrachte eine formale Regel, z. B. Modus Ponens:

$$
(p \rightarrow q),; p ;\vdash; q
$$

Im Trainingskorpus entspricht das einer Häufigkeitsstruktur:

$$
P(q \mid p \rightarrow q,, p) \approx 1
$$

Während:

$$
P(\neg q \mid p \rightarrow q,, p) \approx 0
$$

→ Logische Regeln erscheinen als **hochgradig asymmetrische bedingte Wahrscheinlichkeiten**

---

# 4. Approximation von Inferenzregeln

Das Modell approximiert:

$$
P_\theta(q \mid p \rightarrow q,, p)
$$

Wenn die Daten konsistent sind, konvergiert:

$$
P_\theta(q \mid \cdot) \to 1
$$

Damit entsteht funktional:

$$
(p \rightarrow q), p ;\Rightarrow; \text{hohe Wahrscheinlichkeit für } q
$$

Das ist **formal keine Ableitung**, aber:

> eine probabilistische Approximation der Inferenzrelation (\vdash)

---

# 5. Rolle der Repräsentationen

Im Transformer (Transformer Architecture) werden Tokens auf Vektoren abgebildet:

$$
x_i \mapsto h_i \in \mathbb{R}^d
$$

Selbstaufmerksamkeit (Attention Mechanism) erzeugt:

$$
h_i^{(l+1)} = \sum_j \alpha_{ij} W_V h_j^{(l)}
$$

Diese Vektoren kodieren:

* syntaktische Muster
* semantische Ähnlichkeiten (implizit)
* logische Rollen (nur statistisch)

---

# 6. Entstehung latenter „logischer Features“

Unter geeigneten Bedingungen entstehen lineare Strukturen:

$$
h \approx \sum_k \lambda_k \phi_k
$$

wobei einige $$\phi_k$$ interpretierbar sind als:

* „Implikation“
* „Negation“
* „Quantifikation“ (rudimentär)

Diese sind jedoch:

* nicht explizit symbolisch
* nicht garantiert korrekt
* nicht invariant

---

# 7. Bedingung für logikähnliches Verhalten

Das Verhalten wird gut approximiert, wenn:

### (1) Datenkonsistenz

$$
\forall \Gamma,\varphi: \Gamma \vdash \varphi \Rightarrow P_D(\varphi \mid \Gamma) \approx 1
$$

### (2) Redundanz

Viele verschiedene Formulierungen derselben Regel existieren:

$$
\text{Paraphrasen}(\Gamma \vdash \varphi)
$$

### (3) Lokale Ableitbarkeit

Die Ableitung ist in kurzer Distanz darstellbar:

$$
|\Gamma| \ll L
$$

(Kontextfenster)

---

# 8. Grenzfall: Idealisierte Konvergenz

Angenommen:

* unendliche Daten
* perfektes Modell
* konsistente Logik im Korpus

Dann:

$$
P_\theta(\varphi \mid \Gamma) =
\begin{cases}
1 & \text{falls } \Gamma \vdash \varphi \
0 & \text{sonst}
\end{cases}
$$

Das wäre eine **probabilistische Repräsentation der logischen Konsequenzrelation**.

Aber:

> Diese Gleichheit ist extrem instabil und in realen Systemen nie exakt erfüllt.

---

# 9. Warum die Approximation bricht

## 9.1 Verteilungsverschiebung

Wenn Eingaben außerhalb des Trainings liegen:

$$
x \not\sim D
$$

→ keine Garantie für logisches Verhalten

---

## 9.2 Kombinatorische Explosion

Logik wächst exponentiell:

$$
|\text{Formeln}| \sim 2^n
$$

Trainingsdaten wachsen nur polynomial.

→ unvollständige Abdeckung

---

## 9.3 Fehlende Kompositionalität

Ein echtes logisches System erfüllt:

$$
\lbrack\!\lbrack f(g(x)) \rbrack\!\rbrack = F(\lbrack\!\lbrack g(x) \rbrack\!\rbrack)
$$

Ein Sprachmodell approximiert:

$$
f_\theta(g_\theta(x))
$$

ohne Garantie, dass diese Struktur erhalten bleibt.

---

## 10. Interpretation als Projektion

Man kann das Modell als Projektion verstehen:

$$
\vdash ;;\longrightarrow;; P_\theta(\cdot \mid \cdot)
$$

Dabei gilt:

* Logik: diskret, exakt
* Modell: kontinuierlich, approximativ

---

# 11. Verbindung zur Informationstheorie

Das Modell lernt:

$$
\max I(x_t; x_{< t})
$$

Wenn logische Strukturen stark informativ sind:

$$
I(\varphi; \Gamma) \text{ hoch}
$$

→ werden sie gut approximiert

---

# 12. Emergenz-These (präzise formuliert)

„Logikähnliches Verhalten“ entsteht, wenn:

> logische Relationen als hochstabile statistische Regularitäten in der Datenverteilung kodiert sind und vom Modell approximiert werden.

---

# 13. Fazit

Ein Sprachmodell ist kein logisches System, sondern:

$$
\text{ein Approximationoperator für } P(\text{Text})
$$

Logik erscheint darin als Spezialfall:

$$
\vdash ;\approx; \arg\max P_\theta(\cdot \mid \cdot)
$$

---

# 14. Zusammenfassung in einem Satz

> Ein Transformer führt keine Schlüsse aus – er approximiert die Wahrscheinlichkeit, dass ein Mensch an dieser Stelle einen gültigen Schluss formulieren würde.

---

