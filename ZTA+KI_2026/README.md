# ZTA+KI 2026 – Zero Trust Architektur mit KI-Assistenz in Industrie 4.0

**Plattform Industrie 4.0 – Initiative für sichere, konforme und resiliente OT/IT-Konvergenz**

Dieser Zweig enthält die gesamte Dokumentation, Recherche und Prompt-Engineering-Arbeiten zum Thema **Zero Trust Architektur (ZTA) kombiniert mit Künstlicher Intelligenz** im Kontext von Industrie 4.0 (Stand Februar 2026).

Ziel ist die Entwicklung einer auditierbaren, regulatorisch konformen (EU AI Act, ISO/IEC 42001, IEC 62443, NIST SP 800-207) und praxistauglichen Blaupause für KI-gestützte Sicherheits- und Governance-Lösungen in OT-Umgebungen.

## Aktueller Stand – V1 vs. V2

### Version 1 (V1) – Ursprungsversion (im Ordner `/Compliance`)
- Erste konzeptionelle Dokumente (2025–Anfang 2026)
- Governance, Policy und drei Module ZTA Teil 1–3 in Rohform
- Sehr kompakt, teilweise stichpunktartig, ohne Evidenz-Spalten, ohne vollständiges SoA-Mapping
- Gut als Einstieg und Proof-of-Concept, aber **nicht auditfähig**

→ Pfad: [`/Compliance`](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/Compliance)

### Version 2 (V2) – QA-gesicherte, finale Version (aktuell empfohlen)
- Stark erweitert und operationalisiert (Februar 2026)
- Vollständige Sätze, Evidenz-Nachweis-Spalten, RACI-Matrizen, Risiko-Tabellen, KPIs, Lifecycle-View
- Detailliertes **Statement of Applicability (SoA)** mit allen 38 Controls aus ISO/IEC 42001 Annex A + IEC 62443 SRs
- Interaktive Mermaid-Diagramme, klickbare Referenzen, Audit-Readiness nahe 10/10
- Ordner `/Compliance/V2` ist **die aktuelle produktive Version**

→ Empfohlener Einstieg: [`/Compliance/V2`](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/Compliance/V2)  
→ Zentrales Mapping-Dokument: [`SoA.md`](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/SoA.md)

## Ordner-Übersicht

- **/Compliance**  
  → V1 (ursprüngliche Dateien) + **V2** (aktuelle, QA-gesicherte Version)

- **/research**  
  → **Noch leer** – wird in den nächsten Wochen gefüllt  
  → Geplante Inhalte:  
    • Prompt-Engineering-Workflows (EU-AI-Act-kompatibel)  
    • Test-Prompts und Antwort-Analysen (JSON-Aggregation, Abweichungsdetektion)  
    • Mixture-of-Experts-Steuerung und Domain-Prompting (z. B. SAP Security)  
    • Vergleich verschiedener LLM-Provider (Output-Qualität, Halluzinationsrate, Robustheit)  
    • Datensätze für Fine-Tuning / RAG (falls Open Source möglich)

## EU-AI-Act-kompatible Prompt-Strategie (Workflow-Basis)

Im Rahmen dieses Projekts wurde eine **systematische Prompt-Engineering-Methode** entwickelt, die sicherstellt, dass LLM-Ausgaben

- nachvollziehbar,  
- reproduzierbar,  
- risikobewusst und  
- konform mit Art. 9–15 EU AI Act (High-Risk-Anforderungen)  

sind.

**Kernprinzipien der Strategie** (detailliert im Word-Dokument beschrieben):

1. **Domain- & Context-Pinning**  
   Jeder Prompt beginnt mit einer klaren Domänen- und Kontext-Angabe (z. B. „Domain: SAP Security“) → aktiviert spezialisierte Mixture-of-Experts-Pfade im LLM

2. **Strukturierter JSON-Output**  
   Antworten werden strikt auf vordefinierte Attribute (CriticalityScore, Recommendation, CriticalityReason, OtherInformation usw.) beschränkt → keine freie Prosa außerhalb des Schemas

3. **Guardrails & Fail-safes**  
   - „Wenn unbekannt → ObjectKnown: false“  
   - Maximale Byte-Limits pro Feld (z. B. 500 Bytes)  
   - Explizite Negation von Halluzinationen

4. **Multi-Step-Aggregation & Abweichungsdetektion**  
   Mehrere LLM-Aufrufe → Aggregation → Erkennung von Inkonsistenzen (CriticalityScore-Abweichung, unterschiedliche Recommendations)

**Wo findest du die Details?**

- **Motivation, Prozessbeschreibung und Ergebniszusammenfassung** → im Hauptdokument (Word/PDF)  
- **Rohdaten, vollständige Prompt-Ketten, JSON-Antworten, Abweichungsanalysen (30+ Seiten)** → kommen in Kürze in den Ordner `/research/prompt-engineering`  
  (aktuell noch leer – wird in den nächsten Tagen/Wochen hochgeladen)

## Wie weiter?

- **Kurzfristig** → `/Compliance/V2` als Referenz nutzen (SoA.md + Module)  
- **Mittelfristig** → `/research` füllt sich mit Prompt-Material, Testdaten und Analysen  
- **Langfristig** → Integration in reale SAP-/OT-Umgebungen + Veröffentlichung von Open-Source-Komponenten (falls möglich)

Feedback, Issues und Pull Requests sind ausdrücklich erwünscht – dieses Projekt ist als kollaborative Blaupause gedacht.

---
Letztes Update: 22. Februar 2026
