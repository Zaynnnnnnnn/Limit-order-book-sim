Limit Order Book Simulator

This project is a simplified market microstructure research environment built in Python.

It simulates a price-time priority limit order book, an inventory-aware market maker, and stochastic order flow with momentum (toxic flow) characteristics. The goal is not to build a “profitable trading bot,” but to study how spread capture, adverse selection, and inventory risk interact under different market conditions.

Why I Built This
Most retail trading projects focus on signal generation without modelling execution.
In reality, trading performance depends heavily on:
Queue priority
Order flow toxicity
Inventory exposure
Volatility regimes
Spread compensation

This simulator was built to explore those dynamics in a controlled environment.
Core Components
Matching Engine
Price-time priority
Limit and market order processing
Explicit trade event generation
Market Maker
Posts bid and ask quotes around mid price
Inventory-aware skewing
Volatility-adjusted spread
Order refresh logic
Market Environment
Random walk mid-price process
Momentum-biased market orders (toxic flow)
External liquidity placement
Research Layer
Spread capture vs adverse selection analysis
Inventory tracking
Drawdown and Sharpe metrics
Monte Carlo evaluation across multiple random seeds

Monte Carlo Evaluation
A single backtest is meaningless in a stochastic environment.
To evaluate robustness, the simulator supports Monte Carlo experiments across multiple random seeds:

python -m src.cli --mc --n 20

This produces:
Mean / std PnL
5th / 50th / 95th percentile outcomes

Fill statistics
Average drawdown
Execution quality metrics
This helps assess whether performance is structural or driven by randomness.

What This Project Is
A microstructure research sandbox
A framework for testing passive market making policies
A study of inventory risk and adverse selection

What This Project Is Not
A production trading system
A real-world exchange simulator
A latency model
A high-frequency strategy

The goal is conceptual clarity and research exploration, not production realism.

Example Output
Monte Carlo Summary
Seeds: 20
PnL mean/std: 447 / 1011
PnL p05/p50/p95: -263 / 205 / 1705
Avg spread capture (ticks): 3.10
Avg adverse selection (ticks): 3.13


This demonstrates how thin edge strategies can produce positive expectation with high variance under certain order flow assumptions.
Possible Extensions
Queue position modelling
Order cancellation dynamics
Asymmetric order flow regimes
Cross-asset market making
Statistical significance testing

Technologies Used
Python
NumPy
Dataclasses
Structured modular architecture
