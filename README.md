# The Math of Market Making: Avellaneda-Stoikov Simulation

[![Launch Dashboard](https://img.shields.io/badge/App-Launch_Dashboard_📊-FF4B4B?style=flat&logo=rocket)](https://avellaneda-stoikov-mm-single-limit-order.streamlit.app/)
[![Read Case Study](https://img.shields.io/badge/Research-Full_Case_Study_📚-blue?style=flat&logo=read-the-docs&logoColor=white)](https://jordanchongja.github.io/projects/avellaneda-stoikov-MM-single-limit-order/)

![Simulation Dashboard in Action](images/dashboard_demo.gif)
*(Above: Pitting an inventory-based stochastic control strategy against naive market making in high-frequency limit order books.)*

## 💡 The Premise
Most retail trading algorithms quote symmetrically around the mid-price. But professional market makers can't do that—if the price trends against them, they end up holding toxic inventory. 

I built this simulation to explore the foundational market-making model proposed by Avellaneda & Stoikov (2006). Instead of just reading the paper, I wanted to build the engine from scratch to visually pit this stochastic control strategy against naive market making, seeing exactly when and how the naive strategy blows up.

> **My thoughts on the implementation:** [Insert your personal narrative/thoughts here...]

## 🧮 Under the Hood
To model the market maker's behavior, the engine handles a few key implementations:
* **The Reservation Price:** Using a CARA (Constant Absolute Risk Aversion) utility framework, the algorithm calculates the subjective valuation of the asset based on current inventory ($q$).
* **Optimal Spread Calibration:** Using the Hamilton-Jacobi-Bellman (HJB) equation to solve for the optimal, asymmetric distance to place bid ($\delta_b$) and ask ($\delta_a$) quotes.
* **Monte Carlo Order Flow:** Simulating the arrival of market orders using a Poisson process to test how the spreads hold up under realistic market microstructure conditions.

## 📊 Key Findings

![PnL Comparison Chart](images/pnl_comparison.png)

* **Inventory Control:** [Insert finding here, e.g., "The inventory-aware strategy consistently kept net holdings within a +/- 5 unit bound, drastically reducing capital requirements."]
* **PnL Stability:** [Insert finding here, e.g., "During simulated directional price shocks, the naive strategy suffered a severe drawdown, while the AS model skewed its quotes and captured a risk-free spread."]

## 💻 Tech Stack
* **Language:** Python 3.10
* **Math/Simulation:** `numpy`, `scipy`
* **Visualization/Frontend:** `streamlit`, `matplotlib`

## 🚀 Run the Simulation Locally

1. Clone the repository:
   ```bash
   git clone [https://github.com/jordanchongja/avellaneda-stoikov-MM-single-limit-order.git](https://github.com/jordanchongja/avellaneda-stoikov-MM-single-limit-order.git)
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Boot up the Streamlit interface:
   ```bash
   streamlit run app.py
   ```

## 📖 Deep Dive & Documentation
For the full mathematical derivation, the Hamilton-Jacobi-Bellman setup, and the comparative performance metrics, please visit the full research notebook on my website:

👉 **[Read the full breakdown at jordanchongja.github.io](https://jordanchongja.github.io/notes/posts/Paper%20-%20High-frequency%20trading%20in%20a%20limit%20order%20book/)**