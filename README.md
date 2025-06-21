# American-Options-Trading
# American-Options-Trading

This repository implements a unified research framework for pricing and trading American-style options. It combines Longstaff-Schwartz optimal stopping theory with a real-time implied volatility surface model grounded in market data and updated using Bayesian techniques.

---

## Concepts

- **LSMC Optimal Stopping**: Uses Monte Carlo simulation to identify early exercise regions for American puts, visualized in log-moneyness and time to maturity space.
- **Implied Volatility Surface**: Builds a 3D implied volatility surface from Black-Scholes-inverted market prices, fit in log-moneyness space.
- **Bayesian Surface Update**: Blends real market observations with theoretical fits to maintain a realistic and adaptive volatility surface, preserving structure and incorporating noise.

---

## File Descriptions

### `LSMC Optimal Stopping Log-Moneyness Heat Map.ipynb`

Simulates American put options using the Longstaff-Schwartz method and visualizes the frequency of optimal exercise across a grid of time to maturity and log-moneyness.

#### Example Output:

<p align="center">
  <img src="images/Optimal_Stopping_Heatmap.png" alt="LSMC Heatmap" width="500"/>
</p>

---

### `IV Surface on Log-Moneyness.ipynb`

Builds a 3D implied volatility surface using polynomial regression over log-moneyness and time. The surface captures volatility smile and term structure features and can be evaluated across a grid.

#### Example Output:

<p align="center">
  <img src="images/IV_Surface.png" alt="IV Surface" width="500"/>
</p>

---

### `IV Surface Log-Moneyness Bayes.ipynb`

Applies a Bayesian update to the previously fitted IV surface by blending it with noisy or observed market data. This creates a surface that reflects real-time conditions while retaining the theoretical structure.

#### Example Output:

<p align="center">
  <img src="images/IV_Surface_Bayes.png" alt="Bayesian Adjusted IV Surface" width="500"/>
</p>

---

## Features

- Reusable framework for American option exercise simulation
- Visualized early exercise heatmaps for interpretability
- Volatility surface modeling in log-moneyness
- Bayesian updates for adaptive, noise-aware pricing
- Fully modular and extendable for real market data or trading bots

---

## To test

```bash
pip install numpy pandas matplotlib scikit-learn scipy
