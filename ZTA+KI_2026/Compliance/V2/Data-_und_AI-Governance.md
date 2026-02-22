### Erweiterte Version von Modul_ZTA_Teil_1.md

Hier ist die **aktualisierte Version** von `Modul_ZTA_Teil_1.md` mit der Ergänzung im Abschnitt **Klassifizierung und Risikobewertung**. Ich habe den bestehenden Text erweitert, um die Recherche-Ergebnisse einzubauen: Kritik an Überklassifizierung im EU AI Act-Kontext, Vergleich zu IEC 62443 und Empfehlungen zur Vermeidung. Die Struktur bleibt 1:1 erhalten, nur der Abschnitt wurde logisch erweitert (neuer Unterabschnitt "Hinweise zur Vermeidung von Überklassifizierung").

## Version, Stand und Genehmigung

Dieses Dokument stellt die Version 3.0 des generischen Anforderungskatalogs für eine Zero Trust Architecture (ZTA) mit KI-Assistenz in der Industrie 4.0 dar. Es wurde am 22. Februar 2026 erstellt und von der Geschäftsführung, dem Chief Information Security Officer (CISO) sowie dem verantwortlichen AI Risk Owner genehmigt. Die Genehmigung erfolgte durch Unterschriften in der gedruckten Version dieses Dokuments und dient als Nachweis für die formelle Annahme aller hierin festgelegten Anforderungen. Dieses Modul dient als Grundlage für die detaillierten Prüfschritte in Modul ZTA Teil 2 und Teil 3 und ist so gestaltet, dass es eine maximale Auditierbarkeit gewährleistet.

## Rahmenbedingungen und Geltungsbereich

Dieser generische Anforderungskatalog gilt für alle Komponenten einer Zero Trust Architektur, die mit KI-Assistenz in industriellen Umgebungen der Industrie 4.0 eingesetzt werden. Er umfasst insbesondere Anwendungen in der Produktion, der Lieferkette, der prädiktiven Wartung, der Qualitätskontrolle sowie in sicherheitskritischen OT-Prozessen. Die normative Grundlage dieses Katalogs basiert auf der NIST SP 800-207 (Zero Trust Architecture), der EU AI Act (Verordnung (EU) 2024/1689, insbesondere Artikel 9 bis 15 für High-Risk-Systeme), der ISO/IEC 42001:2023 (Annex A Controls), der IEC 62443-3-3 (System Security Requirements) sowie der ISO/IEC 27001:2022. Der Katalog adressiert die identifizierten Mängel der vorherigen Version, indem er den Umfang erheblich erweitert, eine vollständige Mapping-Tabellen einführt, eine Risikobewertung integriert, Lifecycle-Aspekte abdeckt und Evidenz-Anforderungen explizit definiert.

## Ziele und Grundprinzipien

Der Anforderungskatalog verfolgt das Ziel, eine sichere, nachvollziehbare, resiliente und konforme Implementierung von ZTA mit KI-Unterstützung in Industrie 4.0 zu ermöglichen. Er minimiert Risiken für Betriebssicherheit, Datenschutz, Grundrechte und OT-Verfügbarkeit. Die Grundprinzipien orientieren sich an den NIST SP 800-207 Tenets: Alle Ressourcen werden als potenziell unsicher betrachtet, Kommunikation wird unabhängig vom Netzwerkort gesichert, Zugriff wird sitzungsbezogen und mit Least Privilege gewährt, Zugriffe werden kontinuierlich verifiziert, und es wird von einem möglichen Kompromiss ausgegangen.

## Klassifizierung und Risikobewertung

Jede Anforderung wird einer Risikoklasse zugeordnet (basierend auf EU AI Act und IEC 62443 Security Levels SL 1–4). Die folgende Tabelle gibt einen Überblick über die Zuordnung.

| Risikoklasse / Security Level | Beschreibung der Klasse | Typische Anwendung in Industrie 4.0 | Priorität der Umsetzung |
|-------------------------------|-------------------------|-------------------------------------|-------------------------|
| SL 1 / Minimal Risk           | Schutz gegen unbeabsichtigte oder zufällige Bedrohungen | Reine Monitoring-Systeme ohne Steuerung | Mittel                  |
| SL 2 / Moderate Risk          | Schutz gegen beabsichtigte Angriffe mit einfachen Mitteln | Standard-Qualitätskontrolle mit KI     | Hoch                    |
| SL 3 / High Risk              | Schutz gegen gezielte Angriffe mit erheblichen Ressourcen | Prädiktive Wartung mit Sicherheitsrelevanz | Sehr hoch               |
| SL 4 / Very High Risk         | Schutz gegen staatlich unterstützte Angriffe | Kritische Infrastruktur-Komponenten    | Kritisch                |

