# ZTA + KI in der Industrie 4.0

## Semantik als fehlendes Bindeglied

Die industrielle Digitalisierung steht an einem Wendepunkt. Systeme werden zunehmend autonom, Entscheidungen werden datengetrieben, und Künstliche Intelligenz rückt in den Mittelpunkt operativer Prozesse. Gleichzeitig steigt die Notwendigkeit, Vertrauen nicht mehr vorauszusetzen, sondern systematisch zu prüfen. Genau hier treffen **Industrie 4.0**, **Zero Trust Architecture (ZTA)** und **KI** aufeinander – und genau hier zeigt sich ein grundlegendes Problem:

> KI kann heute überzeugend entscheiden, aber nicht verstehen, was sie entscheidet.

Dieses Repository untersucht diese Spannung und macht sichtbar, warum sie nicht nur technisch, sondern strukturell ist.

---

## Ausgangslage: Vernetzte Systeme ohne zentrales Vertrauen

Industrie 4.0 beschreibt keine einzelne Technologie, sondern eine Zustandsveränderung. Produktionssysteme sind nicht mehr isoliert, sondern Teil eines dynamischen Netzwerks aus Maschinen, Plattformen und digitalen Zwillingen. Entscheidungen entstehen verteilt, oft automatisiert und in Echtzeit. Vertrauen wird damit zu einer variablen Größe.

ZTA greift genau hier ein. Vertrauen wird nicht mehr vorausgesetzt, sondern kontinuierlich geprüft. Jede Interaktion ist potenziell unsicher, jede Entscheidung muss kontextualisiert werden. In dieser Architektur wird KI zum operativen Bindeglied zwischen Daten und Entscheidung.

---

## Reales Szenario: Autonome Fertigungszelle im ZTA-Verbund

Betrachtet wird eine vernetzte Fertigungszelle mit Komponenten unterschiedlicher Hersteller. Die Anlage produziert variantenreiche Bauteile und organisiert sich weitgehend selbst. Kommunikation und Zugriff sind vollständig durch ZTA abgesichert. Kein Gerät vertraut einem anderen ohne Prüfung.

Die Entscheidungsarchitektur ist dreistufig aufgebaut:

| Ebene | System               | Rolle                                                    |
| ----- | -------------------- | -------------------------------------------------------- |
| 1     | Embedded GNN         | lokale Zustandsbewertung direkt an der Maschine          |
| 2     | Edge SLM             | kontextuelle Aggregation und kurzfristige Entscheidungen |
| 3     | LLM (Control Center) | Generierung und Anpassung von Policies                   |

Die Systeme arbeiten kooperativ, aber ohne zentrales Vertrauen. Jede Ebene trifft autonome Entscheidungen auf Basis ihrer Sicht auf das System.

---

## Ablauf einer typischen Entscheidung

Ein Werkstück durchläuft mehrere Bearbeitungsschritte. Währenddessen erkennt das Embedded-System einer Maschine eine Abweichung im Vibrationsmuster. Das GNN klassifiziert diese als potenziellen Verschleißzustand und meldet dies an die Edge-Ebene.

Das Edge-SLM aggregiert weitere Informationen. Es berücksichtigt:

* Produktionsauftrag
* aktuelle Auslastung
* Historie ähnlicher Fälle

Auf dieser Basis entscheidet das Edge-System, die Produktionsparameter leicht anzupassen, um Ausschuss zu vermeiden.

Parallel wird das Ereignis an das Control Center gemeldet. Das dort eingesetzte LLM generiert eine neue Policy, die beschreibt, unter welchen Bedingungen ähnliche Maschinen ihr Verhalten anpassen sollen.

Diese Policy wird zurück in das System verteilt und von den Komponenten interpretiert.

---

## Das Dilemma: Plausible Entscheidungen ohne Verständnis

Auf den ersten Blick funktioniert das System. Es reagiert schnell, passt sich dynamisch an und optimiert den Prozess. Doch genau hier liegt das Problem.

Die beteiligten KI-Systeme treffen ihre Entscheidungen auf Basis von Approximationen. Sie erkennen Muster, aber sie verstehen nicht, was diese bedeuten.

