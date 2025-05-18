# Trading Strategy Analysis Assignments

## Assignment 1: Profit Factor & Win Rate Sensitivity
**Goal:** Simulate trades and analyze how Profit Factor and Win Rate interact.

**Tasks:**
- Generate synthetic trade data using:
  - `n_trades = 1000`
  - `win_rate` varying from 0.3 to 0.7
  - `avg_win` and `avg_loss` as parameters (e.g., 2:1 reward-to-risk)
- Calculate Profit Factor and visualize its relationship with Win Rate
- Identify the minimum Win Rate needed for Profit Factor > 1.5 when reward:risk = 2:1
- **Bonus:** Add random noise to trade sizes (e.g., ±20% variation)

**Key Python Tools:**
- `numpy.random` for trade simulation
- `matplotlib` for plotting
- `pandas` for data aggregation

---

## Assignment 2: Tharp Expectancy vs. Alternative Formula
**Goal:** Compare the two Expectancy formulas and their sensitivity to parameter changes.

**Tasks:**
- Simulate a strategy with variable `win_rate`, `avg_win`, and `avg_loss`
- Compute both versions of Expectancy:
  1. Tharp's: `(win% * avg_win) - (loss% * avg_loss)`
  2. Alternative: `[ (avg_win * win%) + (avg_loss * loss%) ] / -avg_loss`
- Plot how Expectancy changes when:
  - Reward:Risk increases from 1:1 to 5:1
  - Win Rate drops from 60% to 30%
- **Insight:** Identify scenarios where the two formulas diverge in interpretation

---

## Assignment 3: Sharpe Ratio & Volatility Sensitivity
**Goal:** Understand how volatility impacts Sharpe Ratio.

**Tasks:**
- Generate daily returns for a strategy with:
  - `mean_return = 0.1%` (daily)
  - `volatility` varying from 0.5% to 3% (daily)
- Annualize the Sharpe Ratio (`sqrt(252)` scaling)
- Visualize Sharpe Ratio vs. Volatility
- **Monte Carlo Simulation:** Run 10,000 paths to see the distribution of Sharpe Ratios for a fixed mean/volatility
- **Question:** Why might a strategy with high Profit Factor still have a low Sharpe Ratio?

---

## Assignment 4: Combining Metrics for Strategy Evaluation
**Goal:** Build a "strategy report card" using multiple metrics.

**Tasks:**
- Simulate a strategy with known flaws (e.g., occasional huge losses)
- Compute:
  - Profit Factor
  - Sharpe Ratio
  - Tharp Expectancy
  - Max Drawdown
- Create a radar chart to visualize strengths/weaknesses
- **Experiment:** Tweak parameters (e.g., reduce max loss size) and rerun metrics

---

## Assignment 5: Real-World Backtesting (with yfinance)
**Goal:** Apply metrics to historical data.

**Tasks:**
- Download S&P 500 data using `yfinance` (e.g., 5 years of daily prices)
- Implement a simple moving average crossover strategy
- Calculate:
  - Profit Factor
  - Sharpe Ratio (use risk-free rate = 0 for simplicity)
  - Win Rate & Expectancy
- **Critical Analysis:** Why might these metrics mislead in live trading?

---

## Assignment 6: Monte Carlo Robustness Testing
**Goal:** Stress-test a strategy's sensitivity to randomness.

**Tasks:**
- Take a strategy with fixed `win_rate` and reward:risk
- Run 10,000 Monte Carlo simulations of 100 trades each
- For each simulation, compute Profit Factor and Expectancy
- Plot histograms and calculate:
  - Probability of Profit Factor > 2.0
  - 95% confidence interval for Expectancy
- **Insight:** How does trade count affect metric reliability?

---

## Assignment 7: Risk-of-Ruin Simulation
**Goal:** Model the probability of blowing up an account.

**Tasks:**
- Simulate a strategy with:
  - `starting_capital = $10,000`
  - Fixed risk per trade (e.g., 1-5% of capital)
- Use Tharp Expectancy to model equity curves over 100 trades
- Calculate the probability of:
  - 20% drawdown
  - Full account wipeout
- **Visualization:** Plot 100 equity curves on a single graph

---

## Final Project: Optimize a Strategy Using Metrics
**Goal:** Build a genetic algorithm to maximize Sharpe Ratio or Expectancy.

**Tasks:**
- Define a parameter space (e.g., moving average periods, risk per trade)
- Use DEAP (evolutionary algorithm framework) to evolve strategies
- Fitness function = Sharpe Ratio (or Expectancy)
- Analyze the Pareto frontier between Profit Factor and Max Drawdown