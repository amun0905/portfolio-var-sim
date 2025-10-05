# Backtesting Parametric Value-at-Risk (VaR) Approaches with Scaling

This project investigates three **parametric Value-at-Risk (VaR)** estimation approaches and evaluates their performance with and without **time-horizon scaling**.  
The notebook simulates correlated asset returns, computes rolling VaR estimates under different assumptions, and applies **Kupiec backtests** to assess model accuracy.

---

## 📘 Project Overview

The notebook constructs a synthetic portfolio of multiple assets with specified volatilities and correlations.  
Assuming **geometric Brownian motion**, it simulates log-returns that are normally distributed and derives simple returns for the portfolio.  

Three VaR approaches are compared:

| Approach | Description | Assumption |
|-----------|--------------|-------------|
| **A. Simple Normal** | VaR based on portfolio simple returns | Portfolio returns are normally distributed |
| **B. Lognormal** | VaR derived from the lognormal transformation of returns | Portfolio log-returns are normal |
| **C. Normal on Log** | VaR estimated directly in log-return space | Same as B but expressed as quantile in log space |

Each approach is evaluated for both **1-day** and **10-day scaled VaR** using the square-root-of-time rule.

---

## 🔬 Methodology

1. **Portfolio Simulation**
   - Three assets with user-defined mean, standard deviation, and correlation of log-returns  
   - Returns generated via a multivariate normal model  
   - Portfolio returns computed using specified weights  

2. **VaR Computation**
   - Rolling window approach for volatility estimation  
   - 99% confidence level (Z = 2.33)  
   - Scaled VaR computed as:  
     \[
     \text{VaR}_{h} = \text{VaR}_{1} \times \sqrt{h}
     \]

3. **Backtesting**
   - Count of VaR exceedances (actual losses > VaR)
   - Comparison to expected number of breaches
   - **Kupiec proportion-of-failures (POF)** test applied to assess model accuracy:
     \[
     LR_{uc} = -2 \ln \frac{(1-p)^{n-x} p^x}{(1-\hat{p})^{n-x} \hat{p}^x}
     \]
   - p-values below 0.05 indicate model rejection

---

## 📊 Key Results

### 1-Day VaR (Unscaled)
| Approach | Breaches | Expected | Kupiec p-value | Outcome |
|-----------|-----------|-----------|----------------|----------|
| Normal (Simple) | 59 | 97.5 | 0.00002 | ❌ Rejected |
| Lognormal | 88 | 97.5 | 0.33 | ✅ Accepted |
| Normal on Log | 61 | 97.5 | 0.00007 | ❌ Rejected |

### 10-Day Scaled VaR (Non-Overlapping)
| Approach | Breaches | Expected | Kupiec p-value | Outcome |
|-----------|-----------|-----------|----------------|----------|
| Normal (Simple) | 4 | 10 | 0.03 | ❌ Rejected |
| Lognormal | 14 | 10 | 0.23 | ✅ Accepted |
| Normal on Log | 5 | 10 | 0.08 | ✅ Accepted (borderline) |

**Conclusion:**  
The **lognormal approach** consistently performs best, aligning most closely with expected exceedance frequencies both with and without scaling.

---

## ⚙️ Requirements

```bash
pip install numpy pandas matplotlib scipy
