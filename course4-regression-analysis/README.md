# Course 4: Regression Analysis — Simplify Complex Data Relationships

**Google Advanced Data Analytics Professional Certificate — Course 4 of 6**

## What this course was about

This course moves from statistical testing (Course 3) into predictive modeling. The goal shifts from "is there a relationship?" to "can we predict who will churn?" — using a binomial logistic regression model built from the behavioral features explored in earlier courses.

## Project: Logistic Regression Model (Waze)

**Scenario:** Waze leadership wants a churn prediction model. The team's supervisor confirms they'll build a binomial logistic regression model and asks for help building it and preparing an executive summary of the results.

**What the project covers:**
- EDA and outlier checks specific to modeling — reviewing shape, missing values, and quartile ranges to flag variables likely to contain outliers (`sessions`, `drives`, `total_sessions`, `total_navigations_fav1`, `total_navigations_fav2`, `driven_km_drives`, `duration_minutes_drives`)
- Feature engineering: creating `km_per_driving_day` (with divide-by-zero handling) and a binary `professional_driver` flag (60+ drives and 15+ driving days in the month) — professional drivers showed a notably lower churn rate (~7.6%) than non-professionals (~19.9%)
- Dropping rows with missing `label` values (under 5% of the data, no evidence of non-random missingness)
- Imputing outliers by capping values at the 95th percentile rather than removing them
- Encoding categorical variables: `label2` (binary churn target) and `device2` (binary device type)
- Checking logistic regression assumptions — independence, outlier handling, and **multicollinearity** (found between `sessions`/`drives` and `driving_days`/`activity_days`, so one variable from each pair was dropped before modeling)
- Verifying the linearity-of-logit assumption with a regplot of log-odds vs. `activity_days`
- Splitting data with `train_test_split`, using `stratify=y` to preserve the churned/retained class imbalance (82%/18%) across train and test sets
- Fitting the logistic regression model (`penalty=None`, since predictors were left unscaled) and extracting coefficients
- Evaluating the model with accuracy, a confusion matrix, precision, recall, and a full classification report
- Visualizing feature importance via model coefficients

**Key findings:**
- `activity_days` was the strongest predictor — more days engaging with the app was associated with a lower likelihood of churning
- `km_per_driving_day`, despite looking meaningful in earlier EDA, turned out to be a weaker predictor once other variables were controlled for in the model — a good illustration of the difference between a single-variable relationship and a variable's contribution within a multivariate model
- The model reached decent overall accuracy (~82%) but **low recall on churn**, meaning it missed most of the users who actually churned — a serious limitation if the business goal is proactively catching at-risk users
- **Recommendation:** not suitable as the primary churn-detection tool given the recall issue, but useful as a baseline and for surfacing which behaviors correlate with retention
- Suggested next steps: tune the classification threshold to prioritize recall, scale features before applying regularization, and compare against more flexible models like random forest or gradient boosting; richer behavioral data (routes, notification engagement, longer observation windows) would likely improve results further

`waze_regression_model.ipynb` contains the full analysis and code.

## Why this course matters for the rest of the repo

This is the first course to produce an actual predictive model rather than description or inference alone — and its honest limitation (low recall) sets up Course 5's shift to more flexible machine learning approaches (e.g., tree-based models) that can better handle the churn class imbalance.
