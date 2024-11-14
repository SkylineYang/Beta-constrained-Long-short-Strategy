# Beta-constrained Long-short Strategy

## 1. Get Data

In this part, we focus on how to get daily market data, which are useful when constructing the trading strategy.

Here I used `yfinance` library in Python, which can get data from Yahoo Finance, and store all the data into the folder *History* and differentiate them into long and short stocks.

## 2. Find Benchmark Index

The second step of constructing this strategy is to find an appropriate benchmark index, which can be not only stable but also profitable.

To get this, I used `sharpe ratio` to make the decision. The index with highest sharpe ratio will be chosen as the benchmark index.

## 3. Construct Trading Strategy

Here I assume that the original capital is $5,000,000. And there is no limit for trading, only when the loss reaches 3% should I sell/short-purchase the constituent stocks.

To be specific on how to rebalance the portfolio's $\beta$ value, I used `scipy.optimize.minimize` to optimize the weights of all constituent stocks with the constraints:

+ $\sum{weight_i} = 1$
+ $\sum{weight_i*\beta_i} = 0$

And I adjusted the weights weekly to ensure the beta of portfolio is around 0.
