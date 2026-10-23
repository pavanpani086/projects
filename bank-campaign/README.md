# Bank Campaign Response Analysis using Extra Trees

## Overview

A course-guided machine learning project that classifies whether a customer subscribed to a term deposit using client attributes and recorded marketing-call information.

## Dataset

- Records: 11,162
- Target: `deposit` — Yes or No
- Subscribed: 5,289 customers
- Did not subscribe: 5,873 customers
- Dataset file: `bank_campaign_for_deposit.xls`

Although the filename ends in `.xls`, the supplied file contains CSV-formatted text and is read using `pd.read_csv()`.

## Workflow

1. Inspect the dataset and categorical attributes.
2. Encode categorical variables using OrdinalEncoder.
3. Create a stratified 80% training and 20% testing split.
4. Evaluate the classifier using five-fold stratified cross-validation on the training data.
5. Train the final classifier and evaluate it on the held-out test set.

## Model Configuration

- Algorithm: Extra Trees Classifier
- Number of trees: 150
- Maximum features per split: Square root of the feature count
- Maximum leaf nodes per tree: 2
- Random state: 42

## Results

| Metric | Result |
|---|---:|
| Test accuracy | 69.01% |
| Mean five-fold cross-validation accuracy | 69.12% |
| Subscription-class precision | 88% |
| Subscription-class recall | 40% |
| Subscription-class F1-score | 0.55 |

The classifier identifies subscribers with relatively high precision but misses many actual subscribers, as reflected in its lower recall.

## Repository Files

- `bank_campaign.ipynb` — notebook containing analysis, model training and saved outputs.
- `bank_campaign_for_deposit.xls` — CSV-formatted dataset.
- `README.md` — project documentation.

## How to Run

1. Download the notebook and dataset.
2. Open `bank_campaign.ipynb` in Google Colab.
3. Upload `bank_campaign_for_deposit.xls` through Colab’s Files panel.
4. Keep the dataset-loading line as `pd.read_csv('bank_campaign_for_deposit.xls')`.
5. Run the notebook cells sequentially.

Required libraries: NumPy, Pandas, Matplotlib, Seaborn and Scikit-learn.

## Limitations

- Call duration is available only after the call. The model therefore supports analysis of recorded campaign outcomes rather than direct pre-call targeting.
- Each tree is restricted to two leaf nodes, limiting model complexity.
- Subscription-class recall is 40%, so accuracy alone does not fully describe the model’s performance.

## Credits

Course-guided implementation based on the Bank Campaign Success Analysis using Extra Trees project in EduMentor Deepti’s Machine Learning Bootcamp course on Udemy. Credit for the original instructional code belongs to the instructor.
