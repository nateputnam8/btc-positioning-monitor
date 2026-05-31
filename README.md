# BTC Positioning Monitor

## Overview

This project analyzes Bitcoin market structure through a combination of spot price action, derivatives positioning, and institutional capital flows.

The objective is to identify periods of:

- Aggressive Long Buildup
- Aggressive Short Buildup
- Short Covering Rallies
- Long Liquidations
- Strong Institutional ETF Inflows

and evaluate how Bitcoin has historically performed following each regime.

---

## Data Sources

### CoinGecko
- BTC Spot Price
- Trading Volume

### CoinGlass
- Funding Rates
- Open Interest
- Spot Bitcoin ETF Flows

---

## Features

### Price & Volatility

- Daily Returns
- 7-Day Returns
- 30-Day Returns
- Rolling Volatility

### Derivatives Positioning

- Funding Rate Z-Score
- 7-Day Open Interest Change

### Institutional Flows

- Bitcoin ETF Net Flows
- ETF Flow Z-Score

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

### Strong ETF Inflows

- ETF Flow Z-Score > 1.5

---

## Research Framework

For each signal, the project evaluates:

- Forward 7-Day BTC Returns
- Forward 30-Day BTC Returns

to determine whether positioning conditions have historically been associated with future market performance.

---

## Sample Findings

Using Bitcoin funding, open interest, and ETF flow data, the monitor identified several positioning regimes and evaluated their subsequent forward returns.

| Signal | Median 7D Return | Median 30D Return |
|----------|----------|----------|
| Strong ETF Inflows | +2.00% | -2.35% |
| Aggressive Long Buildup | -1.24% | -4.47% |
| Long Liquidation | -1.88% | -3.57% |
| Aggressive Short Buildup | +3.24% | -12.10% |
| Short Covering Rally | -1.74% | -3.62% |

These results suggest institutional spot demand may be more supportive than leverage-driven positioning.
## Disclaimer

This project is intended for educational and research purposes only and should not be interpreted as investment advice.
