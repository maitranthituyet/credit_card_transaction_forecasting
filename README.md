# Credit-Card Transaction Forecasting & Anomaly Detection

Time-series forecasting project that predicts daily credit-card spending and highlights anomalous spikes/drops that may indicate campaigns, holidays, or potential fraud.

| Metric | Value |
|--------|-------|
| **RMSE** | **1 ,605** |
| **MAE** | 1 ,101 |
| **R²**  | 0.78 |

> **Tech stack:** Python · Pandas · Plotly · Prophet · Scikit-Learn

---

## 1 · Project Goals
1. **Forecast** daily spend 30 days ahead to support budgeting and risk monitoring.  
2. **Detect anomalies** in historical data via residual analysis ( >|3σ| ).  
3. **Demonstrate an end-to-end workflow**: data cleaning → feature engineering → EDA → modeling → evaluation → insight delivery.

---

## 2 · Dataset
- **Source:** [Kaggle – Credit Card Transactions Dataset](https://www.kaggle.com/datasets/priyamchoksi/credit-card-transactions-dataset)  
- **Records:** ≈ 26 k transactions  
- **Period:** Jan 2019 – Jun 2020  
- **Core fields used:**  
  `trans_date_trans_time`, `amt`, `merchant`, `category`, `cc_num`, `gender`, `state`, `city`, `job`, `dob`

---

## 3 · Key Steps

| Stage | Highlights |
|-------|------------|
| **EDA** | Trend plots, weekday/hour heat-map, day-in-month patterns |
| **Data Prep** | Winsorization (IQR), `log1p` transform ↓ skew 42 → -0.5 |
| **Feature Eng.** | `weekday`, `hour`, `day_in_month`, `customer_age` |
| **Aggregation** | Daily total spend series (`ds`, `y`) |
| **Prophet Model** | Weekly ✓  Yearly ✓  Custom monthly (30.5 d, 5 Fourier terms) |
| **Evaluation** | Hold-out last 30 days → RMSE 1.6 k, R² 0.78 |
| **Anomaly Detection** | Residuals > 3 × σ flagged; plotted red in forecast chart |
| **Visualization** | Interactive Plotly lines + heat-map + component plots |

---

## 4 · Results
- **Forecast accuracy** adequate for high-level budgeting; large spikes remain hard to predict without external signals.
- **Anomalies** cluster around late-2019 peaks → likely holiday promos or card-holder incentives.
- **Business takeaway:** incorporate holiday/calendar regressors and campaign tags to improve predictive power.
