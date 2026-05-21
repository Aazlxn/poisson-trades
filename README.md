# Poisson Trade Arrival Model

Modelling the number of BTC/USDT trades per second on Binance 
and testing whether arrivals follow a Poisson distribution.

## What I did
- Fetched 1000 recent trades from the Binance public API
- Binned trades into 1-second windows
- Estimated lambda (average trades per window)
- Compared empirical distribution to theoretical Poisson PMF
- Ran a chi-square goodness-of-fit test

## Results
- Lambda: ~28 trades/second
- Variance-to-mean ratio: ~100 (Poisson assumes this equals 1)
- Chi-square p-value: ~0

The Poisson model is a poor fit. Trades are heavily clustered —
quiet periods punctuated by sudden bursts of activity. This 
violates the Poisson assumption of independent, constant-rate arrivals.

## Why it fails
BTC/USDT is one of the most liquid pairs on earth. Large orders, 
price movements, and algorithmic reactions cause trades to arrive 
in bursts rather than smoothly. A Hawkes process or Negative 
Binomial model would be a better fit.

## Stack
Python, pandas, numpy, scipy, matplotlib, Binance public API