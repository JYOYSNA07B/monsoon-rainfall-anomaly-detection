# 🌧 Monsoon Rainfall Anomaly Detection

A machine learning-based system for detecting anomalies in monsoon rainfall patterns using historical data from 2001–2025. This final year project compares multiple regression models with Bayesian hyperparameter optimization to accurately predict and flag abnormal rainfall events.

---

## 📌 Project Overview

Monsoon rainfall irregularities can have severe socioeconomic impacts. This project builds a robust anomaly detection pipeline that:

- Ingests and preprocesses raw historical rainfall data (2001–2025)
- Engineers lag-based and rolling statistical features
- Trains and evaluates multiple ML regressors
- Detects rainfall anomalies using a **1.5σ adaptive threshold** on model residuals
- Compares all models by MSE, RMSE, MAE, and R² scores

---

## 🗂️ Repository Structure

```
├── Finial_Year_Project.ipynb       # Main notebook (EDA, modelling, evaluation)
├── Data_Set_2001_2025_*.xlsx       # Raw rainfall dataset
├── FINAL_DATASET_WITH_ROLLING.csv  # Preprocessed dataset with lag & rolling features
├── modei_camp.xlsx                 # Model comparison results
└── README.md
```

---

## 🧠 Models Implemented

| Model | Optimization |
|---|---|
| Linear SVR (LSVR) | Optuna Bayesian Search |
| Decision Tree Regressor | Optuna Bayesian Search |
| AdaBoost Regressor | Optuna Bayesian Search |
| Random Forest Regressor | Optuna Bayesian Search |
| Gradient Boosting Regressor | Optuna Bayesian Search |
| **Hybrid RF + Gradient Boosting** | Optuna Bayesian Search ✅ Best |

---

## ⚙️ Feature Engineering

- **Lag features** — previous time-step rainfall values
- **Rolling statistics** — rolling mean and standard deviation
- **Monthly Z-score normalization** — month-wise mean and standard deviation
- **Datetime decomposition** — month and seasonal indicators

---

## 📊 Evaluation Metrics

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R² Score

Anomaly detection is performed on model residuals using an adaptive **1.5σ threshold**, with specific focus on monsoon months (June–September).

---

## 🛠️ Tech Stack

- **Python 3**
- `pandas`, `numpy` — data handling
- `scikit-learn` — machine learning models
- `optuna` — Bayesian hyperparameter optimization
- `matplotlib`, `seaborn` — visualization
- Google Colab — development environment

---

## 🚀 Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/monsoon-rainfall-anomaly-detection.git
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn optuna matplotlib seaborn openpyxl
   ```

3. Open the notebook in Google Colab or Jupyter and update dataset paths as needed.

4. Run cells sequentially: Raw Inspection → Preprocessing → EDA → Model Training → Comparison.

---

## 📈 Results — Model Comparison

### Overall Performance (Test Set)

| Model | MSE | RMSE | MAE | R² |
|---|---|---|---|---|
| Linear SVR | 4.5761 | 2.1392 | 0.9429 | 0.8940 |
| Decision Tree | 5.7269 | 2.3931 | 0.7583 | 0.8836 |
| AdaBoost | 5.7996 | 2.4082 | 0.8417 | 0.8755 |
| Random Forest | 5.2163 | 2.2839 | 0.7051 | 0.8940 |
| Gradient Boosting | 5.1487 | 2.2691 | 0.7362 | 0.8953 |
| **Hybrid RF + GB** | **1.3969** | **1.1819** | **0.3493** | **0.9724** ✅ |

> ✅ The **Hybrid RF + GB model** outperforms all individual models significantly — nearly **8% higher R²** and **~55% lower RMSE** than the next best model.

---

### Anomaly Detection Summary (Test Set)

| Model | Threshold (±σ) | Anomalies Detected | Anomaly % |
|---|---|---|---|
| Linear SVR | ±1.5σ → 3.782 | 388 | 4.42% |
| Decision Tree | ±1.5σ → 3.318 | 1,294 | 4.92% |
| AdaBoost | ±1.5σ → 3.217 | 891 | 6.81% |
| Random Forest | ±1.5σ → 2.955 | 1,402 | 5.33% |
| Gradient Boosting | ±1.2σ → 2.255 | — | — |
| **Hybrid RF + GB** | **±1.2σ → 0.784** | **3,247** | **Heavy: 1,634 / Low: 1,613** |

---

### Top 5 Feature Importances (Random Forest)

| Feature | Importance |
|---|---|
| RPI_lag_1 | 75.75% |
| RPI_lag_3 | 17.50% |
| RPI_lag_6 | 3.65% |
| TQV | 1.43% |
| ALLSKY_SFC_SW_DWN | 0.21% |

---

## 🎓 Academic Context

This project was developed as a Final Year Project (FYP) for a M.Sc Artificial intelligence program. The dataset covers rainfall records from **2001 to 2025**.

---

## 📄 License

This project is for academic purposes. Please cite appropriately if you use this work.
