# Data and methods

## Main task: default prediction

- Source file restored by the notebook: `credit_risk_dataset.csv`.
- Raw data: 32,581 rows. After removing 165 exact duplicates: 32,416 rows.
- Target: `loan_status`, with 1 = default and 0 = non-default.
- Split: stratified 80:20 with random state 42, before fitting preprocessing.
- Training/test sizes: 25,932 / 6,484; the test set contains 1,418 defaults and 5,066 non-defaults.

### Course predictors retained in the classifiers

| Field | Type |
|---|---|
| `person_age` | Numeric |
| `person_income` | Numeric |
| `person_emp_length` | Numeric |
| `loan_int_rate` | Numeric |
| `person_home_ownership` | Categorical |
| `loan_intent` | Categorical |
| `cb_person_default_on_file` | Categorical |

Loan amount is used in exploratory analysis but is excluded from the final seven predictors, matching the supplied modelling scripts. `loan_percent_income` is described as a loan-to-income ratio; it is not a full debt-service ratio.

### Preprocessing and validation

- Numeric pipeline: median imputation, then StandardScaler.
- Categorical pipeline: most-frequent imputation, then fitted one-hot encoding; unseen categories are handled without rebuilding columns.
- Preprocessing is fitted separately inside every cross-validation fold and on the final training partition.
- Five-fold StratifiedKFold uses shuffle=True and random state 42. The same folds are used for all three default classifiers.
- Logistic Regression: max_iter=1000; Random Forest: 100 trees; KNN: five neighbours.
- The preferred model is selected using mean training-CV ROC-AUC. No grid search or test-set threshold tuning is performed.
- Classification threshold remains 0.5. Test accuracy, default precision/recall/F1, ROC-AUC, average precision and Brier score are recorded.
- Random Forest impurity importance is a model diagnostic, not a causal explanation.
- Applicant inputs pass through the saved fitted preprocessing/model pipeline.

The exploratory section examines loan-to-income/default patterns and loan-intent/default-rate relationships on training data. The notebook also records unusual ages and employment lengths retained from the educational dataset.

## Numerical credit-score demonstration

- Source: `credit_score.csv`; 1,000 rows, split into 800 training / 200 test rows.
- Predictors: `INCOME`, `SAVINGS`, `DEBT`, `CAT_CREDIT_CARD`, `DEFAULT`.
- Target: the supplied `CREDIT_SCORE` column.
- Method: median imputation and Decision Tree regression, compared with a mean-prediction baseline.
- Recorded Decision Tree metrics: MAE 35.3250, RMSE 48.5581, R² 0.4060.

The source does not establish the timing of the `DEFAULT` history field or calibrate this score to a bureau scale. This demonstration is separate from probability-of-default classification.

## Loan-approval demonstration

- Source: `loan.csv`, the 61-row Simple Loan Classification Dataset referenced by the course script.
- Numeric fields: age, income, credit_score.
- Categorical fields: gender, occupation, education_level, marital_status.
- Target: Approved = 1, Denied = 0.
- Stratified split: 48 training / 13 test rows.
- Pipeline: imputation, one-hot encoding, scaling, training-only SMOTE, MLP with hidden layers (50, 25), max_iter=500.
- Recorded accuracy: 84.62% (11/13 correct). Approved-class precision, recall and F1 are each 0.90.

SMOTE is applied only during fitting of this approval model. It is not used by the default classifiers. The dataset is very small, and interpolation after one-hot encoding can produce fractional categorical indicators; the notebook retains this course method and explains its limits.

## Saved files and reproducibility

The notebook restores the three bundled CSVs and checks SHA-256 hashes. It exports fitted pipelines, prediction CSVs, CV metrics, final metrics and plots to `course_credit_outputs/`. A reload check confirms that the saved model bundle reproduces the notebook's predictions.

The static `results/` directory in this repository is extracted from the supplied executed notebook rather than from a fresh training run. Its table values retain the displayed rounding. It contains no newly calculated or substituted model scores.

The recorded run reports Python 3.12, pandas 2.2.3, scikit-learn 1.6.1 and imbalanced-learn 0.14.2. The requirements file pins the three printed package versions. Other package versions, hardware and numerical-library differences can affect a later run; keep a later run's exported summary with its own artifacts.
