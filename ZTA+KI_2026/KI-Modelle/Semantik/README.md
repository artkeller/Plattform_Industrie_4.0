# ZTA + KI in der Industrie 4.0

## Semantik als fehlendes Bindeglied

Die industrielle Digitalisierung steht an einem Wendepunkt. Systeme werden zunehmend autonom, Entscheidungen werden datengetrieben, und Künstliche Intelligenz rückt in den Mittelpunkt operativer Prozesse. Gleichzeitig steigt die Notwendigkeit, Vertrauen nicht mehr vorauszusetzen, sondern systematisch zu prüfen. Genau hier treffen Industrie 4.0, Zero Trust Architecture (ZTA) und KI aufeinander – und genau hier zeigt sich ein grundlegendes Problem:

> KI kann heute überzeugend entscheiden, aber nicht verstehen, was sie entscheidet.

Dieses Repository beschreibt dieses Spannungsfeld – technisch, architektonisch und anhand eines realitätsnahen Szenarios.

---

## Ausgangslage: Vernetzte Systeme ohne zentrales Vertrauen

Industrie 4.0 bedeutet vollständig vernetzte, dynamische Systeme. Maschinen, Plattformen und digitale Zwillinge interagieren kontinuierlich. Entscheidungen entstehen verteilt und oft autonom.

ZTA ersetzt dabei implizites Vertrauen durch permanente Verifikation. Jede Kommunikation, jede Entscheidung und jede Interaktion muss kontextabhängig bewertet werden.

KI übernimmt in diesem Umfeld eine zentrale Rolle: Sie verarbeitet Daten, erkennt Muster und trifft operative Entscheidungen. Doch genau hier entsteht ein strukturelles Problem.

---

## Das strukturelle Problem: KI ohne Semantik

Moderne KI-Systeme erzeugen den Eindruck von Verständnis. Tatsächlich arbeiten sie jedoch auf Basis von Approximationen.

| Dimension    | Mensch     | KI                         |
| ------------ | ---------- | -------------------------- |
| Bedeutung    | vorhanden  | nicht vorhanden            |
| Kontext      | verstanden | statistisch angenähert     |
| Wissen       | explizit   | implizit                   |
| Entscheidung | begründet  | wahrscheinlichkeitsbasiert |
| Wahrheit     | bewertbar  | nicht unterscheidbar       |

Diese Differenz bleibt oft unsichtbar – bis Systeme autonom handeln.

---

## Semantik-Kapitel (Grundlage)

Die folgenden Dokumente bilden die theoretische Basis:

| Kapitel                                                                                                                            | Inhalt                     | Leitfrage                          |
| ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------- | ---------------------------------- |
| [Transformer](Transformer.md)     | Funktionsweise heutiger KI | Wie arbeitet KI wirklich?          |
| [Hybrid-Modell](Hybrid-Modell.md) | Kombination mit Wissen     | Wie ergänzt man Semantik?          |
| [Approximation](Approximation.md) | fundamentale Grenze        | Warum bleibt das Problem bestehen? |

Diese drei Kapitel erklären, warum KI strukturell kein echtes Verständnis entwickeln kann.

---

## Ergänzende Praxis und Intuition

Die theoretischen Grundlagen werden durch zwei zusätzliche Perspektiven ergänzt:

| Dokument                                                                                                                                           | Rolle     | Nutzen                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ----------------------------------------- |
| [Beispiel: Autonome Fertigungszelle](Beispiel.md) | Praxis    | zeigt das Problem im realen Systemverbund |
| [Chinese Room Erklärung](Chinese-room.md)         | Intuition | macht das Problem einfach verständlich    |

Das Beispiel zeigt konkret, wie ein dreistufiges System aus Embedded GNN, Edge SLM und LLM in einer ZTA-geschützten Fertigung formal korrekt arbeitet – und dennoch falsche Entscheidungen trifft.

Die Chinese-Room-Erklärung liefert die intuitive Begründung dafür:

> Ein System kann sich korrekt verhalten, ohne zu verstehen, was es tut.

---

## ZTA trifft auf KI: Der eigentliche Konflikt

ZTA verlangt überprüfbare, kontextabhängige Entscheidungen.
KI liefert statistische Approximationen.

| ZTA-Anforderung     | KI-Eigenschaft  | Problem                           |
| ------------------- | --------------- | --------------------------------- |
| Verifikation        | Approximation   | keine semantische Prüfung möglich |
| Kontextbewertung    | Mustererkennung | Kontext wird nicht verstanden     |
| Nachvollziehbarkeit | Black Box       | Entscheidungen schwer erklärbar   |
| Vertrauen           | Simulation      | kein echtes Verständnis           |

Damit entsteht ein grundlegender Widerspruch.

---

## Architekturfolgen

Die Lösung liegt nicht in besseren Modellen, sondern in klarer Architekturtrennung:

| Ebene     | Funktion                                 |
| --------- | ---------------------------------------- |
| Daten     | KI zur Mustererkennung                   |
| Bedeutung | explizite Semantik (Modelle, Ontologien) |
| Vertrauen | ZTA-Regeln und Verifikation              |

Nur dieses Zusammenspiel ermöglicht robuste Systeme.

---

## Lesehilfe

Dieses Repository kann je nach Ziel unterschiedlich gelesen werden:

| Ziel                    | Einstieg      |
| ----------------------- | ------------- |
| Technisches Verständnis | Transformer   |
| Architektur             | Hybrid-Modell |
| Grundsatz               | Approximation |
| Praxis                  | Beispiel      |
| Intuition               | Chinese Room  |

Empfohlene Reihenfolge:

> Theorie → Architektur → Grenze → Praxis → Intuition

---

## Fazit

Industrie 4.0 braucht:

* KI für Skalierung
* ZTA für Sicherheit
* Semantik für Verständnis

Aber:

> KI allein liefert keine Semantik.

Und daraus folgt:

> Man kann einem System kein Vertrauen übertragen, wenn es nicht versteht, was es tut.

---

