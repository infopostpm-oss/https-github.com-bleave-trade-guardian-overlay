# Chart-Setup Review — /ES & /MNQ Multi-Timeframe-Layout

**Analysierte Instrumente:** /MNQ:XCME (1H, 1m), /ES:XCME (1m, 3m)
**Plattform:** TheTradingPit (dxFeed-Datenfeed), Trading-Simulator
**Aktive Tools:** TD Sequential, Fair Value Gaps (FVG), Fractals, RSI (14, Close), Cumulative Delta (by Volume), Footprint/Order-Flow-Ansicht, horizontale S/R-Zonen

---

## 1. Layout-Bewertung

### Stärken
- **Zwei Fenster, vier Charts** — saubere Trennung zwischen /MNQ (links) und /ES (rechts), jeweils mit einem höheren (1H bzw. 3m) und einem niedrigeren (1m) Zeitrahmen. Das deckt eine sinnvolle Top-Down-Struktur ab: Kontext oben, Ausführung unten.
- **Footprint-Chart** für /ES 1m ist gut platziert direkt neben dem 3m-Kontextchart — ermöglicht schnellen Abgleich zwischen Orderflow-Details und übergeordneter Struktur.
- **Account-Panel** mittig sichtbar (Margin, PnL-Ziele, Drawdown-Limits) — wichtig für Prop-Trading-Regeln, gut integriert statt in separatem Fenster versteckt.

### Schwächen
- **Zu viele Fenster/Charts gleichzeitig (4 Preisdarstellungen + Account + Orderbuch-artige Footprint-Matrix).** Auf einem Monitor-Layout wie diesem sind die einzelnen Candlesticks sehr klein — TD-Sequential-Zahlen (1–9, "Perfected"-Signale) sind kaum lesbar, was in einem schnellen Markt zu Fehlinterpretationen führt.
- **Keine klare visuelle Hierarchie zwischen den Zeitebenen.** 1H-, 3m- und 1m-Chart sehen vom Farbschema/Kontrast her identisch aus. Ohne unterschiedliche Rahmenfarben oder Titel-Hervorhebung ist im schnellen Blick nicht sofort erkennbar, welcher Chart der "Leitchart" für die Bias-Bildung ist.
- **RSI und Cumulative Delta sind separat untereinander gestapelt**, wodurch die eigentliche Preis-Chart-Fläche stark schrumpft (bei /MNQ 1m sind es geschätzt nur noch ~50 % der Fensterhöhe für Price Action). Das erschwert das Ablesen von Fractal-Hoch/Tiefs und FVG-Zonen.
- **Fehlende Uhrzeit-/Session-Markierung** (z. B. NY-Open, London-Close, Economic-Calendar-Linien) — bei Index-Futures wie /ES und /MNQ sind Sessiongrenzen für TD-Sequential- und Delta-Signale hochrelevant, sind hier aber nicht sichtbar.

---

## 2. Indikator-Konfiguration

### TD Sequential
- Auf 1H (/MNQ) und im Footprint-Chart (/ES) aktiv. TD Sequential liefert auf höheren Zeitebenen (1H+) deutlich zuverlässigere Erschöpfungssignale als auf 1m — auf dem 1m-Chart ist die Signalqualität von Setup/Countdown wegen des Noise-Anteils in Indexfutures fragwürdig.
- **Verbesserung:** TD Sequential nur auf 15m/1H/4H führen, nicht auf 1m/3m. Auf den niedrigen Zeitebenen erzeugt es zu viele "Perfected 9"-Fehlsignale, die gegen den übergeordneten Trend laufen können.

### Fair Value Gaps (FVG)
- FVGs sind auf mehreren Zeitebenen aktiv (grüne/rote Zonen sichtbar auf /MNQ 1m und 1H). Das ist grundsätzlich sinnvoll, sofern die FVGs unterschiedlich priorisiert werden (HTF-FVG als Ziel, LTF-FVG als Einstieg).
- **Verbesserung:** HTF-FVGs (aus 1H) farblich klar von LTF-FVGs (aus 1m/3m) unterscheiden (z. B. per Transparenzstufe oder Rahmenstärke), sonst verschmelzen die Zonen visuell und die Priorität geht verloren. Zusätzlich sollten gefüllte/invalidierte FVGs automatisch ausgeblendet oder ausgegraut werden, um Chart-Clutter zu reduzieren.

### Fractals
- Fractal-Pfeile sind auf allen Charts sichtbar, teils sehr dicht (z. B. /ES 1m rechts). Das Standard-Fractal (5-Bar) neigt in volatilen Marktphasen zu häufigen, wenig aussagekräftigen Signalen.
- **Verbesserung:** Periodenlänge erhöhen (z. B. 7- oder 9-Bar-Fractal) oder mit einem ATR-/Swing-Filter kombinieren, damit nur strukturell relevante Hochs/Tiefs markiert werden. Aktuell wirken die Fractals eher als Nebenrauschen denn als klare Struktur-Marker.

