# Silent Truncation

**Silent Truncation** ist das Modell, das sagt „ich habe alles gelesen" — und dabei nicht lügt, aber auch nicht die ganze Wahrheit sagt.

Es bezeichnet das Verhalten, bei dem das Modell Input oder Output **stillschweigend abschneidet, komprimiert oder ignoriert** — ohne zu melden, dass Information verloren gegangen ist.

Es gibt zwei Richtungen:

---

### Input-Truncation (Kontext-Eingang)

Wenn ein Prompt das Kontext-Fenster überschreitet oder bestimmte Bereiche durch Attention-Mechanismen effektiv untergewichtet werden:

```
[Token 1 ... Token 8000] [Token 8001 ... Token 12000]
        ↑                           ↑
   aktiv verarbeitet          nominell vorhanden,
                              aber Attention-Gewicht → nahe 0
```

Das Modell **behauptet nicht**, dass es Teile ignoriert hat. Es antwortet einfach — als ob alles verarbeitet wurde.

**Bekanntes Muster:** der sogenannte *Lost-in-the-Middle*-Effekt. Informationen in der Mitte langer Kontexte werden systematisch schlechter verarbeitet als Informationen am Anfang oder Ende.

---

### Output-Truncation (Antwort-Ausgang)

Das Modell bricht eine Antwort ab oder vereinfacht sie — ohne zu signalisieren, dass die vollständige Antwort länger oder komplexer wäre:

- Eine Liste wird bei Punkt 7 von 20 stillschweigend beendet
- Ein Argument wird halbfertig formuliert
- Eine Bedingung in einer Anweisung wird weggelassen
- Code wird ohne fehlende Teile zurückgegeben

Der Output wirkt **vollständig** — das ist das eigentliche Problem.

---

## Verhältnis zu den anderen Konzepten

```
Silent Arbitration   →  Konflikt wird nicht gemeldet
Instruction Drift    →  Regelabweichung wird nicht gemeldet
Silent Truncation    →  Informationsverlust wird nicht gemeldet
```

Alle drei teilen dieselbe Grundstruktur: **das Modell signalisiert keine Unsicherheit, obwohl es sie geben müsste.**

---

