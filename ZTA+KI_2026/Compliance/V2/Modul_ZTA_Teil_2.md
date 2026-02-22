# Modul ZTA Teil 2 – Prüfschritte zur Dynamischen Richtlinienanpassung (ZTA-01)

**Wichtiger Hinweis zum Scope**  

Dieses Dokument enthält **ausschließlich** exemplarische Prüfschritte zur Verifizierung der Anforderung **ZTA-01** (Dynamische Richtlinien-Durchsetzung) aus Modul ZTA Teil 1.

Für alle weiteren Anforderungen (ZTA-02 bis ZTA-15) **fehlen** derzeit entsprechende Prüfschritt-Module. Diese müssen analog erstellt werden, um eine vollständige Prüfbarkeit des gesamten Anforderungskatalogs zu erreichen.

## Prüfschritte

| ID          | Beschreibung des Prüfschritts                                                                                          | Erwartetes Ergebnis                                                                 | Bewertungsstatus | Referenz                          | Evidenz / Nachweis (neu)                                                                 |
|-------------|------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|------------------|-----------------------------------|-------------------------------------------------------------------------------------------|
| ZTA-01-001  | Überprüfung, ob alle relevanten Kontextattribute (User-Identität, Geräteintegrität, Netzwerkkontext, OT-Prozesszustand, Verhaltensmuster) in Echtzeit erfasst und der Policy Engine zur Verfügung gestellt werden. | Alle definierten Kontextattribute sind innerhalb von < 200 ms verfügbar und werden korrekt in die Entscheidung einbezogen. | Offen            | ISO 42001 A.10, IEC 62443 SR 2.1, NIST SP 800-207 Tenet 6 | Kontext-Sensor-Logs mit Zeitstempel, API-Response der Policy Engine (JSON-Beispiel), Konfigurationsscreenshots der Sensor-Integration |
| ZTA-01-002  | Funktionstest: Simulation einer signifikanten Kontextänderung (z. B. Gerät wechselt von „compliant“ zu „non-compliant“ oder OT-Prozesszustand wechselt in kritischen Bereich). | Sofortige Neubewertung der Policy → Zugriff wird innerhalb von < 2 Sekunden entzogen / blockiert. | Offen            | NIST SP 800-207 Tenet 3, EU AI Act Art. 15 | Testprotokoll mit Vorher-/Nachher-Zustand, Session-Logs (Terminierung), Alert/SIEM-Eintrag |
| ZTA-01-003  | Nachweis der Nachvollziehbarkeit: Jede Policy-Entscheidung muss mit allen berücksichtigten Kontextwerten, angewandten Regeln und Begründung protokolliert werden. | Jeder Log-Eintrag enthält: Zeitstempel, Kontext-Snapshot, Regel-ID, Entscheidung (allow/deny), Begründungstext. | Offen            | EU AI Act Art. 13, ISO 42001 A.8.3 | Beispiel-Audit-Log-Eintrag (JSON oder CSV-Export), Suchfunktion im Log-System nachgewiesen |
| ZTA-01-004  | Fail-safe-Verhalten: Bei Ausfall oder Fehlen eines oder mehrerer Kontextattribute muss die Policy standardmäßig auf „deny“ entscheiden. | Zugriffsversuch wird verweigert, wenn ≥1 relevantes Attribut fehlt oder ungültig ist (Zero-Trust-Default). | Offen            | NIST SP 800-207 Tenet 1, IEC 62443 SR 1.1 | Test mit simuliertem Sensorausfall, Log-Eintrag „deny – missing context“, Policy-Konfiguration (Screenshot) |
| ZTA-01-005  | Performance unter Last: Die dynamische Bewertung muss auch bei hoher Anfragenrate (≥ 500 Anfragen/s) Latenz < 500 ms einhalten. | Latenz bleibt < 500 ms, keine Fehlentscheidungen oder Timeouts bei definierter Last. | Offen            | EU AI Act Art. 15 (Robustheit), NIST SP 800-207 | Lasttest-Report (z. B. JMeter/Locust), Latenz-Histogramm, Error-Rate = 0 % |
| ZTA-01-006  | Integration KI-basierter Kontextbewertung: Anomalie-Erkennung durch KI-Modell (z. B. Verhaltensdrift, ungewöhnliche OT-Sequenz) muss in die Policy-Entscheidung einfließen. | Bei KI-erkannter Anomalie (Score > Schwellwert) wird Zugriff blockiert oder auf „human review“ eskaliert. | Offen            | ISO 42001 A.6.2.7, EU AI Act Art. 14 | KI-Inferenz-Log + Policy-Trace, Anomalie-Score + Entscheidung (Beispiel-Log), Alert-Screenshot |
| ZTA-01-007  | End-to-End-Nachweisbarkeit: Die gesamte Kette von Kontextdatenerfassung → Aggregation → Policy-Entscheidung → Enforcement muss rekonstruierbar sein. | Durchgängiger Trace mit einheitlicher Trace-ID vom Sensor bis zum Enforcement Point. | Offen            | ISO 42001 A.8.4, NIST SP 800-207 Tenet 7 | Vollständiger Trace-Beispiel (Log-Kette mit Trace-ID), Trace-Visualisierung (falls vorhanden) |
Ergänzungen / Änderungen gegenüber dem Original

Evidenz / Nachweis-Spalte neu hinzugefügt (konkrete, prüfbare Nachweise)
Beschreibungen etwas ausformuliert (vollständige Sätze), aber nicht die Tabellenstruktur verändert
Einige Prüfschritte leicht präzisiert / erweitert (OT-Kontext, KI-Integration, Fail-safe klarer)
Referenzen etwas erweitert und konsistenter gemacht
