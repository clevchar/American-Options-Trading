# American-Options-Trading

This repository implements a unified research framework for pricing and trading American-style options. It combines Longstaff-Schwartz optimal stopping theory with a real-time implied volatility surface model grounded in market data and updated using Bayesian techniques.

## Overview of First Principle American Option Trading logic

This includes:

- A Longstaff-Schwartz Monte Carlo (LSMC) simulation to estimate early exercise policies for American put options.
- Construction of a 3D implied volatility surface in log-moneyness and time to maturity space.
- A Bayesian updating mechanism to blend market-observed IVs with a fitted surface, preserving structure while reflecting real-time noise.
- A SABR parametric IV Surface
- A machine learning approach to IV surface

## File Descriptions

### LSMC Optimal Stopping Heat Map

Simulates American put option exercise using Longstaff-Schwartz and visualizes optimal stopping frequency across log-moneyness and maturity. This is a particualrly satisfying result as we can see a density distribution around a definite optimal execution boundary! 

**Example Output:**

![LSMC Heatmap](images/Optimal%20Stopping%20Heatmap.png)

---

### LSMC-Based Optimal Stopping Policy NN Learning and Residuals

Simulates American put option exercise using Longstaff-Schwartz and visualizes optimal stopping frequency across log-moneyness and maturity. The density axis being the third axis allows for a learnable surface, but the pyTorch prior being the surface rather than the multitude of Markovian paths the original surface was derived from means this NN policy is currently not extrapolable. 

**Example Output:**

![LSMC Optimal Stopping Policy Inferred vs NN Residuals](![LSMC-Based Optimal Stopping Policy to NN](images/LSMC-Based%20Optimal%20Stopping%20Policy%20to%20NN.png)

---

### IV Surface on Log-Moneyness

Fits a polynomial surface to synthetic implied volatility data across log-moneyness and maturity. Captures smile and term structure. Utilized Guassian smoothing as although LSMC should approach a perfect surface with infinite iteration, the 1,000 paths simulated in this example where still relatively noisy.

**Example Output:**

![IV Surface](images/IV%20Surface.png)

---

### Bayes IV Surface

Applies a Bayesian update to the fitted IV surface, blending with market-observed data while preserving shape. This in practice - should be between the thoeretically perfect IV surface we can create through infinite simulation and the real time data to allow for smoothing over curvature to capture micro-structure and volatility clustures. A promising way to synthesize this is by utilizing Bates jump diffusion via the Poisson process.

**Example Output:**

![Bayes IV Surface](images/Bayes%20IV%20Surface.png)

---

### Residual comparison of Nueral Net and SABR against true IV Surface

Although SABR is a extapolable physics equation using parameterization, it loses true structure due to effective reduction to 2D as can be observed in the residuals. Observe the nueral net can reconstruct IV surface far more accurately, but with obvious limitations in extrapolability we hope to fix through correct prior selection (path perterbation) which with high enough simulation and training time on a GPU is feasible. 
**Example Output:**

![Residuals LSMC - SABR](images/Residuals%20LSMC%20-%20SABR.png)
![Neural Net Fit to LSMC IV Surface](images/Neural%20Net%20Fit%20to%20LSMC%20IV%20Surface.png)


## Order Matching Engine
An effective order matching engine firstly stores sumbitted orders across all levels and respects the firms prioritized trade style (sit for n seconds or FOK) and then matches orders in level of time submitted (oldest has first) and then price. 

## Simulated Trading / Backtesting Engines

Simulating options trading is a decidedly complex topic. The first bifercation is trading on historical data or simulated data. L2 historical data is proprietary which creates the following problem; although historical data captures the imperfection of the markets without full orderbook data this means we must either simulate orderbook data with a density function or populate it with market representative agents (both highly perscriptive) and additionally it raises the issue of trade impacts on market states (injecting volatility into a definite pre-perscribed path). One solution is to use a simulated Markovian underlying and then from that perterb various Black-Scholes paths with injected volitility to leave room for alpha capture. In this framework agents can populate the order book which in turn impacts on the pricing path without distorting true historical data.

![Underlying Markovian Path + BS Perturbed Paths for Various Strikes](images/Simulated%20Options%20Prices.png)

## Orderbook Topology 

By projecting orderbook data (real or simulated) onto a multi-dimensional metric, say log-moneyness, IV, and TTE it is possible to analyze the varying topologies of firms proprietary first principle logic. Observing the time-series development and discontinous (buy and sell inhabit different spaces in the metric by nature) geometries of the strategies may be insightful for inter-firm advesarial dynamics. Overlap is either adveserial trades of the same asset (one buys from another) or latency wars (two hoping to buy). 

![Mathematical Formulas](images/Outline.pdf)



## Dependencies

```bash
pip install numpy pandas matplotlib scikit-learn scipy torch

