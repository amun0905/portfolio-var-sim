# Portfolio VaR Backtesting Simulation

This project simulates portfolio log returns and compares three parametric Value-at-Risk (VaR) approaches.  
It then backtests these models with 1-day and 10-day horizons using Kupiec tests.

## Features

- Simulated multivariate normal **log returns** with clustered correlations and adjustable volatilities.
- Flexible **portfolio weighting**:
  - Fixed or time-varying weights
  - Short positions allowed or disallowed
  - Net long / short tilt control
- Three VaR methods implemented:
  1. **Normal-Simple**: assumes simple returns are normal  
     Formula:  
     ```
     VaR = - z * σ * √h
     ```
  2. **Lognormal**: assumes log returns are normal, maps back to simple returns  
     Formula:  
     ```
     VaR = - ( exp(z * σ * √h) - 1 )
     ```
  3. **Normal-Log**: assumes log returns are normal, converted to simple % for backtesting  
     Formula:  
     ```
     VaR = - z * σ * √h
     → converted via exp(VaR) - 1
     ```
- **Backtesting**:
  - 1-day horizon
  - 10-day overlapping returns
  - 10-day non-overlapping returns
  - Kupiec likelihood ratio test for exceedances
- Detailed summary of:
  - Expected vs actual exceedances
  - Exceedance rate
  - Average VaR
  - Kupiec LR statistic and p-value
  - Asset volatilities, correlation matrix, portfolio weights, exposures

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/portfolio-var-sim.git
cd portfolio-var-sim
