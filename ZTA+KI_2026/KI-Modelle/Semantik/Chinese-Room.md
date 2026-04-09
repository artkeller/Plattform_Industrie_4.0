# Das KI-Dilemma einfach erklärt

## Der „Chinese Room“-Effekt in der Fertigung

Stellen wir uns eine ganz einfache Situation vor.

Eine Fertigungsanlage arbeitet vollautomatisch. Sensoren liefern Daten, Systeme reagieren darauf, und KI unterstützt Entscheidungen. Alles läuft stabil – bis auf einmal eine Abweichung erkannt wird.

Die KI reagiert sofort, passt Parameter an, generiert neue Regeln und verteilt diese im System. Technisch gesehen funktioniert alles korrekt.

Und trotzdem entsteht ein Fehler.

Warum?

---

## Der „Chinese Room“ – das Gedankenexperiment

Der Philosoph John Searle hat ein bekanntes Beispiel formuliert, den sogenannten „Chinese Room“.

Ein Mensch sitzt in einem Raum und bekommt chinesische Schriftzeichen hereingereicht. Er versteht kein Chinesisch. Trotzdem hat er ein Regelbuch, mit dem er passende Antworten erzeugen kann.

Für jemanden außerhalb des Raums sieht es so aus, als würde der Mensch Chinesisch verstehen.

In Wirklichkeit passiert etwas anderes:

| Beobachtung von außen   | Realität im Inneren      |
| ----------------------- | ------------------------ |
| sinnvolle Antworten     | reine Symbolverarbeitung |
| scheinbares Verständnis | kein Verständnis         |
| richtige Reaktion       | Anwendung von Regeln     |

---

## Übertragung auf die Fertigung

Genau das passiert in modernen KI-Systemen in der Industrie.

Die KI:

* verarbeitet Sensordaten
* erkennt Muster
* erzeugt Entscheidungen

Aber sie versteht nicht:

* was eine Maschine ist
* was Verschleiß bedeutet
* warum ein Prozess kritisch ist

Die folgende Gegenüberstellung macht das deutlich:

| Verhalten der KI     | Tatsächliche Fähigkeit            |
| -------------------- | --------------------------------- |
| erkennt Fehler       | erkennt statistische Abweichungen |
| bewertet Situation   | vergleicht Muster                 |
| entscheidet sinnvoll | erzeugt wahrscheinliche Antworten |

---

## Das konkrete Problem im System

Im beschriebenen Beispiel mit GNN, Edge-SLM und LLM passiert Folgendes:

Die Systeme reagieren auf Daten und erzeugen eine neue Regel (Policy), die im gesamten Fertigungsverbund angewendet wird.

Diese Regel ist:

* technisch korrekt formuliert
* konsistent mit bisherigen Daten
* logisch nachvollziehbar

Aber sie kann trotzdem falsch sein.

Warum?

Weil die KI wie der „Chinese Room“ arbeitet:

> Sie kombiniert Zeichen und Muster – ohne zu verstehen, was sie bedeuten.

---

## Warum das gefährlich ist

In einer Fertigung ist das kein theoretisches Problem.

Es führt konkret zu:

| Erwartung                        | Realität                           |
| -------------------------------- | ---------------------------------- |
| KI versteht den Prozess          | KI simuliert ihn                   |
| KI bewertet richtig              | KI schätzt wahrscheinlich          |
| KI trifft sichere Entscheidungen | KI trifft plausible Entscheidungen |

Das Problem tritt besonders dann auf, wenn:

* Situationen leicht vom Training abweichen
* mehrere Systeme interagieren
* Entscheidungen automatisch skaliert werden

---

## Verbindung zu ZTA

Zero Trust bedeutet:

> Jede Entscheidung muss überprüfbar und vertrauenswürdig sein.

Doch hier entsteht ein Widerspruch:

| ZTA-Anforderung     | KI-Verhalten                  |
| ------------------- | ----------------------------- |
| Vertrauen begründen | keine Begründung möglich      |
| Kontext verstehen   | Kontext wird nicht verstanden |
| Entscheidung prüfen | nur Ergebnis sichtbar         |

Die KI liefert Antworten, aber keine Bedeutung.

---

## Fazit

Der „Chinese Room“-Effekt zeigt das eigentliche Problem:

> KI kann sich so verhalten, als würde sie verstehen – tut es aber nicht.

Für die Industrie bedeutet das:

* Systeme wirken intelligent
* Entscheidungen wirken korrekt
* aber die Grundlage bleibt unverständlich

Und genau deshalb gilt:

> In kritischen Systemen reicht „plausibel“ nicht aus.
> Es muss „verstanden“ sein.

Das ist der Punkt, an dem Architektur entscheidend wird.
