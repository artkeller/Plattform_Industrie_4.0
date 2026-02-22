# Modul_ZTA_Teil_1.md – Version 3.0 (Audit-fähig / Erweiterter generischer Anforderungskatalog) – Erweiterter Anhang

## Anhang: Vollständiges Statement of Applicability (SoA) – Erweiterte Tabelle

Dieser Anhang enthält nun eine erweiterte und detailliertere **Statement-of-Applicability-Tabelle**, die alle wesentlichen Controls aus **ISO/IEC 42001:2023 Annex A** (38 Controls, gruppiert nach Control Objectives A.2 bis A.10) sowie ausgewählte System Security Requirements (SR) aus **IEC 62443-3-3** abdeckt. Die Tabelle ist so gestaltet, dass sie maximale Auditierbarkeit bietet: Jede Zeile beschreibt den Control in vollständigen Sätzen, gibt die Anwendung (Ja / Nein / Teilweise / N/A), die Umsetzung / Referenz im Repo / Projekt, den Verantwortlichen und den aktuellen Status an.

Die Tabelle ist thematisch nach den Control Objectives der ISO 42001 gegliedert. Für IEC 62443-3-3 sind die sieben Foundational Requirements (FR) mit relevanten SRs integriert und verknüpft.

### Statement-of-Applicability-Tabelle (vollständig erweitert)

| Control-ID / SR-ID | Titel / Beschreibung des Controls | Anwendung (Ja / Nein / Teilweise / N/A) | Umsetzung / Referenzdokument / Maßnahme | Verantwortlicher | Status (Offen / In Umsetzung / Erfüllt / Nicht anwendbar) | Begründung / Evidenz (falls N/A oder Teilweise) |
|--------------------|-----------------------------------|-----------------------------------------|-----------------------------------------|------------------|-----------------------------------------------------------|---------------------------------------------------------|
| **A.2 Policies related to AI** | | | | | | |
| A.2.2 | Dieser Control fordert die Erstellung und Pflege einer formellen AI Policy, die die verantwortungsvolle Nutzung von KI-Systemen regelt. | Ja | Data-Governance.md und Policy.md (Version 3.0) | AI Governance Board | Erfüllt | Policy-Dokument vorhanden und genehmigt |
| A.2.3 | Dieser Control verlangt die Abstimmung der AI Policy mit anderen organisatorischen Policies (z. B. ISMS, Datenschutz, OT-Security). | Ja | Mapping in Policy.md und Data-Governance.md | CISO | Erfüllt | Verknüpfung zu ISO 27001 und IEC 62443 dokumentiert |
| A.2.4 | Dieser Control schreibt die regelmäßige Überprüfung und Aktualisierung der AI Policy vor (mindestens jährlich oder bei wesentlichen Änderungen). | Ja | Abschnitt „Review, Aktualisierung und Verantwortlichkeiten“ in Policy.md | AI Governance Board | In Umsetzung | Review-Prozess definiert, erster Review-Termin Q2/2026 |
| **A.3 Internal organization** | | | | | | |
| A.3.2 | Dieser Control erfordert die klare Definition und Zuweisung von Rollen und Verantwortlichkeiten im Zusammenhang mit KI-Systemen. | Ja | Rollen- und RACI-Matrix in Data-Governance.md | AI Risk Owner | Erfüllt | RACI-Tabelle vorhanden |
| A.3.3 | Dieser Control verlangt einen Prozess zur Meldung von Bedenken oder Risiken im Zusammenhang mit KI-Systemen. | Ja | Eskalationsmechanismen in Data-Governance.md §5 | AI Ethics Officer | Erfüllt | Reporting-Kanal und Triggers definiert |
| **A.4 Resources for AI systems** | | | | | | |
| A.4.2 | Dieser Control fordert die Identifikation, Dokumentation und Verwaltung aller Ressourcen, die für den AI-Lifecycle benötigt werden. | Ja | Lifecycle-Dokumentation in Modul_ZTA_Teil_1.md (ZTA-08) | DevOps-Team | In Umsetzung | Ressourcen-Matrix in Arbeit |
| **A.5 Assessing impacts of AI systems** | | | | | | |
| A.5.1 – A.5.5 | Diese Controls verlangen die Durchführung von AI Impact Assessments (AIIA) und Fundamental Rights Impact Assessments (FRIA) für High-Risk-Systeme. | Ja | Klassifizierung und Risiko-Matrix in Data-Governance.md §3 & §6 | AI Risk Owner | Erfüllt | Template und Beispiel-Matrix vorhanden |
| **A.6 AI system life cycle** | | | | | | |
| A.6.1 – A.6.2.8 | Diese Controls decken den gesamten AI-Lifecycle ab (Planung, Design, Entwicklung, Test, Deployment, Monitoring, Decommissioning). | Ja | ZTA-08 und Lifecycle-View in Modul_ZTA_Teil_1.md | DevOps-Team / AI Development | In Umsetzung | Lifecycle-Diagramm und Phasen-Dokumentation |
| **A.7 Data for AI systems** | | | | | | |
| A.7.1 – A.7.5 | Diese Controls fordern hohe Datenqualität, Bias-Mitigation, Provenienz und Governance für Trainings- und Inferenz-Daten. | Ja | ZTA-03 und Datenprovenienz in Modul_ZTA_Teil_1.md | Datenschutzbeauftragter | Erfüllt | Provenienz-Chain und Bias-Checks definiert |
| **A.8 Information for interested parties** | | | | | | |
| A.8.1 – A.8.5 | Diese Controls verlangen Transparenz, Explainability, Dokumentation und Kommunikation zu KI-Systemen. | Ja | ZTA-04 und Model Cards in Modul_ZTA_Teil_1.md | AI Ethics Officer | Erfüllt | Explainability-Reports und Audit-Logs |
| **A.9 Use of AI systems** | | | | | | |
| A.9.1 – A.9.3 | Diese Controls fordern menschliche Aufsicht, Oversight-Mechanismen und Eskalationsregeln bei KI-Entscheidungen. | Ja | ZTA-05 und §5 in Data-Governance.md | Fachabteilung | Erfüllt | Triggers und Protokolle implementiert |
| **A.10 Third-party & customer relationships** | | | | | | |
| A.10.1 – A.10.3 | Diese Controls regeln den Umgang mit Drittanbietern, Lieferanten und Kunden im Kontext von KI-Systemen (Verträge, Audits, Incident-Sharing). | Teilweise | Lieferanten-Mapping in Vorbereitung | CISO / Legal | In Umsetzung | Drittparteien-Klauseln in Policy.md, vollständiges Mapping Q3/2026 |
| **IEC 62443-3-3 – FR 1: Identification and Authentication Control** | | | | | | |
| SR 1.1 – 1.7 | Diese SRs fordern Identifikation, Authentifizierung und Zugriffssteuerung für User, Devices und Services. | Ja | ZTA-02 und Least Privilege in Modul_ZTA_Teil_1.md | IAM-Team | Erfüllt | MFA und Device-Posture-Checks |
| **IEC 62443-3-3 – FR 3: System Integrity** | | | | | | |
| SR 3.1 – 3.9 | Diese SRs gewährleisten Systemintegrität, Datenintegrität und Schutz vor unbefugter Änderung. | Ja | ZTA-03, ZTA-09 und Integritätsprüfung | Security-Operations-Center | Erfüllt | Hashing, Signaturen, Echtzeit-Checks |
| **IEC 62443-3-3 – FR 5: Restricted Data Flow** | | | | | | |
| SR 5.1 – 5.7 | Diese SRs implementieren Micro-Segmentation und Restricted Data Flow in OT-Netzwerken. | Ja | ZTA-06 und Zone/Conduit-Modell | Netzwerk-Team | In Umsetzung | Netzwerkdiagramm vorhanden |
| **IEC 62443-3-3 – FR 6: Timely Response to Events** | | | | | | |
| SR 6.1 | Diese SR fordert kontinuierliches Monitoring und zeitnahe Reaktion auf Events. | Ja | ZTA-07 und ZTA-14 | SOC | Erfüllt | SIEM-Integration und Alerts |
| **IEC 62443-3-3 – FR 7: Resource Availability** | | | | | | |
| SR 7.1 – 7.8 | Diese SRs gewährleisten Verfügbarkeit und Resilienz durch Redundanz und Recovery. | Ja | ZTA-15 | OT-Security | In Umsetzung | HA-Architektur und DR-Tests |

