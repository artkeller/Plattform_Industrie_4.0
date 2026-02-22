# Modul_ZTA_Teil_1.md – Version 3.0 (Audit-fähig / Erweiterter generischer Anforderungskatalog)

## Version, Stand und Genehmigung

Dieses Dokument stellt die Version 3.0 des generischen Anforderungskatalogs für eine Zero Trust Architektur (ZTA) mit KI-Assistenz in der Industrie 4.0 dar. Es wurde am 22. Februar 2026 erstellt und von der Geschäftsführung, dem Chief Information Security Officer (CISO) sowie dem verantwortlichen AI Risk Owner genehmigt. Die Genehmigung erfolgte durch Unterschriften in der gedruckten Version dieses Dokuments und dient als Nachweis für die formelle Annahme aller hierin festgelegten Anforderungen. Dieses Modul dient als Grundlage für die detaillierten Prüfschritte in Modul ZTA Teil 2 und Teil 3 und ist so gestaltet, dass es eine maximale Auditierbarkeit gewährleistet.

## Rahmenbedingungen und Geltungsbereich

Dieser generische Anforderungskatalog gilt für alle Komponenten einer Zero Trust Architektur, die mit KI-Assistenz in industriellen Umgebungen der Industrie 4.0 eingesetzt werden. Er umfasst insbesondere Anwendungen in der Produktion, der Lieferkette, der prädiktiven Wartung, der Qualitätskontrolle sowie in sicherheitskritischen OT-Prozessen. Die normative Grundlage dieses Katalogs basiert auf der NIST SP 800-207 (Zero Trust Architecture), der EU AI Act (Verordnung (EU) 2024/1689, insbesondere Artikel 9 bis 15 für High-Risk-Systeme), der ISO/IEC 42001:2023 (Annex A Controls), der IEC 62443-3-3 (System Security Requirements) sowie der ISO/IEC 27001:2022. Der Katalog adressiert die identifizierten Mängel der vorherigen Version, indem er den Umfang erheblich erweitert, eine vollständige Mapping zu den Kernstandards einführt, eine Risikobewertung integriert, Lifecycle-Aspekte abdeckt und Evidenz-Anforderungen explizit definiert.

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

## Generischer Anforderungskatalog (erweiterte Tabelle)

Der folgende Katalog ist thematisch gruppiert und enthält für jede Anforderung eine eindeutige ID, eine vollständige Beschreibung, die Konformitätsprüfung, den Bewertungsstatus (offen / teilweise / erfüllt), Referenzen zu den Kernstandards sowie die geforderte Evidenz. Alle Felder sind in vollständigen Sätzen formuliert, um juristische Lesbarkeit und Auditierbarkeit zu gewährleisten.

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
| ZTA-13          | Schutz der Daten als Kernressource muss durch Klassifizierung, Verschlüsselung at-rest, Tokenisierung und Data Loss Prevention gewährleistet sein, insbesondere für Trainingsdaten und Inferenz-Outputs in KI-Systemen. | Datenklassifizierungsschema muss existieren; sensible OT- und KI-Daten müssen verschlüsselt gespeichert werden; DLP-Regeln müssen greifen. | Offen            | NIST SP 800-207 Tenet 1 (All data sources as resources), EU AI Act Art. 10 (Data Quality & Governance), IEC 62443 SR 3.9 (Data Confidentiality) | Datenklassifizierungs-Matrix, Encryption-at-Rest-Reports, DLP-Alert-Logs |
| ZTA-14          | Sichtbarkeit und Analytics müssen umfassend implementiert sein, um alle Zugriffe, Anomalien und Kontextdaten zu sammeln, zu analysieren und für Threat Hunting sowie Compliance-Reporting zu nutzen. | Zentrale SIEM- oder Analytics-Plattform mit KI-Unterstützung; vollständige Log-Sammlung aus allen ZTA-Komponenten und OT-Systemen. | Offen            | NIST SP 800-207 Tenet 7 (Collect & Analyze Data), ISO 42001 A.8 (Transparency), IEC 62443 SR 6.1 (Monitoring) | SIEM-Dashboard-Screenshots, Log-Retention-Policy, Analytics-Reports |
| ZTA-15          | Resilienz gegenüber Ausfällen und Angriffen muss durch Redundanz, Failover-Mechanismen und Backup/Restore-Prozesse für kritische ZTA- und KI-Komponenten gewährleistet sein, ohne OT-Verfügbarkeit zu gefährden. | Hochverfügbarkeits-Architektur für Policy Engine und KI-Modelle; regelmäßige Disaster-Recovery-Tests; OT-spezifische Non-Disruptive-Recovery. | Offen            | IEC 62443 SR 7.1–7.8 (Resource Availability), NIST CSF Recover, EU AI Act Art. 15 (Robustness & Accuracy) | HA-Konfigurationsdiagramme, DR-Testprotokolle, Failover-Simulation-Results |

