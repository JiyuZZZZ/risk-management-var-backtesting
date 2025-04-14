# 📉 Portfolio Risk Management with VaR, ES and Backtesting

This project implements a full-cycle **Value-at-Risk (VaR)** and **Expected Shortfall (ES)** estimation and evaluation framework for a 4-asset portfolio.  
It was completed as part of my MSc Risk Management coursework and explores multiple risk quantification and validation techniques.

---

## 🎯 Project Goal

Estimate the **minimum capital requirement** for a financial institution using:

> **C = 2.5 × VaR₀.₉₉**

and critically assess the robustness of this estimate using **statistical backtesting** and **distributional diagnostics**.

---

## 🧠 Key Components

### 1. **Parametric VaR & ES (Variance-Covariance Method)**

- Assumes multivariate normality
- Uses historical mean vector and covariance matrix
- Applies linear approximation to compute portfolio-level loss statistics
- Calculates:
  - VaR₀.₉₉
  - ES₀.₉₉
  - Capital requirement `C`

### 2. **Historical Simulation Method**

- Makes no distributional assumptions
- Uses actual historical losses of the portfolio
- Provides a more conservative tail estimate compared to parametric VaR

---

## 📊 Backtesting Methods

- **Standard Coverage Test**: Compares the actual exceedance count with the 1% threshold
- **Kupiec PF Test**: Performs likelihood ratio test to determine if exceedances follow expected binomial distribution
- Results are validated using both custom functions and the `GAS` R package

### 🔍 Key Finding:
> The historical VaR method passed both backtests,  
> while the parametric method **underestimated tail risk**, with excessive exceedances.

---

## 🧪 Distribution Diagnostics

- Q-Q plots and Shapiro–Wilk test reveal **strong departure from normality**
- All four asset returns display **heavy tails**
- Explains why variance-covariance VaR tends to **understate the true risk**

---

## 🧮 Capital as VaR (C = 2.5 × VaR)

This project also tests using **capital C directly as VaR**:
- Results in significantly fewer exceedances
- Passes coverage tests
- But may be **overly conservative**, impacting capital efficiency

> **Conclusion:** While C improves coverage, it may lead to under-utilization of capital in practice.

---

## 📁 Project Files

- `Risk_Management_VaR_Analysis.Rmd` – R Markdown code with full analysis
- `sample_returns.csv` – Simulated daily log returns for 4 hypothetical assets

---

## 📁 Sample Data

The file `sample_returns.csv` contains **simulated daily log-returns** for four hypothetical assets over 600 trading days.  
It is generated solely for demonstration purposes and does **not** reflect real financial market data.

---
## 🧬 Technologies Used

- R, tidyverse, MASS, GAS, stats
- Q-Q plots, statistical hypothesis testing
- Portfolio aggregation and loss modeling

---

## 👤 Author

Jiyu Zhang  
MSc Financial Mathematics, University of Leeds