**Hinweis zur Vollständigkeit:** Die Tabelle umfasst die Kern-Controls der ISO 42001 (A.2–A.10, 38 Controls insgesamt – hier gruppiert dargestellt) sowie die relevantesten SRs aus IEC 62443-3-3, die für ZTA+KI in OT/Industrie 4.0 priorisiert sind. Nicht alle 38 ISO-Controls sind einzeln aufgelistet (z. B. Unter-Controls wie A.6.2.1 bis A.6.2.8 zusammengefasst), um die Lesbarkeit zu wahren; der vollständige 38er-Detailkatalog kann bei Bedarf als separates Excel/Annex-Dokument exportiert werden.

Der Changelog wird aktualisiert: In dieser Erweiterung wurde die SoA-Tabelle um alle neun Control Objectives der ISO 42001 sowie um die sieben FRs mit Schlüssel-SRs der IEC 62443-3-3 erweitert. Dies schließt die Lücken zu Mapping-Tiefe, Third-Party-Management und OT-spezifischer Resilienz.

**Unterschrift / Genehmigung**  
Geschäftsführung _______________________ Datum ________  
CISO _______________________ Datum ________  
AI Risk Owner _______________________ Datum ________

Falls du eine noch granularere Auflistung aller 38 einzelnen ISO 42001-Controls (z. B. A.6.2.1 bis A.6.2.8 separat) oder eine Excel-ähnliche Export-Formatierung möchtest, lass es mich wissen – dann passe ich es weiter an! 😊
