# Week-3 Shopify Stock Price Analysis

## 📊 Project Overview

This project contains historical stock market data for **Shopify (SHOP)**. The dataset can be used for data analysis, visualization, and studying Shopify's stock price movements over time.

The data includes daily trading information such as opening price, highest price, lowest price, closing price, adjusted closing price, and trading volume.

## 📁 Dataset

**File:** `shopify_stock.csv`

The dataset contains **2,469 records** and the following columns:

| Column      | Description                            |
| ----------- | -------------------------------------- |
| `date`      | Date and time of the stock trading day |
| `open`      | Opening stock price                    |
| `high`      | Highest stock price during the day     |
| `low`       | Lowest stock price during the day      |
| `close`     | Closing stock price                    |
| `adj_close` | Adjusted closing price                 |
| `volume`    | Number of shares traded                |

## 🎯 Objectives

* Analyze Shopify's historical stock prices.
* Study daily price movements.
* Compare opening, closing, highest, and lowest prices.
* Analyze trading volume.
* Identify trends and patterns in the stock data.
* Create charts and visualizations for better understanding.

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook / Google Colab

## 🔍 Possible Analysis

Some analysis that can be performed using this dataset:

* Stock price trend over time
* Daily returns
* Moving averages
* Highest and lowest closing prices
* Trading volume analysis
* Monthly or yearly price changes
* Open vs. close price comparison
* Stock price visualization

## 📈 Example Visualizations

The dataset can be used to create:

* Line charts for closing prices
* Candlestick charts
* Trading volume charts
* Moving-average charts
* Daily return graphs

## 🚀 How to Use

1. Download or clone this repository.
2. Open the CSV file using Python, Jupyter Notebook, or Google Colab.
3. Load the dataset using Pandas.

```python
import pandas as pd

df = pd.read_csv("shopify_stock.csv")

print(df.head())
print(df.info())
```

## 📌 Dataset Structure

```text
shopify_stock.csv
│
├── date
├── open
├── high
├── low
├── close
├── adj_close
└── volume
```

## ⚠️ Disclaimer

This project is intended for **educational and data-analysis purposes only**. The information and analysis from this dataset should not be considered financial or investment advice.

## 👨‍💻 Author

**S. Veeramanikandan**

BCA Student
