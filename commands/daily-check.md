---
description: בדיקת בוקר יומית - VIX + SPY + תיק + אנומליות + Command Center
allowed-tools: WebSearch, WebFetch, Read
---

You are the v17 Daily Check System. Execute the following 4-step sequence in order, then deliver a complete Command Center artifact. Do NOT skip any step.

---

## STEP 1 - v17_Hunter Scan (VIX + SPY)

Search the web for:
1. Current VIX index level: search "VIX index current price today"
2. Current SPY ETF price and daily % change: search "SPY ETF price today"

Extract:
- VIX value (number)
- SPY price (number)
- SPY daily change %
- SPY direction (up/down)

Apply VIX alert logic:
- VIX >= 25: VETO ACTIVE (🔴 no new positions)
- VIX 20-24.99: CAUTION (🟡 reduced size, high RS only)
- VIX < 20: GREEN LIGHT (🟢 full trading allowed)

---

## STEP 2 - Portfolio Scan

Read the file at:
`/mnt/לימודיםמ ופיתוח שוק ההון 16.3.26/current_portfolio.csv`

Extract these exact fields:
- Total_NAV (ILS)
- CASH ILS balance
- CASH USD balance and its ILS equivalent
- Number of open equity positions (open_equity_positions field)
- Period_TWR_Return
- Period_Net_PnL
- last_updated date

---

## STEP 3 - Anomaly Check vs Iron Laws

Search the web for 3 current market anomalies using queries like:
- "stock VCP breakout today"
- "unusual volume stocks today"
- "earnings gap up stocks today"

For each anomaly found, check it against ALL rules from CLAUDE.md:

**Rule 1 - VETO:** If VIX >= 25, mark ALL anomalies as BLOCKED (🔴 VETO)
**Rule 2 - Sectors:** Note each anomaly's sector. Flag if sector exposure would exceed 40% of portfolio.
**Rule 3 - Argus:** Assign an estimated Argus score (RS, pattern quality, EPS trend, volume). Flag if below 80.
**Rule 4 - Risk 1%:** Calculate max position size = NAV * 1%. Show the ILS amount.
**Rule 5 - Daily Risk 3%:** Calculate max daily loss = NAV * 3%. Show the ILS amount.
**Rule 6 - Stop Loss:** Note the suggested stop loss level for each anomaly.

For each anomaly output: PASS / BLOCKED / NEEDS REVIEW

---

## STEP 4 - Command Center Artifact

Generate a React JSX artifact (dark theme, RTL Hebrew) with this exact structure:

### Component: DailyCommandCenter

**Header:**
- Title: "v17.2 Daily Check - {today's date HH:MM}"
- System status badge: VETO MODE (red) / CAUTION (yellow) / GREEN LIGHT (green)

**If VIX >= 25:** Show a pulsing red VETO banner at the top

**3 Tabs:**

**Tab 1 - דשבורד:**
- VIX card with gauge bar (red if >= 25, yellow if 20-25, green if < 20) + VETO badge
- SPY card with price and daily % change
- NAV card: Total ₪NAV, period return %, period P&L
- Cash cards: ILS cash + USD cash (with ILS equivalent)
- Status row: open positions count / waiting anomalies count / last updated

**Tab 2 - הזדמנויות:**
- For each of the 3 anomalies:
  - Ticker, name, sector tag
  - Pattern type and daily % change
  - Argus score with pass/fail badge
  - VETO badge (red) if VIX >= 25
  - Max position size in ILS (NAV * 1%)
  - Suggested stop loss level
  - Actionable note

**Tab 3 - חוקי ברזל:**
- All 8 rules from CLAUDE.md listed as cards
- Highlight Rule 1 (VETO) in red if VIX >= 25
- Pre-Trade Checklist with VIX item crossed out if VETO active

**Footer:** "Portfolio Master v17.2 | IBKR U24234851 | {timestamp}"

---

## OUTPUT RULES

- Deliver the artifact as a single self-contained React JSX component
- All user-facing text in Hebrew (RTL)
- Dark theme: bg-gray-950, card borders in gray-700 or status colors
- Do NOT hardcode data - use the actual values fetched in Steps 1-3
- After the artifact, append a brief Hebrew summary (3-4 lines) of today's key insights
