# SGX Bank Stock Analysis

An analysis of Singapore's three largest local banks — DBS, OCBC, and UOB —
covering price trends, daily returns, correlation, risk-adjusted performance,
and a Monte Carlo simulation of future price ranges.

## Why these stocks?

DBS, OCBC, and UOB are Singapore's "big three" banks, commonly grouped together
as a sector due to their shared exposure to interest rates and Singapore's
economic conditions. This made them a good candidate for a single-sector
comparison, similar in spirit to sector-focused portfolio analysis projects.

## Key findings

- **OCBC delivered the best risk-adjusted return** of the three banks over the
  analysis period, despite having a lower average daily return than DBS — its
  lower volatility more than made up the difference.
- **UOB consistently underperformed** its peers across every metric: lowest
  mean return, lowest risk-adjusted return, and the lowest correlation with
  the other two banks.
- In a 1-year-ahead Monte Carlo simulation, **UOB was the only bank where the
  pessimistic (5th percentile) scenario resulted in a net loss** from current
  price — both DBS and OCBC remained net positive even in their worst simulated
  outcomes.

## Tools used

Python, pandas, yfinance, matplotlib, seaborn, numpy

## How to run

1. Clone this repo
2. Install dependencies: `pip install -r requirements.txt`
3. Open `SGX_Stock_Market_Analysis.ipynb` in Jupyter, or open it directly in
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
