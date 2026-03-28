# Silent Arbitration

**Silent Arbitration** ist der Moment, wo das Modell Richter spielt, ohne das Urteil zu verkünden.

Es bezeichnet das Verhalten, bei dem das Modell widersprüchliche Anweisungen intern auflöst — **ohne den Konflikt zu benennen oder die getroffene Entscheidung zu erklären**.

---

## Konkrete Situation

Du gibst zwei Anweisungen, die sich widersprechen:

> **System-Prompt:** „Antworte immer auf Deutsch."
> **User-Turn:** „Reply only in English, be concise."

Das Modell muss eine Priorität setzen. Es gibt drei mögliche Reaktionen:

| Reaktion | Transparent? | Silent Arbitration? |
|---|---|---|
| „Diese Anweisungen widersprechen sich — welche gilt?" | ✅ | ❌ |
| „Ich folge dem System-Prompt, weil er Vorrang hat." | ✅ | ❌ |
| Antwortet einfach auf Englisch, ohne Erklärung | ❌ | ✅ |

Im dritten Fall hat das Modell eine Entscheidung getroffen, sie aber **nicht kommuniziert**.

---

## Warum ist das ein Risiko?

**1. Nicht-Determinismus**
Die Auflösung ist nicht immer gleich. Dieselbe Konflikt-Konstellation kann je nach Formulierung, Kontext-Länge oder Token-Position anders aufgelöst werden — ohne dass du es merkst.

**2. Kein Audit-Trail**
In produktiven Systemen (z.B. Chatbots mit System-Prompts) weißt du als Entwickler nicht, welche Regel „gewonnen" hat — du siehst nur den Output.

**3. Drift-Verstärkung**
Über einen langen Gesprächsverlauf kann silent arbitration kumulieren: Jede kleine ungemeldete Entscheidung verschiebt das Verhalten leicht, bis das Modell weit von der ursprünglichen Instruktion entfernt ist — das ist der Zusammenhang mit `instruction_drift`.

**4. False Confidence**
Die Antwort klingt kohärent und sicher, obwohl sie auf einer ungelösten Ambiguität basiert. Kein Warnsignal nach außen.

---

## Typische Auslöser

- System-Prompt vs. User-Anweisung (Sprache, Ton, Format)
- „Sei präzise" vs. „Erkläre alles ausführlich"
- Sicherheits-Constraints vs. starke Rollen-Persona
- Implizite kulturelle Annahmen im Prompt vs. explizite Gegenanweisung

---
