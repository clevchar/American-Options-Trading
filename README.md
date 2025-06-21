# American-Options-Trading

This repository implements a unified research framework for pricing and trading American-style options. It combines Longstaff-Schwartz optimal stopping theory with a real-time implied volatility surface model grounded in market data and updated using Bayesian techniques.

## Overview

This project includes:

- A Longstaff-Schwartz Monte Carlo (LSMC) simulation to estimate early exercise policies for American put options.
- Construction of a 3D implied volatility surface in log-moneyness and time to maturity space.
- A Bayesian updating mechanism to blend market-observed IVs with a fitted surface, preserving structure while reflecting real-time noise.

## File Descriptions

### `LSMC Optimal Stopping Log-Moneyness Heat Map.ipynb`
Simulates early exercise decisions for American puts and visualizes the frequency of optimal stopping as a function of log-moneyness and time to maturity.

**Example Output:**

![LSMC Heatmap](images/Optimal_Stopping_Heatmap.png)

---

### `IV Surface on Log-Moneyness.ipynb`
Fits a polynomial surface to synthetic implied volatility data across log-moneyness and maturity. Captures both smile and term structure effects.

**Example Output:**

![IV Surface](images/IV_Surface.png)

---

### `IV Surface Log-Moneyness Bayes.ipynb`
Applies a Bayesian update to the fitted surface by blending it with noisy market-observed implied volatilities. The result is an adaptive surface that retains structural form while responding to microstructure and data.

**Example Output:**

![Bayesian IV Surface](images/IV_Surface_Bayes.png)

## Features

- Reusable framework for American option exercise simulation
- Visualized early exercise heatmaps for interpretability
- Volatility surface modeling in log-moneyness
- Bayesian updates for adaptive, noise-aware pricing
- Modular and extendable for real market data or strategy backtests

## Dependencies

```bash
pip install numpy pandas matplotlib scikit-learn scipy
