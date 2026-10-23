# Customer Churn Prediction using Ensemble Learning

## Overview

A course-guided machine learning project that predicts whether a telecom customer will churn using customer demographics, account details and subscribed services.

The project explores classification models relevant to customer-retention analysis.

## Dataset

- Dataset: Telco Customer Churn
- Original records: 7,043
- Records after cleaning: 7,032
- Target: `Churn` — Yes or No
- Dataset file: `WA_Fn-UseC_-Telco-Customer-Churn.csv`

## Workflow

1. Explore the dataset and inspect missing values.
2. Convert `TotalCharges` to numeric and remove rows with missing values.
3. Remove the customer identifier and encode categorical features.
4. Split the data into 75% training and 25% testing.
5. Standardize features using the training data.
6. Train classification models and evaluate their predictions.

## Models and Recorded Results

| Model | Test accuracy |
|---|---:|
| K-Nearest Neighbors | 76.68% |
| Decision Tree | 72.98% |
| Random Forest | 79.24% |
| Bernoulli Naive Bayes | 72.87% |
| Support Vector Classifier | 80.03% |
| Logistic Regression | 80.32% |
| AdaBoost | 79.86% |
| Gradient Boosting | 80.38% |
| XGBoost | 80.60% |

**Evaluation note:** The notebook creates a separate random train/test split for XGBoost. Its score is therefore not directly comparable with the other models under an identical split. No fixed random seed is specified, so scores can vary when rerun.

## Repository Files

- `customer_churn.ipynb` — notebook containing preprocessing, training and saved outputs.
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` — dataset.
- `README.md` — project documentation.

## How to Run

1. Download the notebook and CSV from this folder.
2. Open `customer_churn.ipynb` in Google Colab.
3. Upload the CSV through Colab’s Files panel.
4. Ensure the dataset-loading cell points to `/content/WA_Fn-UseC_-Telco-Customer-Churn.csv`.
5. Run the cells sequentially.

Required libraries: NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn and XGBoost.

## Limitations

- Accuracy alone does not fully describe performance on customers who churn; precision, recall and F1 should also be considered.
- The notebook demonstrates model development and evaluation; it does not measure the effect of an actual retention campaign.

## Credits

Course-guided implementation based on the ensemble-learning material provided in Dr. Satyajit Pattnaik’s Data Science & AI Masters course on Udemy. Credit for the original instructional code belongs to the instructor.
