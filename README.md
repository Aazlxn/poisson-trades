# Poisson Trade Arrival Model

I'm currently studying Poisson distributions in my stats class and wanted to 
apply the theory to something I'm actually interested in being financial markets.

The idea is simple: if trades arrive randomly and independently, the number 
of trades in a fixed time window should follow a Poisson distribution. 
I'm testing that assumption on live BTC/USDT data from Binance.

## What the notebook covers

Fetching live trade data from the Binance public API, binning trades into 
1-second windows, estimating lambda, and comparing the empirical distribution 
to the theoretical Poisson PMF.

## What I found

The Poisson model doesn't fit well. The variance-to-mean ratio is way above 1, 
and the plots make it obvious — most seconds are quiet but every so often 
there's a burst of hundreds of trades. Trades on a liquid exchange aren't 
independent random events, they react to price moves and large orders hitting 
the book.

## Stack

Python, pandas, numpy, scipy, matplotlib, Binance public API