# Portfolio management with R
Here, I focus in the typical scenario faced by a portfolio manager in an investment fund. I apply the empirical methods listed below in order to find the portfolio investment strategy that minimizes market risk. For this exercise, I use real financial data downloaded from Yahoo Finance (historical daily stock prices) .

In this exercise I apply three key methodologies widely used in Financial Econometrics:
1. A GJR-GARCH model for conditional volatility with unconditional mean and a Hansen's (1994) Skewed-t distribution for the errors.
2. A C-Vine/R-Vine copula model for dependence.
3. Portfolio optimization problem as in Rockafellar and Uryasev (2000).

 

## 1) portfolio_optimization
In the "portfolio_optimization" notebook, I illustrate the whole process followed to solve the portfolio optimization problem as suggested by Rockafellar and Uryasev (2000). This methodology requires the simulation of a large number of tomorrow return series. To do this, I use a GJR-GARCH (1,1,1) with Skewed-t errors and a C-Vine (or R-Vine) copula.

In short, the problem that I solve here is the following. We have d stocks and want to conform a portfolio of them, that is, we need to decide the proportion of our wealth that w_{i,t} that will be invested in each stock. How do we choose this allocation? We choose the portfolio strategy that minimizes market risk.

## 2) rolling_window_evaluation
In this notebook, I evaluate the portfolio performance using the approach illustrated in 1). How? As new information arrives for each stock at day t, the
portfolio manager has to make a forecast of asset returns for the next day t + 1. Based upon the forecast of asset returns, the manager rebalances the portfolio weights  to construct a new portfolio that achieves the desired investment objective (e.g., market risk minimization). In this example, weights rebalancing is done every 20 days.

To measure performance, I compute the evolution of wealth by hypothetically investing $1,000 at day t=0. The evolution of wealth is given by  
```math
W_{t+1}=W_t(1 + w_{1,t}r_{1,t}+w_{2,t}r_{2,t}+...+w_{d,t}r_{d,t})
```
where 
 
```math
W_0=1000
```
 
