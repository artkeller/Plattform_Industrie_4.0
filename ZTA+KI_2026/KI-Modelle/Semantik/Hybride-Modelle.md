# 1. Ausgangspunkt: Defizit rein statistischer Modelle

Wie [gezeigt](Transformer.md), approximieren Sprachmodelle primär:

$$
P(x_t \mid x_{< t})
$$

Das führt zu:

* fehlender expliziter Semantik
* fehlender Inferenzstruktur
* fehlender Weltmodellbindung

Daraus entsteht die Motivation für **hybride Architekturen**.

---

# 2. Ziel hybrider Modelle

Ziel ist die Kombination von:

### (A) Subsymbolischer Komponente

* kontinuierliche Vektoren
* neuronale Netze (z. B. Transformer Architecture)
* robust gegen Rauschen, skalierbar

### (B) Symbolischer / semantischer Komponente

* explizite Relationen
* Graphstrukturen
* logiknahe Operationen

Formal:

$$
\text{Hybrid} = f_{\text{neural}} ;\oplus; f_{\text{symbolic}}
$$

---

# 3. Semantische Graphen

Ein semantischer Graph ist typischerweise:

$$
G = (V, E, R)
$$

mit:

* (V): Entitäten
* (E): Kanten
* (R): Relationstypen

Beispiel:

$$
(\text{Sokrates}, \text{ist}, \text{Mensch})
$$

Bekannte Instanzen sind **Knowledge Graphs** (Knowledge Graph).

---

# 4. Vektorisierung von Semantik

Um neuronale Modelle mit Graphen zu koppeln, werden diese eingebettet:

$$
\phi: V \cup R \rightarrow \mathbb{R}^d
$$

→ sogenannte **Embeddings**

Ziel:

$$
\phi(h) + \phi(r) \approx \phi(t)
$$

für Tripel ((h, r, t))

---

# 5. Beispiel: TransE-artige Modelle

Ein klassischer Ansatz:

$$
| \mathbf{h} + \mathbf{r} - \mathbf{t} | \approx 0
$$

Das bedeutet:

* Relationen werden als **Translationen im Vektorraum** modelliert
* Semantik wird geometrisch interpretiert

---

# 6. Integration in Sprachmodelle

## 6.1 Architekturprinzipien

### (1) Retrieval-Augmented Models

Externe Wissensbasis:

$$
\text{Kontext} = x_{< t} \cup \text{retrieve}(G)
$$

→ das Modell bekommt strukturierte Information zusätzlich

---

### (2) Joint Embedding Spaces

Text und Graph werden in denselben Raum projiziert:

$$
\phi_{\text{text}}(x) \approx \phi_{\text{graph}}(v)
$$

→ semantische Alignment-Bedingung

---

### (3) Graph Neural Networks

Graphstruktur wird direkt verarbeitet:

$$
h_v^{(k+1)} = \sigma\left( \sum_{u \in \mathcal{N}(v)} W h_u^{(k)} \right)
$$

(Graph Neural Network)

---

# 7. „Semantische Vektoren“ – präzise Bedeutung

Der Begriff ist unscharf, lässt sich aber formal fassen als:

$$
\mathbf{s} \in \mathbb{R}^d \quad \text{mit semantischen Invarianten}
$$

Eigenschaften:

* ähnliche Bedeutung → kleine Distanz
* Relationen → Transformationen
* Komposition → Vektoroperationen

Aber wichtig:

> Diese Vektoren sind keine Bedeutung selbst, sondern eine **metrische Approximation von Bedeutungsrelationen**.

---

# 8. Hybridisierung: mathematische Sicht

Ein hybrides System kann man schreiben als:

$$
y = f_\theta(x, G, \phi(G))
$$

wobei:

* (x): Text
* (G): Graphstruktur
* (\phi(G)): Vektorembedding des Graphen

---

# 9. Erwarteter Gewinn

## 9.1 Explizite Relationen

Graphen liefern:

$$
(\text{A} \rightarrow \text{B}) \in G
$$

→ nicht nur implizit gelernt

---

## 9.2 Bessere Generalisierung

Wenn:

$$
(\text{A}, r, \text{B}),; (\text{B}, r, \text{C})
$$

dann kann modelliert werden:

$$
(\text{A}, r, \text{C})
$$

→ strukturgetriebene Inferenz

---

## 9.3 Stabilere Semantik

Graphen sind:

* diskret
* explizit
* überprüfbar

---

# 10. Fundamentale Grenzen

Trotz Hybridisierung bleiben Probleme:

### 10.1 Symbol–Vektor-Gap

$$
\text{diskrete Lgik} ;\neq; \text{kontinuierlicher Raum}
$$

---

### 10.2 Unschärfe der Embeddings

$$
\mathbf{h} + \mathbf{r} \approx \mathbf{t}
$$

ist nur näherungsweise gültig

---

### 10.3 Skalierungsproblem

Große Graphen:

$$
|V| \to 10^9
$$

→ schwierig integrierbar

---

# 11. Forschungslinien

Aktuelle Richtungen:

* Neuro-symbolic AI (Neuro-symbolic AI)
* Differenzierbare Logik
* Program-of-Thought / Tool-Use
* Wissensaugmentierte Transformer

---

# 12. Präzises Fazit

Das Ziel ist nicht, „Verstehen einzubauen“, sondern:

> die Approximation $$P(\text{Text})$$ durch strukturelle Nebenbedingungen zu **regularisieren**

Formal:

$$
P_\theta(x_t \mid x_{< t}, G)
$$

mit zusätzlicher Nebenstruktur (G).

---

# 13. Kurzformel

Hybride Modelle versuchen:

$$
\text{Statistik} + \text{Struktur} \rightarrow \text{robustere Semantikapproximation}
$$

---

# 14. Was wir wirklich erhalten

Es bleibt bei [Approximation logikähnlichen Verhaltens](Approximation.md)

---
