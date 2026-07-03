# Blog Engagement Prediction with Machine Learning

## Project Overview

This project predicts the future number of blog comments using historical blog engagement features.

Several regression models were developed and compared to identify the best-performing model based on validation performance.

---

## Objective

The objective of this project was to predict the target variable (`target`), representing the future number of blog comments, using the provided blog activity features.

---

## Dataset

The dataset contains numerical features describing blog activity, including previous comment activity, link information, and time-based engagement features.

Target variable:

- `target` – future number of blog comments

---

## Project Workflow

1. Data loading
2. Duplicate removal
3. Exploratory Data Analysis (EDA)
4. Missing value analysis and imputation
5. Correlation analysis
6. Feature validation
7. Removal of constant features
8. Train-validation split
9. Model development
10. Hyperparameter tuning
11. Model evaluation
12. Feature importance analysis
13. Prediction and residual analysis

---

## Data Preprocessing

The following preprocessing steps were performed:

- Removed duplicate records (excluding `blog_id`)
- Removed numerical features containing only one unique value
- Imputed missing values
- Validated the engineered feature `difference_total_24h_comment_page`
- Recalculated inconsistent values using the original variables
- Removed `blog_id` before model training

---

## Models Evaluated

The following regression models were evaluated on the validation dataset.

| Model | RMSE | MAE | R² |
|------|------:|------:|------:|
| Gradient Boosting Regressor | 26.79 | 6.73 | 0.528 |
| Tuned Gradient Boosting Regressor | 27.34 | 6.94 | 0.509 |
| Random Forest Regressor | 28.06 | 6.43 | 0.483 |
| Linear Regression | 31.68 | 9.39 | 0.341 |

Gradient Boosting Regressor achieved the lowest validation RMSE and was selected as the final model.

---

## Feature Validation

The engineered feature

`difference_total_24h_comment_page`

was validated by checking whether it satisfied the following relationship:

```
total_comment_before_basetime_page
−
24h_comment_before_basetime_page
```

Inconsistent values were identified and recalculated before model training.

---

## Feature Importance

According to the final Gradient Boosting model, the most important features included:

- `difference_24h_comment_between_basetime_blogpost_page`
- `24h_comment_before_basetime_page`
- `difference_total_24h_comment_page`

These features had the highest importance scores in the final model.

---

## Model Evaluation

Models were evaluated using:

- RMSE
- MAE
- R²

Gradient Boosting Regressor produced the best validation performance among the evaluated models.

Hyperparameter tuning using `RandomizedSearchCV` did not improve validation performance, so the default Gradient Boosting model was selected as the final model.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn

---

## Skills Demonstrated

- Exploratory Data Analysis (EDA)
- Data cleaning
- Duplicate removal
- Missing value handling
- Feature validation
- Correlation analysis
- Regression modeling
- Hyperparameter tuning
- Model evaluation
- Feature importance analysis
- Residual analysis