### RSI (14, Close)
- Standardkonfiguration, auf 1m/1H-Charts identisch. RSI (14) auf 1m-Charts bei Futures reagiert sehr träge im Verhältnis zur Bar-Frequenz und liefert selten klare Divergenzsignale in kurzen Zeitfenstern.
- **Verbesserung:** Divergenz-Erkennung (Preis macht neues Hoch/Tief, RSI nicht) manuell oder per Zusatz-Tool markieren — aktuell wird RSI nur als Overbought/Oversold-Linie genutzt, was in trendstarken Futures-Sessions zu früh gegen den Trend gedeutet werden kann.

### Cumulative Delta
- Auf /MNQ 1m aktiv, zeigt eine klare divergente Bewegung (Preis steigt, kumulative Delta fällt in der zweiten Hälfte) — das ist ein potenziell wertvolles Signal, wird aber isoliert unten im Chart dargestellt statt direkt mit der Preisachse verglichen.
- **Verbesserung:** Cumulative Delta als Overlay direkt am Preis-Chart (z. B. als zweite Skala rechts) statt als separates Subpanel, um Divergenzen ohne Blickwechsel zu erkennen. Zusätzlich einen Reset pro Session (statt fortlaufender Kumulierung über mehrere Tage) einstellen, damit die Delta-Werte pro Handelstag vergleichbar bleiben.

### Footprint-Analyse
- Nur auf /ES 1m sichtbar, mit Volumen-Zahlen pro Preislevel/Kerze. Die Zellgröße ist auf dem gezeigten Zoom-Level sehr klein — einzelne Bid/Ask-Werte sind kaum lesbar.
- **Verbesserung:** Footprint auf einen eigenen, größeren Chart-Bereich legen (ggf. Vollbild bei Bedarf) und nur auf die aktuell relevanten letzten 20–30 Kerzen zoomen statt der vollen 3-Tage-Ansicht. Ein Imbalance-Highlighting (z. B. 300 %-Schwelle) ist nicht erkennbar aktiviert — würde die Signalgebung deutlich verbessern.

---

## 3. Zusammenspiel der Signale (Konfluenz)

- Aktuell gibt es keine sichtbare Markierung, **wann mehrere Indikatoren gleichzeitig ein Signal geben** (z. B. TD-Sequential-9 + Fractal-Hoch + FVG-Fill + Delta-Divergenz). Jedes Tool wird separat abgelesen, was den mentalen Aufwand erhöht und Timing-Fehler begünstigt.
- **Empfehlung:** Ein klar definiertes Konfluenz-Setup dokumentieren (z. B. "Short nur bei: TD-9 auf 1H + Delta-Divergenz auf 1m + Preis in HTF-FVG") und im Chart durch eine gemeinsame Marker-Farbe oder Alert-Kombination sichtbar machen, statt vier Indikatoren unabhängig zu interpretieren.

---

## 4. Priorisierte Verbesserungsvorschläge

1. **Zeitebenen entzerren:** TD Sequential nur ≥15m nutzen; 1m-Charts auf Footprint/Delta/Fractal-Timing beschränken.
2. **Chart-Fläche vergrößern:** RSI und Cumulative Delta in kompaktere Subpanels (max. 15–20 % der Höhe) verschieben, um mehr Platz für Price Action, FVGs und Fractals zu schaffen.
3. **FVG-Hierarchie visualisieren:** HTF- vs. LTF-FVGs farblich trennen, gefüllte Zonen automatisch ausblenden.
4. **Fractal-Rauschen reduzieren:** Größere Periode oder Filter, um nur relevante Swing-Punkte zu zeigen.
5. **Delta als Preis-Overlay statt Subpanel**, mit Session-Reset.
6. **Footprint fokussieren:** Zoom auf relevanten Bereich, Imbalance-Schwelle aktivieren.
7. **Session-/Zeitmarker ergänzen** (NY-Open, Kassaeröffnung) für besseren Kontext bei TD-Sequential- und Delta-Signalen.
8. **Konfluenz-Regelwerk definieren** und im Chart sichtbar machen, um Entry-Timing über mehrere Indikatoren hinweg zu vereinheitlichen.

---

*Hinweis: Diese Bewertung basiert ausschließlich auf der visuellen Analyse des bereitgestellten Screenshots (Layout, sichtbare Indikator-Parameter, Chart-Struktur). Eine tiefere Aussage zur tatsächlichen Signal-Trefferquote erfordert Backtesting der beschriebenen Konfluenz-Regeln auf historischen /ES- und /MNQ-Daten.*
