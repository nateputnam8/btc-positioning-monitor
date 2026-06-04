# BTC Positioning Monitor

## Overview

The BTC Positioning Monitor is a market-structure framework designed to identify the dominant positioning forces driving Bitcoin.

The project combines spot price action, institutional capital flows, derivatives positioning, and liquidation activity to generate a daily positioning report summarizing the market environment.

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

The positioning monitor generates a daily market-structure summary designed to identify the dominant positioning regime driving Bitcoin.

Example output:

```text
BTC DAILY POSITIONING REPORT
-----------------------------------
Generated: 2026-06-04
Market Data Through: 2026-06-03

PRICE
BTC Price: $64,022
1D Return: -3.9%
7D Return: -13.9%
30D Return: -19.8%
Rolling 7D Volatility: 2.6%

INSTITUTIONAL DEMAND
ETF Flow Z-Score: -0.8
Institutional Signal: Neutral

LEVERAGE POSITIONING
Funding Z-Score: 0.2
OI Z-Score: -2.8
OI 7D Change: -17.3%
Leverage Signal: Long Liquidation

LIQUIDATION ACTIVITY
Long Liquidation Z-Score: 1.1
Short Liquidation Z-Score: 0.0
Liquidation Signal: Elevated Long Liquidation

PRIMARY MARKET REGIME IDENTIFICATION
Risk-Off / Deleveraging

INTERPRETATION
- Positioning data indicates a risk-off / deleveraging environment.
- ETF flows were neutral, suggesting institutional demand was not the primary driver.
- BTC fell -3.9% while open interest reached a -2.8 Z-score, consistent with long positioning being unwound.
- Elevated long liquidations indicate forced selling pressure from leveraged longs.
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

The primary analysis is contained in:

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