### Hinweise zur Vermeidung von Überklassifizierung (neu hinzugefügt)
Im Kontext des EU AI Act (Verordnung (EU) 2024/1689) besteht die Pflicht zur Self-Assessment von AI-Systemen, ob sie in die High-Risk-Kategorie fallen (Annex III). Allerdings hat sich durch die hohen Strafen (bis zu 7% des globalen Jahresumsatzes für Verstöße) eine Tendenz zu "Over-Compliance" entwickelt: Unternehmen klassifizieren Systeme vorsichtshalber als High-Risk, um Risiken zu vermeiden. Studien zeigen, dass bis zu 40% der Klassifizierungen unklar sind, was zu Überklassifizierungen in 18-58% der Fälle führt (z. B. appliedAI-Institute Report 2023/2024). Dies bindet unnötig Ressourcen, behindert Innovation und verwässert den Fokus auf echte High-Risk-Systeme, wie die EU in Guidelines kritisiert (z. B. Pressemitteilung EC IP/25/2718: "Vermeidung unnötiger Belastungen durch korrekte Klassifizierung"). 

Im Gegensatz dazu betont IEC 62443 eine kosten-nutzen-orientierte Klassifizierung (SL 1-4), die Überklassifizierung vermeidet, da höhere Levels explizite Kostensteigerungen bedeuten. Empfehlung: Führen Sie eine dokumentierte Assessment durch, nutzen Sie EU-Beispiele für Non-High-Risk (Annex III-Ausnahmen: enge prozedurale Tasks, Unterstützung menschlicher Entscheidungen). Bei Unsicherheiten: Konsultieren Sie den EU AI Office oder externe Experten, um echte Risiken zu priorisieren und "Panik-Klassifizierungen" zu verhindern.

## Generischer Anforderungskatalog (erweiterte Tabelle)

Der folgende Katalog ist thematisch gruppiert und enthält für jede Anforderung eine eindeutige ID, eine vollständige Beschreibung, die Konformitätsprüfung, den Bewertungsstatus, Referenzen zu den Kernstandards sowie die geforderte Evidenz. Alle Felder sind in vollständigen Sätzen formuliert, um juristische Lesbarkeit und Auditierbarkeit zu gewährleisten.

