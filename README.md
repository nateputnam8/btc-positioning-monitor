# BTC Positioning Monitor

## Overview

The BTC Positioning Monitor is a market-structure framework designed to identify the dominant positioning forces driving Bitcoin.

The project combines spot price action, institutional capital flows, derivatives positioning, and liquidation activity to generate a daily positioning report and AI-generated market structure commentary summarizing the market environment.

The objective is not to predict price directly, but to explain whether market moves are being driven by institutional flows, leverage positioning, or liquidation dynamics.

The framework is designed to answer questions such as:

- Is the market being driven by institutional demand or leverage?
- Are traders adding risk or reducing exposure?
- Is price action being amplified by liquidations?
- Which positioning regimes have historically been associated with future BTC performance?

In addition to generating a daily positioning report, the monitor evaluates how Bitcoin has historically performed following specific positioning regimes using forward 7-day and 30-day returns.

The framework is inspired by institutional positioning analysis commonly used across prime brokerage, derivatives, and market structure teams.

---

## Data Sources

### CoinGecko
- BTC Spot Price
- BTC Trading Volume

### Hyperliquid
- Funding Rates

### CoinGlass
- Open Interest
- Spot Bitcoin ETF Flows
- Long Liquidations
- Short Liquidations

---

## Features

### Price & Volatility

- Daily Returns
- 7-Day Returns
- 30-Day Returns
- Rolling 7-Day Volatility

### Institutional Demand

- Bitcoin ETF Net Flows
- ETF Flow Z-Score

### Leverage Positioning

- Funding Rate Z-Score
- Open Interest Z-Score
- 7-Day Open Interest Change

### Liquidation Activity

- Long Liquidation Z-Score
- Short Liquidation Z-Score

### Market Structure Classification

- Institutional Demand Signals
- Leverage Positioning Signals
- Liquidation Signals
- Primary Market Driver Identification
- Daily Positioning Report Generation

## AI Market Commentary

The monitor automatically generates institutional-style market commentary using the OpenAI API.

Commentary is generated from the daily positioning report and incorporates:

- BTC price action
- ETF flow signals
- Funding rates
- Futures open interest
- Liquidation activity
- Market regime classification

The commentary is designed to answer:

- What is driving today's move?
- Is the market institutionally driven or leverage driven?
- Is positioning improving or deteriorating?
- Are liquidation dynamics becoming more or less important?
- What risks should traders monitor next?

Output is structured into:

- Summary
- Key Takeaways
- What To Watch

Daily commentary and positioning metrics are archived in JSON format to support historical analysis and future contextual commentary generation.

---

## Positioning Regimes

### Aggressive Long Buildup

- BTC 7D Return > 3%
- Funding Z-Score > 0.5
- Open Interest Rising

### Aggressive Short Buildup

- BTC 7D Return < -3%
- Funding Z-Score < -0.5
- Open Interest Rising

### Short Covering Rally

- BTC 7D Return > 3%
- Open Interest Falling

### Long Liquidation

- BTC 7D Return < -7%
- Open Interest Falling

### Strong Institutional Inflows

- ETF Flow Z-Score > 1.5

### Institutional Outflows

- ETF Flow Z-Score < -1.5

### Elevated Long Liquidation

- Long Liquidation Z-Score > 1

### Elevated Short Liquidation

- Short Liquidation Z-Score > 1

---
---

## Example Daily Positioning Report

The monitor generates a daily market structure report and AI commentary summarizing the dominant drivers of BTC price action.

### Report Output

