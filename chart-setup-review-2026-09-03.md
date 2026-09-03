# Chart-Setup Review — /MNQ & /ES, 03.09.2026 (10:48)

**Instrumente:** /MNQ:XCME (1H, 1m), /ES:XCME (Footprint 1m, 3m)
**Plattform:** TheTradingPit (dxFeed), Trading-Simulator
**Aktive Tools:** TD Sequential (Lvl2 sichtbar), Fractals, FVG, RSI (14, Close), Cumulative Delta (by Volume), Footprint/Orderflow (nur /ES)

Marktlage im Screenshot: /MNQ 1m ist von ~29.180 auf ~29.300 gelaufen und konsolidiert/pullt jetzt zurück in Richtung 29.230–29.250. /ES zeigt einen scharfen Flush von ~7.500 auf ~7.477 mit anschließender V-förmiger Erholung Richtung 7.493–7.505.

---

## 1. Zeitebenen-Kombination (1H / 1m / 5m bzw. 3m) — sinnvoll oder lückenhaft?

**Kernproblem: Die beiden Instrumente fahren ein asymmetrisches Multi-Timeframe-Setup.**

- **/MNQ:** 1H (Kontext) + 1m (Ausführung) — großer Sprung zwischen den Ebenen, es fehlt eine Bindeglied-Zeitebene (z. B. 10m/15m), die die 1H-Struktur mit dem 1m-Timing verbindet.
- **/ES:** 1m (Footprint) + 3m (Kontext) — hier ist die Lücke klein, aber es fehlt umgekehrt eine höhere Zeitebene (15m/1H), die dem /MNQ-1H-Chart entspricht. /ES hat dadurch keinen übergeordneten Trendrahmen, nur kurzfristigen Kontext.

**Konsequenz:** Für /MNQ hat man eine fundierte Top-Down-Bias, aber grobes Timing; für /ES hat man feines Timing, aber keine verlässliche übergeordnete Struktur (Trend, Major S/R, TD-Sequential auf Tagesbasis fehlt komplett für /ES).

**Empfehlung:**
- Für beide Instrumente dasselbe 3-Ebenen-Schema fahren, z. B. **1H (Bias) → 15m (Struktur/Setup) → 1m (Trigger)**.
- Falls der 3m-Chart bewusst als "mittlere" Ebene für /ES gedacht ist, dann fehlt dort noch eine 1H-Ebene, um Konsistenz zur MNQ-Seite herzustellen.
- Die aktuelle Kombination ist nicht falsch, aber **nicht symmetrisch** — dadurch wird /ES faktisch nur intraday-taktisch gehandelt, während /MNQ strategischer bewertet wird. Das sollte eine bewusste Entscheidung sein, keine Lücke aus Versehen.

---

## 2. FVG- und Fractal-Markierung im Verhältnis zu TD Sequential (Lvl2)

**TD Sequential steht aktuell erst bei Zählung 2** (sowohl auf /MNQ 1H als auch 1m sichtbar). Das ist früh in der Setup-Phase — eine Erschöpfungsaussage (Countdown 8/9, "Perfected") ist noch nicht gegeben.

- Die **FVG-Zonen** (rote Zone ~29.270–29.290 auf 1m, größere Zone auf 1H) markieren dagegen bereits potenzielle Reaktionsbereiche. Wenn TD Sequential erst bei 2 steht, ist eine FVG-Reaktion an dieser Stelle **kein bestätigtes Reversal-Signal**, sondern bestenfalls eine taktische Zone innerhalb eines noch laufenden Trendsegments.
- Die **Fractal-Marker auf /MNQ 1m** liegen bei 29.232,75 und 29.231,75 — das sind **nur 1 Tick auseinander**, also praktisch derselbe Bereich. Das deutet auf eine zu sensible Fractal-Periode (Standard 5-Bar) hin, die zwei benachbarte Kerzen als "Swing-Hoch/Tief" markiert, obwohl strukturell kein relevanter Swing vorliegt. Diese Feinkörnigkeit passt nicht zur Größenordnung der FVG-Zonen, die 15–20 Punkte breit sind.

**Fazit:** FVG- und Fractal-Signale sind aktuell **nicht kohärent** mit dem TD-Sequential-Stand — sie zeigen taktische Zonen, während TD Sequential noch keine Timing-Bestätigung liefert.

**Empfehlung:**
- FVG-Reaktionen erst als hochwertiges Signal werten, wenn TD Sequential im Bereich **7–9 (Setup) bzw. Countdown 12–13** steht — vorher nur als "Beobachtungszone" markieren, nicht als Trigger.
- Fractal-Periode erhöhen (7- oder 9-Bar) oder mit Mindestabstand zum letzten Fractal filtern, damit nur Marker erscheinen, die auch strukturell zur Größe der FVG-Zonen passen.

---

## 3. RSI vs. Cumulative Delta — Divergenzen im Screenshot?

