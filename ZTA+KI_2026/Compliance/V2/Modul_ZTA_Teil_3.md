# Modul ZTA Teil 3 – Version 2.0

Modul ZTA Teil 3 – Detaillierte Verifikation der Kontextdatenerfassung (ZTA-01-001)

**Wichtiger Hinweis zum Scope** 

Dieses Dokument enthält **ausschließlich** die detaillierte Verifikation des Prüfschritts **ZTA-01-001** (Kontextdatenerfassung) aus Modul ZTA Teil 2.  

Es zerlegt die Anforderung ZTA-01-001 in attributspezifische Verifikationspunkte. 

Für alle weiteren Prüfschritte (ZTA-01-002 bis ZTA-01-007) sowie für alle anderen Anforderungen (ZTA-02 ff.) **fehlen** in diesem Beispiel derzeit entsprechende Detail-Module. Diese müssen analog erstellt werden, um eine vollständige, attribut- und prüfschrittgenaue Auditierbarkeit zu erreichen.

## Verifikationspunkte für ZTA-01-001 (Kontextdatenerfassung)

| ID             | Beschreibung des Verifikationspunkts                                                                 | Erwartetes Ergebnis                                                                                   | Bewertungsstatus | Referenz                                      | Evidenz / Nachweis (neu)                                                                 |
|----------------|------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|------------------|-----------------------------------------------|-------------------------------------------------------------------------------------------|
| ZTA-01-001-01  | Überprüfung der Erfassung und Aktualität der User-Identitäts-Attribute (z. B. User-ID, Rolle, MFA-Status, letzte Authentifizierung). | Alle User-Identitätsattribute sind aktuell (< 60 s) verfügbar und werden korrekt an die Policy Engine weitergegeben. | Offen            | NIST SP 800-207 Tenet 6, IEC 62443 SR 1.1–1.2 | IAM-Log-Auszug mit Zeitstempel, API-Response der Identity-Provider-Integration, Konfigurationsscreenshots |
| ZTA-01-001-02  | Überprüfung der Geräteintegrität (Device-Posture): Endpoint-Security-Status, OS-Patch-Level, Zertifikat-Gültigkeit, TPM/Trusted Boot. | Geräte mit fehlendem Patch oder ungültigem Zertifikat werden als „non-compliant“ markiert und an Policy Engine gemeldet. | Offen            | NIST SP 800-207 Tenet 6, IEC 62443 SR 1.3     | Device-Posture-Report (z. B. Intune/CrowdStrike), Non-Compliant-Beispiel-Log, Screenshot Dashboard |
| ZTA-01-001-03  | Überprüfung des Netzwerkkontexts (Source-IP, VLAN/Zone, Geo-Location, VPN-Status, Netzwerk-Integrität). | Netzwerkkontext wird in Echtzeit ermittelt; Zugriffe aus nicht autorisierten Zonen werden als riskant klassifiziert. | Offen            | IEC 62443 SR 5.1–5.2 (Restricted Data Flow)   | Netzwerk-Flow-Logs (z. B. Zeek/Suricata), Zone-Mapping-Tabelle, Geo-IP-Check-Beispiel     |
| ZTA-01-001-04  | Überprüfung des OT-Prozesszustands (Maschinenstatus, Produktionsphase, kritische Parameter wie Druck/Temperatur/Drehzahl). | Relevante OT-Prozesswerte werden < 1 s alt an die Policy Engine geliefert; Abweichungen vom Normalzustand triggern höhere Risikobewertung. | Offen            | IEC 62443 SR 2.1, 6.1                         | OPC UA / MQTT-Log-Snippet, Prozesswert-Trend mit Zeitstempel, Alert bei Grenzwertüberschreitung |
| ZTA-01-001-05  | Überprüfung von Verhaltensmustern (User-, Geräte- und Prozessverhalten) mittels Baseline und KI-basierter Anomalie-Erkennung. | Abweichungen vom gelernten Normalverhalten (z. B. ungewöhnliche Zugriffszeit, Befehlssequenz) werden erkannt und mit Risikoscore versehen. | Offen            | ISO 42001 A.6.2.7, EU AI Act Art. 14          | UEBA/KI-Anomalie-Log (Score + Attribut), Baseline-Modell-Report, Beispiel anomaler Sequenz |
| ZTA-01-001-06  | Sicherstellung der Integrität und Authentizität der Kontextdaten während der Übertragung (TLS, Signaturen, Zeitstempel). | Alle Kontextdaten sind signiert und über TLS 1.3+ übertragen; Manipulationen werden erkannt und verworfen. | Offen            | IEC 62443 SR 3.1–3.3, NIST SP 800-207 Tenet 2 | TLS-Handshake-Log, Signatur-Verifikationsprotokoll, Manipulations-Test (Fail-Log)         |
| ZTA-01-001-07  | Überprüfung der Vollständigkeit: Fehlende oder veraltete Kontextattribute müssen erkannt und als Fehler behandelt werden. | Bei ≥1 fehlendem Attribut wird „incomplete context“ gemeldet und Policy-Entscheidung auf Deny gesetzt. | Offen            | NIST SP 800-207 Tenet 1 (never trust)         | Test mit absichtlich deaktiviertem Sensor, Log-Eintrag „deny – incomplete context“, Policy-Konfig |

## Mapping zu Kernstandards (für ZTA-01-001)

- NIST SP 800-207: Tenet 6 (Continuous verification of context)
- EU AI Act: Art. 15 (Robustness & Cybersecurity)
- IEC 62443-3-3: SR 1.x (Identification), SR 2.1 (Use Control), SR 5.x (Restricted Data Flow), SR 6.1 (Monitoring)
- ISO/IEC 42001: A.7 (Data), A.8 (Transparency), A.10 (Continuous monitoring)

## Changelog Version 2.0

- Scope klar auf ZTA-01-001 beschränkt und Ergänzungsbedarf für alle anderen Prüfschritte / Anforderungen explizit dokumentiert
- Evidenz / Nachweis-Spalte neu hinzugefügt
- OT-spezifische Kontextattribute (Prozesszustand) und KI-basierte Verhaltensanalyse stärker hervorgehoben

**Unterschrift / Genehmigung** 

Geschäftsführung _______________________ Datum ________  

CISO _______________________ Datum ________

AI Risk Owner _______________________ Datum ________
