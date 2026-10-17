# portfolio-risk-analyzer

> How reliable are standard risk measures like VaR for a diversified portfolio of Indian stocks, especially in market stress?
> This project measures portfolio risk with volatility, beta, Sharpe and VaR, backtests VaR against actual losses, and delivers it in a Streamlit dashboard.

## Status
Work in progress.
- Done: data pull, returns, volatility, correlation, beta, Sharpe, historical and Monte Carlo VaR, Expected Shortfall, VaR backtest
- Next: EWMA (volatility-adjusted) VaR, efficient frontier, out-of-sample comparison
- Later: Streamlit dashboard and deployment

## Planned features
- Returns, volatility, correlation and beta vs Nifty 50
- Sharpe ratio (risk-free rate stated in the notebook)
- Historical and Monte Carlo VaR, plus Expected Shortfall
- VaR backtest: breaches vs the expected rate
- Efficient frontier: min-variance vs max-Sharpe portfolios
- Interactive Streamlit dashboard

## Tech stack
Python, Pandas, NumPy, SciPy, yfinance, Matplotlib/Plotly, Streamlit

## Repo structure
- `notes/`: concept notes with formulas
- `notebooks/`: analysis notebooks
- 
## Results

Setup: Equal-weighted portfolio of 8 Indian large-cap stocks across sectors (banks, IT, FMCG, pharma, autos, infrastructure, energy), benchmarked against Nifty 50. 5 years of daily data from yfinance, risk-free rate assumed at 7%.
Stock-level metrics:
- Annualized volatility ranged from about 20% (ITC) to 26% (Infosys), against 13.8% for the Nifty 50.
- Betas vs Nifty ranged from 0.56 (Sun Pharma) to 1.19 (L&T).
- Correlations between sectors were low to moderate (mostly 0.14 to 0.43), while Infosys and TCS were highly correlated (0.73), so diversification benefit comes mainly from mixing sectors.
- Several stocks (Infosys, TCS, HDFC Bank) had negative Sharpe ratios because their returns over this window fell below the 7% risk-free rate.

VaR (1-day, equal-weighted portfolio)
| Method | 95% | 99% |
| Monte Carlo VaR | 1.40% | 2.00% |
| Historical Expected Shortfall | 1.94% | 2.78% |

VaR backtest: A 250-day rolling historical VaR (95%) was breached on 54 of 985 days (5.48%) vs 5% expected. Overall calibration is close, but breaches cluster in high-volatility periods (for example Feb to May 2026), which shows that rolling historical VaR adapts slowly when volatility rises.

![VaR backtest](images/var_backtest.png)

Limitations: Equal weights only so far, normal-distribution assumption in Monte Carlo, a single 5-year window, and no transaction costs.
Breach rate 4.87% vs 5.48% for rolling VaR, with fewer breaches in high-volatility years (2026: 14 vs 21), though breaches still cluster in volatile periods.

