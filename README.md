# BRICS Inflation Convergence: Stationarity and OLS Time-Series Analysis
Semester course project for Managerial Macroeconomics. Code originally written in Google Colab.

This project conducts a time series analysis by transforming the original non‑stationary variables (e.g., via differencing/log transforms/detrending) into stationary series, and then estimating relationships using ordinary least squares (OLS) regression on the transformed data.

Due to the limited sample size and the simple OLS framework (rather than full ARIMA/ARCH‑GARCH modeling), the results should be interpreted as exploratory rather than fully robust.

## Study Question
**Research topic:** A study into the leading macroeconomic factors driving inflation rate convergence among BRICS between 2000 and 2020.

## Setup Note
- Jupyter Notebook code fetches data from files in the same Google Drive directory (no longer accessible).
- Won't run as-is; for demonstration only.

## Results

### Model Specification
$$
\begin{align*}
    \text{Inflation Dispersion among BRICS}_t = \beta_0 
    + \beta_1(\text{Intra-BRICS Trade Mean}_t) \\
    + \beta_2(\text{BRICS-USA Trade Mean}_t) \\
    + \beta_3(\text{Commodity Reliance (oil and gas) Std}_t) \\
    + \beta_4(\text{Unemployment Gap Mean}_t) \\
    + \varepsilon_t
\end{align*}
$$

### OLS Coefficient Estimates
|   | Coefficient | Std. error | P>\|t\| |
|---|---|---|---|
| Constant                  | 47.5796   | 6.628     | 0.000 |
| Intra-BRICS Trade Mean    | 0.6538    | 2.803     | 0.819 |
| BRICS-USA Trade Mean      | -4.8152   | 0.720     | 0.000 |
| Commodity Reliance Std    | -5.9766   | 17.949    | 0.744 |
| Unemployment Gap Mean     | 21.0772   | 6.036     | 0.003 |

### Model Fit Statistics
- $R^2 = 0.798$
- Adjusted $R^2 = 0.744$

### Stationarity Diagnostics
- **ADF test on OLS residuals:** $p = 0.0264$.
- At the 5% significance level, this suggests the residual series is stationary.
- This supports model adequacy against spurious-regression concerns, but does not by itself rule out all model issues.

### Multicollinearity Diagnostics
- **Multicollinearity check (VIF):** All four independent variables have VIF values in the 2-3 range, indicating low-to-moderate multicollinearity and no severe collinearity concern in this model specification.

### Conclusion
- The model has moderate explanatory power, with roughly 80% of variance explained.
- The main statistically significant contributors are BRICS-USA Trade Mean ($p=0.000$) and Unemployment Gap Mean ($p=0.003$).
- Intra-BRICS Trade Mean and Commodity Reliance Std are not statistically significant in this specification.

## Limitations
- Inflation dynamics are inherently complex and are not fully captured by this simplified OLS framework.
- Qualitative and institutional factors that can affect inflation convergence are not explicitly modeled.
- Black-swan events (e.g., COVID-19 and the Russia-Ukraine war) may introduce structural breaks not fully addressed in this specification.

## Acknowledgements
Big special thanks to my teammates Aaron, Riva, and Iman for all of their help on the report, the presentation, model design, and data collection.
