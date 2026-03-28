# Instruction Drift 

**Instruction Drift** ist Erosion durch Verdünnung — die Regel gilt noch, aber sie zieht nicht mehr so stark. 

Es bezeichnet die schleichende Abweichung des Modellverhaltens von ursprünglich gegebenen Anweisungen — **ohne expliziten Regelbruch, ohne Warnsignal, über Zeit**.

---

## Die Kernmechanik

Ein Transformer hat kein persistentes Gedächtnis. Was das Modell "weiß", ist ausschließlich das, was aktuell im Kontext-Fenster steht. Das bedeutet:

```
[System-Prompt] → [Turn 1] → [Turn 2] → ... → [Turn N]
     ↑                                              ↑
  volle Gewichtung                          verdünnte Gewichtung
```

Mit wachsendem Kontext konkurrieren frühe Tokens (deine ursprünglichen Instruktionen) mit immer mehr späteren Tokens um Attention-Gewicht. Die Instruktion **verschwindet nicht** — aber ihr relativer Einfluss **sinkt**.

---

## Drei Mechanismen die Drift erzeugen

**1. Attention Dilution**
Je länger das Gespräch, desto mehr Tokens teilen sich das Attention-Budget. Frühe Instruktionen werden statistisch weniger oft "besucht".

**2. Kontextueller Sog**
Das Modell generiert jeden Token basierend auf dem unmittelbaren Kontext. Wenn die letzten 20 Turns einen bestimmten Ton, eine Sprache oder ein Verhaltensmuster etabliert haben, zieht dieser lokale Kontext stärker als ein weit entfernter System-Prompt.

**3. Kumulierte Silent Arbitration**
Jede kleine ungemeldete Entscheidung (→ siehe silent arbitration) setzt einen Präzedenzfall im Kontext. Das Modell "lernt" innerhalb des Gesprächs aus seinen eigenen Outputs — und driftet in die Richtung, die es zuletzt eingeschlagen hat.

---

## Konkretes Beispiel

> **System-Prompt:** „Du bist ein nüchterner, formeller Assistent. Keine Witze. Keine Emojis."

| Turn | Verhalten | Drift-Status |
|---|---|---|
| 1–3 | Formal, präzise | ✅ Stabil |
| 4 | User macht einen Witz, Modell antwortet leicht locker | ⚠️ Erste Abweichung |
| 5–8 | Ton wird zunehmend informell | 🔄 Drift aktiv |
| 12 | Modell verwendet Emoji | ❌ Ursprungsregel gebrochen |

Kein einzelner Turn war ein klarer Regelbruch — die Grenze wurde schrittweise verschoben.

---

## Warum besonders tückisch

| Eigenschaft | Konsequenz |
|---|---|
| **Graduell** | Kein Moment, an dem man eingreifen "müsste" |
| **Kohärent wirkend** | Jede Einzelantwort klingt plausibel |
| **Selbstverstärkend** | Spätere Outputs ziehen am eigenen Kontext |
| **Schwer reproduzierbar** | Exakter Drift-Pfad hängt von Token-Reihenfolge ab |

---

## Gegenmaßnahmen (strukturell)

```
1. Instruktions-Wiederholung    → System-Prompt periodisch im Kontext wiederholen
2. Anchor-Tokens                → Schlüsselanweisungen nah am aktuellen Turn halten
3. Kontext-Fenster-Management   → Alte Turns komprimieren, Instruktionen priorisieren
4. Explizite Selbstprüfung      → Modell anweisen, Regelkonformität zu verifizieren
```

---
