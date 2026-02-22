# ZTA+KI 2026

Zero Trust Architektur mit KI-Assistenz in Industrie 4.0

**Plattform Industrie 4.0 – Unterarbeitsgruppe „KI für I40-Security“**  
**Update 2026 – Perspektiven durch den Einsatz generativer KI und Zero Trust**

Dieser Zweig enthält die komplette Dokumentation, Forschung und Prompt-Engineering-Arbeiten zum Thema **Zero Trust Architektur (ZTA) kombiniert mit Künstlicher Intelligenz** im Industrie-4.0-Kontext (Stand Februar 2026).

Ziel ist eine **auditierbare, EU-AI-Act-konforme und praxistaugliche Blaupause** für KI-gestützte Sicherheits- und Governance-Lösungen in OT-Umgebungen – speziell auch für kleine und mittlere Unternehmen (KMU).

## Hintergrund & Motivation

Die Komplexität von Industrie-4.0-Netzwerken (globale Lieferketten, OT/IT-Konvergenz, steigende Angriffsflächen) macht klassische Perimeter-Sicherheit obsolet. **Zero Trust** wird zwingend notwendig. Gleichzeitig hat sich seit 2023/24 der KI-Markt radikal verändert: Generative Modelle (LLMs) bieten neue Chancen für dynamische Richtlinien, Anomalie-Erkennung und Reasoning in Security-Kontexten.

Das Diskussionspapier der UAG „KI für I40-Security“ (Hannover Messe 2024) fokussierte noch auf klassische ML-Methoden (GNN etc.). Dieses Update 2026 berücksichtigt den Durchbruch generativer KI (GPT-ähnliche Modelle, DeepSeek R1/R2, Agentic AI, Reasoning-Fähigkeiten) und zeigt konkrete Wege zur Integration in ZTA – immer unter Einhaltung des **EU AI Act** (High-Risk-Anforderungen).

**Dokumentationsstrategie**  
- **Word-Dokument** (Hauptpublikation): Motivation, Prozess, Ergebniszusammenfassung, strategische Empfehlungen – schlank und lesbar  
- **GitHub (dieser Zweig)**: Detaillierte Umsetzung, Rohdaten, 30+ Seiten Prompt-Analysen, JSON-Aggregationen, Abweichungsdetektion – alles, was zu umfangreich fürs gedruckte Dokument ist

## Versionen im Überblick

### V1 – Ursprungsversion (/Compliance)
- Erste konzeptionelle Dokumente (2025–Anfang 2026)
- Governance, Policy, Module ZTA Teil 1–3 in Rohform
- Kompakt, teilweise stichpunktartig, ohne Evidenz-Spalten oder vollständiges SoA
- Gut als Einstieg, aber **nicht auditfähig**

→ [Zur V1-Dokumentation](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/Compliance)

### V2 – QA-gesicherte, finale Version (/Compliance/V2) ← **aktuell empfohlen**
- Stark erweitert (Februar 2026): vollständige Sätze, Evidenz-Nachweise, RACI, Risiko-Matrizen, KPIs, Lifecycle-View
- Detailliertes **Statement of Applicability (SoA)** mit allen 38 ISO 42001 Annex-A-Controls + IEC 62443 SRs
- Interaktive Mermaid-Diagramme, klickbare Referenzen, Audit-Readiness nahe 10/10
- **Dies ist die produktive, zitierfähige Version**

→ [Direkt zu V2](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/Compliance/V2)  
→ Zentrales Mapping: [SoA.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/SoA.md)

## Ordnerstruktur

- **/Compliance**  
  → V1 (ursprünglich) + **V2** (final, QA-gesichert)

- **/research**  
  → **Aktuell noch leer** – wird in den nächsten Wochen gefüllt  
  → Geplante Inhalte:  
    • EU-AI-Act-kompatible Prompt-Workflows (Domain-Pinning, strukturierter JSON-Output, Guardrails)  
    • Vollständige Prompt-Ketten (Use Case SAP Security + weitere)  
    • Roh-JSON-Antworten mehrerer LLMs + Aggregation + Abweichungsanalysen  
    • Vergleich: Halluzinationsrate, Reasoning-Qualität, Robustheit  
    • Mixture-of-Experts-Steuerung durch Domain- & Context-Prompts  
    • Test-Datensätze / RAG-Beispiele (falls Open Source möglich)

## EU-AI-Act-kompatible Prompt-Strategie (Kurzüberblick)

Im Projekt wurde eine **Workflow-basierte Prompt-Engineering-Methode** entwickelt, die LLM-Ausgaben

- **nachvollziehbar**, **strukturiert** und **konform** mit EU AI Act Art. 9–15 macht  
- **Guardrails** einbaut (z. B. „bei Unbekannt → ObjectKnown: false“)  
- **JSON-only-Output** erzwingt (CriticalityScore 0–10, Recommendation max. 500 Bytes usw.)  
- **Domain-Expertise aktiviert** (z. B. „Domain: SAP Security“ → Mixture-of-Experts)  
- **Multi-Step-Aggregation** ermöglicht (mehrere Aufrufe → Konsens + Abweichungsdetektion)

**Wo findest du die Details?**  
- Motivation, Prozess und Ergebniszusammenfassung → im **Hauptdokument (Word/PDF)**  
- Rohdaten, vollständige Prompts, 30+ Seiten JSON-Analysen → kommen bald in **/research** (derzeit leer)

## Wie du startest (3 Minuten)

1. **Strategischer Einstieg** → [Data-_und_AI-Governance.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Data-_und_AI-Governance.md)  
   (Warum? Rollen, Risikoklassifizierung, EU AI Act)

2. **Verbindliche Regeln** → [Policy.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Policy.md)  
   (Was? Prinzipien, Zugriff, Monitoring)

3. **Technische Tiefe** → [Modul_ZTA_Teil_1.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Modul_ZTA_Teil_1.md)  
   (Wie? Vollständiger Katalog ZTA-01 bis ZTA-15 + SoA)

4. **Audit & Mapping** → [SoA.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/SoA.md)  
   (38 Controls ISO 42001 + IEC 62443)

Feedback, Issues und Pull Requests sind ausdrücklich willkommen – dieses Projekt ist als offene Blaupause gedacht.

---
**Letztes Update:** 22. Februar 2026