```text
BTC DAILY POSITIONING REPORT
-----------------------------------
Generated: 2026-06-10
Market Data Through: 2026-06-09

PRICE
BTC Price: $61,658
1D Return: -2.3%
7D Return: -7.5%
30D Return: -24.9%
Rolling 7D Volatility: 2.8%

INSTITUTIONAL DEMAND
ETF Flow Z-Score: 0.2
Institutional Signal: Neutral

LEVERAGE POSITIONING
Funding Rate: 0.0%
Funding Z-Score: -0.3
OI Z-Score: -1.5
OI 7D Change: -6.7%
Leverage Signal: Long Liquidation

LIQUIDATION ACTIVITY
Long Liquidation Z-Score: -0.1
Short Liquidation Z-Score: -0.2
Liquidation Signal: Neutral

PRIMARY MARKET DRIVER
Risk-Off / Deleveraging

Summary:
The broader Risk-Off / Deleveraging regime remains intact, though positioning conditions have become materially less extreme. Open interest continues to contract, but the pace of deleveraging has slowed significantly from recent lows. Funding has normalized from the modest long bias observed earlier in the week, suggesting much of the residual long positioning has been removed from the system.

Key Takeaways:
- Ongoing deleveraging remains the dominant market theme, though positioning conditions continue to improve.
- Funding has normalized, indicating long positioning imbalances have largely been flushed out.
- Liquidation activity remains subdued, suggesting forced-position unwinds are no longer a major driver of price action.
- Neutral ETF flows imply institutional participation was not a significant contributor to recent market moves.

What To Watch:
- Whether open interest stabilizes after several sessions of contraction.
- Whether funding begins rebuilding from neutral levels.
- Whether BTC can establish a base now that liquidation pressure has largely normalized.
```

The report combines spot price action, ETF flows, funding rates, open interest, and liquidation activity into a single positioning framework designed to explain the dominant drivers of market behavior.

### Example Use Cases

- Daily market structure monitoring
- Institutional flow analysis
- Positioning regime identification
- Risk management and exposure monitoring
- Crypto market commentary generation

## Historical Signal Evaluation

For each signal, the project evaluates:

- Forward 7-Day BTC Returns
- Forward 30-Day BTC Returns

to determine whether positioning conditions have historically been associated with future market performance.

---

## Historical Signal Performance

Using Bitcoin funding, open interest, ETF flow, and liquidation data, the monitor identified several positioning regimes and evaluated their subsequent forward returns.

| Signal | Observations (7D) | Observations (30D) | Median 7D Return | Median 30D Return |
|---|---:|---:|---:|---:|
| Aggressive Short Buildup | 8 | 8 | +3.24% | -12.10% |
| Elevated Short Liquidation | 39 | 39 | +2.29% | +0.91% |
| Strong ETF Inflows | 22 | 22 | +2.00% | -3.67% |
| Aggressive Long Buildup | 30 | 28 | -1.24% | -4.47% |
| Short Covering Rally | 14 | 12 | -1.74% | -3.62% |
| Long Liquidation | 25 | 25 | -1.88% | -3.57% |
| Elevated Long Liquidation | 36 | 29 | -3.13% | -0.38% |

These results are based on approximately one year of historical data and should be viewed as exploratory rather than statistically conclusive. The objective is to identify how different positioning environments have historically influenced subsequent Bitcoin performance.

## Example Visualizations

### BTC Price with Leverage Regime Signals

![Leverage Regimes](outputs/charts/leverage_regime_signals.png)

### BTC ETF Flow Z-Score

![ETF Flow Z-Score](outputs/charts/etf_flow_zscore.png)

### BTC ETF 7-Day Rolling Net Flows

![Rolling ETF Flows](outputs/charts/rolling_etf_flows.png)

### BTC Price with Composite Positioning Signals

![Composite Signals](outputs/charts/composite_positioning_signals.png)

## Notebook

## Notebook

The primary notebook performs:

- Data collection and normalization
- Market structure signal generation
- Daily positioning report generation
- OpenAI-powered commentary generation
- Historical commentary archiving

Primary notebook:

`notebooks/btc_positioning_monitor.ipynb`

If GitHub notebook rendering is unavailable, a static HTML export is also included:

[View HTML Export](notebooks/btc_positioning_monitor.html)

## Methodology Notes

### Daily Price Alignment

BTC price data is sourced from CoinGecko and uses daily observations at 00:00 UTC.

### ETF Flow & Liquidation Alignment

ETF flow and liquidation metrics represent activity occurring throughout a trading day, while BTC prices represent a point-in-time snapshot.

To improve interpretability of the daily positioning report, ETF flow and liquidation signals are shifted forward one day when generating report-card commentary. This aligns activity-based metrics with the subsequent daily price observation.

Forward-return studies use unshifted ETF flow and liquidation data to evaluate historical predictive relationships from the day the signal occurred.

### Sample Size Considerations

Conditional forward-return studies are based on approximately one year of historical data. Certain positioning regimes occur infrequently, so results should be interpreted as exploratory rather than statistically conclusive.

## Disclaimer

This project is intended for educational and research purposes only and should not be interpreted as investment advice.
