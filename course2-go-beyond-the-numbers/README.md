# Course 2: Go Beyond the Numbers — Translate Data into Insights

**Google Advanced Data Analytics Professional Certificate — Course 2 of 6**

## What this course was about

This course picks up where Course 1 left off — the Waze churn dataset has already been inspected and cleaned, and now it's time to actually explore it: exploratory data analysis (EDA) and visualization. The goal is to go from "here's a clean dataframe" to "here's what the data is actually telling us," using plots to surface patterns that summary statistics alone don't make obvious.

## Project: Exploratory Data Analysis & Visualization (Waze)

**Scenario:** The team's Senior Data Analyst asks for help digging deeper into the Waze user data, since Waze's Director of Data Analysis wants to see a notebook showing the exploration and visualizations before moving forward.

**What the project covers:**
- Loading and further exploring the dataset — structure, summary stats, and checking for anything that needs cleaning before visualization
- Choosing the right chart type for each variable — box plots and histograms for numeric variables like `sessions`, `drives`, `driven_km_drives`, and `duration_minutes_drives`; pie charts for categorical variables like `device` and `label` (churn status)
- Spotting and interpreting skewed distributions — most usage variables are right-skewed, meaning a small number of very active "power users" pull the averages up
- Investigating outliers, including deriving `km_per_driving_day` and handling divide-by-zero edge cases (users with 0 driving days) and capping unrealistic values (e.g., driving distances that would be physically impossible in a day)
- Comparing churn rate across device type, driving distance, and driving frequency to look for patterns
- Cross-checking two related variables — `activity_days` (days the app was opened) vs. `driving_days` (days the user actually drove) — to catch inconsistencies or better understand user behavior
- Writing an executive summary translating the visual findings into insights the Director of Data Analysis (a non-technical stakeholder) can act on

`waze_eda_visualizations.ipynb` contains the full analysis and code.

## Why this course matters for the rest of the repo

This is where the churn question first starts getting concrete answers — it builds directly on Course 1's initial data check and sets up the variables and patterns that Courses 3–6 test more rigorously with statistics, regression, and machine learning.
