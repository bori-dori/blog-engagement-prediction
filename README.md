# Blog Engagement Prediction with Machine Learning

## Project Overview

This project predicts the future number of blog comments using historical blog activity features.

Several regression models were developed and compared to identify the model that achieved the best validation performance. The project covers the complete machine learning workflow, including data preprocessing, feature validation, model development, evaluation, and interpretation.

---

## Business Objective

The objective of this project was to predict the future number of blog comments using the provided blog activity features.

Accurately forecasting future engagement can support data-driven decision making for content platforms by providing early estimates of potential user engagement.

---

## Potential Business Applications

Although this project focuses on offline model development, a blog engagement prediction model could potentially be used to:

- Estimate future engagement before content promotion
- Support editorial decisions using engagement predictions
- Help prioritize content for additional promotion
- Assist with planning content distribution strategies

These examples illustrate how engagement prediction models may be applied in real-world business settings.

---

## Dataset

The dataset contains numerical features describing blog activity, including:

- Previous comment activity
- Link information
- Time-based engagement features

**Target Variable**

- **target** – Future number of blog comments

---

## Project Workflow

- Data loading
- Duplicate removal
- Exploratory Data Analysis (EDA)
- Missing value analysis and imputation
- Correlation analysis
- Feature validation
- Removal of constant features
- Train-validation split
- Model development
- Hyperparameter tuning
- Model evaluation
- Feature importance analysis
- Prediction analysis
- Residual analysis

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
|-------|------:|------:|------:|
| Gradient Boosting Regressor | **26.79** | 6.73 | **0.528** |
| Tuned Gradient Boosting Regressor | 27.34 | 6.94 | 0.509 |
| Random Forest Regressor | 28.06 | **6.43** | 0.483 |
| Linear Regression | 31.68 | 9.39 | 0.341 |

The default **Gradient Boosting Regressor** achieved the lowest validation RMSE and the highest R² among the evaluated models and was selected as the final model.

Hyperparameter tuning using RandomizedSearchCV did not improve validation performance, so the default Gradient Boosting model was retained.

---

## Feature Validation

The engineered feature

`difference_total_24h_comment_page`

was validated by verifying that it satisfied the following relationship:

```
total_comment_before_basetime_page
-
24h_comment_before_basetime_page
```

Inconsistent observations were identified and recalculated before model training.

---

## Feature Importance

According to the final Gradient Boosting model, the most important features included:

- `difference_24h_comment_between_basetime_blogpost_page`
- `24h_comment_before_basetime_page`
- `difference_total_24h_comment_page`

These variables contributed most to predicting future blog engagement.

---

## Model Evaluation

Models were evaluated using multiple regression metrics:

- RMSE
- MAE
- R²

RMSE was used as the primary metric for model comparison, while MAE and R² provided additional perspectives on prediction performance.

---

## Key Findings

- Gradient Boosting achieved the best overall validation performance.
- Hyperparameter tuning did not improve model performance on the validation dataset.
- Previous engagement-related features contributed most to predicting future comments.
- Careful data validation and preprocessing improved overall data quality before modeling.

---

## Limitations

This project has several limitations.

- The model was trained using a single historical dataset.
- Textual blog content was not included.
- External factors such as social media activity or marketing campaigns were unavailable.
- The project focused on offline model development and did not include deployment or production monitoring.

Possible future improvements include:

- Evaluating XGBoost or LightGBM
- Incorporating NLP-based text features
- Using temporal validation
- Deploying the model in a production environment
- Monitoring model performance over time

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
- Data Cleaning
- Duplicate Removal
- Missing Value Handling
- Feature Validation
- Correlation Analysis
- Regression Modeling
- Hyperparameter Tuning
- Model Evaluation
- Feature Importance Analysis
- Residual Analysis
- Business Interpretation of Machine Learning Results
