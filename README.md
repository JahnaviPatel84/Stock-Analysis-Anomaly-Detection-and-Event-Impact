# 📈 Comparative Stock Prediction  
**Multivariate Regression & Event-Based Analysis of Stock Movements**

This project explores how macroeconomic indicators affect stock performance across major tech and energy companies. We used a combination of statistical modeling, anomaly detection, and event-based analysis to identify trends, performance shifts, and impactful financial events.

---

## 📘 Overview

We analyzed historical stock data for companies like Meta, Microsoft, and ExxonMobil, alongside macroeconomic variables such as crude oil prices, interest rates, and inflation indicators. Our goal was to assess whether certain market events and macro indicators could predict stock movements.

Key components:
- Multivariate regression to model stock behavior
- PCA for dimensionality reduction
- Anomaly detection using Mahalanobis Distance and Z-scores
- Event-based analysis to study stock volatility around significant events

---

## 🧠 Techniques Used

- Multivariate Linear Regression (OLS, LASSO/ElasticNet)
- Principal Component Analysis (PCA)
- Anomaly Detection (Z-score, Mahalanobis Distance)
- Event-Based Analysis (volatility before/after economic events)
- Statistical hypothesis testing (False Discovery Rate control)

---

## 📂 Notebooks

| Notebook | Description |
|----------|-------------|
| `PreliminaryAnalysis.ipynb` | Raw data exploration and initial feature correlation |
| `1_AnomalyDetection.ipynb` | Outlier detection using PCA and multivariate methods |
| `2_MultivariateRegression.ipynb` | OLS + LASSO regression modeling and evaluation |
| `3_Event_Based_Analysis.ipynb` | Stock behavior analysis around major economic events |

---

## 🗃️ Dataset

- Source: [Yahoo Finance API](https://www.yfinance.com/)
- Period: January 2013 – December 2024
- Assets: Meta, Microsoft, ExxonMobil, S&P 500
- Macroeconomic Features: Interest Rate, Crude Oil Price, Inflation Rate

---

## ✅ Key Findings

- **Regression Models:** S&P 500 emerged as a strong predictor for all three stocks; Oil and Interest Rates had stock-specific effects.
- **Anomalies Detected:** COVID-19 crash, US-China trade war, Fed Rate Hikes
- **Events Evaluated:** 2015 China crash, 2020 pandemic, Brexit, GameStop short squeeze
- **Volatility shifts** were statistically significant before and after key events

---

## 📌 Visuals

All relevant visualizations (correlation matrices, anomaly plots, regression results) are available within the notebooks listed above.

---

## 📚 Key Takeaways

- Built interpretable ML/stat models for financial trend analysis
- Gained experience with macroeconomic impact measurement
- Practiced hypothesis testing and statistical diagnostics for real-world time-series data

