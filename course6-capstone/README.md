# Course 6: Capstone — Providing Data-Driven Suggestions for HR

**Google Advanced Data Analytics Professional Certificate — Course 6 of 6 (Capstone)**

## What this course was about

This is the final, consolidating project in the certificate — a full end-to-end analysis for a fictional HR department (Salifort Motors), rather than a continuation of the Waze case study used in Courses 1–5. It pulls together everything from the program: EDA, statistics, feature engineering, and machine learning, applied to a new business problem from scratch.

## Project: Predicting Employee Turnover (Salifort Motors)

**Scenario:** Salifort Motors' HR department wants to understand what's driving employees to leave and asked for data-driven suggestions to improve retention. The goal: analyze the HR dataset (15,000 employees, 10 variables — satisfaction, evaluation scores, project count, hours worked, tenure, salary, department, etc.) and build a model to predict whether an employee is likely to leave.

**What the project covers:**

**Data cleaning:**
- Renamed columns to consistent `snake_case` and fixed naming issues (e.g., `Work_accident` → `work_accident`, `time_spend_company` → `tenure`)
- Checked for missing values (none found) and duplicates (~3,000 duplicate rows identified and removed)
- Checked `tenure` for outliers using the IQR method, and made a deliberate choice to **retain** legitimate outliers rather than remove them, since the modeling approach (tree-based) is robust to them and unusual tenure/workload values may carry genuine predictive signal

**Exploratory data analysis:**
- Examined the overall turnover rate and its distribution across the dataset
- Visualized relationships between turnover and satisfaction level, monthly hours, project count, tenure, and salary
- Identified two distinct at-risk employee profiles: those with **low workload and low satisfaction**, and those with **very high workload/project counts and long hours** — suggesting both under-engagement and burnout as separate churn drivers
- Found that employees with roughly 3–5 years of tenure were disproportionately represented among leavers, and that lower salary levels correlated with higher turnover

**Modeling:**
- Framed as a binary classification problem (`left`: 0 or 1)
- One-hot encoded categorical variables (`department`, `salary`)
- Split data with `train_test_split`, stratified on the target to preserve class balance
- Built a **Random Forest classifier** to predict employee turnover
- Evaluated using accuracy, precision, recall, F1-score, ROC-AUC, and a confusion matrix

**Key findings:**
- Employee turnover could be meaningfully predicted from the available HR variables, with **satisfaction level, tenure, number of projects, average monthly hours, and last evaluation score** emerging as the strongest predictors
- The relationship between workload and turnover was non-linear — both low engagement and overwork were associated with higher churn risk, rather than turnover simply increasing with hours worked
- **Recommendations:** regularly monitor satisfaction and workload, review whether high performers are being overloaded, revisit compensation and promotion pathways (especially for employees around the 3–5 year tenure mark), and use the model as a decision-support signal — not as an automated basis for action against individual employees
- **Ethical considerations:** predictions should never be used punitively or to automate termination decisions; correlation in the data (e.g., long hours) shouldn't be read as proven causation; and the dataset likely omits real drivers of turnover (manager quality, engagement, compensation history), so findings should be treated as directional rather than complete

`salifort_turnover_capstone.ipynb` contains the full analysis and code.

## A note on this write-up

A few numeric results in the notebook (final accuracy, precision, recall, F1, and ROC-AUC scores) were left as placeholders rather than filled in with actual computed values, and the "Model assumptions" and "Do the assumptions hold" reflection questions in the Construct stage weren't answered. Before publishing this as your flagship portfolio piece, it's worth filling those in with your real model output — a capstone with placeholder metrics undercuts the piece precisely where a reviewer is most likely to look first.

## Why this course matters for the rest of the repo

This is the portfolio's headline project — it demonstrates the full analytics workflow independently, on a new dataset and business problem, rather than continuing the guided Waze case study. It's the strongest single piece to point to when discussing this certificate in an interview.
