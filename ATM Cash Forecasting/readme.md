# ATM Cash Demand Forecasting

Forecasting ATM cash demand is critical for optimizing cash replenishment, minimizing idle cash, and preventing cash-out situations. This project develops a machine learning-based forecasting pipeline that predicts daily cash withdrawals using historical transaction patterns, temporal features, and engineered time-series features.

The solution was developed as part of a machine learning case study and demonstrates an end-to-end data science workflow, from exploratory data analysis and feature engineering to model development and evaluation.

---

## Problem Statement

Banks replenish ATMs periodically to ensure uninterrupted cash availability while avoiding excessive idle cash.

The objective of this project is to predict the daily cash dispensed by each ATM using historical transaction data, enabling more efficient cash replenishment planning.

---

## Dataset

The dataset contains historical ATM transaction records collected across multiple banks.

### Features

| Feature | Description |
|----------|-------------|
| Account | Bank identifier |
| ATMID | Unique ATM identifier |
| caldate | Transaction date |
| Dispense | Cash dispensed (Target Variable) |
| DT | ATM downtime (hours) |
| MaxCapacity | Maximum ATM cash capacity |
| CountTotalTxn | Number of transactions |

Dataset Characteristics

- 14,593 observations
- 21 ATMs
- 3 Banks
- Date Range: January 2021 – February 2023
- No missing values
- No duplicate records

---

## Project Workflow

### 1. Data Preprocessing

- Cleaned column names
- Parsed date fields
- Sorted observations chronologically
- Encoded categorical variables
- Created train-test split based on time

---

### 2. Exploratory Data Analysis

Performed exploratory analysis to understand:

- Cash withdrawal distribution
- ATM-wise demand patterns
- Bank-wise comparisons
- Transaction frequency
- Capacity utilization
- Temporal trends
- Feature correlations

---

### 3. Feature Engineering

Generated several predictive features including:

#### Calendar Features

- Year
- Month
- Day
- Quarter
- Week
- Day of Week
- Day of Year
- Month Start
- Month End
- Weekend Indicator

#### Time-Series Features

- Lag-1
- Lag-2
- Lag-3
- Lag-7
- Lag-14
- Lag-21
- Lag-28

#### Rolling Statistics

- Rolling Mean (3, 7, 14, 30 days)
- Rolling Standard Deviation

#### Exponential Moving Average

- EMA-7
- EMA-14

#### Operational Features

- ATM Downtime
- Transaction Count
- Maximum Capacity

---

## Machine Learning Model

Model used:

- XGBoost Regressor

Baseline model predictions were compared against the XGBoost model to evaluate forecasting performance.

---

## Evaluation Metrics

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

### Results

| Model | MAE | RMSE |
|-------|------:|------:|
| Baseline | 140,623 | 191,705 |
| XGBoost | 1,018 | 1,306 |

The XGBoost model significantly outperformed the baseline by effectively capturing temporal demand patterns.

---

## Visualizations

The project includes:

- Exploratory Data Analysis
- ATM-wise demand trends
- Actual vs Predicted comparison
- Feature Importance Analysis

---

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook

---

## Repository Structure

```
ATM-Cash-Forecasting/
│
├── notebook.ipynb
├── requirements.txt
├── presentation.pptx
├── data Excel
├── forecast.csv
├── problem statement docx
└── Readme.md
```

---

## Future Improvements

- Time-series cross-validation
- Hyperparameter optimization
- SHAP-based model explainability
- Holiday and festival feature engineering
- Multi-step forecasting
- Production deployment using FastAPI or Streamlit

---

## Key Takeaways

- Built an end-to-end forecasting pipeline for ATM cash demand.
- Applied feature engineering techniques tailored to time-series data.
- Trained and evaluated an XGBoost regression model.
- Demonstrated how machine learning can support operational decision-making in banking by improving cash replenishment strategies.
