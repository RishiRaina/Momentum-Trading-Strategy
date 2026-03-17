# 📈 Momentum Trading Strategy (ML-Based)

## 🚀 Overview
This project implements a machine learning–driven momentum trading strategy for Indian equities. The model predicts the probability of positive next-week returns and constructs a weekly rebalanced portfolio using a strict out-of-sample framework.

The strategy combines:
- Feature engineering (momentum, volatility, volume)
- Ensemble learning
- Transaction cost modeling
- Portfolio-level backtesting

---

## 🎯 Objective
To design a robust trading strategy that:
- Avoids look-ahead bias  
- Uses strict out-of-sample evaluation  
- Generates consistent risk-adjusted returns  

---

## 📊 Dataset

### 📌 Asset Universe
- RELIANCE  
- TCS  
- INFY  
- HDFCBANK  
- ICICIBANK  
- BHARTIARTL  
- BAJFINANCE  
- HINDUNILVR  
- HCLTECH  
- MARUTI  

### 📅 Data Details
- Type: Daily OHLCV  
- Period: Jan 2015 – Dec 2025  
- Frequency Used: Weekly (W-MON)  

---

## ⚙️ Methodology

### 🔄 Weekly Resampling
Daily data is converted into weekly bars:
- Open → first price of the week  
- High → weekly maximum  
- Low → weekly minimum  
- Close → last price of the week  
- Volume → total weekly volume  

---

### 🧠 Feature Engineering

#### 📈 Momentum Features
- 1-week momentum  
- 4-week momentum  
- 12-week momentum  

#### 📉 Volatility Features
- 4-week rolling volatility  
- 12-week rolling volatility  

#### 📊 Volume Feature
- Volume Z-score (12-week rolling window)  

All features use only historical data (no look-ahead bias).

---

### 🏷️ Label Construction

Binary classification task:

target_t = 1 if R_{t+1} > 0 else 0

---

## 🤖 Model Architecture

### 🔹 Ensemble (Soft Voting)

P(up) = (P_LR + P_RF + P_GB) / 3

### 🔧 Base Models
- Logistic Regression  
- Random Forest  
- Gradient Boosting  

---

## 📊 Training & Testing

| Period | Usage |
|------|------|
| 2015–2022 | Training + Validation |
| 2023–2025 | Out-of-sample Testing |

Strict separation ensures no data leakage.

---

## 💼 Portfolio Construction

### 📌 Strategy Rules
- Rank stocks by predicted probability  
- Select top 2 stocks  
- Equal weights (50% each)  
- Weekly rebalancing  

---

### 💸 Transaction Costs
- 10 bps per trade  
- 20 bps round-trip  

---

## 🔁 Backtesting

Portfolio return:

R_p,t = Σ (w_i * R_i,t+1)

Net return:

R_net = R_p,t - transaction costs

---

## 📈 Performance (2023–2025)

- CAGR (Net): 12.26%  
- Volatility: 17.15%  
- Sharpe Ratio (Gross): 1.36  
- Sharpe Ratio (Net): 0.75  
- Max Drawdown: -13.37%  
- Weekly Turnover: 0.70  
- Cumulative Return: ~1.93x  

---

## 📌 Key Insights
- Momentum signal is effective in Indian equities  
- Ensemble models improve robustness  
- Transaction costs significantly impact performance  
- Strategy delivers steady growth with controlled risk  

---

## ⚠️ Assumptions & Limitations

### Assumptions
- Weekly rebalancing at close  
- Constant transaction costs  
- Full execution at modeled prices  

### Limitations
- Fixed transaction cost assumption  
- No handling of market holidays  
- Limited asset universe  

---

## 🏁 Conclusion
This project demonstrates that small, consistent predictive edges can compound into meaningful returns when applied with discipline and proper validation.

---

## 🛠️ Tech Stack
- Python  
- Pandas, NumPy  
- Scikit-learn  
- Matplotlib / Seaborn  

---
