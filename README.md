# Comparative Stock Prediction: Multivariate Regression and Event-Aligned Anomaly Analysis

This project presents a robust empirical study on sectoral stock behavior using multivariate regression modeling, PCA-informed anomaly detection, and event-based volatility diagnostics. It investigates how macroeconomic indicators and major global events influence the return dynamics and volatility profiles of key stocks in the tech and energy sectors over a 12-year period (2013–2024).

> Developed as part of the final project for DSC 244: Time Series Analysis & Financial Econometrics.

---

## Objectives

- Quantify the impact of macroeconomic factors (S&P 500, crude oil, interest rates) on stock returns of META, MSFT, and XOM.
- Identify stock-specific and cross-stock anomalies in weekly log returns using multivariate and PCA-based methods.
- Evaluate the structural changes in volatility and correlation patterns before and after known economic events (e.g., COVID-19 crash, Fed hikes).
- Assess the limitations of OLS regression and propose regularized extensions.

---

## Dataset

- **Source**: Yahoo Finance API (`yfinance`)
- **Time Range**: Jan 1, 2013 – Dec 31, 2024
- **Stocks Analyzed**:
  - META (Tech)
  - MSFT (Tech)
  - XOM (Energy)
  - ^GSPC (S&P 500 Index)
- **Derived Features**:
  - Weekly averaged log returns
  - Rolling volatility
  - Principal Components (PCs)
  - Sectoral correlation matrices

---

## Methodology

### 1. Anomaly Detection
- **Univariate**: Z-score testing on median-centered IQR-based normal distribution (price only)
- **Bivariate**: PCA on price & volume → Mahalanobis distance → BH-corrected p-values
- **Multivariate (m=8)**: Three approaches using raw features, all PCs, and top 2 PCs (from Marčenko–Pastur distribution)
- **Validation**: Simulated null distributions verified the robustness of PC-based Mahalanobis detection

### 2. Multivariate Regression
- **Target**: Log returns of META, MSFT, XOM
- **Features**: S&P500, crude oil prices, interest rates
- **Model**: OLS with BH correction, VIF diagnostics, and exploratory ElasticNet (L1) for overfit mitigation
- **Key Insight**: S&P500 consistently emerges as the strongest predictor

### 3. Event-Based Volatility & Correlation Analysis
- Assessed rolling volatility (30-day), correlation matrices, and return distributions across:
  - COVID-19 crash
  - China market crash
  - Inflation surge and cooldown
  - Fed rate decisions
  - GME short squeeze
- Statistical significance tested via two-sample t-tests with FDR correction

---

## Key Results

| Stock | R² (OLS) | Significant Features                         |
|-------|----------|-----------------------------------------------|
| META  | 0.22     | S&P500                                        |
| MSFT  | 0.47     | S&P500, Crude Oil, Interest Rates             |
| XOM   | 0.37     | S&P500, Crude Oil, Interest Rates             |

- Anomalies from COVID-19 (low + rebound), Fed events, and trade slowdowns were successfully detected across price-only, price+volume, and all-stocks detection
- Correlation shifts post-events revealed sectoral decoupling (e.g., META-MSFT drop from 0.97 to 0.90 during COVID)

---

## Insights

- **Tech stocks** show higher volatility and stronger response to sentiment-driven shocks
- **Energy stocks** (XOM) remained more stable across most events but reflected commodity price impacts
- Multivariate outlier detection is more reliable when reducing noise via PCA
- Regularization in regression mitigates overfitting but makes parameter inference non-trivial
- Statistical significance of return shifts is rare despite strong visual evidence—reinforcing the importance of multiple forms of validation

---

## Limitations

- Anomaly detection assumes linear structure via PCA; nonlinear manifold-based methods could improve results
- Regression results limited by low R² (especially for META) and potential omitted-variable bias
- Event-based testing suffers from short pre/post windows, reducing test power

---

## Tech Stack

- Python (`pandas`, `numpy`, `scikit-learn`, `statsmodels`)
- Data source: Yahoo Finance via `yfinance`
- Visualization: `matplotlib`, `seaborn`
- Outlier detection: Mahalanobis distance, PCA, chi-square testing
- Statistical modeling: OLS, ElasticNet
