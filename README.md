# Expiration-day-effects-BTC

***Study of expiration days effects for CME bitcoin futures

The daily data with calcs file shows all the daily data sourced from CoinMetrics as well as our own calculations for weekly return, 48-hour returns and so on. This file is used to create the graphs comparing expiration days versus non-expiration days for things like daily return, weekly return, daily volatility and so on. Daily volume is provided by the Bitcoin Real Volume indicator on TradingView. Volatility is defined as (high-low)/open. 

The 4-hour data for BTC-USD is sourced from the Bitcoin Liquid Index from TradingView. This file is used to investigate expiration day effects at the intraday level. Tests are run in RStudio using the 4-hour data file.

We also want to compare expiration with non-expiration Fridays, which is the purpose of the Fridays.csv file. 

The Wilcox-Mann-Whitney U test is used to compare the distributions of price changes, volatility and returns to see if there is a significant difference and identify whether expiration day efects are present. 

All code used in R Studio is available in the R Code file. 
