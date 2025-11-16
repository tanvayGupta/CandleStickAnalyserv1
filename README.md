# Candlestick Pattern Analyser

This project analyzes historical stock data to identify common candlestick patterns, providing insights into market trends and potential trading opportunities. It fetches data from Yahoo Finance, processes it using pandas, and visualizes the results with mplfinance and matplotlib.

## Libraries Used

- **yfinance**: A popular library for accessing historical market data from Yahoo Finance.
- **pandas**: Used for data manipulation and analysis, particularly for handling time-series data in DataFrames.
- **mplfinance**: A specialized library for financial data visualization, used here to create candlestick charts.
- **matplotlib**: A widely-used plotting library for creating static, animated, and interactive visualizations in Python.
- **numpy**: A fundamental package for scientific computing with Python, used for numerical operations.

## Data Implementation

The `main.ipynb` notebook demonstrates how to fetch historical stock data using the `yfinance` library. By providing a stock ticker (e.g., "MSFT" for Microsoft), you can retrieve data for a specified period, such as the last year ("1Y"). The data is returned as a pandas DataFrame, which is then used for analysis and plotting.

The notebook also includes a utility to scrape the list of S&P 500 companies from Wikipedia, allowing for broader market analysis.

## Candlestick Pattern Identification

The `CandlestickPatternAnalyser.ipynb` notebook contains the core logic for identifying candlestick patterns. The process involves several steps:

1. **Calculating Candle Properties**:
   - `CandleHeight`: The difference between the closing and opening prices.
   - `WickToWick`: The difference between the high and low prices.
   - `Trend`: A binary value indicating whether the candle is bullish (0) or bearish (1).

2. **Identifying Doji Patterns**:
   A Doji pattern is identified when the candle's body is significantly smaller than its wicks. The `is_doji` function checks if the total wick height is at least 15 times the absolute candle height.

3. **Identifying Marubozu Patterns**:
   A Marubozu pattern occurs when the candle has no wicks, meaning the opening and closing prices are the same as the low and high prices, respectively. The `is_marubozo` function checks if the absolute candle height is equal to the wick-to-wick distance.

4. **Identifying Engulfing Patterns**:
   - **Bullish Engulfing**: A bullish candle that completely engulfs the previous bearish candle.
   - **Bearish Engulfing**: A bearish candle that completely engulfs the previous bullish candle.

   The `is_bullEng` and `is_bearEng` functions check for these patterns by comparing the current and previous candle's open and close prices.

Finally, the notebook uses `mplfinance` to plot the candlestick chart, with identified patterns marked for easy visualization.
