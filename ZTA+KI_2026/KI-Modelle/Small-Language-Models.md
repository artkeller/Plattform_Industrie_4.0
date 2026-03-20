### Repräsentative Small Language Models (SLMs) und zugehörige Ausführungsumgebungen

(Stand März 2026)

| Kategorie                              | Modell / Tool                                      | Parameteranzahl | Entwickler / Anbieter     | Hauptanwendung / Stärken                                      | Lizenz / Verfügbarkeit          | Lokale / On-Premise-Ausführung |
|----------------------------------------|----------------------------------------------------|-----------------|---------------------------|-----------------------------------------------------------------------|---------------------------------|--------------------------------|
| **1. Open-Source Basis-Modelle**      | Microsoft Phi-3.5-mini / Phi-4-mini               | 3.8B            | Microsoft                 | Logisches Denken, Reasoning, Coding                                   | Open-Weights (MIT-ähnlich)     | Ja (Ollama, LM Studio, llama.cpp) |
|                                        | Meta Llama 3.1 / 3.2                              | 1B, 3B, 8B      | Meta                      | Gutes Größe-Intelligenz-Verhältnis, multilingual, Tool-Calling       | Llama License (kommerziell nutzbar) | Ja                             |
|                                        | Google Gemma 3                                    | 1B, 2B–4B       | Google DeepMind           | Geschwindigkeit, CPU-/Edge-freundlich, teilw. multimodal              | Open-Weights                   | Ja                             |
|                                        | Mistral Nemo                                      | 12B             | Mistral AI                | Hohe Leistung bei moderater Größe, lokale Anwendungen                 | Apache 2.0                     | Ja                             |
|                                        | Mistral 7B Instruct (ältere Generation)           | 7B              | Mistral AI                | Sehr populär für lokale / ressourcenarme Umgebungen                   | Apache 2.0                     | Ja                             |
|                                        | SmolLM2 / SmolLM3                                 | 1.7B            | Hugging Face              | Extrem kompakt, sehr ressourcenarme Geräte                            | Apache 2.0                     | Ja                             |
|                                        | Alibaba Qwen 2 / 2.5                              | 0.5B–7B         | Alibaba                   | Stark bei Coding, Mathematik, multilingual                            | Apache 2.0                     | Ja                             |
|                                        | DeepSeek R1 (Distill-Varianten)                   | 1.5B–7B         | DeepSeek AI               | Herausragend bei komplexen Reasoning-Aufgaben                         | Open-Weights                   | Ja                             |
| **2. Lokale Ausführungstools**        | Ollama                                            | –               | Ollama Team               | Einfachste lokale Ausführung (macOS, Linux, Windows), Modell-Management | Open-Source                    | Vollständig lokal / offline    |
|                                        | LM Studio                                         | –               | LM Studio                 | Desktop-GUI, einfaches Suchen/Herunterladen/Chat-Interface            | Freeware (mit Open-Source-Kern)| Vollständig lokal              |
|                                        | GPT4All                                           | –               | Nomic AI                  | Speziell für Consumer-Hardware (auch reine CPU), Open-Source-Client   | Open-Source                    | Vollständig lokal / offline    |
| **3. Kommerzielle / Proprietäre SLMs**| Mistral Small 3.1                                 | 24B             | Mistral AI                | Multimodal (Text + Vision), Alternative zu GPT-4o mini, 128k Context  | Open-Weights + API             | Ja (Open-Weights-Version)      |
|                                        | Microsoft Phi-3.5-Vision / Phi-4-multimodal       | ~3.8–5B         | Microsoft                 | Bild- und Video-Verstehen auf mobilen / Edge-Geräten                  | Open-Weights                   | Ja                             |
|                                        | ABBYY Marketplace-Lösungen                        | <10B (spezialisiert) | ABBYY                | Spezialisierte Modelle für Dokumentenverarbeitung & OCR               | Proprietär / Marketplace       | Ja (on-premise-fähig)          |

**Anmerkungen zur Tabelle:**

- Die Auswahl konzentriert sich auf Modelle und Tools, die typischerweise als **Small Language Models** (SLMs) klassifiziert werden (Parameterbereich überwiegend 1–24 Milliarden).
- Alle genannten **Open-Source-** und **Open-Weights-Modelle** sind vollständig lokal/on-premise ausführbar (z. B. via Ollama, LM Studio, vLLM, llama.cpp oder Hugging Face Transformers), was sie besonders für datenschutzsensible, latenzkritische oder kostensensitive Anwendungen attraktiv macht.
- Proprietäre Varianten (z. B. reine API-Modelle ohne Gewichte-Download) wurden bewusst ausgeschlossen; nur on-premise-fähige kommerzielle SLMs sind aufgeführt.
- Stand: März 2026. Die tatsächliche Leistung kann je nach Fine-Tuning, Quantisierung (z. B. 4-bit, 8-bit) und Hardware stark variieren.
