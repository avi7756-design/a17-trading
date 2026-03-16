# v17_Hunter Plugin

A market anomaly scanner built for the v17 trading system. Monitors real-time VIX and SPY levels, issues volatility alerts, and surfaces 3 actionable market anomalies on demand.

## Components

| Component | Name | Purpose |
|-----------|------|---------|
| Command | `/hunt` | Scan VIX + SPY, alert on volatility, surface 3 market anomalies |

## Setup

No API keys or environment variables required. The plugin uses live web search to fetch market data.

## Usage

Type `/hunt` in any Claude Cowork or Claude Code session where this plugin is active.

The command will:
1. Fetch the current VIX index value
2. Fetch the current SPY price and daily change
3. Issue a color-coded volatility alert:
   - GREEN: VIX < 20 (calm conditions)
   - YELLOW: VIX 20-24 (moderate volatility)
   - ORANGE: VIX 25-29 (elevated fear - threshold alert)
   - RED: VIX >= 30 (extreme fear)
4. Identify and describe 3 current market anomalies (VCP breakouts, volume surges, gap-ups, etc.)

Output is delivered in Hebrew in a structured report format.

## Alert Thresholds

| VIX Level | Signal | Recommended Action |
|-----------|--------|--------------------|
| < 20 | Green | Favorable for momentum setups |
| 20-24 | Yellow | Stay selective, high-RS only |
| 25-29 | Orange | Tighten stops, reduce size |
| >= 30 | Red | Hedge aggressively / reduce exposure |
