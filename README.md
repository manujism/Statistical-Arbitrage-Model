# Statistical-Arbitrage-Model

**Pairs Trading Strategy for Indian Bank Stocks**

Overview

This readme section contains the comprehensive implementation of a statistical arbitrage strategy using pairs trading between HDFC Bank and Axis Bank stocks from the National Stock Exchange (NSE) of India. The strategy leverages the statistical relationship between these correlated securities to generate market-neutral returns.

## Features
- Historical stock price data download from Yahoo Finance
- Statistical tests for cointegration to verify pair suitability
- Rolling correlation analysis to monitor relationship stability
- Z-score based trading signal generation
- Comprehensive performance metrics and visualization
- Benchmark comparison against NIFTY50 index

## Requirements
The following Python libraries are required:
- numpy
- pandas
- matplotlib
- seaborn
- yfinance
- statsmodels

## How It Works

### 1. Data Collection
The code downloads 3 years of historical adjusted closing prices (2021-2023) for HDFC Bank and Axis Bank using the Yahoo Finance API.

### 2. Cointegration Testing
Before implementing the strategy, the code tests whether the pair is suitable for pairs trading by:
- Directly testing for cointegration using the Engle-Granger method

### 3. Spread Analysis
- Calculates the price spread between the two stocks
- Normalizes the spread using a Z-score transformation (how many standard deviations from the mean)
- Uses a 60-day rolling window for mean and standard deviation calculations

### 4. Signal Generation
The strategy generates trading signals based on the following rules:
- When Z-score < -1.5: Buy signal (go long on the spread)
- When Z-score > 1.5: Sell signal (go short on the spread)
- When Z-score crosses 0: Exit position

### 5. Performance Evaluation
The code calculates and visualizes several performance metrics:
- Cumulative returns
- Comparison against NIFTY50 benchmark
- Risk-adjusted metrics (Alpha, Beta, Sharpe Ratio)
- Maximum drawdown analysis
- Trade statistics (win rate, profit/loss ratio)

## Trading Logic
In pairs trading, we're not simply buying or selling individual stocks, but rather trading the spread between them:
- When the spread widens beyond historical norms (high Z-score), we sell the outperforming stock and buy the underperforming one
- When the spread narrows beyond historical norms (low Z-score), we buy the outperforming stock and sell the underperforming one
- We exit positions when the spread returns to its historical mean

## Results Interpretation
The strategy's performance should be evaluated on several dimensions:
- Total return compared to benchmark
- Risk-adjusted metrics (Sharpe ratio > 1 is generally good)
- Maximum drawdown (lower is better)
- Win rate and profit/loss ratio

## Customization
The strategy can be adapted by modifying:
- The stock tickers in the `tickers` variable
- The analysis period using `start_date` and `end_date`
- The rolling window size (`window` variable)
- The Z-score thresholds for trade entry and exit

## Limitations and Considerations
- Past cointegration doesn't guarantee future cointegration
- Transaction costs are not included in the performance metrics
- The strategy assumes perfect execution at closing prices
- Market impact and liquidity constraints are not considered
- The relationship between pairs can break down during market stress

## Extensions
Possible enhancements to the strategy:
- Implement transaction costs and slippage
- Add stop-loss mechanisms
- Test across multiple pairs simultaneously
- Implement dynamic Z-score thresholds based on volatility
- Add regime detection to avoid trading during unstable periods

## Disclaimer
This code is provided for educational and research purposes only. It is not financial advice, and should not be used for actual trading without thorough testing and customization. Always conduct your own analysis and consider consulting a financial professional before trading.
