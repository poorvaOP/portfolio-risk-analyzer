# portfolio-risk-analyzer

> How reliable are standard risk measures like VaR for a diversified portfolio of Indian stocks, especially in market stress?
> This project measures portfolio risk with volatility, beta, Sharpe and VaR, backtests it (including the 2020 crash), and delivers it in a Streamlit dashboard.

## Status
Work in progress.
- Done: repo setup
- Next: data pull, returns, volatility, correlation, beta, Sharpe
- Later: VaR (historical + Monte Carlo), backtest, efficient frontier, Streamlit dashboard

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

## Results
Coming soon.
