# Course 5: The Nuts and Bolts of Machine Learning

**Google Advanced Data Analytics Professional Certificate — Course 5 of 6**

## What this course was about

This course moves from a single logistic regression model (Course 4) into tree-based machine learning — building and comparing a random forest and an XGBoost classifier to predict Waze user churn, with a stronger emphasis on rigorous model selection and evaluation.

## Project: Machine Learning Model Comparison (Waze)

**Scenario:** Waze leadership wants a machine learning model to predict user churn, to support proactive retention efforts. The team decides to build and compare two tree-based models — random forest and XGBoost — and recommend a champion.

**What the project covers:**

**Ethical framing before modeling:**
- Weighing the consequences of false negatives (a user churns despite being predicted as "retained" — a missed retention opportunity) against false positives (a user is unnecessarily sent a retention offer — a low-cost error)
- Concluding the benefits outweigh the risks, provided the model is used as decision support rather than the sole basis for action, with limitations clearly documented

**Feature engineering** — built on top of features from Courses 1–4, plus several new ones:
- `km_per_driving_day`, `km_per_drive`, `km_per_hour`
- `percent_sessions_in_last_month`, `percent_of_sessions_to_favorite`
- `total_sessions_per_day`
- `professional_driver` (60+ drives and 15+ driving days in a month)
- Handled divide-by-zero edge cases (infinite values → 0) across engineered ratio features

**Data preparation:**
- Dropped rows with missing `label` values (consistent with earlier courses, no evidence of non-random missingness)
- No outlier imputation needed — tree-based models are robust to outliers, unlike the regression approach in Course 4
- Encoded `device2` (binary) and `label2` (binary churn target)
- Chose **recall** as the primary evaluation metric, since false positives carry minimal cost for this business use case, while false negatives (missed churners) are more costly

**Modeling workflow:**
- Split data 60/20/20 into train/validation/test sets, stratified on the churn label to preserve class balance across splits
- Tuned a **random forest** via `GridSearchCV`, optimizing for recall
- Tuned an **XGBoost** classifier via `GridSearchCV`, optimizing for recall
- Compared both models on validation data to select a champion, then evaluated the champion on the held-out test set

**Results:**
- XGBoost outperformed both the random forest and the Course 4 logistic regression model, roughly doubling the recall achieved by logistic regression while maintaining similar accuracy and precision
- On the test set, the champion XGBoost model correctly identified only **~16.6% of users who actually churned** — a meaningful improvement over prior models, but still low in absolute terms
- Feature importance analysis showed XGBoost distributed importance across many more features than the logistic regression model (which leaned heavily on `activity_days` alone) — engineered features made up 6 of the top 10 most important features, underscoring the value of feature engineering
- **Recommendation:** not suitable as a sole churn-detection system given the recall limitation, but a meaningful improvement over prior approaches and useful as a decision-support signal alongside other retention strategies
- Suggested next steps: tune the classification threshold instead of using the default 0.50, apply class weighting or resampling (e.g., SMOTE) to address class imbalance, and gather richer longitudinal features (change in activity over time, time since last session, route cancellations) to improve predictive signal

`waze_ml_model_comparison.ipynb` contains the full analysis and code.

## Why this course matters for the rest of the repo

This is the most technically complete modeling course in the series — comparing multiple algorithms with a proper train/validation/test workflow. It sets up the capstone (Course 6) to consolidate the strongest findings across all prior courses into one final, stakeholder-facing deliverable.
