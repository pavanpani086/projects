# Saved results

These files were extracted directly from the outputs stored in the supplied executed notebook. Packaging did not retrain a model or substitute a validation run.

| File | Contents |
|---|---|
| `default_test_comparison.csv` | Four-model default-risk test comparison, including the majority baseline |
| `default_training_cv_comparison.csv` | Training-only five-fold classifier comparison |
| `default_classification_reports.txt` | Saved per-class reports for Logistic Regression, Random Forest and KNN |
| `credit_score_test_metrics.csv` | Decision Tree and mean-baseline regression results |
| `approval_demo_test_metrics.csv` | Small-sample MLP approval results |
| `training_loan_intent_analysis.csv` | Training-set intent groups, default rates and loan amounts |
| `random_forest_top12_feature_importance.csv` | The top 12 encoded features displayed in the notebook |
| `recorded_metrics.json` | Saved tables, split metadata, environment notes and source-notebook hash |

Six PNG files preserve the notebook's figures: loan-to-income analysis, loan-intent analysis, default confusion matrices, default ROC curves, debt/credit-score analysis, and the approval confusion matrix.

CSV/JSON summaries retain the precision shown in the saved tables. Re-running the notebook writes full-precision exports, full feature importance and row-level predictions into `course_credit_outputs/`. Those generated files and the model bundle are excluded by the project's `.gitignore`.
