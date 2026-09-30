# Concept Notes

## 1. Returns
Gain or loss from an investment over a specific period of time.
Simple return = (P_t - P_t-1) / P_t-1
Logarithmic return = ln(P_t / P_t-1)​
Example: If the price of a stock changes from $100 to $110 then 
         Simple Return = (110-100)/100 = 0.10 i.e. 10%
         Logarithmic Return = ln(110/100) i.e. 9.53%
It is the base input required for other metrics in this project: volatility, correlation, beta, Sharpe and VaR.
These metrics are all calculated from returns, and not from the raw prices.

## 2. Volatility
Standard deviation of returns, measuring the degree of fluctuation or uncertainty in investment returns.
σ = √{Σ(R_i − R̄)²/n-1} where R_i = individual return, R̄ = mean return, n = number of returns.
Example: If returns = {10%, 0%, -10%}, volatility = 10%
It quantifies portfolio risk by measuring how much returns fluctuate, and it feeds directly into Sharpe ratio and VaR calculations.

## 3. Correlation and Covariance
Measures the relationship between two assets' returns.
Covariance indicates their direction of movement.
Correlation indicates the strength and direction of the relationship between two assets' returns, ranging from -1 to +1.
Cov(X,Y) = Σ{(X_i − X̄)(Y_i − Ȳ)} / (n − 1)
Corr(X,Y) = Cov(X,Y) / (σX × σY)
Example: If stocks A and B move together → Positive covariance & correlation.
Correlation and covariance determine how diversification can benefit a portfolio. 
This project uses it to build a correlation matrix and to check if combining assets actually reduces portfolio risk.

## 4. Beta and CAPM 
Beta measures an asset's sensitivity to overall market movements.
CAPM estimates an asset's expected return based on a risk free rate and its systematic risk (beta).
β = Cov(R_i, R_m) / Var(R_m) where R_i = asset return, R_m = market return
Expected Return = Rf + β(Rm − Rf) where Rf = risk-free rate, Rm = expected market return, (Rm − Rf) = market risk premium
Example: If risk free rate = 5%, beta = 1.2, expected market return = 10% -> expected return = 11%  
Beta shows how sensitive each stock is to overall market moves and is useful for understanding which stocks in the portfolio add the most systematic risk.

## 5. Sharpe Ratio
Sharpe Ratio measures how much excess return is earned per unit of risk.
Sharpe Ratio = (Rp − Rf) / σp where Rp = portfolio return ,Rf = risk free rate, σp = portfolio volatility
Example: If portfolio return = 12%, risk free rate  = 4%, portfolio volatility = 10% -> Sharpe Ratio = 0.8
It enables risk-adjusted comparison of portfolios and helps the optimizer find the portfolio weights that maximize return per unit of risk.
