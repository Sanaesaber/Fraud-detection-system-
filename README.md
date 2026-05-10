# 🔍 Fraud Detection System

> Intelligent card transaction fraud detection using XGBoost, SQL feature engineering, SHAP explainability, and Power BI monitoring.



![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)




![XGBoost](https://img.shields.io/badge/XGBoost-ML-orange)




![PostgreSQL](https://img.shields.io/badge/PostgreSQL-SQL-336791?logo=postgresql)




![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)




![SHAP](https://img.shields.io/badge/SHAP-Explainability-green)



---

## 📊 Project Results

| Metric | Result |
|---|---|
| Transactions Analyzed | 284,807 |
| Fraud Rate | 0.172% |
| Model Accuracy | 99.6% |
| Fraud Recall | 91.4% |
| F1-Score | 88.2% |
| ROC-AUC | **0.981** |

---

## 🧩 Business Context

A commercial bank processing millions of card transactions daily relied on a legacy rule-based fraud detection system that generated excessive false positives while still missing sophisticated fraud patterns. Global card fraud losses exceeded **$33 billion in 2023**. The goal was to build an intelligent scoring system to replace manual review, reduce fraud losses, and minimize friction for legitimate customers.

---

## ⚙️ Technical Challenges

- **Severe class imbalance**: only 492 of 284,807 transactions were fraudulent (0.172%)
- **Behavioral mimicry**: fraudsters deliberately imitate legitimate patterns — small amounts, similar timing
- **Concept drift**: fraud strategies evolve, requiring a model designed for scheduled retraining

---

## 🔬 Methodology

### 1. SQL-Based Profiling (PostgreSQL)
Extracted fraud KPIs by hour of day, amount distribution, and transaction patterns.

### 2. Feature Engineering
| Feature | Description |
|---|---|
| `log_amount` | Log-transformed amount to reduce skew |
| `hour_of_day` | Hour extracted from timestamp |
| `is_night` | Binary flag — confirmed 3.3× higher fraud rate at night |
| `amount_zscore` | Z-score for outlier detection |

### 3. Class Imbalance — SMOTE
Applied SMOTE exclusively on the training set to prevent data leakage.

### 4. Model Comparison
| Model | Accuracy | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|
| Logistic Regression | 97.8% | 62.3% | 68.1% | 0.921 |
| Random Forest | 99.4% | 83.7% | 84.9% | 0.967 |
| **XGBoost (Final)** | **99.6%** | **91.4%** | **88.2%** | **0.981** |

Optimized with GridSearchCV — 5-fold cross-validation.

### 5. SHAP Explainability
Per-transaction fraud signal explanation for operational use by risk teams.

### 6. Power BI Dashboard
Real-time operational monitoring dashboard for fraud risk teams.

---

## 💼 Business Impact

- **91.4% of fraudulent transactions** identified before financial loss occurs
- Fraud peaks between **1 AM – 4 AM** (2.5× daytime rate) — enables time-based risk thresholds
- 10% recall improvement on a $500M portfolio → estimated **$2.4M saved annually**

---

## 🗂️ Project Structure
fraud-detection-system/
├── data/
│   └── creditcard.csv
├── sql/
│   └── fraud_profiling.sql
├── notebooks/
│   ├── 01_EDA_and_SQL_Profiling.ipynb
│   ├── 02_Feature_Engineering.ipynb
│   ├── 03_Modeling_and_Evaluation.ipynb
│   └── 04_SHAP_Explainability.ipynb
├── dashboard/
│   └── fraud_monitoring.pbix
├── requirements.txt
└── README.md

---

## 🛠️ Tech Stack

| Tool | Usage |
|---|---|
| Python | Core language |
| PostgreSQL | SQL profiling and KPI extraction |
| XGBoost | Final classification model |
| Scikit-learn | Pipeline, GridSearchCV, SMOTE |
| SHAP | Model explainability |
| Power BI | Operational monitoring dashboard |
| Pandas / NumPy | Data manipulation |
| Matplotlib / Seaborn | Visualization |

---

## 🚀 Getting Started

```bash
git clone https://github.com/SanaeSaber/fraud-detection-system.git
cd fraud-detection-system
pip install -r requirements.txt
jupyter notebook

👤 Author
Sanae Saber — Data Analyst & Machine Learning Engineer
📧 sanaesaber03@gmail.com | 🔗 github.com/SanaeSaber
