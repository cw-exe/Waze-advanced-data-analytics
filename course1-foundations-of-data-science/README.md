# Course 1: Foundations of Data Science

**Google Advanced Data Analytics Professional Certificate — Course 1 of 6**

## What this course was about

This course lays the groundwork before the certificate gets deeper into statistics and modeling. It covers what data professionals actually do day-to-day, how different roles overlap (data analyst vs. data scientist), the tools people typically use, and — most importantly — the **PACE framework**, which structures every project from here through the capstone:

- **Plan** — figure out what problem you're actually solving
- **Analyze** — dig into the data and understand what you're working with
- **Construct** — build the model, analysis, or output
- **Execute** — share what you found in a way stakeholders can actually use

Alongside the conceptual material, this course also includes a hands-on end-of-course project — a first look at the Waze dataset that later courses build on.

## Project: Inspect and Analyze Data (Waze)

**Scenario:** Waze's data analytics team is in the early stages of a user churn investigation. Before any exploratory analysis or modeling can happen, the raw user data needs to be inspected and prepared.

**What I did:**
- Loaded the dataset into a pandas dataframe and reviewed its structure (14,999 rows, 13 columns)
- Identified missing values — 700 nulls, all located in the `label` (churn) column
- Compared summary statistics between rows with and without missing values to check for a pattern in the missingness (found none — the missing data appeared random and proportionally consistent with device split)
- Compared churned vs. retained users across key behaviors: number of drives, driving days, distance driven, and km per driving day
- Checked for churn imbalance across iPhone vs. Android users (found none — churn was consistent across both platforms)
- Wrote an executive summary of findings for the (simulated) data team

**Key finding:** Churned users tended to drive significantly farther per driving day than retained users, despite using the app on fewer distinct days — a pattern that hints the dataset may be skewed toward heavy/long-haul drivers rather than typical commuters, which could itself be worth flagging to the team before drawing broader conclusions.

`waze_data_inspection.ipynb` contains the full analysis and code.

## Why this course matters for the rest of the repo

The PACE framework introduced here, and this first look at the Waze dataset, set up everything that follows — Courses 2 through 6 continue working with the same dataset, applying progressively more advanced techniques (EDA, statistics, regression, machine learning) to the same churn question first explored here.
