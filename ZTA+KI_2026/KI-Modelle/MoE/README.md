# MoE (Mixture of Experts)

## Thema
Mixture-of-Experts-Architekturen und deren Komponenten im Kontext von skalierbaren, effizienten KI-Modellen für ZTA + Industrie 4.0.

## Motivation
Industrie-4.0-Systeme benötigen latenzarme, ressourcenschonende Modelle, die gleichzeitig hohe Kapazität bieten. MoE-Architekturen ermöglichen dies durch selektive Aktivierung von Experten-Netzwerken – relevant für die Mid-Layer der ZTA-Kaskade.

## Hauptmessages
- Mixture-of-Experts zerlegt Feed-Forward-Netzwerke in spezialisierte Experten.
- Sparse-Mixture-of-Experts-Architecture und Top-k-Routing steuern die Experten-Aktivierung.
- Expert-Collapse ist eine bekannte Fehlermöglichkeit, die vermieden werden muss.
- Die Architektur ist zentral für effiziente Skalierung ohne vollständige Dense-Berechnung.

## Dokumente im Ordner
- Expert-Collapse.md
- Feed-Forward-Netzwerke-(FFN).md
- Mixture-of-Experts-(MoE).md
- Sparse-Mixture-of-Experts-Architecture.md
- Top-k-Routing.md

## Empfohlene Lesereihenfolge
1. Mixture-of-Experts-(MoE).md  
2. Feed-Forward-Netzwerke-(FFN).md  
3. Sparse-Mixture-of-Experts-Architecture.md  
4. Top-k-Routing.md  
5. Expert-Collapse.md  

## Verbindung zum Gesamtprojekt ZTA+KI_2026
Stellt die Architektur-Bausteine für die Mid-Layer der ZTA-Kaskade bereit (Stufe 2: Small LLM / MoE) und ergänzt damit SLM sowie die Semantik- und Attention-Erosion-Betrachtungen.
Vorgesehener Platz für MoE-spezifische Architekturentscheidungen (siehe ZTA-Kaskade).
