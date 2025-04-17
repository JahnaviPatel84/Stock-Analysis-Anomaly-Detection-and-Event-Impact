# Comparative Stock Prediction: Sectoral Behavior under Market Forces

## Project Summary

This project explores the predictive relationships between major market indices and sectoral stock movements using a combination of multivariate regression and anomaly detection techniques. Drawing from time-series theory and financial econometrics, it identifies latent volatility trends and market anomalies by combining price, volume, and macroeconomic indicators.

> This work demonstrates proficiency in statistical modeling, unsupervised outlier detection, dimensionality reduction, and explainable financial analysis — all crucial for real-world ML applications in finance and economics.

---

## Problem Statement

- How do stocks in different sectors (Tech vs. Energy) respond to macroeconomic changes and S&P 500 movements?
- Can we reliably detect stock price anomalies in response to global events (e.g., COVID-19 crash, Fed rate hikes)?
- Which features have predictive power in forecasting stock returns over a weekly horizon?

---

## Data

- **Source**: Yahoo Finance API (`yfinance`)
- **Timeframe**: Jan 2013 – Dec 2024
- **Instruments**:
  - META (Technology)
  - MSFT (Technology)
  - XOM (Energy)
  - S&P 500 (^GSPC)
- **External Variables**:
  - Crude Oil Prices
  - Interest Rates
  - Inflation Index

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Rolling average and log return computation
- Sector-level volatility visualization
- Correlation heatmaps of stock movements

### 2. Anomaly Detection
- **Univariate**: Z-score based detection using IQR-derived normal distribution
- **Bivariate**: Mahalanobis distance on PCA-reduced price-volume pairs
- **Multivariate**: PCA (m=8 → m=2) for all stocks, followed by chi-squared thresholding

### 3. Event Analysis
- Aligned anomalies with economic events:
  - 2015 China Market Crash
  - 2020 COVID-19 Crash
  - 2022 Inflation Cooldown
  - GameStop Short Squeeze (2021)
- Conducted return differential and volatility shift analysis around these dates

### 4. Multivariate Regression
- **Target**: Weekly log returns of META, MSFT, XOM
- **Features**: S&P 500, Crude Oil Prices, Interest Rates
- Used both:
  - OLS (Ordinary Least Squares)
  - ElasticNet (L1 Regularization)

---

## Key Results

| Stock | R² (OLS) | Significant Predictors |
|-------|----------|------------------------|
| META  | 0.22     | S&P500                 |
| MSFT  | 0.47     | S&P500, Oil, Interest  |
| XOM   | 0.37     | S&P500, Oil, Interest  |

- Regularization stabilized weights and fixed interpretability issues
- PCA-informed anomaly detection successfully flagged outliers across low-volatility periods

---

## Insights

- Combining PCA and Mahalanobis distance allows for effective multivariate outlier detection
- S&P 500 is the most consistently predictive factor across all sectors
- Crude oil prices significantly affect XOM and even MSFT due to indirect economic ties
- Sector-specific anomalies reveal non-linear dependencies not captured in linear models

---

## Limitations & Future Work

- Linear models struggle with low R² for tech stocks like META — nonlinear alternatives (e.g., Random Forest) may perform better
- Feature selection can be enhanced with time-varying coefficients or regime-switching models
- Explore minimum covariance determinant or Isolation Forest with non-Gaussian assumptions

---

## Tech Stack

- **Python Libraries**: `pandas`, `numpy`, `scikit-learn`, `statsmodels`, `yfinance`
- **Modeling Tools**: OLS, ElasticNet, PCA, Mahalanobis distance
- **Visualization**: `matplotlib`, `seaborn`
