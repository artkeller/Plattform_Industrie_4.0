# ZTA + KI in der Industrie 4.0

## Semantik als fehlendes Bindeglied

Die industrielle Digitalisierung steht an einem Wendepunkt. Systeme werden zunehmend autonom, Entscheidungen werden datengetrieben, und Künstliche Intelligenz rückt in den Mittelpunkt operativer Prozesse. Gleichzeitig steigt die Notwendigkeit, Vertrauen nicht mehr vorauszusetzen, sondern systematisch zu prüfen. Genau hier treffen **Industrie 4.0**, **Zero Trust Architecture (ZTA)** und **KI** aufeinander – und genau hier zeigt sich ein grundlegendes Problem:

> KI kann heute überzeugend entscheiden, aber nicht verstehen, was sie entscheidet.

Dieses Repository untersucht diese Spannung und macht sichtbar, warum sie nicht nur technisch, sondern strukturell ist.

---

## Ausgangslage: Vernetzte Systeme ohne zentrales Vertrauen

Industrie 4.0 beschreibt keine einzelne Technologie, sondern eine Zustandsveränderung. Produktionssysteme sind nicht mehr isoliert, sondern Teil eines dynamischen Netzwerks aus Maschinen, Plattformen und digitalen Zwillingen. Entscheidungen entstehen verteilt, oft automatisiert und in Echtzeit. Vertrauen wird damit zu einer variablen Größe.

ZTA greift genau hier ein. Das Paradigma verschiebt sich von implizitem Vertrauen zu expliziter Verifikation. Jede Anfrage, jede Kommunikation, jede Entscheidung muss begründet und überprüfbar sein. Vertrauen ist kein Zustand mehr, sondern ein Prozess.

In dieser Umgebung wird KI zum entscheidenden Faktor. Sie aggregiert Daten, erkennt Muster und trifft Vorhersagen. Doch genau an dieser Stelle entsteht ein Bruch.

---

## Das strukturelle Problem: KI operiert ohne Semantik

Moderne KI-Systeme erzeugen den Eindruck von Verständnis, weil sie Sprache, Muster und Zusammenhänge überzeugend modellieren. Tatsächlich operieren sie jedoch auf einer anderen Ebene. Sie approximieren Funktionen, nicht Bedeutungen.

Die folgende Gegenüberstellung verdeutlicht diesen Unterschied:

| Dimension    | Menschliches Verständnis         | Aktuelle KI                            |
| ------------ | -------------------------------- | -------------------------------------- |
| Bedeutung    | intrinsisch vorhanden            | nicht vorhanden                        |
| Kontext      | bewusst integriert               | statistisch angenähert                 |
| Wissen       | strukturiert und interpretierbar | implizit und verteilt                  |
| Entscheidung | begründet                        | wahrscheinlichkeitsbasiert             |
| Wahrheit     | bewertbar                        | nicht unterscheidbar von Plausibilität |

Diese Differenz bleibt oft verborgen, solange KI unterstützend arbeitet. In autonomen, vernetzten Systemen wird sie jedoch kritisch.

---

## Semantik als zentrale Leerstelle

Die eigentliche Herausforderung liegt nicht in der Leistungsfähigkeit der Modelle, sondern in ihrem Fundament. KI-Modelle, insbesondere Transformer-basierte Architekturen, verarbeiten Sprache als Sequenz von Symbolen. Bedeutung entsteht dabei nicht, sondern wird simuliert.

Die drei Kapitel dieses Repositories beschreiben diese Problematik aus unterschiedlichen Perspektiven und bauen logisch aufeinander auf:

| Kapitel                                                                                                                            | Perspektive              | Aussage                                 |
| ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | --------------------------------------- |
| [Transformer](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/KI-Modelle/Semantik/Transformer.md)     | technische Basis         | KI erkennt Muster, aber keine Bedeutung |
| [Hybrid-Modell](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/KI-Modelle/Semantik/Hybrid-Modell.md) | architektonischer Ansatz | Semantik muss explizit ergänzt werden   |
| [Approximation](https://github.com/artkeller/Plattform_Industrie_4.0/tree/main/ZTA%2BKI_2026/KI-Modelle/Semantik/Approximation.md) | theoretische Grenze      | KI bleibt grundsätzlich Approximation   |

Die Kapitel sind so aufgebaut, dass sie sowohl einzeln gelesen werden können als auch gemeinsam eine vollständige Argumentation ergeben. Jedes Kapitel beantwortet eine eigene Frage, die im industriellen Kontext unmittelbar relevant ist: Wie funktioniert KI tatsächlich, wie lässt sie sich erweitern, und wo liegen ihre unüberwindbaren Grenzen?

---

## ZTA trifft auf KI: Ein ungelöstes Spannungsfeld

ZTA verlangt, dass Systeme Entscheidungen über Vertrauen treffen. Diese Entscheidungen müssen kontextabhängig, nachvollziehbar und korrekt sein. KI hingegen liefert genau das Gegenteil: probabilistische Ergebnisse ohne intrinsische Bedeutung.

Die daraus entstehende Spannung lässt sich klar strukturieren:

| Anforderung ZTA        | Eigenschaft KI            | Konflikt                                           |
| ---------------------- | ------------------------- | -------------------------------------------------- |
| Verifikation           | Approximation             | Ergebnisse sind nicht prüfbar im semantischen Sinn |
| Kontextbewertung       | Mustererkennung           | Kontext wird nicht verstanden                      |
| Nachvollziehbarkeit    | Black Box                 | Entscheidungen sind nicht erklärbar                |
| Vertrauensentscheidung | Wahrscheinlichkeitsmodell | Vertrauen wird simuliert, nicht bewertet           |

Damit wird deutlich, dass KI allein keine tragfähige Grundlage für vertrauensrelevante Entscheidungen sein kann.

---

## Architekturfolgen für Industrie 4.0

In einer klassischen IT-Umgebung lassen sich diese Schwächen oft kompensieren. In der Industrie 4.0 hingegen wirken sie systemisch. Fehler verbreiten sich nicht lokal, sondern entlang vernetzter Strukturen. Entscheidungen skalieren unmittelbar.

Die notwendige Konsequenz ist architektonisch:

| Ebene     | Rolle    | Notwendigkeit                             |
| --------- | -------- | ----------------------------------------- |
| Daten     | KI       | Verarbeitung und Mustererkennung          |
| Bedeutung | Semantik | explizite Modellierung (z. B. Ontologien) |
| Vertrauen | ZTA      | regelbasierte, nachvollziehbare Bewertung |

Erst das Zusammenspiel dieser Ebenen ermöglicht robuste Systeme. KI bleibt dabei ein Werkzeug, aber nicht die Instanz, die Bedeutung oder Vertrauen definiert.

---

## Fazit

Die Integration von KI in industrielle Systeme ist keine reine Technologiefrage. Sie ist eine Frage der Architektur und des Verständnisses ihrer Grenzen.

> KI liefert leistungsfähige Approximationen.
> Semantik und Vertrauen müssen außerhalb der KI entstehen.

ZTA macht diese Notwendigkeit sichtbar, Industrie 4.0 macht sie unvermeidbar.

Dieses Repository liefert die Grundlage, um genau diese Zusammenhänge zu verstehen und systematisch zu adressieren.
