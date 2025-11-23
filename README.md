

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

### Challenges Faced in Task 1

* `nltk` required additional downloads (`punkt`, `wordnet`, `stopwords`)
* Tokenization was initially slow for the full dataset
* Missing `"date"` column led to KeyError when resampling
* Fixed by converting `"published"` to datetime and renaming to `"date"`

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

Replaced TA-Lib due to installation errors and missing `distutils` on Python 3.12+.

Computed:

#### **Simple Moving Average (SMA-20)**

```python
df["SMA_20"] = df["Close"].rolling(20).mean()
```

#### **Relative Strength Index (RSI-14)**

Manual pandas implementation when TA-Lib failed.

#### **MACD (12/26/9)**

Implemented using pandas exponential moving averages.

#### **Daily Returns**

```python
df["Daily_Returns"] = pn.daily_returns(df["Close"])
```

#### **Volatility (Rolling Std-Dev)**

```python
df["Volatility_20"] = df["Daily_Returns"].rolling(20).std()
```

### ✔ 3. **Visualizations**

For each of the six stocks, plotted:

* Price + SMA
* RSI
* Daily returns
* Volatility

### Challenges Faced in Task 2

* **TA-Lib** failed installation due to:

  * Deprecated `distutils` on Python 3.12
  * C-library compilation requirements
* Switched to **pandas** implementations
* PyNance installation required switching to GitHub version
* Missing documentation for PyNance functions → implemented manually