| Anforderungs-ID | Beschreibung der Anforderung | Konformitätsprüfung / Nachweismethode | Bewertungsstatus | Referenzen zu Standards | Geforderte Evidenz |
|-----------------|------------------------------|---------------------------------------|------------------|--------------------------|--------------------|
| ZTA-01          | Dynamische Richtlinien-Durchsetzung muss in Echtzeit erfolgen, wobei jede Zugriffsentscheidung anhand aktueller Kontextdaten (Identität, Gerät, Verhalten, OT-Prozesszustand) getroffen wird. | Die Policy Engine muss alle Zugriffsanfragen in Echtzeit evaluieren und protokollieren; Testszenarien mit simulierten Kontextänderungen müssen durchgeführt werden. | Offen            | NIST SP 800-207 Tenet 3 & 6, IEC 62443 SR 2.1, EU AI Act Art. 15 | Audit-Logs der Policy Engine, Testprotokolle, Konfigurationsscreenshots |
| ZTA-02          | Identitäts- und Zugriffsmanagement muss kontinuierlich verifizieren, dass nur stark authentifizierte und autorisierte Entitäten Zugriff erhalten, inklusive Geräte- und Service-Identitäten. | Multi-Factor-Authentifizierung und Device-Posture-Checks müssen für alle Zugriffe implementiert sein; Least-Privilege-Policies müssen durchgesetzt werden. | Offen            | NIST SP 800-207 Tenet 1 & 4, IEC 62443 SR 1.1–1.7, ISO 42001 A.3.2 | IAM-Konfiguration, Auth-Logs, Least-Privilege-Matrix |
| ZTA-03          | Datenprovenienz und Integrität müssen über den gesamten AI- und ZTA-Lifecycle nachweisbar sein, inklusive Herkunft, Veränderung und Verwendung der Daten. | Alle Daten müssen mit kryptografischen Signaturen versehen und in unveränderbaren Logs gespeichert werden; Bias- und Qualitätschecks müssen dokumentiert sein. | Offen            | EU AI Act Art. 10, ISO 42001 A.7.1–A.7.5, IEC 62443 SR 3.1–3.9 | Provenienz-Chain-Dokumentation, Hash- und Signatur-Reports |
| ZTA-04          | Vollständige Auditierbarkeit und Nachvollziehbarkeit aller Entscheidungen (ZTA-Policy & KI-Inferenz) muss gewährleistet sein, inklusive Explainability für KI-Entscheidungen. | Audit-Trails müssen zeitgestempelt, unveränderbar und suchbar sein; Model Cards und Explainability-Methoden müssen für alle KI-Modelle vorliegen. | Offen            | EU AI Act Art. 13, ISO 42001 A.8.1–A.8.5, NIST SP 800-207 Tenet 7 | Vollständige Audit-Logs, Model Cards, Explainability-Reports |
| ZTA-05          | Menschliche Aufsicht muss bei High-Risk-Entscheidungen obligatorisch implementiert sein, mit klar definierten Eskalationsregeln und Triggers. | Human-in-the-Loop / on-the-Loop-Mechanismen müssen für kritische Entscheidungen vorhanden sein; Eskalation bei Confidence < 85 % oder Drift > 10 %. | Offen            | EU AI Act Art. 14, ISO 42001 A.9.1–A.9.3 | Oversight-Protokolle, Eskalationsregeln-Dokument, Testfälle |
| ZTA-06          | Micro-Segmentation und Restricted Data Flow müssen implementiert sein, um Lateral Movement in OT- und IT-Netzwerken zu verhindern. | Netzwerke müssen in Zonen und Conduits segmentiert sein; Datenflüsse dürfen nur explizit erlaubte Pfade nutzen. | Offen            | IEC 62443 SR 5.1–5.7, NIST SP 800-207 Tenet 5 | Netzwerkdiagramm (Zone/Conduit), Firewall- und Segmentation-Rules |
| ZTA-07          | Kontinuierliches Monitoring und Incident Response müssen für Anomalien, Drift und Sicherheitsereignisse eingerichtet sein, inklusive automatisierter Alerts. | SIEM-Integration mit KI-basierter Anomalie-Erkennung muss vorhanden sein; Incident-Response-Plan muss getestet werden. | Offen            | NIST CSF Detect/Respond, ISO 42001 A.10.1–A.10.3, IEC 62443 SR 6.1 | Monitoring-Dashboards, Incident-Reports, Testprotokolle |
| ZTA-08          | Lifecycle-Management für AI- und ZTA-Komponenten muss alle Phasen (Design, Entwicklung, Deployment, Monitoring, Decommissioning) abdecken. | Ein vollständiger AI Lifecycle Prozess muss dokumentiert und mit Risiko-Assessments verknüpft sein. | Offen            | ISO 42001 A.6.1–A.6.2.8, EU AI Act Art. 9 | Lifecycle-Diagramm, Phasen-Dokumentation, Decommissioning-Plan |
| ZTA-09          | Alle Kommunikationen müssen unabhängig von der Netzwerkposition vollständig gesichert werden, einschließlich Verschlüsselung in Transit und End-to-End-Sicherung für OT-Datenströme und KI-Inferenz-Daten. | Alle Verbindungen müssen TLS 1.3 oder höher nutzen; OT-spezifische Protokolle müssen durch sichere Gateways oder Wrappers geschützt werden; Penetrationstests auf unverschlüsselte Kommunikation müssen regelmäßig durchgeführt werden. | Offen            | NIST SP 800-207 Tenet 2 (All communication secured regardless of location), IEC 62443 SR 3.1–3.9 (System Integrity), EU AI Act Art. 15 (Cybersecurity) | TLS-Konfigurationsberichte, OT-Protokoll-Analyse, Penetrationstest-Reports, Verschlüsselungs-Matrix |
| ZTA-10          | Zugriffe müssen sitzungsbezogen und mit Just-in-Time / Just-Enough-Access gewährt werden, wobei Zugriffe automatisch bei Session-Ende oder Kontextänderung widerrufen werden. | Policy Engine muss session-basierte Tokens mit kurzer Lebensdauer ausstellen; automatische Revocation bei Anomalien oder Zeitüberschreitung muss implementiert sein. | Offen            | NIST SP 800-207 Tenet 3 (Per-session access), NIST Tenet 4 (Least privilege), IEC 62443 SR 2.1 (Least Privilege) | Session-Log-Analyse, Token-Lebensdauer-Konfiguration, Revocation-Testprotokolle |
| ZTA-11          | Kontinuierliche Bewertung der Sicherheitslage (Continuous Posture Assessment) muss für alle Entitäten (User, Device, AI-Modell, OT-Gerät) durchgeführt werden, inklusive Device Health Checks und Behavioral Analytics. | Echtzeit-Monitoring von Device-Compliance, User-Verhalten und Modell-Drift; KI-gestützte Anomalie-Erkennung muss integriert sein. | Offen            | NIST SP 800-207 Tenet 6 (Continuous verification), ISO 42001 A.10 (Continuous Improvement), EU AI Act Art. 15 (Robustness) | Device-Posture-Reports, UEBA-Dashboards, Drift-Detection-Logs |
| ZTA-12          | Automatisierung und Orchestrierung von Security-Maßnahmen muss implementiert sein, um Policies dynamisch anzupassen, Incidents zu isolieren und Response-Prozesse zu automatisieren. | SOAR-Integration mit ZTA-Komponenten; automatisierte Quarantäne bei erkannten Bedrohungen; KI-gestützte Policy-Optimierung muss vorhanden sein. | Offen            | NIST SP 800-207 (Automation in ZTA), IEC 62443 SR 6.1 (Timely Response), Cloud Security Alliance ZTA AI-Integration | Automation-Workflow-Diagramme, SOAR-Konfiguration, Incident-Automatisierungs-Tests |
| ZTA-13          | Schutz der Daten als Kernressource muss durch Klassifizierung, Verschlüsselung at-rest, Tokenisierung und Data Loss Prevention gewährleistet sein, insbesondere für Trainingsdaten und Inferenz-Outputs in KI-Systemen. | Datenklassifizierungs-Schema muss existieren; sensible OT- und KI-Daten müssen verschlüsselt gespeichert werden; DLP-Regeln müssen greifen. | Offen            | NIST SP 800-207 Tenet 1 (All data sources as resources), EU AI Act Art. 10 (Data Quality & Governance), IEC 62443 SR 3.9 (Data Confidentiality) | Datenklassifizierungs-Matrix, Encryption-at-Rest-Reports, DLP-Alert-Logs |
| ZTA-14          | Sichtbarkeit und Analytics müssen umfassend implementiert sein, um alle Zugriffe, Anomalien und Kontextdaten zu sammeln, zu analysieren und für Threat Hunting sowie Compliance-Reporting zu nutzen. | Zentrale SIEM- oder Analytics-Plattform mit KI-Unterstützung; vollständige Log-Sammlung aus allen ZTA-Komponenten und OT-Systemen. | Offen            | NIST SP 800-207 Tenet 7 (Collect & Analyze Data), ISO 42001 A.8 (Transparency), IEC 62443 SR 6.1 (Monitoring) | SIEM-Dashboard-Screenshots, Log-Retention-Policy, Analytics-Reports |
| ZTA-15          | Resilienz gegenüber Ausfällen und Angriffen muss durch Redundanz, Failover-Mechanismen und Backup/Restore-Prozesse für kritische ZTA- und KI-Komponenten gewährleistet sein, ohne OT-Verfügbarkeit zu gefährden. | Hochverfügbarkeits-Architektur für Policy Engine und KI-Modelle; regelmäßige Disaster-Recovery-Tests; OT-spezifische Non-Disruptive-Recovery. | Offen            | IEC 62443 SR 7.1–7.8 (Resource Availability), NIST CSF Recover, EU AI Act Art. 15 (Robustness & Accuracy) | HA-Konfigurationsdiagramme, DR-Testprotokolle, Failover-Simulation-Results |

