# Building Better Stock Portfolios: Mean-Variance, CAPM and Shrinkage

**Author:** Francisca (Kika) Freixo  

Constructing and back-testing mean-variance optimal portfolios on real stock data, then improving their out-of-sample performance by shrinking sample means toward CAPM-implied returns.

**R · quantmod · quadprog · xts · ggplot2 · R Markdown**

📄 **[View the full report (HTML)](https://kika2006.github.io/reports/optimal_portfolios.html)**

---

## Approach (team of 4)
1. Download daily stock prices (`quantmod`) and the 3-month T-bill rate (FRED DTB3), then convert to daily excess returns.
2. **Odd/even day cross-validation**: build portfolios on one half of the data and test them on the other. Two-sample t-tests check how stable the means and volatilities are.
3. **Mean-variance optimisation** with `quadprog`, with and without short-selling.
4. **CAPM**: estimate betas against SPY and optimise on CAPM-implied expected returns.
5. **Shrinkage**: blend the two estimates with μ = κ · sample mean + (1 − κ) · CAPM, testing κ from 0 to 1.

## Key finding
Raw sample means overfit, because they look great in-sample and disappoint out-of-sample. Blending in CAPM helps. **κ = 0.5 gave the best out-of-sample Sharpe ratio (0.060)**, beating pure CAPM (0.045) and pure sample means (0.054).

## Running it
Open `optimal_portfolios.Rmd` in RStudio and knit it. Prices are downloaded automatically. Put your ticker list in `data/teamticker.csv`.

*Maastricht University, eLab Business Case (2025).*
