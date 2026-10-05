

# Algorithmic Trading Strategy for SP500 Stocks

## Overview

This project implements a quantitative algorithmic trading strategy focused on SP500 stocks. It involves downloading historical stock price data, calculating technical indicators and features, applying clustering for asset grouping, and optimizing portfolios using the Efficient Frontier (maximum Sharpe ratio). The strategy evaluates monthly portfolio performance and compares cumulative returns to the SP500 benchmark.

The core workflow is implemented in a Jupyter Notebook (`Algo_trading_strategy_quant.ipynb`), which processes data from 2015-09-29 to 2023-09-26 (end date in the code). This can be extended or updated by modifying the date ranges.

Key components:
- **Data Acquisition**: Fetches SP500 stock symbols from Wikipedia and downloads historical prices using `yfinance`.
- **Feature Engineering**: Computes technical indicators like Garman-Klass Volatility, RSI, Bollinger Bands, ATR, MACD, and Dollar Volume.
- **Aggregation and Analysis**: Aggregates data monthly, identifies local maxima for ATR, and calculates rolling CAPM Beta using Fama-French factors.
- **Clustering**: Uses K-Means to group stocks based on features each month.
- **Portfolio Optimization**: Selects assets from clusters and optimizes for maximum Sharpe ratio using the Efficient Frontier.
- **Backtesting**: Computes and visualizes cumulative returns, comparing the strategy to the SP500.

This strategy is for educational and research purposes. Backtested results do not guarantee future performance. Always consider transaction costs, slippage, and market risks in real-world applications.

## Requirements

- Python 3.8+ (tested on 3.8.8)
- Jupyter Notebook or JupyterLab
- Dependencies (install via `pip install -r requirements.txt`):
  - `pandas`
  - `numpy`
  - `yfinance`
  - `pandas_ta` (for technical indicators)
  - `statsmodels`
  - `matplotlib`
  - `scikit-learn` (for K-Means clustering)
  - `PyPortfolioOpt` (for Efficient Frontier optimization; implied in the code for Sharpe ratio maximization)
  - `pandas_datareader` (for Fama-French factors)

Create a `requirements.txt` file with the above packages if needed.

No external APIs or paid services are required beyond free tiers of `yfinance`.

## Installation

1. Clone the repository:
   ```
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Launch Jupyter Notebook:
   ```
   jupyter notebook
   ```
   Open `Algo_trading_strategy_quant.ipynb` in your browser.

## Usage

1. **Run the Notebook**:
   - Execute cells sequentially.
   - The first cell downloads SP500 symbols and historical data (may take time for 503 tickers over 8 years).
   - Subsequent cells compute features, perform clustering, optimize portfolios, and visualize results.

2. **Customization**:
   - Update `start_date` and `end_date` in the data download section to change the time period.
   - Adjust K-Means parameters (e.g., number of clusters) in the clustering section.
   - Modify optimization constraints in the portfolio formation step (e.g., risk tolerance or asset weights).

3. **Output**:
   - DataFrames with stock data, features, and indicators.
   - Monthly clustered groups and optimized portfolios.
   - Plots: Cumulative strategy returns (as a percentage) compared to SP500.
   - Final visualization shows intraday strategy returns over the backtest period.

## Data Sources

- **SP500 Symbols**: Scraped from Wikipedia (`https://en.wikipedia.org/wiki/List_of_S%26P_500_companies`).
- **Stock Prices**: Yahoo Finance via `yfinance`.
- **Fama-French Factors**: Downloaded via `pandas_datareader` from Kenneth French's data library.
- Data is historical and static in the notebook; re-running will fetch live data if dates are updated.

Note: Ensure compliance with Yahoo Finance's terms of use for data scraping.

## Results

- The strategy generates monthly portfolios based on clustered stocks and Sharpe-optimized weights.
- Backtested cumulative returns are plotted, showing potential outperformance or underperformance vs. SP500.
- Example output (from notebook): A plot titled "Intraday Strategy Returns" with y-axis in percentage format.

For detailed results, run the notebook. Historical performance (2015-2023) shows varying returns depending on market conditions.