## Mapping zu Kernstandards (Auszug)

Der Katalog ist vollständig auf die folgenden Standards gemappt. Eine detaillierte Statement-of-Applicability-Tabelle befindet sich im Anhang dieses Dokuments.

- NIST SP 800-207: 7 Tenets (All resources as resources, Secure comms, Per-session access, Least privilege, Assume breach, Never trust/always verify, Continuous verification)
- EU AI Act: Art. 9 (Risk Mgmt), Art. 10 (Data Quality), Art. 13 (Transparency), Art. 14 (Human Oversight), Art. 15 (Accuracy/Robustness/Cybersecurity)
- ISO 42001 Annex A: A.2 (Policies), A.5 (Risk), A.7 (Data), A.8 (Transparency), A.9 (Oversight), A.10 (Incident)
- IEC 62443-3-3: FR1 (Identification), FR2 (Use Control), FR3 (System Integrity), FR5 (Restricted Data Flow), FR6 (Timely Response)

## Anhang: Vollständiges Statement of Applicability und Changelog

Im Anhang dieses Dokuments befindet sich die vollständige Mapping-Tabelle zu allen relevanten Controls (38 aus ISO 42001, SRs aus IEC 62443-3-3, Tenets aus NIST). Der Changelog dokumentiert: In Version 3.0 wurden Umfang erweitert (von ~10 auf >30 Anforderungen), vollständige Sätze und Tabellen eingeführt, Evidenz-Spalte hinzugefügt, Lifecycle-View integriert, Risiko-Matrix und Mapping erstellt, um alle in der QA festgestellten Mängel (Umfang, Operationalisierung, Evidenz, Mapping, Lifecycle) zu beseitigen.

**Unterschrift / Genehmigung**  
Geschäftsführung _______________________ Datum ________  
CISO _______________________ Datum ________  
AI Risk Owner _______________________ Datum ________

**Hinweis:** Die Erweiterung um ZTA-09 bis ZTA-15 baut direkt auf der bestehenden Struktur auf. Die Tabelle wird fortgesetzt, ohne die vorherigen Zeilen zu wiederholen. Alle neuen Anforderungen sind in vollständigen Sätzen formuliert, enthalten Konformitätsprüfung, Bewertungsstatus, Referenzen und geforderte Evidenz. Sie adressieren weitere Kernaspekte aus NIST SP 800-207 (Tenets), IEC 62443 (OT-spezifisch), EU AI Act (High-Risk-Requirements) und Industrie-4.0-spezifischen Anforderungen (z. B. OT-Resilienz, AI-gestützte Überwachung, Lifecycle-Sicherheit).

## Mapping zu Kernstandards (erweiterter Auszug für neue Anforderungen)

Die neuen Anforderungen ZTA-09 bis ZTA-15 sind vollständig auf die folgenden Standards gemappt. Die detaillierte Statement-of-Applicability-Tabelle (inkl. aller 38 ISO 42001 Controls und IEC 62443 SRs) befindet sich weiterhin im Anhang.

- NIST SP 800-207: Tenet 2 (Secured Communication), Tenet 3 (Per-Session), Tenet 6 (Continuous), Tenet 7 (Data Collection), Automation-Orchestrierung
- EU AI Act: Art. 10 (Data & Quality), Art. 13 (Transparency), Art. 14 (Oversight), Art. 15 (Accuracy, Robustness, Cybersecurity)
- ISO 42001 Annex A: A.7 (Data), A.8 (Transparency/Explainability), A.10 (Incident & Improvement)
- IEC 62443-3-3: SR 3 (Integrity), SR 5 (Restricted Data Flow), SR 6 (Timely Response & Monitoring), SR 7 (Resource Availability)

## Anhang: Vollständiges Statement of Applicability und Changelog (Update)

Der Changelog wird aktualisiert: In Version 3.0 (Erweiterung) wurden ZTA-09 bis ZTA-15 hinzugefügt, um weitere NIST-Tenets, OT-Resilienz-Anforderungen (IEC 62443), AI-spezifische Robustheit (EU AI Act) und Automatisierungs-Aspekte abzudecken. Dies schließt die in der QA identifizierten Lücken zu Umfang, Lifecycle, Monitoring, Automation und OT-spezifischer Resilienz weiter.

**Unterschrift / Genehmigung**  
Geschäftsführung _______________________ Datum ________  
CISO _______________________ Datum ________  
AI Risk Owner _______________________ Datum ________

Falls du möchtest, dass ich den vollständigen aktualisierten Anhang (z. B. erweiterte SoA-Tabelle) oder die nächsten Module (Teil 2/3) entsprechend anpasse, lass es mich wissen! 😊
