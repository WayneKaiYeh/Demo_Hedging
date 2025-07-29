# 🛡️ Beta Hedge Strategy Demo

This repository demonstrates a **beta-hedging strategy** using inverse ETFs (e.g., SH) to protect long equity portfolios from market drawdowns. The model dynamically estimates asset-level exposure to SPY via rolling OLS regression, and calculates the hedge ratio required during stress periods.

> This is a **public demo repository** — full position data and model code are private.  
> Please contact me for collaboration or implementation access.

---

## 🚀 Features

- Rolling OLS beta estimation per asset (vs. SPY)
- Dynamic hedge ratio calculation per asset
- Supports multi-asset portfolios with variable position sizes
- Transaction cost and liquidity-aware
- Historical backtesting framework using market crash events
- Visual breakdown of portfolio beta exposure and inverse ETF hedge amounts

---

## 🧱 Strategy Pipeline
Load Position Holdings + SPY Price Data
↓
Compute log returns and rolling OLS β (per stock vs SPY)
↓
During market drawdown: trigger inverse ETF hedge calculator
↓
Output required SH quantity & capital usage
↓
Backtest hedge effectiveness vs unhedged baseline

---

## 📊 Demo: Real-World Event Replay (NVDA x SH)

### 🗓️ March 31, 2025 – Strategy Entry Signal Triggered
- 📈 Strategy A buys **NVDA**: 100 shares @ $108 → Total position value: **$10,800**
- 📉 SH ETF (Inverse S&P 500) triggered by Decision Tree logic (same date)

### 🔍 Estimated β Exposure (OLS Result)

Beta: 1.3784 (SPY ↑1% → NVDA ↑1.3784%)
Alpha: 0.0063 (average excess return, ignore)
R²: 0.782 (strong linear relationship)

---

### 🧮 Hedge Amount Calculation

```python
stock_position_value = 10800
beta = 1.3784
etf_price = 44.57
fee_rate = 0.001
tax_rate = 0.0000278
fixed_fee = 3.0
proportional_fee = tax_rate * 2

hedge_value = stock_position_value * beta
etf_shares = hedge_value / etf_price
cost_estimate = hedge_value + (etf_shares * etf_price * proportional_fee) + fixed_fee
```
---
###  📦 Output
📦 Position Value: $10,800.00
📉 Beta Value: 1.3784
🔁 Hedge Notional (pre-cost): $14,887.13
💸 Fixed Transaction Fee: $3.00
📊 Proportional Transaction Cost (round-trip): 0.000056
💵 Suggested Inverse ETF Purchase: 334.02 shares (ETF Price: $44.57)
🧾 Estimated Total Hedge Cost ≈ $14,890.95

---

### 🧪 Outcome: April Tariff Crash Impact
📦 Position Value: $10,800.00  
📉 Beta Value: 1.3784  
🔁 Hedge Notional (pre-cost): $14,887.13  
💸 Fixed Transaction Fee: $3.00  
📊 Proportional Transaction Cost (round-trip): 0.000056  
💵 Suggested Inverse ETF Purchase: 334.02 shares (ETF Price: $44.57)  
🧾 Estimated Total Hedge Cost ≈ $14,890.95  
---


## 📎 Contact

For collaboration or access to the full codebase, please contact:

**Kai Yeh**  
Email: KaiYeh820206@gmail.com  
GitHub: [WayneKaiYeh](https://github.com/yourusername)

---

## 📄 License

This repository is shared under the [**Creative Commons BY-NC-ND 4.0 License**](https://creativecommons.org/licenses/by-nc-nd/4.0/).

- ❌ No commercial use
- ❌ No derivatives or redistribution
- ✅ Attribution required

All rights to the full code, trained models, and source notebooks are reserved.



