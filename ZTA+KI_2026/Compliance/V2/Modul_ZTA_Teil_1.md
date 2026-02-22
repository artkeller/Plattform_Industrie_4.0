# Modul_ZTA_Teil_1.md – Version 2.0 (Audit-fähig / Erweiterter generischer Anforderungskatalog) – Fortsetzung

**Hinweis:** Die Erweiterung um ZTA-09 bis ZTA-15 baut direkt auf der bestehenden Struktur auf. Die Tabelle wird fortgesetzt, ohne die vorherigen Zeilen zu wiederholen. Alle neuen Anforderungen sind in vollständigen Sätzen formuliert, enthalten Konformitätsprüfung, Bewertungsstatus, Referenzen und geforderte Evidenz. Sie adressieren weitere Kernaspekte aus NIST SP 800-207 (Tenets), IEC 62443 (OT-spezifisch), EU AI Act (High-Risk-Requirements) und Industrie-4.0-spezifischen Anforderungen (z. B. OT-Resilienz, AI-gestützte Überwachung, Lifecycle-Sicherheit).

## Generischer Anforderungskatalog (Fortsetzung – ZTA-09 bis ZTA-15)

| Anforderungs-ID | Beschreibung der Anforderung | Konformitätsprüfung / Nachweismethode | Bewertungsstatus | Referenzen zu Standards | Geforderte Evidenz |
|-----------------|------------------------------|---------------------------------------|------------------|--------------------------|--------------------|
| ZTA-09          | Alle Kommunikationen müssen unabhängig von der Netzwerkposition vollständig gesichert werden, einschließlich Verschlüsselung in Transit und End-to-End-Sicherung für OT-Datenströme und KI-Inferenz-Daten. | Alle Verbindungen müssen TLS 1.3 oder höher nutzen; OT-spezifische Protokolle müssen durch sichere Gateways oder Wrappers geschützt werden; Penetrationstests auf unverschlüsselte Kommunikation müssen regelmäßig durchgeführt werden. | Offen            | NIST SP 800-207 Tenet 2 (All communication secured regardless of location), IEC 62443 SR 3.1–3.9 (System Integrity), EU AI Act Art. 15 (Cybersecurity) | TLS-Konfigurationsberichte, OT-Protokoll-Analyse, Penetrationstest-Reports, Verschlüsselungs-Matrix |
| ZTA-10          | Zugriffe müssen sitzungsbezogen und mit Just-in-Time / Just-Enough-Access gewährt werden, wobei Zugriffe automatisch bei Session-Ende oder Kontextänderung widerrufen werden. | Policy Engine muss session-basierte Tokens mit kurzer Lebensdauer ausstellen; automatische Revocation bei Anomalien oder Zeitüberschreitung muss implementiert sein. | Offen            | NIST SP 800-207 Tenet 3 (Per-session access), NIST Tenet 4 (Least privilege), IEC 62443 SR 2.1 (Least Privilege) | Session-Log-Analyse, Token-Lebensdauer-Konfiguration, Revocation-Testprotokolle |
| ZTA-11          | Kontinuierliche Bewertung der Sicherheitslage (Continuous Posture Assessment) muss für alle Entitäten (User, Device, AI-Modell, OT-Gerät) durchgeführt werden, inklusive Device Health Checks und Behavioral Analytics. | Echtzeit-Monitoring von Device-Compliance, User-Verhalten und Modell-Drift; KI-gestützte Anomalie-Erkennung muss integriert sein. | Offen            | NIST SP 800-207 Tenet 6 (Continuous verification), ISO 42001 A.10 (Continuous Improvement), EU AI Act Art. 15 (Robustness) | Device-Posture-Reports, UEBA-Dashboards, Drift-Detection-Logs |
| ZTA-12          | Automatisierung und Orchestrierung von Security-Maßnahmen muss implementiert sein, um Policies dynamisch anzupassen, Incidents zu isolieren und Response-Prozesse zu automatisieren. | SOAR-Integration mit ZTA-Komponenten; automatisierte Quarantäne bei erkannten Bedrohungen; KI-gestützte Policy-Optimierung muss vorhanden sein. | Offen            | NIST SP 800-207 (Automation in ZTA), IEC 62443 SR 6.1 (Timely Response), Cloud Security Alliance ZTA AI-Integration | Automation-Workflow-Diagramme, SOAR-Konfiguration, Incident-Automatisierungs-Tests |
| ZTA-13          | Schutz der Daten als Kernressource muss durch Klassifizierung, Verschlüsselung at-rest, Tokenisierung und Data Loss Prevention gewährleistet sein, insbesondere für Trainingsdaten und Inferenz-Outputs in KI-Systemen. | Datenklassifizierungsschema muss existieren; sensible OT- und KI-Daten müssen verschlüsselt gespeichert werden; DLP-Regeln müssen greifen. | Offen            | NIST SP 800-207 Tenet 1 (All data sources as resources), EU AI Act Art. 10 (Data Quality & Governance), IEC 62443 SR 3.9 (Data Confidentiality) | Datenklassifizierungs-Matrix, Encryption-at-Rest-Reports, DLP-Alert-Logs |
| ZTA-14          | Sichtbarkeit und Analytics müssen umfassend implementiert sein, um alle Zugriffe, Anomalien und Kontextdaten zu sammeln, zu analysieren und für Threat Hunting sowie Compliance-Reporting zu nutzen. | Zentrale SIEM- oder Analytics-Plattform mit KI-Unterstützung; vollständige Log-Sammlung aus allen ZTA-Komponenten und OT-Systemen. | Offen            | NIST SP 800-207 Tenet 7 (Collect & Analyze Data), ISO 42001 A.8 (Transparency), IEC 62443 SR 6.1 (Monitoring) | SIEM-Dashboard-Screenshots, Log-Retention-Policy, Analytics-Reports |
| ZTA-15          | Resilienz gegenüber Ausfällen und Angriffen muss durch Redundanz, Failover-Mechanismen und Backup/Restore-Prozesse für kritische ZTA- und KI-Komponenten gewährleistet sein, ohne OT-Verfügbarkeit zu gefährden. | Hochverfügbarkeits-Architektur für Policy Engine und KI-Modelle; regelmäßige Disaster-Recovery-Tests; OT-spezifische Non-Disruptive-Recovery. | Offen            | IEC 62443 SR 7.1–7.8 (Resource Availability), NIST CSF Recover, EU AI Act Art. 15 (Robustness & Accuracy) | HA-Konfigurationsdiagramme, DR-Testprotokolle, Failover-Simulation-Results |

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
