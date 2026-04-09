## **Titel**  
Kaskade der Aufmerksamkeitserosion in Transformer-Modellen: Mechanismen und Implikationen für zuverlässige Entscheidungsfindung in Zero-Trust-Architekturen

## **Abstract**  
Transformer-basierte Large Language Models leiden unter systematischer Degradation der Aufmerksamkeitsmechanismen bei langen Kontexten, bekannt als Attention-Erosion. Der zentrale Mechanismus ist die Softmax-Funktion 

$$
\text{softmax}(z_i) = \frac{e^{z_i}}{\sum_{j} e^{z_j}},
$$ 

die exponentiell große Logits verstärkt und zu einem „Winner-takes-most“-Verhalten führt. Mit zunehmender Sequenzlänge kumulieren mehrere Effekte: Lost-in-the-Middle (Mittelpositionen werden ignoriert), Silent Truncation, Instruction Drift und Silent Arbitration. Diese führen dazu, dass das Modell fluent wirkende Ausgaben produziert, obwohl kritische Informationen verdrängt oder ignoriert wurden – ohne internes Fehlersignal.

Zusätzliche Phänomene wie Token Fatigue und abnehmende Attention-Coherence-Score (ACS) verstärken die Erosion. Im industriellen Kontext von Industrie 4.0 und Zero Trust Architecture (ZTA) birgt dies erhebliche Risiken für Edge- und Mid-Layer-Entscheidungen, bei denen lange Kontexte (Logs, Prozesshistorien, Policies) verarbeitet werden müssen. Die Erosion untergräbt die erforderliche Nachvollziehbarkeit und Verlässlichkeit von KI-gestützten ZTA-Verifikationen.

Die Dokumentation schlägt die Messung mittels Attention-Coherence-Score und explizite Gegenmaßnahmen (Hybride-Architekturen, Semantik-Overlay) vor, um die Grenzen reiner statistischer Approximation sichtbar zu machen.

### **Schlüsselwörter:** 
Attention-Erosion, Softmax, Lost-in-the-Middle, Instruction Drift, Token Fatigue, Transformer, Zero Trust Architecture, Industrie 4.0
