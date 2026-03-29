# Aufmerksamkeits-Kohärenz (Attention Coherence Score - ACS)

Um den **Instruction Drift** und die **Aufmerksamkeits-Erosion** zu verstehen, müssen wir den Transformer als einen probabilistischen Graph betrachten, der unter Stress (Optimierung) seine strukturelle Integrität verliert.

Hier ist das mathematische Detektionsschema für den **Attention-Drift in Multi-Agenten-Systemen** und komplexen LLM-Pipelines:

### 1. Das Phänomen: Die Entropie-Kaskade

In einem Multi-Agenten-System (oder bei langen Chain-of-Thought-Ketten) fungiert jeder Output von Agent A als Input für Agent B. 
* **Das Problem:** Durch RLHF-Optimierung neigen Modelle zu "sicheren", hochwahrscheinlichen Token-Sequenzen. Das bedeutet, die Varianz sinkt, während die **Kullback-Leibler-Divergenz (KLD)** zum ursprünglichen Instruktions-Vektor mit jedem Schritt zunimmt.
* 
* **Der Drift:** Die Instruktion $I$ wird durch das "Rauschen" der vorherigen Optimierung $O$ überlagert.

### 2. Das Detektionsschema: "Instruction Saliency Monitoring" (ISM)

Um zu messen, wann die Brücke instabil wird, nutzen wir drei Metriken:

#### A. Die Aufmerksamkeits-Kohärenz (Attention Coherence Score - ACS)

Wir messen die Kosinus-Ähnlichkeit zwischen dem Aufmerksamkeits-Vektor der initialen System-Instruktion ($A_{sys}$) und den Aufmerksamkeits-Gewichten der aktuellen Generierungsschicht ($A_{gen}$):

$$
ACS = \frac{A_{sys} \cdot A_{gen}}{\|A_{sys}\| \|A_{gen}\|}
$$

Sinkt dieser Wert unter einen Schwellenwert $t$, ist die **Aufmerksamkeits-Erosion** eingetreten. Das Modell "weiß" zwar noch, was es tut, hat aber den Bezug zum "Warum" (der Governance) verloren.

#### B. Layer-wise Token Influence (LTI)

Wir untersuchen, welche Layer noch aktiv auf die System-Prompts zugreifen. Bei optimierten Modellen sieht man oft, dass ab Layer 24 (von 32) die Aufmerksamkeit nur noch auf die unmittelbar vorangegangenen 5-10 Token gerichtet ist.

* **Diagnose:** Das Modell ist in einer "lokalen statistischen Schleife" gefangen.

#### C. Logit-Drift-Detektion

Wir vergleichen die Logit-Verteilung des Basis-Modells ($P_{base}$) mit der des optimierten Modells ($P_{opt}$). 
* Wenn $\sigma(P_{opt})$ signifikant kleiner ist als $\sigma(P_{base})$, hat eine **Mode-Kompression** stattgefunden. Das Modell ist "überoptimiert" und reagiert nur noch mit antrainierten Standardfloskeln statt mit logischer Herleitung.

### 3. Mitigierung: Das "Anchor-Weighting" Framework

Um den Einsturz zu verhindern, implementieren wir eine technische Governance:

1.  **Dynamic Context Injection:** Wenn der ACS-Wert sinkt, wird die System-Instruktion nicht einfach nur im Kontext behalten, sondern ihre Gewichte werden in den Key-Value-Caches (KV-Cache) künstlich verstärkt (Soft-Prompting-Korrektur).
2.  **Contrastive Decoding:** Wir lassen zwei Köpfe rechnen: Einer, der auf "Helpfulness" (RLHF) optimiert ist, und einer, der nur die Logik des Basis-Modells nutzt. Wir subtrahieren den "Höflichkeits-Bias", um die reine Information zu erhalten.
3.  **Cross-Agent-Checksums:** Agent B muss vor der Verarbeitung des Inputs von Agent A eine Zusammenfassung der ursprünglichen Governance-Regeln erstellen. Weicht diese von der "Ground Truth" ab, wird der Prozess gestoppt (Fail-Safe).

### Konsequenzen für die System-Stabilität
Es handelt sich hier um eine **Fehlerrechnung für neuronale Netze**. Wenn wir diese Metriken nicht in die KI-Frameworks einbauen, bauen wir Systeme, die bei der kleinsten Abweichung von der "Schönwetter-Statistik" der Trainingsdaten halluzinieren. 