- **/MNQ 1m:** RSI liegt bei ~45,6–45,7 (neutral, leicht unter 50) während der Preis nach der starken Rally auf ~29.300 jetzt zurückkommt. Das allein ist noch keine harte Divergenz. Auffälliger: die **kumulative Delta-Linie fällt sichtbar ab** (Richtung negativ), während der Preis sein Rallyniveau noch relativ gut hält. Das ist eine **leichte bärische Delta-Preis-Divergenz** — Kaufdruck lässt nach, obwohl der Preis noch nicht stark gefallen ist. Als Warnsignal für die Fortsetzung der Aufwärtsbewegung relevant, aber (noch) kein starkes Reversal-Signal.
- **/ES 1m (Footprint-Pane):** Hier sind zwei RSI-Werte weit auseinander sichtbar (38,23 vs. 59,36) — das zeigt, wie schnell RSI während des Flushs auf ~7.477 in den überverkauften Bereich fiel und danach in Richtung neutral zurückschnellte. Parallel dazu kippt das **Delta-Histogramm** von stark grün (Kaufvolumen) vor dem Flush auf stark rot (Verkaufsvolumen) während des Flushs und dann wieder gemischt/leicht grün bei der Erholung. Diese Kombination — RSI-Erholung aus dem überverkauften Bereich **plus** Delta-Wechsel von Verkaufs- zu Kaufdruck — ist das **stärkste und am ehesten handelbare Signal im gesamten Screenshot**: ein klassisches Absorptions-/Exhaustion-Muster am Tief.

**Empfehlung:**
- Die /MNQ-Delta-Divergenz als Frühwarnsignal für eine mögliche tiefere Korrektur nutzen, aber nicht isoliert handeln — auf Bestätigung durch TD Sequential/FVG-Reaktion warten (siehe Punkt 2).
- Die /ES-Absorption am Tief (RSI-Reversal + Delta-Flip) ist das qualitativ beste Signal im Bild — genau solche RSI+Delta-Kombinationen sollten als eigene, dokumentierte Setup-Klasse behandelt werden, da sie hier am klarsten und am schnellsten reagieren.

---

## 4. Layout/Übersichtlichkeit

- **Footprint-Zahlen auf /ES 1m sind bei diesem Zoom-Level sehr klein** — einzelne Bid/Ask-Werte pro Preislevel sind praktisch nicht lesbar, ohne das Fenster zu vergrößern oder reinzuzoomen.
- **RSI wird mit zwei nah beieinanderliegenden Zahlenwerten** (z. B. 45,65006/45,66007) in kleiner Schrift dargestellt — visuell schwer auf einen Blick zu erfassen, welcher Wert die aktuelle Linie und welcher die Signal-/MA-Linie ist.
- **Cumulative Delta als separates Subpanel** unter dem Preis-Chart erschwert das direkte Erkennen der oben beschriebenen Divergenz — man muss zwischen Preis-Chart und Delta-Panel hin- und herspringen.
- **TD-Sequential-Zählung auf dem 1H-Chart ist sehr klein** dargestellt, kaum zu erkennen, ob gerade Zählung 2, 3 oder 8 angezeigt wird — bei einem für die Analyse zentralen Signal ein Lesbarkeitsproblem.
- **FVG-Zonenfarben sind zwischen den Panes nicht konsistent priorisiert** — auf /MNQ 1H und 1m sehen die Zonen gleich aus, obwohl sie unterschiedliches Gewicht haben sollten (übergeordnete vs. kurzfristige FVG).
- **Kein Session-/Zeitmarker** (NY-Open, Kassaeröffnung) sichtbar, obwohl der /ES-Flush und die anschließende Erholung zeitlich sehr wahrscheinlich mit einem Handelssession-Ereignis zusammenfallen — ohne Marker geht dieser Kontext verloren.

---

## Handlungsempfehlungen — beibehalten vs. anpassen

**Beibehalten:**
- Grundstruktur „höhere Zeitebene für Bias + niedrige Zeitebene für Timing" pro Instrument.
- Footprint auf /ES als Ausführungs-Tool — das erzeugte hier das aussagekräftigste Signal (Absorption am Tief).
- Kombination RSI + Cumulative Delta grundsätzlich beibehalten, da sie hier bereits ein verwertbares Signal geliefert hat.

**Anpassen:**
1. **Symmetrisches Zeitebenen-Set für beide Instrumente** einführen (z. B. 1H/15m/1m für /MNQ und /ES gleichermaßen).
2. **TD-Sequential-Zählung erst ab Setup 7–9 / Countdown 12–13 als Trigger** für FVG-Reaktionen werten, nicht bei Zählung 2.
3. **Fractal-Periode erhöhen** (7–9 Bar) oder Mindestabstand filtern, um Rauschen wie die zwei nur 1 Tick auseinanderliegenden Fractal-Marker zu vermeiden.
4. **Cumulative Delta als Preis-Overlay** statt reines Subpanel, um Divergenzen wie die aktuelle /MNQ-Abschwächung direkt am Chart zu erkennen.
5. **Footprint-Ansicht vergrößern/fokussieren** (Zoom auf die letzten 15–20 Kerzen) für lesbare Bid/Ask-Zahlen.
6. **TD-Sequential-Beschriftung vergrößern** auf dem 1H-Chart, da dieser Wert zentral für die Timing-Entscheidung ist.
7. **Session-Zeitmarker ergänzen**, um Flush/Erholungs-Muster wie auf /ES in ihren Session-Kontext einzuordnen.

---

*Hinweis: Diese Bewertung basiert ausschließlich auf der visuellen Analyse des bereitgestellten Screenshots (Stand 03.09.2026, 10:48). Für eine belastbare Aussage zur Signalqualität empfiehlt sich ein Backtest der beschriebenen TD-Sequential/FVG/Delta-Konfluenzregeln auf historischen Daten.*