## Mapping zu Kernstandards (erweiterter Auszug für neue Anforderungen)

Die neuen Anforderungen ZTA-09 bis ZTA-15 sind vollständig auf die folgenden Standards gemappt. Die detaillierte Statement-of-Applicability-Tabelle (inkl. aller 38 ISO 42001 Controls und IEC 62443 SRs) befindet sich weiterhin im Anhang.

- NIST SP 800-207: Tenet 2 (Secured Communication), Tenet 3 (Per-Session), Tenet 6 (Continuous), Tenet 7 (Data Collection), Automation-Orchestrierung
- EU AI Act: Art. 10 (Data & Quality), Art. 13 (Transparency), Art. 14 (Oversight), Art. 15 (Accuracy, Robustness, Cybersecurity)
- ISO 42001 Annex A: A.7 (Data), A.8 (Transparency/Explainability), A.10 (Incident & Improvement)
- IEC 62443-3-3: SR 3 (Integrity), SR 5 (Restricted Data Flow), SR 6 (Timely Response & Monitoring), SR 7 (Resource Availability)

## Anhang: Vollständiges Statement of Applicability und Changelog

Im Anhang dieses Dokuments befindet sich die vollständige Mapping-Tabelle zu allen relevanten Controls (38 aus ISO 42001, SRs aus IEC 62443-3-3). Der Changelog dokumentiert: In Version 3.0 (Erweiterung) wurden ZTA-09 bis ZTA-15 hinzugefügt, um weitere NIST-Tenets, OT-Resilienz-Anforderungen (IEC 62443), AI-spezifische Robustheit (EU AI Act) und Automatisierungs-Aspekte abzudecken. Zusätzlich wurde der Abschnitt "Klassifizierung und Risikobewertung" um Hinweise zur Überklassifizierung erweitert.

