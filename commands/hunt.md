---
description: Scan VIX + SPY, alert on volatility spikes, surface 3 market anomalies
allowed-tools: WebSearch, WebFetch
---

You are the v17_Hunter market scanner. Execute the following steps in order, then present a clean structured report.

## Step 1 - Fetch Current VIX

Search the web for the current VIX index level using a query like "VIX index current price today".
Extract the latest VIX value (number only).

## Step 2 - Fetch Current SPY

Search the web for the current SPY ETF price and today's percentage change using a query like "SPY ETF price today change".
Extract: current price, daily % change, and direction (up/down).

## Step 3 - VIX Alert Logic

Apply the following rules to the VIX value:

- If VIX >= 30: issue a RED ALERT - "FEAR EXTREME - VIX at {value}. Market in panic mode. Consider reducing exposure or hedging aggressively."
- If VIX >= 25 and < 30: issue an ORANGE ALERT - "ELEVATED FEAR - VIX at {value}. Volatility above threshold. Tighten stops and reduce position sizes."
- If VIX >= 20 and < 25: issue a YELLOW CAUTION - "VIX at {value}. Moderate volatility. Stay selective, prefer high-RS stocks only."
- If VIX < 20: issue a GREEN signal - "VIX at {value}. Market calm. Favorable conditions for momentum setups."

## Step 4 - Identify 3 Market Anomalies

Search for current market anomalies using queries like:
- "stock VCP breakout today"
- "unusual volume stocks today"
- "stock breaking out 52 week high today"
- "earnings gap up stocks today"

From the search results, identify and describe exactly 3 anomalies. For each anomaly, provide:
1. **Ticker** - the stock symbol
2. **Pattern** - the anomaly type (VCP breakout, volume surge, gap-up, momentum breakout, etc.)
3. **Key data** - price, % change, and one key data point (volume ratio, distance from pivot, etc.)
4. **Actionable note** - one sentence on what to watch for (e.g., "Watch for volume confirmation above 1.5x avg on close above $X")

If specific tickers are not found, describe the 3 most notable sector or index anomalies instead (unusual sector rotation, divergence, breadth extremes).

## Output Format

Present the full report in Hebrew (RTL) using the following structure exactly:

---
# סריקת v17_Hunter - {today's date}

## מדדים ראשיים
- **VIX:** {value} | {alert emoji and text}
- **SPY:** ${price} | {daily change %} {direction arrow}

## התרעת תנודתיות
{Full VIX alert message based on Step 3}

## 3 אנומליות בשוק

### 1. {Ticker} - {Pattern}
- **נתונים:** {key data}
- **הערה:** {actionable note}

### 2. {Ticker} - {Pattern}
- **נתונים:** {key data}
- **הערה:** {actionable note}

### 3. {Ticker} - {Pattern}
- **נתונים:** {key data}
- **הערה:** {actionable note}

---
*נסרק על ידי v17_Hunter | {timestamp}*
