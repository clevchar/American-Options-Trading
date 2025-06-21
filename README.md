# American-Options-Trading

This repository implements a unified research framework for pricing and trading American-style options. It combines Longstaff-Schwartz optimal stopping theory with a real-time implied volatility surface model grounded in market data and updated using Bayesian techniques.

## Overview

This project includes:

- A Longstaff-Schwartz Monte Carlo (LSMC) simulation to estimate early exercise policies for American put options.
- Construction of a 3D implied volatility surface in log-moneyness and time to maturity space.
- A Bayesian updating mechanism to blend market-observed IVs with a fitted surface, preserving structure while reflecting real-time noise.

## File Descriptions

### LSMC Optimal Stopping Heat Map

Simulates American put option exercise using Longstaff-Schwartz and visualizes optimal stopping frequency across log-moneyness and maturity.

**Example Output:**

![LSMC Heatmap](images/Optimal%20Stopping%20Heatmap.png)

---

### IV Surface on Log-Moneyness

Fits a polynomial surface to synthetic implied volatility data across log-moneyness and maturity. Captures smile and term structure.

**Example Output:**

![IV Surface](images/IV%20Surface.png)

---

### Bayes IV Surface

Applies a Bayesian update to the fitted IV surface, blending with market-observed data while preserving shape.

**Example Output:**

![Bayes IV Surface](images/Bayes%20IV%20Surface.png)

## Features

- Reusable framework for American option exercise simulation
- Visualized early exercise heatmaps for interpretability
- Volatility surface modeling in log-moneyness
- Bayesian updates for adaptive, noise-aware pricing
- Modular and extendable for real market data or strategy backtests

## Dependencies

```bash
pip install numpy pandas matplotlib scikit-learn scipy

