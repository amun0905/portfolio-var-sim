\# Portfolio VaR Backtesting Simulation



This project simulates portfolio log returns and compares three parametric Value-at-Risk (VaR) approaches.  

It then backtests these models with 1-day and 10-day horizons using Kupiec tests.



---



\## Features



\- Simulated multivariate normal \*\*log returns\*\* with clustered correlations and adjustable volatilities.

\- Flexible \*\*portfolio weighting\*\*:

&nbsp; - Fixed or time-varying weights

&nbsp; - Short positions allowed or disallowed

&nbsp; - Net long / short tilt control

\- Three VaR methods implemented:

&nbsp; 1. \*\*Normal-Simple\*\*: assumes simple returns are normal  

&nbsp;    Formula: `VaR = - z \* σ \* √h`

&nbsp; 2. \*\*Lognormal\*\*: assumes log returns are normal, maps back to simple returns  

&nbsp;    Formula: `VaR = - ( exp(z \* σ \* √h) - 1 )`

&nbsp; 3. \*\*Normal-Log\*\*: assumes log returns are normal, converted to simple % for backtesting  

&nbsp;    Formula: `VaR = - z \* σ \* √h` → converted via `exp(VaR) - 1`

\- \*\*Backtesting\*\*:

&nbsp; - 1-day horizon

&nbsp; - 10-day overlapping returns

&nbsp; - 10-day non-overlapping returns

&nbsp; - Kupiec likelihood ratio test for exceedances

\- Detailed summary of:

&nbsp; - Expected vs actual exceedances

&nbsp; - Exceedance rate

&nbsp; - Average VaR

&nbsp; - Kupiec LR statistic and p-value

&nbsp; - Asset volatilities, correlation matrix, portfolio weights, exposures



---



\## Installation



Clone the repository:



```bash

git clone https://github.com/YOUR\_USERNAME/portfolio-var-sim.git

cd portfolio-var-sim



