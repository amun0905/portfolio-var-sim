# Backtesting Parametric Value-at-Risk (VaR) Approaches with Scaling

This project investigates three parametric Value-at-Risk (VaR) estimation approaches and evaluates their performance with and without time-horizon scaling.  
The notebook simulates correlated asset returns, computes rolling VaR estimates under different assumptions, and applies Kupiec backtests to assess model accuracy.


The notebook constructs a synthetic portfolio of multiple assets with specified volatilities and correlations.  
Assuming geometric Brownian motion, it simulates log-returns that are normally distributed and derives simple returns for the portfolio.  

Three VaR approaches are compared:

| Approach | Description | Assumption |
|-----------|--------------|-------------|
| **A. Simple Normal** | VaR based on portfolio simple returns | Portfolio returns are normally distributed |
| **B. Lognormal** | VaR derived from the lognormal transformation of returns | Portfolio log-returns are normal |
| **C. Normal on Log** | VaR estimated directly in log-return space | Same as B but expressed as quantile in log space |

Each approach is evaluated for both 1-day and 10-day scaled VaR using the square-root-of-time rule.

**Key result:**  
The lognormal approach consistently performs best, aligning most closely with expected exceedance frequencies both with and without scaling.

