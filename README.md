# 📊 Quantitative Finance Internship – Learning Tasks

This repository contains a set of structured tasks designed to build strong foundations in **financial markets, quantitative analysis, portfolio theory, and basic ML for trading**.

The goal is not just to compute numbers, but to **understand what they mean and why they matter**.

---

## 📌 General Guidelines

- Use **clean, well-documented Excel sheets and Python notebooks/scripts**
- Clearly mention **assumptions**
- Wherever possible, add **comments and explanations**
- Focus on **intuition + interpretation**, not just calculations
- Final outputs should be reproducible

---

# 🔹 Task 1: Market Statistics & Portfolio Metrics (Excel)

### Objective
Understand returns, risk, and portfolio-level behavior using real stock market data.

---

## 1️⃣ Data Collection

- Download **Open, High, Low, Close (OHLC)** price data using **yfinance**
- Stocks to use:
  - `TCS`
  - `M&M`
  - `ITC`
- Time period: **Last 3 years**
- Frequency: **Daily**

---

## 2️⃣ Return Calculations (Using Closing Prices)

For **each stock**, calculate:

### a. Daily Normal Returns
\[
R_t = \frac{P_t - P_{t-1}}{P_{t-1}}
\]

### b. Daily Log Returns
\[
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
\]

> Use **only closing prices** for return calculations.

---

## 3️⃣ Risk & Performance Metrics (Per Stock)

Calculate the following **for each stock individually**:

1. **Annualized Returns**
2. **Annualized Volatility**
3. **Maximum Drawdown**
4. **Sharpe Ratio**  
   (Assume risk-free rate = 0 unless specified otherwise)

---

## 4️⃣ Portfolio-Level Analysis

Now assume:
- Equal weight portfolio of the 3 stocks (⅓ each)

Calculate **the same metrics** for the portfolio:
- Annualized Returns
- Annualized Volatility
- Maximum Drawdown
- Sharpe Ratio

---

## 5️⃣ Reflection Questions (Important)

Answer these in a separate section or markdown file:

- What differences do you observe between:
  - Individual stock metrics vs portfolio metrics?
- Why does diversification matter?
- **Why do we generally use closing prices instead of open, high, or low prices?**
  - Search and explain the reasoning

---

## 6️⃣ Things to Study (Theory)

Study and understand the intuition behind:

### 📘 Technical & Fundamental Ratios
- ROE (Return on Equity)
- ROCE (Return on Capital Employed)
- PE Ratio
- PB Ratio
- PS Ratio

### 📘 Risk & Market Metrics
- Alpha (via regression)
- Beta (via regression)

---

# 🔹 Task 2: Alpha & Beta Estimation (Python)

### Objective
Understand systematic vs unsystematic risk using linear regression.

---

## 1️⃣ Data Collection

Download **closing prices** for:

### Stocks (Any 5 or use these):
- TCS
- M&M
- ITC
- HDFCBANK
- TATAMOTORS

### Indices (Any 5 or use these):
- NIFTY
- BANKNIFTY
- NIFTYIT
- NIFTYAUTO
- NIFTYMETAL

---

## 2️⃣ Return Computation

- Compute **log returns** for all stocks and indices

---

## 3️⃣ Alpha & Beta Estimation

Using **Linear Regression**:

For **each stock**, calculate:
- Alpha
- Beta

**With respect to each index**, i.e.:

\[
R_{stock} = \alpha + \beta \cdot R_{index} + \epsilon
\]

---

## 4️⃣ Interpretation Questions

Answer clearly:

- What does **beta** represent?
- What does **alpha** represent?
- Can a stock have:
  - High beta and negative alpha?
  - Low beta and positive alpha?
- How would you use alpha & beta in portfolio construction?

---

# 🔹 Task 3: Multi-Market ML Setup (Python)

### Objective
Understand cross-market dependencies and walk-forward modeling for trading.

---

## 1️⃣ Data Collection

Download **closing prices (last 5 years)** for:

- **NIFTY50** (India)
- **S&P 500** (US Market)
- **NIKKEI 225** (Japan)
- **HANG SENG** (China)

---

## 2️⃣ Return Engineering

- Calculate **log returns** for all indices
- Adjust dates carefully considering **market opening & closing times**

### Important Assumption
At **Indian market opening**, assume you have access to:
- Previous day US market data
- Same day Asian market data (if applicable)

---

## 3️⃣ Feature & Label Design

### 📥 Features
- Close-to-close log returns of:
  - S&P 500
  - Nikkei
  - Hang Seng
  - NIFTY (previous day)

### 📤 Label
\[
\log\left(\frac{Open_{NIFTY, t+1}}{Close_{NIFTY, t}}\right)
\]

This represents:
> Predicting **next day open movement** of NIFTY based on global cues

---

## 4️⃣ Modeling Framework

- Study **Walk Forward (Rolling Window) Method**
- Use the following approach:
  - Train on **500 data points**
  - Predict next **10 days**
  - Slide the window forward
  - Repeat until dataset ends

The **10-day predictions** form one evaluation block.

---

## 5️⃣ Strategy Evaluation Metrics

Based on model predictions, compute:

- Annualized Returns
- Maximum Drawdown
- Volatility
- Sharpe Ratio
- Accuracy (Direction prediction)

---

## 6️⃣ Final Reflection

Answer:
- Why is walk-forward validation preferred in financial time series?
- Why is random train-test split dangerous in markets?
- What are the limitations of this setup?

---

# ✅ Expected Deliverables

- Excel files (Task 1)
- Python notebooks/scripts (Task 2 & 3)
- A short **summary document** explaining:
  - Observations
  - Assumptions
  - Key learnings

---

📌 **Reminder**  
Markets are noisy. The objective is not perfect prediction, but **structured thinking, correct methodology, and sound interpretation**.
