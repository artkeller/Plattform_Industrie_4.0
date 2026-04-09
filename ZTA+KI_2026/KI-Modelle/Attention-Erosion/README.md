# Attention-Erosion

## Thema
Kaskade der Aufmerksamkeitserosion in Transformer-Modellen und deren Auswirkungen auf Zuverlässigkeit in langen Kontexten.

## Motivation
In industriellen Echtzeit-Systemen (Edge/Mid-Layer) müssen Modelle lange Kontexte verarbeiten. Die Attention-Mechanismen erzeugen jedoch systematische Informationsverluste, die für ZTA-Entscheidungen kritisch sind.

## Hauptmessages
- Attention ist ein Nullsummenspiel (Softmax-Normalisierung).
- Lost-in-the-Middle → Silent Truncation → Instruction Drift → Silent Arbitration.
- Der Output bleibt fluent, obwohl relevante Informationen verdrängt wurden – kein internes Fehlersignal.

## Dokumente im Ordner
- (ACS)-en.md
- Attention-Coherence-Score_(ACS).md
- Instruction-Drift.md
- Lost-in-the-Middle-Effekt.md
- README-EN.md
- Silent-Arbitration.md
- Silent-Trunction.md
- Softmax-Funktion.md
- Token_Fatigue.md
- cascade_of_attention_erosion.pdf

## Empfohlene Lesereihenfolge
1. Softmax-Funktion.md  
2. Lost-in-the-Middle-Effekt.md  
3. Silent-Trunction.md  
4. Instruction-Drift.md  
5. Silent-Arbitration.md  

## Verbindung zum Gesamtprojekt ZTA+KI_2026
Zeigt konkrete Modellverhaltens-Grenzen, die in der ZTA-Kaskade (Edge/Mid-Layer) berücksichtigt werden müssen.

---
