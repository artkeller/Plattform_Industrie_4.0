# Funktionsweise der Mixture of Experts (MoE)

Die **Mixture of Experts (MoE)**-Architektur ist eine hochentwickelte Weiterentwicklung der **Transformer-Architektur**. Sie löst das klassische Dilemma „mehr Parameter = mehr Leistung, aber auch mehr Rechenaufwand“ auf: MoE-Modelle können **Milliarden oder sogar Billionen Parameter** haben und trotzdem bei der **Inferenzgeschwindigkeit** (Antwortzeit) fast so schnell bleiben wie kleine Modelle.

Statt in jeder Transformer-Schicht eine einzelne, „dichte“ Feed-Forward-Schicht (FFN) zu nutzen, ersetzt MoE genau diese FFN-Schicht durch ein spezielles MoE-Modul. Dieses Modul besteht aus zwei Teilen:

- **Den Experten**: Mehrere unabhängige, vollwertige Feed-Forward-Netzwerke (meist 8 oder mehr). Jeder Experte ist während des Trainings auf bestimmte Datenmuster spezialisiert – einer wird z. B. richtig gut bei Mathematik, ein anderer bei Code oder Mehrsprachigkeit.
- **Dem Gating-Netzwerk** (auch **Router** genannt): Ein kleines, trainierbares neuronales Netz, das wie ein intelligenter „Verteiler“ arbeitet.

**So läuft es pro Token ab** (ein Token ist übrigens eine kleine Texteinheit – z. B. ein Wort oder Wortteil):

1. Das Token kommt in die Schicht.
2. Der Router berechnet blitzschnell für jeden Experten eine „Passgenauigkeit“ (Score).
3. Er wählt nur eine **kleine, feste Anzahl** der besten Experten aus – meist die **Top-2** (manchmal Top-3 oder Top-4). Das nennt man **Top-k-Routing**.
4. Nur diese ausgewählten Experten führen die eigentliche Berechnung durch.
5. Ihre Ergebnisse werden gewichtet (basierend auf den Router-Scores) addiert und als Ausgabe weitergegeben.

Der entscheidende Trick ist die **sparsame Aktivierung** (sparse activation): Von hunderten Milliarden Parametern sind pro Token nur ein Bruchteil aktiv. Der Rest „schläft“. Dadurch bleibt die reale Rechenlast pro Token gering – und genau das macht MoE so mächtig.

**Einfache Analogie fürs Verständnis**  
Stell dir eine große Klinik vor: Statt dass jeder Patient von **allen** Ärzten gleichzeitig untersucht wird (wie in einem normalen dichten Modell), gibt es viele Fachabteilungen (die Experten). Der Empfang (Router) schaut sich die Symptome an und schickt den Patienten (das Token) nur zu den **2–3 passendsten Spezialisten**. Der Rest der Klinik bleibt dunkel und spart Energie. Ergebnis: superschnelle, hochpräzise Behandlung bei riesiger Gesamtkapazität.

**Konkrete Beispiele**  
- **Mixtral 8x7B (Mistral AI)**: 8 Experten pro Schicht. Pro Token werden nur **2 Experten** aktiviert. Gesamtparameter: ca. 47 Milliarden – aber nur ca. **13 Milliarden aktiv** pro Token. Das Modell läuft deshalb so schnell wie ein 13B-Modell, schlägt aber in vielen Benchmarks (Mathe, Code, Mehrsprachigkeit) sogar dichte 70B-Modelle wie Llama 2 70B.  
- **Grok-1 (xAI)**: Ein offenes MoE-Modell mit **314 Milliarden Parametern**, ebenfalls 8 Experten und **Top-2-Routing** (nur 2 Experten pro Token aktiv – ca. 25 % der Parameter). Genau diese Architektur macht ein so riesiges Modell überhaupt erst praktikabel und schnell genug für den echten Einsatz.

Zusammengefasst: MoE ist wie ein Superteam, bei dem nicht jeder gleichzeitig arbeiten muss – nur die Besten für den jeweiligen Job. Dadurch skalieren Modelle heute auf ganz neue Größenordnungen, ohne dass die Antwortzeit explodiert.