Die folgende Tabelle zeigt die kritische Differenz:

| Entscheidungsebene | Wahrnehmung      | Realität                              |
| ------------------ | ---------------- | ------------------------------------- |
| Embedded GNN       | erkennt Anomalie | erkennt statistische Abweichung       |
| Edge SLM           | bewertet Kontext | kombiniert Wahrscheinlichkeiten       |
| LLM                | erzeugt Policy   | generiert sprachlich plausible Regeln |

Die erzeugte Policy kann formal korrekt und technisch umsetzbar sein, aber sie basiert nicht auf einem echten Verständnis des Prozesses. Bedeutung wird nicht erkannt, sondern simuliert.

---

## Kritischer Vorfall: Semantische Fehlinterpretation

Im weiteren Betrieb wird eine ähnliche Situation erkannt, jedoch mit leicht veränderten Rahmenbedingungen. Das LLM hat aus früheren Fällen eine Policy abgeleitet, die aggressive Anpassungen erlaubt, um Produktionsausfälle zu vermeiden.

In diesem Fall führt die Anwendung der Policy jedoch zu einer Überkompensation:

* Maschinenparameter werden zu stark angepasst
* Material wird außerhalb der Spezifikation bearbeitet
* Qualitätsprobleme entstehen verzögert

Das System hat konsistent gehandelt, aber falsch entschieden.

Der Grund liegt in der fehlenden Semantik:

| Aspekt                   | Erwartung                 | Realität im System   |
| ------------------------ | ------------------------- | -------------------- |
| Bedeutung der Abweichung | physikalischer Verschleiß | statistisches Muster |
| Kontextbewertung         | situativ korrekt          | ähnlichkeitsbasiert  |
| Policy-Interpretation    | zielgerichtet             | sprachlich plausibel |

---

## ZTA-Perspektive: Vertrauen ohne Verständnis ist unmöglich

ZTA verlangt, dass jede Entscheidung überprüfbar und begründet ist. In diesem Szenario jedoch entstehen Entscheidungen, deren Grundlage nicht semantisch interpretierbar ist.

Die folgende Gegenüberstellung zeigt das Problem:

| ZTA-Anforderung        | Verhalten des Systems  | Ergebnis                            |
| ---------------------- | ---------------------- | ----------------------------------- |
| Verifikation           | Policy wird angewendet | keine inhaltliche Prüfung möglich   |
| Kontextbewertung       | KI nutzt Muster        | Kontext nicht verstanden            |
| Vertrauensentscheidung | automatisiert          | Vertrauen basiert auf Approximation |

Das System erfüllt formal die Anforderungen von ZTA, verletzt aber deren eigentliche Intention.

---

## Architekturbruch: Wo das System scheitert

Das Problem liegt nicht in einzelnen Komponenten, sondern in der Gesamtarchitektur. Die drei Ebenen sind funktional korrekt, aber semantisch entkoppelt.

| Ebene    | Stärke            | Schwäche           |
| -------- | ----------------- | ------------------ |
| Embedded | Echtzeitfähigkeit | keine Kontexttiefe |
| Edge     | Aggregation       | keine Bedeutung    |
| LLM      | Generalisierung   | keine Wahrheit     |

Die Systeme erzeugen gemeinsam eine Illusion von Verständnis, die in kritischen Situationen zusammenbricht.

---

## Konsequenz: Semantik muss explizit werden

Die Lösung liegt nicht in größeren Modellen oder mehr Daten. Sie liegt in der Architektur.

Bedeutung muss explizit modelliert werden:

* durch Ontologien
* durch formale Prozessmodelle
* durch klare semantische Regeln

Erst dann können:

* KI Entscheidungen unterstützen
* ZTA Vertrauen bewerten
* Industrie 4.0 Systeme robust agieren

---

## Fazit

Das beschriebene Szenario ist kein Sonderfall, sondern prototypisch für zukünftige industrielle Systeme.

> Autonome Systeme können Entscheidungen skalieren.
> Aber ohne Semantik skalieren sie auch Fehler.

KI liefert die Dynamik, ZTA liefert die Kontrolle.
Was fehlt, ist das Verständnis.

---
