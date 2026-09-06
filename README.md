# SGX Bank Stock Analysis

An analysis of Singapore's three largest local banks — DBS, OCBC, and UOB —
covering price trends, daily returns, correlation, risk-adjusted performance,
and a Monte Carlo simulation of future price ranges.

**TL;DR:** OCBC delivered the best risk-adjusted return of the three banks,
while UOB was the only one to show a net loss in the pessimistic 1-year
Monte Carlo scenario — despite being the least correlated with its peers.

## Why these stocks?

DBS, OCBC, and UOB are Singapore's "big three" banks, commonly grouped together
as a sector due to their shared exposure to interest rates and Singapore's
economic conditions. This made them a good candidate for a single-sector
comparison, similar in spirit to sector-focused portfolio analysis projects.

## Price Trends

![Closing price trends](images/price_trends.png)

All three banks trended upward from 2023 to 2026, but DBS pulled significantly
ahead of OCBC and UOB, particularly from 2025 onward. All three show a sharp,
synchronized dip in early-to-mid 2025, coinciding with a period of broader
global market volatility.

## Returns & Risk

![Daily returns](images/daily_returns.png)

| Stock | Mean Daily Return | Std Dev (Volatility) | Risk-Adjusted Return (Mean/Std) |
|---|---|---|---|
| DBS  | 0.132% | 1.06% | 0.124 |
| OCBC | 0.134% | 0.98% | **0.137** |
| UOB  | 0.063% | 0.99% | 0.063 |

- **OCBC delivered the best risk-adjusted return** of the three banks over the
  analysis period, despite having a marginally lower average daily return than
  DBS — its lower volatility more than made up the difference.
- **UOB consistently underperformed** its peers on both raw and risk-adjusted
  return, with less than half OCBC's risk-adjusted return despite carrying
  similar volatility.

![Risk vs Return scatter plot](images/risk_return.png)

## Correlation & Diversification

![Correlation heatmap](images/correlation_heatmap.png)

| | DBS | OCBC | UOB |
|---|---|---|---|
| DBS | 1.000 | 0.729 | 0.664 |
| OCBC | 0.729 | 1.000 | 0.692 |
| UOB | 0.664 | 0.692 | 1.000 |

DBS and OCBC were the most closely correlated pair (0.729), consistent with
being Singapore's two largest banks by market cap. Interestingly, **UOB was
the least correlated with both peers** — meaning that despite being the
weakest performer on a returns basis, it would still offer some genuine
diversification benefit if held alongside DBS or OCBC in a portfolio.

## Monte Carlo Simulation (1-Year Ahead)

![Monte Carlo simulation - DBS](images/monte_carlo_dbs.png)

Using Geometric Brownian Motion with 1,000 simulated paths over 252 trading
days (one trading year), based on each stock's historical drift and volatility:

| Stock | Current Price | Mean (1yr) | 5th %ile | 95th %ile | 5th %ile vs. Current |
|---|---|---|---|---|---|
| DBS  | $78.65 | $109.48 | $81.93 | $142.07 | +4.2% |
| OCBC | $32.27 | $45.20  | $34.66 | $57.48  | +7.4% |
| UOB  | $42.01 | $49.14  | $37.49 | $62.75  | **-10.8%** |

**UOB was the only bank where the pessimistic (5th percentile) scenario
resulted in a net loss** from current price — both DBS and OCBC remained net
positive even in their worst simulated outcomes.

## Tools used

Python, pandas, yfinance, matplotlib, seaborn, numpy

## How to run

1. Clone this repo
2. Install dependencies: `pip install -r requirements.txt`
3. Open `sgx_bank_stock_analysis.ipynb` in Jupyter, or open it directly in
   [Google Colab](https://colab.research.google.com) via the badge at the top
   of the notebook

## Data source

Historical price data pulled via [yfinance](https://pypi.org/project/yfinance/)
(Yahoo Finance), covering January 2023 to September 2026.

## Caveats

This project uses Geometric Brownian Motion for the Monte Carlo simulation,
which assumes returns are normally distributed and that future volatility/drift
will resemble the historical period analyzed. Real markets can deviate
significantly from this assumption, especially around macro shocks.


