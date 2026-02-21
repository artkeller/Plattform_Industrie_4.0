## Modul ZTA Teil 3: Beispielhafter Ausschnitt zur detaillierten Verifikation der Kontextdatenerfassung (ZTA-01-001)

**Aufteilung der Anforderung ZTA-01-001 in Prüfschritte:**

Diese umfassende Anforderung wird in weitere Prüfschritte aufgeteilt, um eine detaillierte Verifizierung auf Attributebene und eine präzisere Bewertung zu ermöglichen

Hier ist die weitere Untergliederung der Anforderung ZTA-01-001: Verifikation der Kontextdatenerfassung in einzelne, spezifische Prüfschritte, die jeweils die Erfassung eines bestimmten Kontextdatums oder Signals adressieren und eine individuelle Bewertung erlauben.

**Hinweis**: Detaillierte Prüfkataloge für ZTA-Systeme mit KI-Assistenz in dynamischen Industrie 4.0-Umgebungen sind erst im Aufbau und müssen flexibel an die spezifischen Systemarchitekturen angepasst werden.

Tabelle 5 - Ausschnitt: Detaillierte Verifikationspunkte der Kontextdatenerfassung (ZTA-01-001)

| Prüfschritt-ID | Verifikationspunkt-Beschreibung | Erwartetes Ergebnis | Bewertungsstatus (PASSED / INAPPRAISED/ FAILED) | Referenz (z.B. ISO 42001, ISO 27001, IEC 62443) |
| --- | --- | --- | --- | --- |
| Erfassung von Identitätskontext (Benutzer & Maschine) |  |  |
| ZTA-01-001-001 | Benutzeridentität (Mensch): Überprüfung, ob die ZTA-Plattform die aktive und verifizierte Identität des menschlichen Benutzers in Echtzeit erfasst (z.B. über IAM-Systeme). | Die authentifizierte und autorisierte Benutzeridentität wird durchgängig an die ZTA-Richtlinien-Engine übermittelt und ist in den Zugriffs-Logs nachvollziehbar. |  | ISO 42001: 8.2.1; ISO 27001: A.9.2.1 |
| ZTA-01-001-002 | Maschinen-/Geräteidentität (OT/IT): Überprüfung, ob die eindeutige und verifizierte Identität jedes anfragenden Geräts (z.B. IoT-Sensor, SPS, Roboter, Workstation) in Echtzeit erfasst wird. | Jedes Gerät im Netzwerk besitzt eine eindeutige, verwaltete Identität (z.B. Zertifikat, ID), die an die ZTA-Engine übermittelt und protokolliert wird. |  | ISO 42001: 8.2.1; ISO 27001: A.9.2.2 |
| ZTA-01-001-003 | Rollen/Berechtigungen: Überprüfung, ob die aktuell zugewiesenen Rollen und Berechtigungen der anfragenden Identität (Benutzer oder Maschine) dynamisch erfasst werden. | Die aktuellen Rollen und Berechtigungen der Identität werden konsistent aus dem zentralen Verzeichnisdienst abgerufen und fließen in die Zugriffsentscheidung ein. |  | ISO 42001: 8.2.1;ISO 27001: A.9.2.3 |
| Erfassung von Geräteintegrität und Haltung |  |  |
| ZTA-01-001-004 | Geräteintegrität (Software/Firmware): Überprüfung, ob der Integritätszustand der Software und Firmware des anfragenden Geräts (z.B. ungepatchte Schwachstellen, unerlaubte Konfiguration) in Echtzeit erfasst wird. | Der Integritätsstatus (z.B. 'compliant', 'vulnerable', 'compromised') jedes Geräts wird in Echtzeit bewertet und an die ZTA-Engine übermittelt. |  | ISO 42001: 8.2.1;ISO 27001: A.13.1.2 |
| ZTA-01-001-005 | Geräteintegrität (Hardware/Physikalisch): Überprüfung, ob physische Integritätsmerkmale des Geräts (z.B. Manipulationsschutz, nicht-autorisierte USB-Geräte) erfasst und in die Bewertung einbezogen werden, sofern relevant. | Physische Integritätssensoren/Überwachungssysteme melden ihren Status an die ZTA-Plattform, und diese Daten fließen in die Gerätebewertung ein. |  | ISO 42001: 8.2.1;ISO 27001: A.11.2.5 |
| Erfassung von Netzwerk- und Standortkontext |  |  |
| ZTA-01-001-006 | Netzwerksegment/Zonen: Überprüfung, ob das aktuelle Netzwerksegment oder die Sicherheitszone, aus der die Zugriffsanfrage kommt, korrekt identifiziert wird (insbesondere OT-Zonen). | Die ZTA-Plattform identifiziert korrekt das Quellnetzwerksegment oder die Sicherheitszone der Anfrage, basierend auf der Netzwerktopologie. |  | ISO 42001: 8.2.1;ISO 27001: A.13.1.3 |
| ZTA-01-001-007 | Geografischer Standort/Logischer Standort: Überprüfung, ob der geografische oder logische Standort des anfragenden Geräts/Benutzers erfasst und in die Richtlinienbewertung einbezogen wird. | Der Standort (z.B. interne IP-Range, GPS-Daten für mobile Geräte, externe IP-Adresse) der Anfrage wird korrekt erfasst und für standortbasierte Richtlinien verwendet. |  | ISO 42001: 8.2.1;ISO 27001: A.13.1.4 |
| Erfassung von OT-Prozesszustand und Umgebungskontext |  |  |
| ZTA-01-001-008 | OT-Prozesszustand: Überprüfung, ob der aktuelle Betriebsstatus des angefragten oder beeinflussten OT-Prozesses (z.B. "Produktion läuft", "Wartungsmodus", "Not-Aus") in Echtzeit erfasst wird. | Die ZTA-Plattform empfängt den aktuellen und korrekten OT-Prozesszustand aus den Leitsystemen oder relevanten Sensoren. |  | ISO 42001: 8.2.1;IEC 62443-3-3: SR 3.1 |
| ZTA-01-001-009 | Umgebungsbedingungen (Kontext-Sensoren): Überprüfung, ob relevante Umgebungsdaten (z.B. Temperatur, Druck, Vibrationen) von Sensoren erfasst und bei kritischen ZTA-Entscheidungen berücksichtigt werden. | Kritische Umgebungsdaten werden in Echtzeit von den Sensoren gesammelt und sind für die ZTA-Richtlinien-Engine zugänglich. |  | ISO 42001: 8.2.1;IEC 62443-3-3: SR 3.2 |
| Erfassung von Verhaltensmustern und Risikoindikatoren (KI-gestützt) |  |
| ZTA-01-001-010 | Verhaltenshistorie/Baseline: Überprüfung, ob die historische Verhaltensbaseline für Benutzer und Geräte (was ist "normales" Verhalten) erfasst und von KI-Systemen gepflegt wird. | Eine Baseline des normalen Verhaltens wird für relevante Entitäten geführt, und Abweichungen werden von der KI erkannt. |  | ISO 42001: 8.2.1, 8.2.3 |
| ZTA-01-001-011 | Risikobewertung durch KI: Überprüfung, ob KI-Systeme in Echtzeit eine dynamische Risikobewertung für jede Zugriffsanfrage basierend auf allen erfassten Kontextdaten und Verhaltensmustern durchführen und dieses Risiko an die ZTA-Engine übermitteln. | Die KI generiert für jede Anfrage einen dynamischen Risikowert, der in die ZTA-Richtlinienbewertung einfließt, und die KI-Entscheidungsgrundlage ist nachvollziehbar. |  | ISO 42001: 8.2.1, 8.2.3 |
| ZTA-01-001-012 | Bedrohungsinformationen (Threat Intelligence): Überprüfung, ob aktuelle Bedrohungsinformationen (z.B. IOCs, C&C-Server) in Echtzeit erfasst und von der ZTA-Plattform sowie integrierten KI-Systemen zur Risikobewertung genutzt werden. | Die ZTA-Plattform und KI-Systeme integrieren relevante und aktuelle Threat Intelligence Feeds zur Verbesserung der Detektionsfähigkeit. |  | ISO 42001: 8.2.1;ISO 27001: A.16.1.7 |

Dieses Beispiel dient der **Referenzierung** und kann auch als Orientierungshilfe verstanden werden, die je nach Kontext individuell angepasst werden sollte.