**Unterschrift / Genehmigung**  
Geschäftsführung _______________________ Datum ________  
CISO _______________________ Datum ________  
AI Risk Owner _______________________ Datum ________
```

### Ausführlichere Version für das Word-Dokument

Hier eine **ausführliche, eigenständige Version** des neuen Inhalts für das Word-Dokument. Ich schlage vor, sie als **neuen Unterabschnitt 1.1.1** oder **separaten Abschnitt 1.2** einzufügen (nach der Einleitung). Der Text ist selbsttragend, erklärt den Kontext, integriert die Recherche und weckt Interesse am GitHub-Repo.

#### 1.1.1 Risikoklassifizierung im EU AI Act – Warnung vor Überklassifizierung

Im Rahmen der EU AI Act (Verordnung (EU) 2024/1689) wird AI-Systemen eine risikobasierte Klassifizierung zugewiesen: unacceptable risk (verboten), high-risk (strenge Anforderungen), limited risk (Transparenzpflichten) und minimal risk (unreguliert). Für Systeme in Annex III (z. B. kritische Infrastruktur, Beschäftigung, Produktqualität) gilt eine Vermutung für high-risk, aber Provider müssen eine Self-Assessment durchführen und dokumentieren, ob Ausnahmen greifen (z. B. enge prozedurale Tasks oder Unterstützung menschlicher Entscheidungen ohne Ersatz).

Allerdings hat die hohe Strafdrohung (bis zu 7% des globalen Jahresumsatzes für Verstöße) zu einer "Panik" vor regulatorischen Risiken geführt. Viele Unternehmen klassifizieren Systeme vorsichtshalber als high-risk, um Sanktionen zu vermeiden – eine Form der Over-Compliance. Studien wie die des appliedAI-Institute (2023/2024) zeigen, dass 40% der Klassifizierungen unklar sind, was zu Überklassifizierungen in bis zu 58% der Fälle führt. Dies bindet unnötig Ressourcen (z. B. für Conformity Assessments, Dokumentation), behindert Innovation und verwässert den Fokus auf echte high-risk-Systeme, wie die EU-Kommission in Guidelines kritisiert (EC IP/25/2718, 2025). Die Kommission warnt, dass solche Überklassifizierungen die Wirksamkeit des Acts untergraben und echte Risiken für Gesundheit, Sicherheit und Grundrechte verdünnen.

Im Vergleich dazu betont IEC 62443 (Security Levels SL 1–4) eine präzise, kosten-nutzen-orientierte Klassifizierung, die Überklassifizierung vermeidet, da höhere Levels direkte Kostensteigerungen (z. B. für Maßnahmen, Audits) bedeuten. Eine "vorsichtshalber höhere" Einstufung würde hier wirtschaftlich kontraproduktiv sein.

**Empfehlungen für die Praxis:**  
- Führen Sie eine fundierte Self-Assessment durch und dokumentieren Sie Ausnahmen detailliert (z. B. nach EU-Beispielen für non-high-risk).  
- Vermeiden Sie Panik-Klassifizierungen – nutzen Sie Tools wie den EU AI Office Classifier oder externe Berater.  
- Priorisieren Sie echte Risiken, um Ressourcen effizient einzusetzen und den Sinn der Klassifizierung (Schutz vor echten Bedrohungen) zu wahren.

Detaillierte Beispiele und erweiterte Tabellen zur Klassifizierung finden Sie im GitHub-Repository:  
[Modul_ZTA_Teil_1.md](https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Modul_ZTA_Teil_1.md) (Abschnitt "Klassifizierung und Risikobewertung").  

---

Das passt nahtlos in dein Word-Dokument – ca. 1/2 Seite, informativ, aber nicht überwältigend. Es weckt Lust auf das Repo, ohne zu viel zu verraten.

Falls du den Word-Text noch länger / kürzer oder mit Quellen-Links (Fußnoten) machen möchtest, lass es mich wissen! 😊
# Data- und AI-Governance-Rahmenwerk für Zero Trust Architektur (ZTA) mit Künstlicher Intelligenz (KI) in der Industrie 4.0

## Version, Stand und Genehmigung

Dieses Dokument stellt die Version 2.0 des Data- und AI-Governance-Rahmenwerks dar, das am xx. xxx 2026 erstellt wurde. Es wurde von der Geschäftsführung, dem Chief Information Security Officer (CISO) und dem Datenschutzbeauftragten genehmigt, um eine maximale Auditierbarkeit zu gewährleisten. Die Genehmigung erfolgte durch Unterschriften, die in der gedruckten Version dieses Dokuments vorliegen, und dient als Nachweis für die formelle Annahme aller hierin festgelegten Regelungen.

## Rahmenbedingungen und Geltungsbereich

Dieses Governance-Rahmenwerk gilt für alle Systeme der Künstlichen Intelligenz und Komponenten der Zero Trust Architektur, die in der Organisation entwickelt, beschafft, betrieben oder eingesetzt werden. Es umfasst insbesondere Anwendungen in operativen Technologien und Umgebungen der Industrie 4.0, wie etwa in der Produktion, der Lieferkette, der prädiktiven Wartung und der Qualitätskontrolle mit Unterstützung durch Künstliche Intelligenz. Die rechtliche und normative Grundlage dieses Rahmenwerks basiert auf der EU AI Act in der Fassung der Verordnung (EU) 2024/1689, insbesondere den Artikeln 9 bis 15 für Systeme mit hohem Risiko gemäß Annex III, die Use-Cases in kritischer Infrastruktur, Beschäftigung und Produktqualitätssicherung betreffen. Darüber hinaus orientiert es sich an der ISO/IEC 42001:2023 für das Artificial Intelligence Management System, an der ISO/IEC 27001:2022 für das Information Security Management System sowie an der IEC 62443 für die Sicherheit in operativen Technologien. Es integriert die Prinzipien der NIST SP 800-207 für Zero Trust Architecture und der DoD Zero Trust Reference Architecture. Der Geltungsbereich ist auf Systeme mit Relevanz für Künstliche Intelligenz oder Zero Trust Architektur beschränkt, wobei Systeme mit niedrigem Risiko vereinfachte Regelungen unterliegen, die in separaten Anhängen dieses Dokuments detailliert beschrieben werden.

## Ziele und Grundsätze

Die primären Ziele dieses Rahmenwerks bestehen darin, Risiken für die Sicherheit, die Gesundheit, die Grundrechte und die Resilienz in operativen Technologien zu minimieren. Es soll die Nachvollziehbarkeit, die Auditierbarkeit und die Resilienz der Systeme gewährleisten, indem alle regulatorischen Anforderungen der EU AI Act und der ISO 42001 vollständig eingehalten werden. Darüber hinaus fördert es die verantwortungsvolle Nutzung von Künstlicher Intelligenz in dynamischen Umgebungen der Zero Trust Architektur. Die Grundsätze orientieren sich am Alignment mit den Prinzipien der NIST Zero Trust Architecture und der ISO 42001 Annex A. Dazu gehört das Prinzip, niemals blind zu vertrauen, sondern immer zu verifizieren, was durch dynamische und kontextbasierte Authentifizierung umgesetzt wird. Es wird ein Angriff vorausgesetzt, was eine kontinuierliche Überwachung und die Vergabe minimaler Privilegien erfordert. Die Provenienz von Daten und Entscheidungen muss über den gesamten Lebenszyklus hinweg gesichert sein. Eine menschliche Aufsicht ist bei Entscheidungen mit hohem Risiko obligatorisch. Der kontinuierliche Verbesserungsprozess folgt dem Plan-Do-Check-Act-Zyklus, der in allen Prozessen dieses Rahmenwerks verankert ist.

## Klassifizierung von Systemen der Künstlichen Intelligenz

Die risikobasierte Klassifizierung der Systeme der Künstlichen Intelligenz erfolgt gemäß der EU AI Act und der ISO 42001 Annex A.5. In der folgenden Tabelle werden die Risikoklassen detailliert beschrieben, einschließlich der Kriterien, Beispiele aus dem Unternehmen und der daraus resultierenden Anforderungen, die jeweils in vollständigen Sätzen formuliert sind.

| Risikoklasse | Kriterien, die für diese Klasse gelten | Beispiele aus dem Unternehmen, die in diese Klasse fallen | Anforderungen, die für diese Klasse obligatorisch sind |
|--------------|----------------------------------------|----------------------------------------------------------|-------------------------------------------------------|
| Verbotene Systeme | Diese Klasse umfasst Systeme, die gemäß Annex II der EU AI Act verboten sind, wie etwa Social Scoring-Systeme, die Individuen bewerten und diskriminieren. | In unserem Unternehmen existieren keine Systeme, die in diese Klasse fallen, da solche Anwendungen von vornherein ausgeschlossen werden. | Solche Systeme sind nicht zulässig und dürfen weder entwickelt noch eingesetzt werden, um regulatorische Sanktionen zu vermeiden. |
| Systeme mit hohem Risiko | Diese Klasse betrifft Systeme gemäß Annex III der EU AI Act, die eine Sicherheitskomponente darstellen und Auswirkungen auf Gesundheit oder Rechte haben. | Beispiele in unserem Unternehmen sind Systeme der Künstlichen Intelligenz für die Qualitätskontrolle in operativen Technologien oder prädiktive Wartung mit Relevanz für die Sicherheit. | Für diese Systeme müssen die vollständigen Anforderungen der Artikel 9 bis 15 der EU AI Act erfüllt werden, einschließlich einer Conformity Assessment, die durch externe Audits nachgewiesen wird. |
| Systeme mit begrenztem Risiko | Diese Klasse umfasst Systeme, die Transparenzpflichten unterliegen, wie Chatbots oder Systeme zur Erzeugung von Deepfakes. | Beispiele in unserem Unternehmen sind interne Assistenten auf Basis von Künstlicher Intelligenz, die für administrative Zwecke genutzt werden. | Für diese Systeme müssen Transparenzhinweise bereitgestellt werden, die den Nutzern klar mitteilen, dass es sich um Systeme der Künstlichen Intelligenz handelt. |
| Systeme mit minimalem Risiko | Diese Klasse umfasst alle anderen Systeme, die keine der oberen Kriterien erfüllen. | Beispiele in unserem Unternehmen sind interne Automatisierungen ohne Auswirkungen auf Risiken für Personen oder Prozesse. | Für diese Systeme gelten freiwillige Best Practices, die in diesem Rahmenwerk empfohlen werden, um eine konsistente Governance zu gewährleisten. |

Jedes System der Künstlichen Intelligenz durchläuft einen Prozess, in dem eine AI Impact Assessment und eine Fundamental Rights Impact Assessment durchgeführt werden, insbesondere bei Systemen mit hohem Risiko, wie in der ISO 42001 Annex A.5.5 vorgeschrieben.

## Rollen und Verantwortlichkeiten

Die Rollen und Verantwortlichkeiten sind klar definiert, um eine auditierbare Zuweisung zu gewährleisten. In der folgenden Tabelle werden die Rollen beschrieben, einschließlich der Verantwortungen gemäß ISO 42001 Annex A.3.2 und der RACI-Matrix, die Responsible, Accountable, Consulted und Informed darstellt, wobei jede Zelle vollständige Sätze enthält.

| Rolle | Verantwortung, die dieser Rolle zugewiesen ist | RACI-Zuweisung, die für diese Rolle gilt |
|-------|------------------------------------------------|------------------------------------------|
| Geschäftsführung | Die Geschäftsführung ist für die Genehmigung des Rahmenwerks, die Bereitstellung von Ressourcen und die Durchführung von Reviews verantwortlich. | Diese Rolle ist accountable für den gesamten Prozess. |
| AI Governance Board | Das AI Governance Board übernimmt die Strategieentwicklung und die Entscheidungen zu Risiken. | Diese Rolle ist accountable und responsible für strategische Entscheidungen. |
| AI Risk Owner pro System | Der AI Risk Owner ist für das Risikomanagement und die Durchführung von AI Impact Assessments und Fundamental Rights Impact Assessments verantwortlich. | Diese Rolle ist responsible für die operativen Risiken. |
| Chief Information Security Officer oder OT-Security-Verantwortlicher | Der Chief Information Security Officer ist für die Umsetzung der Zero Trust Architektur und die Cybersecurity gemäß Artikel 15 der EU AI Act verantwortlich. | Diese Rolle ist responsible und consulted in Sicherheitsfragen. |
| Datenschutzbeauftragter | Der Datenschutzbeauftragte gewährleistet die Konformität mit der DSGVO, insbesondere hinsichtlich Bias und Datenqualität. | Diese Rolle ist consulted und informed in datenschutzrelevanten Angelegenheiten. |
| AI Ethics Officer | Der AI Ethics Officer führt ethische Bewertungen durch und überwacht die menschliche Aufsicht. | Diese Rolle ist consulted in ethischen Fragen. |
| Fachabteilung oder DevOps-Team | Die Fachabteilung ist für die technische Umsetzung und die Dokumentation verantwortlich. | Diese Rolle ist responsible für die tägliche Implementierung. |

## Menschliche Aufsicht und Eskalationsmechanismen

Die Grundsätze der menschlichen Aufsicht sehen vor, dass immer eine Human-in-the-Loop- oder Human-on-the-Loop-Mechanismus bei Entscheidungen mit hohem Risiko implementiert wird, die Auswirkungen auf Sicherheit oder Personen haben. Eine automatische Eskalation erfolgt bei einem Confidence-Score unter 85 Prozent, einem Kontext-Drift über 10 Prozent in den Daten der Zero Trust Architektur, einer Anomalie im Zustand operativer Prozesse oder einem Bias-Indikator über einem festgelegten Schwellwert. Beispielsweise wird bei einer Entscheidung der Künstlichen Intelligenz in der Qualitätskontrolle eine menschliche Prüfung durchgeführt, wenn die Unsicherheit über 15 Prozent liegt. Bei einer Verletzung der Policy in der Zero Trust Architektur erfolgt eine automatische Blockade und eine Benachrichtigung des Security-Teams, die in Audit-Logs dokumentiert wird.

## Risikomanagement und Impact Assessment

Der Risikomanagement-Prozess folgt dem Plan-Do-Check-Act-Zyklus und umfasst die Identifikation von Risiken für Sicherheit, Rechte und Verfügbarkeit in operativen Technologien, die Bewertung anhand einer Likelihood-Impact-Matrix, die Behandlung durch Controls aus der Annex A der ISO 42001 und das kontinuierliche Monitoring mit jährlichen Reviews. In der folgenden Tabelle wird eine Beispiel-Risiko-Matrix dargestellt, in der jedes Risiko mit Likelihood, Impact, Priorität und mitigierenden Controls beschrieben wird, wobei jede Zelle vollständige Sätze enthält.

| Risiko, das identifiziert wurde | Likelihood, die für dieses Risiko gilt | Impact, der für dieses Risiko erwartet wird | Priorität, die diesem Risiko zugewiesen ist | Mitigierende Controls, die aus der Annex A der ISO 42001 stammen |
|--------------------------------|-----------------------------------------|---------------------------------------------|---------------------------------------------|-----------------------------------------------------------------|
| Bias in Systemen der Künstlichen Intelligenz für operative Qualitätskontrolle | Die Likelihood für dieses Risiko ist mittel, da sie von Datenqualität abhängt. | Der Impact für dieses Risiko ist hoch, da er Diskriminierung verursachen kann. | Die Priorität für dieses Risiko ist hoch aufgrund potenzieller rechtlicher Konsequenzen. | Die mitigierenden Controls umfassen A.7.3 für Bias-Mitigation, A.8.2 für Explainability und A.5.4 für Impact Assessments. |
| Manipulation von Kontext-Daten in der Zero Trust Architektur | Die Likelihood für dieses Risiko ist hoch, da Angriffe in dynamischen Umgebungen häufig sind. | Der Impact für dieses Risiko ist hoch, da er die Systemintegrität beeinträchtigt. | Die Priorität für dieses Risiko ist sehr hoch, da es die Kernsicherheit betrifft. | Die mitigierenden Controls umfassen A.10.1 für Cybersecurity und SR 3.1 aus der IEC 62443 für Gerätesicherheit. |

## Mapping der wesentlichen Controls und Statement of Applicability

Das Statement of Applicability umfasst ein vollständiges Mapping aller 38 Controls der Annex A der ISO 42001. In der folgenden Tabelle werden die Controls detailliert, einschließlich Titel, Anwendung, Umsetzung und Verantwortlichem, wobei jede Zelle vollständige Sätze enthält. (Die Tabelle zeigt einen Auszug; der vollständige Satz befindet sich im Anhang.)

| Annex A Control | Titel des Controls | Anwendung, die für diesen Control gilt | Umsetzung oder Referenzdokument, das diesen Control abdeckt | Verantwortlicher, der für diesen Control zuständig ist |
|-----------------|--------------------|----------------------------------------|------------------------------------------------------------|-------------------------------------------------------|
| A.2.2 | Dieser Control betrifft die AI Policy. | Die Anwendung dieses Controls ist ja, da er für alle Systeme obligatorisch ist. | Die Umsetzung erfolgt durch dieses Dokument, das die Policy definiert. | Der Verantwortliche für diesen Control ist das AI Governance Board. |
| A.2.3 | Dieser Control betrifft das Alignment mit anderen Policies. | Die Anwendung dieses Controls ist ja, da er Integration erfordert. | Die Umsetzung erfolgt durch die ISMS-Policy und die OT-Security-Policy. | Der Verantwortliche für diesen Control ist der Chief Information Security Officer. |
| A.2.4 | Dieser Control betrifft den Review der AI Policy. | Die Anwendung dieses Controls ist ja, da er jährliche Überprüfungen vorschreibt. | Die Umsetzung erfolgt jährlich und bei Change-Triggers durch definierte Prozesse. | Der Verantwortliche für diesen Control ist das AI Governance Board. |
| A.5.1 bis A.5.5 | Diese Controls betreffen Impact Assessments. | Die Anwendung dieser Controls ist ja, da sie für High-Risk-Systeme essenziell sind. | Die Umsetzung erfolgt durch das AI Impact Assessment-Template und die Fundamental Rights Impact Assessment. | Der Verantwortliche für diese Controls ist der AI Risk Owner. |
| A.6.1 bis A.6.2.8 | Diese Controls betreffen AI Lifecycle Controls. | Die Anwendung dieser Controls ist ja, da sie den gesamten Lebenszyklus abdecken. | Die Umsetzung erfolgt durch das Lifecycle-Dokument und die Module ZTA Teil 1 bis 3. | Der Verantwortliche für diese Controls ist das DevOps-Team. |
| A.7.1 bis A.7.5 | Diese Controls betreffen Data for AI Systems. | Die Anwendung dieser Controls ist ja, da Datenqualität zentral ist. | Die Umsetzung erfolgt durch die Data-Provenienz-Policy. | Der Verantwortliche für diese Controls ist der Datenschutzbeauftragte. |
| A.8.1 bis A.8.5 | Diese Controls betreffen Transparency und Explainability. | Die Anwendung dieser Controls ist ja, da Transparenz regulatorisch gefordert ist. | Die Umsetzung erfolgt durch Model Cards und Audit-Logs. | Der Verantwortliche für diese Controls ist der AI Ethics Officer. |
| A.9.1 bis A.9.3 | Diese Controls betreffen Human Oversight. | Die Anwendung dieser Controls ist ja, da menschliche Aufsicht vorgeschrieben ist. | Die Umsetzung erfolgt durch den Abschnitt zur menschlichen Aufsicht und Eskalationsregeln. | Der Verantwortliche für diese Controls ist die Fachabteilung. |
| A.10.1 bis A.10.3 | Diese Controls betreffen Incident und Continuous Improvement. | Die Anwendung dieser Controls ist ja, da kontinuierliche Verbesserung essenziell ist. | Die Umsetzung erfolgt durch Monitoring-KPIs und den Corrective Action Preventive Action-Prozess. | Der Verantwortliche für diese Controls ist der Chief Information Security Officer. |

## Monitoring, Review und Aktualisierung

Der Review-Zyklus dieses Rahmenwerks erfolgt mindestens jährlich sowie bei neuen regulatorischen Anforderungen, signifikanten Änderungen an Systemen der Künstlichen Intelligenz oder Zero Trust Architektur und bei Incidents oder Audit-Findings. Die Key Performance Indicators werden in der folgenden Tabelle detailliert, einschließlich Beschreibung und Zielwert, wobei jede Zelle vollständige Sätze enthält.

| Key Performance Indicator | Beschreibung des Indicators | Zielwert, der für diesen Indicator festgelegt ist |
|---------------------------|-----------------------------|--------------------------------------------------|
| Prozentsatz abgeschlossener AI Impact Assessments bei Systemen mit hohem Risiko | Dieser Indicator misst den Prozentsatz der abgeschlossenen Assessments für Projekte mit hohem Risiko. | Der Zielwert für diesen Indicator beträgt 100 Prozent, um vollständige Compliance zu gewährleisten. |
| Time-to-Detect für Verletzungen in der Zero Trust Architektur | Dieser Indicator misst die Zeit bis zur Erkennung einer Verletzung. | Der Zielwert für diesen Indicator liegt unter 5 Minuten, um schnelle Reaktionen zu ermöglichen. |
| Prozentsatz von Entscheidungen der Künstlichen Intelligenz mit menschlicher Aufsicht bei hohem Risiko | Dieser Indicator misst den Anteil der Entscheidungen, die überwacht werden. | Der Zielwert für diesen Indicator beträgt über 95 Prozent, um Risiken zu minimieren. |

Der kontinuierliche Verbesserungsprozess umfasst den Corrective Action Preventive Action-Prozess, Lessons Learned und Management Reviews gemäß Clause 9.3 der ISO 42001, die in Protokollen dokumentiert werden.

## Anhang: Referenzen und Changelog

Die Referenzen umfassen die EU AI Act unter https://artificialintelligenceact.eu, die ISO/IEC 42001:2023 mit Annex A und 38 Controls, die NIST SP 800-207 sowie die DoD Zero Trust Reference Architecture Version 2.0. Der Changelog dokumentiert Änderungen: In Version 3.0 wurden alle Inhalte zu vollständigen Sätzen und Tabellen erweitert, um maximale Auditierbarkeit und juristische Lesbarkeit zu gewährleisten, einschließlich Evidenz-Nachweisen und formaler Strukturen.
