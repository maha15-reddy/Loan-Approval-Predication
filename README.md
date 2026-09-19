# 🏦 Loan Approval Prediction

A supervised machine learning project that predicts whether a bank loan application will be **Approved** or **Rejected**, based on an applicant's personal and financial information. The goal is to reduce manual verification effort, speed up the approval process, and minimize the risk of approving high-risk applicants.

<p align="left">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10%2B-blue">
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-ML-orange">
  <img alt="XGBoost" src="https://img.shields.io/badge/XGBoost-Boosting-green">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-lightgrey">
</p>

---

## 📌 Problem Statement

A bank wants to predict whether a loan application should be approved based on the applicant's personal and financial information. This helps reduce manual effort and speeds up the loan approval process.

- **Type:** Supervised Learning
- **Category:** Binary Classification
- **Target Variable:** `loan_status` → `Approved` (1) / `Rejected` (0)

## 🎯 Business Objectives

- Reduce manual verification of loan applications
- Minimize the risk of approving high-risk applicants
- Improve customer experience with faster decisions

## 📂 Dataset

The dataset (`data/loan_approval_dataset_classification.csv`) contains **4,269 loan applications** with the following features:

| Feature | Description |
|---|---|
| `loan_id` | Unique application identifier |
| `no_of_dependents` | Number of dependents the applicant has |
| `education` | Graduate / Not Graduate |
| `self_employed` | Whether the applicant is self-employed |
| `income_annum` | Annual income of the applicant |
| `loan_amount` | Loan amount requested |
| `loan_term` | Loan repayment term (years) |
| `cibil_score` | Credit score indicating creditworthiness |
| `residential_assets_value` | Value of residential assets |
| `commercial_assets_value` | Value of commercial assets |
| `luxury_assets_value` | Value of luxury assets |
| `bank_asset_value` | Bank balance / financial assets |
| `loan_status` | **Target** — Approved / Rejected |

## 🗂️ Project Structure

```
Loan-Approval-Prediction/
├── data/
│   └── loan_approval_dataset_classification.csv
├── notebooks/
│   └── Loan_Approval_Prediction.ipynb
├── reports/
│   ├── Loan_Approval_Project_Report.docx
│   └── Loan_Approval_Presentation.pptx
├── requirements.txt
├── .gitignore
└── README.md
```

## 🔍 Project Workflow

1. **Business Understanding** – Problem statement, target variable, business & ML objectives
2. **Data Understanding** – Shape, types, statistical summary
3. **Data Cleaning** – Duplicate/null checks, column renaming, type fixes
4. **Exploratory Data Analysis (EDA)** – Univariate, bivariate & multivariate analysis, correlation heatmap
5. **Feature Engineering** – Label encoding of categorical variables, feature scaling (`StandardScaler`)
6. **Data Splitting** – 80/20 train-test split
7. **Model Building** – 7 classification algorithms trained and compared
8. **Hyperparameter Tuning** – `GridSearchCV` and `RandomizedSearchCV` on Random Forest
9. **Model Evaluation** – ROC Curve & AUC score
10. **Feature Importance** – Random Forest and XGBoost importances
11. **Model Export** – Best model saved with `joblib`

## 🤖 Models Compared

| Model | Accuracy |
|---|---|
| **Random Forest** | **98.1%** |
| XGBoost | 97.8% |
| Decision Tree | 97.4% |
| AdaBoost | 97.0% |
| Logistic Regression | 90.6% |
| SVM | 62.8% |
| KNN | 57.4% |

After hyperparameter tuning (`GridSearchCV` / `RandomizedSearchCV`), the tuned Random Forest achieved an **AUC score of 0.998**, confirming excellent separability between approved and rejected applications.

### Top Predictive Features

`cibil_score` dominates both Random Forest and XGBoost feature-importance rankings (60–80% of importance), followed by `loan_term`, `loan_amount`, and `income_annum`.

## 💡 Key Business Insights

- Applicants with a **higher CIBIL score** are far more likely to have their loan approved — it is the single strongest predictor.
- Higher **annual income** qualifies applicants for larger loan amounts.
- Loan amount tends to increase with **asset values** (residential, commercial, luxury, bank balance).
- **Education** and **self-employment status** have minimal impact on approval outcomes.
- CIBIL score, loan term, and loan amount together drive the vast majority of the model's decisions.

## 🛠️ Tech Stack

- **Language:** Python 3
- **Data Handling:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** scikit-learn, XGBoost
- **Model Persistence:** Joblib

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/loan-approval-prediction.git
cd loan-approval-prediction
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook notebooks/Loan_Approval_Prediction.ipynb
```

The notebook reads the dataset using a relative path (`../data/loan_approval_dataset_classification.csv`), so it will run as-is once the repo is cloned.

## 📊 Reports & Presentation

- 📄 [Project Report](reports/Loan_Approval_Project_Report.docx) — full write-up of the CRISP-DM-style workflow, EDA insights, model comparison, and recommendations
- 📽️ [Presentation](reports/Loan_Approval_Presentation.pptx) — slide deck summarizing the project for a non-technical audience

## 🔮 Future Improvements

- Handle class imbalance explicitly (e.g., SMOTE) if approval/rejection ratio skews further
- Try additional models (LightGBM, CatBoost, stacked ensembles)
- Build a simple web app (Streamlit/Flask) to serve the saved model for live predictions
- Add SHAP-based explainability for individual predictions

## 📄 License

This project is licensed under the MIT License — feel free to use and adapt it.

## 🙋 Author

Built as a personal data science / ML portfolio project. Contributions and suggestions are welcome — feel free to open an issue or PR.
