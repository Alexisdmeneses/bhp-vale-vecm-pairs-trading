# BHP / VALE — VECM & pairs trading

Cointegration analysis and statistical arbitrage strategy for BHP and VALE3 using a Vector Error Correction Model, based on daily adjusted prices from 2002 to 2006.

## Research question

*Do BHP and VALE share a long-run equilibrium? Can this relationship support a mean-reverting pairs trading strategy?*

## Approach

1. **Stationarity testing** — ADF test at level and first difference for both series
2. **Lag selection** — VARselect with AIC criterion (optimal lag = 2)
3. **Johansen cointegration test** — trace and eigenvalue statistics
4. **VECM estimation** — error correction term, short-run dynamics
5. **Pairs trading** — spread construction, ADF on spread, AR(2) fit, trading thresholds at ±2σ

## Key results

- Both series are I(1): non-stationary in level, stationary in first difference
- Johansen tests (trace and eigenvalue) confirm rank = 1 — one cointegrating vector
- Cointegrating vector: ln(BHP) − 0.7177 · ln(VALE) − 1.8285 = 0
- ECT coefficient in BHP equation: −0.067 (significant) — BHP absorbs ~6.7% of deviation per period
- Spread follows AR(2) with mean ≈ 1.82 and σ ≈ 0.044
- Trading thresholds: upper = 1.910, lower = 1.733

## Data

- Source: Ruey S. Tsay — Financial Time Series (Chicago Booth)
- Tickers: BHP (BHP Group) and VALE (Vale S.A.)
- Frequency: daily adjusted close prices
- Period: 2002–2006 · 946 observations

## Stack

R · vars · urca · forecast · tseries · ggplot2 · timetk

## Structure

```
├── Grupo6_Aula7_TS.ipynb     ← main notebook
├── Grupo6_Aula7_TS.pdf       ← rendered output
└── README.md
```

## How to run

```r
install.packages(c("vars", "urca", "forecast", "tseries", "timetk", "ggplot2"))
```

Data is loaded directly from Ruey Tsay's public repository — no local file needed:

```r
webpage <- "https://faculty.chicagobooth.edu/-/media/faculty/ruey-s-tsay/teaching/fts3/"
```
