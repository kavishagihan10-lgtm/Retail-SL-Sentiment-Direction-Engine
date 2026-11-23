# 📈 Multi-Factor Market Sentiment Proxy Oscillator (`-50` to `+50`)
**Pine Script™ v5 Fixed-Timeframe Market Direction & Sentiment Engine — Identifying Extreme Zones, Turn Points, Zero-Line Shifts & Live Bias**

---

### 1. Live Chart Overview & Core Direction Logic

[මෙතනට ඔයාගේ ෆොටෝ එක Drag & Drop කරන්න]

Built in **Pine Script™ v5** (`overlay=false`), the core purpose of this indicator is to determine **market direction and stretch** on a fixed higher timeframe (default `240` / 4H, with `lookahead=barmerge.lookahead_off` to prevent repainting/future leakage).

#### How Market Direction Is Determined
- **Greed vs. Fear Zones (`+35` / `-35` default):**
  - **Above Greed Level (`>= +thr`):** Shows upside overextension / greed pressure (`SELL` side bias).
  - **Below Fear Level (`<= -thr`):** Shows downside overextension / fear pressure (`BUY` side bias).
- **Turn-Point / Zone-Exit Signals (`BUY bias` / `SELL bias`):** When sentiment pulls back from an extreme zone (`greedExit` / `fearExit`), it plots big dots, labels, and optional bar background highlights to flag potential directional turn points.
- **Zone Entry & Zero-Line Crosses (`0` Midpoint):**
  - Marks `0: lean BUY` / `0: lean SELL` when sentiment crosses the zero line.
  - Displays `MARKET: BUY` / `MARKET: SELL` labels when entering extreme zones.
- **Live Direction Table (Top-Right):** Continuously shows the exact oscillator `Value` and current `Market direction` (`SELL`, `lean SELL`, `NEUTRAL`, `lean BUY`, `BUY`).

---

### 2. How the Indicator Works & How to Use It for Direction

- **Zero (`0`) Midpoint — Neutral Baseline:** The `0` line acts as the neutral midpoint where directional bias is neither committed to one side nor the other.
- **Retail SL Positioning & Direction Confirmation (`-30` to `-33` / Extreme Zones):** When the sentiment line moves well below `0` toward deep fear levels (such as around `-30` to `-33` or the lower fear zone), it reflects heavy downside stretch/fear where a larger concentration of retail stop-losses (SL) sits above current price — helping confirm a **`BUY`** direction bias (and conversely, extreme greed/upside stretch signals **`SELL`** bias).
- **Strongest Direction Confirmation (`1H` & `4H` Alignment):** For the highest-conviction directional confirmation, align the indicator's bias and zone signals with the prevailing **`1H`** and **`4H`** market structure/direction rather than trading against higher-timeframe momentum.

---

### 3. 5-Factor Composite Sentiment Model (`-50` to `+50`)

Five normalized market components are combined and smoothed with an EMA into a `-50` to `+50` scale:
1. **RSI Stretch (`rsiC`):** Measures RSI momentum relative to the `50` level.
2. **EMA / ATR Stretch (`distC`):** Measures price distance from the `50`-period EMA normalized by `ATR` (`±3 ATR` range).
3. **Candle Momentum (`momAvg`):** Tracks average bullish vs. bearish candle pressure.
4. **Directional Volume (`volC`):** Compares up-candle vs. down-candle volume averages against average volume.
5. **Range Position (`posC`):** Shows where price sits inside the `50`-bar high–low range (`-1` to `+1`).

---

### 4. Built-In TradingView Alert Conditions

- **Enter Greed Zone** / **Enter Fear Zone**
- **Leave Greed Zone (`SELL bias`)** / **Leave Fear Zone (`BUY bias`)**
