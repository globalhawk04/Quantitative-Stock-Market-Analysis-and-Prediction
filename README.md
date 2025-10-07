Quantitative Stock Market Analysis and Prediction

This repository contains a collection of Python scripts that demonstrate a complete workflow for quantitative financial analysis. The project starts with fetching historical stock data, moves through data visualization and correlation analysis, and culminates in building a machine learning model to predict future stock price movements for S&P 500 companies.

Additionally, a sample algorithmic trading script for the Quantopian platform is included to illustrate how these concepts can be applied in a simulated trading environment.

Table of Contents

Project Overview

Project Workflow & Scripts

Key Concepts & Libraries

Prerequisites

How to Run

Disclaimer

Project Overview

This project is a step-by-step guide to quantitative analysis, designed to answer the question: Can we use historical price data from all S&P 500 companies to predict the future movement of a single stock?

The workflow covers:

Data Acquisition: Scraping S&P 500 tickers and downloading historical price data for each.

Data Visualization: Plotting stock prices, moving averages, and candlestick charts.

Data Analysis: Compiling a master dataset and analyzing the correlation between all S&P 500 stocks.

Machine Learning: Engineering features and training a classification model to predict whether a stock will rise, fall, or hold steady.

Algorithmic Trading: A conceptual script showing a pairs trading strategy for commodities futures.

Project Workflow & Scripts

The scripts are designed to be run in a specific order to build upon each other, starting from a single stock and scaling up to the entire S&P 500 index.

Part 1: Single Stock Analysis (stock.py - stock3.py)

stock.py: Fetches historical data for a single stock (Tesla) from Yahoo Finance, saves it to a CSV, and creates basic price plots.

stock1.py & stock2.py: Introduces technical analysis by calculating and plotting a 100-day moving average alongside the stock's adjusted close price and trading volume.

stock3.py: Demonstrates advanced visualization by resampling daily data into 10-day chunks and creating a candlestick chart.

Part 2: S&P 500 Data Acquisition and Analysis (stock4.py - stock7.py)

stock4.py: The first step in scaling up. This script scrapes Wikipedia to get an up-to-date list of all S&P 500 company tickers.

stock5.py & stock7.py: Creates a data acquisition pipeline that iterates through all S&P 500 tickers, downloads their historical data from Yahoo Finance, and saves each as a separate CSV file.

stock6.py: Aggregates the data by compiling the 'Adjusted Close' price from all 500+ individual CSVs into a single master data frame (sp500_joined_closes.csv). It then calculates and visualizes the correlation matrix of the entire S&P 500 as a heatmap.

Part 3: Machine Learning for Stock Prediction (stock8.py - stock10.py)

stock8.py: Prepares the data for machine learning. This script defines the prediction target (the "label"): will the stock go up (1), down (-1), or hold (0) within the next 7 days? It then creates the features, which are the daily percentage changes of all other S&P 500 stocks.

stock9.py & stock10.py: The machine learning core. This script trains a scikit-learn classification model (a VotingClassifier combining Linear SVC, K-Nearest Neighbors, and a Random Forest) on the prepared data. It then iterates through every stock in the S&P 500, trains a model for each one, and prints its predictive accuracy.

Part 4: Algorithmic Trading (quant.py)

quant.py: A standalone script written for the Quantopian platform. It implements a statistical arbitrage (pairs trading) strategy on Crude Oil and Gasoline futures, using Z-scores to identify trading opportunities. This demonstrates how quantitative analysis is applied in a simulated "live" trading environment.

Key Concepts & Libraries

Data Manipulation & Analysis: pandas, numpy

Data Visualization: matplotlib

Web Scraping: BeautifulSoup, requests

Financial Data Retrieval: pandas-datareader

Machine Learning: scikit-learn

Saving Python Objects: pickle

Prerequisites

You will need Python 3 and the following libraries installed. You can install them all with pip:

code
Bash
download
content_copy
expand_less
pip install numpy scipy pandas matplotlib pandas-datareader beautifulsoup4 requests scikit-learn lxml

Note: The quant.py script is designed specifically for the Quantopian online platform and will not run in a standard local Python environment, as it depends on Quantopian's proprietary libraries.

How to Run

Clone the repository:

code
Bash
download
content_copy
expand_less
git clone https://github.com/your-username/quantitative-stock-analysis.git
cd quantitative-stock-analysis

Execute the scripts in numerical order to follow the project's logical flow. The output of one script is often the input for the next.

code
Bash
download
content_copy
expand_less
# 1. Scrape tickers
python stock4.py

# 2. Download data for all tickers (this may take a while)
python stock5.py

# 3. Compile data and create correlation matrix
python stock6.py 

# 4. Run the machine learning model on all stocks
python stock9.py
Disclaimer

This project is for educational purposes only and is not intended as financial or investment advice. The models and analyses presented here are based on historical data and do not guarantee future performance. Always conduct your own research before making any investment decisions.
