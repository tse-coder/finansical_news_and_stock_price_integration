

# **TenX Week 1 — Tasks 1 & 2 (News + Stocks Analysis)**

This project contains the work completed for Week 1 of the TenX program.
The goal was to perform exploratory data analysis (EDA) on **news headlines** and **market data** from six major tech stocks.

---

# **Project Structure**

```
├── .vscode/
│   └── settings.json
├── .github/
│   └── workflows
│       ├── ci.yml
├── .gitignore
├── requirements.txt
|
├── README.md
├── src/
│   ├── __init__.py
|
├── notebooks/
│   ├── __init__.py
│   ├── 01_eda_financial_news.ipynb
│   ├── 02_stock_tech_indicators.ipynb
│   └── README.md
|
└── scripts/
    ├── __init__.py
    └── README.md
```

---

# **TASK 1 — News Data Analysis**

### 1. **Headline Descriptive Statistics**

* Calculated headline length
* Generated summary statistics
* Identified unusually short/long headlines

### 2. **Publisher Analysis**

* Counted number of articles per publisher
* Visualized top 10 publishers using bar plot
* Extracted e-mail domains where applicable

### 3. **Time Series Publication Analysis**

* Articles published **per day**
* Articles published **per hour**
* Articles published **per day of week**
* Plots show:

  * Publication spikes
  * News cycles (morning > evening)
  * Weekend drops

### 4. **NLP Processing**

Performed lightweight NLP using **NLTK**:

* Tokenization
* Lowercasing
* Stop-word removal
* Lemmatization
* Extracted tokens per headline

---

# **TASK 2 — Stock Market Data Analysis**

Analyzed six tickers:

* **AAPL, AMZN, GOOG, META, MSFT, NVDA**

### 1. **Data Cleaning & Preparation**

* Loaded CSVs
* Sorted by date
* Set `"Date"` column as index
* Converted index to datetime

### 2. **Technical Indicators (Using Pandas + PyNance)**

used TA-Lib to find the techinal idicators (SMA, RSI and MACD).

### ✔ 3. **Visualizations**

For each of the six stocks, plotted:

* Price + SMA
* RSI
* Daily returns
* Volatility

# **Task 3: Correlation Between News Sentiment and Stock Movements**

## Objective

The goal of Task 3 is to analyze how financial news headlines influence stock price movements by performing sentiment analysis and correlating it with daily stock returns.

## Data

* **Financial News:** `raw_analyst_ratings.csv`
  Contains news headlines, publisher info, and publication dates.
* **Stock Prices:** CSV files from Yahoo Finance for six major stocks (AAPL, AMZN, GOOG, META, MSFT, NVDA).

## Methodology

1. **Date Alignment**

   * Convert the `date` column in news data to datetime.
   * Ensure that news dates align with stock trading dates.

2. **Sentiment Analysis**

   * Used `TextBlob` to compute polarity scores of news headlines (range: -1 negative to +1 positive).
   * Aggregate multiple headlines per day to calculate average daily sentiment.

3. **Stock Returns**

   * Calculated daily returns for each stock as the percentage change in closing prices.

4. **Correlation Analysis**

   * Merged average daily sentiment with corresponding stock returns.
   * Calculated the Pearson correlation coefficient between sentiment and daily returns to quantify the relationship.

5. **Optional Visualization**

   * Scatter plots of daily returns vs. average sentiment were created for visual inspection of correlations.

## Key Insights

* This analysis provides a preliminary understanding of how news sentiment may relate to stock price movements.
* Handling multiple headlines per day is important to avoid duplicates during correlation and plotting.
* Correlation strength varies by stock, indicating that some stocks may be more sensitive to news sentiment than others.

## Libraries Used

* `pandas` – data handling and merging
* `TextBlob` – sentiment analysis
* `matplotlib` / `seaborn` – plotting and visualization

