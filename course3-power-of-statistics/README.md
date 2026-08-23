# Course 3: The Power of Statistics

**Google Advanced Data Analytics Professional Certificate — Course 3 of 6**

## What this course was about

This course moves from visual exploration (Course 2) into formal statistical inference. Instead of just observing that iPhone users *seem* to have more drives on average than Android users, the goal here is to test whether that difference is statistically meaningful or could just be due to random sampling.

## Project: Hypothesis Testing (Waze)

**Scenario:** Waze leadership wants to know whether device type (iPhone vs. Android) has a real relationship with how much users drive. The specific ask: run a two-sample hypothesis test comparing the mean number of drives between the two groups.

**What the project covers:**
- Recoding the categorical `device` column into a numeric `device_type` column using a mapping dictionary, to prep it for analysis
- Computing descriptive statistics (group means) to get an initial read on the data before formal testing
- Formulating the null and alternative hypotheses:
  - **H₀:** No statistically significant difference in mean drives between iPhone and Android users
  - **Hₐ:** A statistically significant difference exists
- Running a two-sample t-test (Welch's t-test, `equal_var=False`) using `scipy.stats.ttest_ind()` at a 5% significance level
- Interpreting the p-value to decide whether to reject or fail to reject the null hypothesis
- Translating the statistical result into a business insight for stakeholders — i.e., explaining *what it means* that device type has no meaningful effect on driving frequency, not just reporting a p-value

**Result:** Failed to reject the null hypothesis — there's no statistically significant difference in average drives between iPhone and Android users. In other words, device type isn't a meaningful factor in how often people drive, which tells the Waze team that any churn or engagement differences seen elsewhere in the data likely aren't driven by platform choice.

`waze_hypothesis_testing.ipynb` contains the full analysis and code.

## Why this course matters for the rest of the repo

This is the first course where a claim gets tested rigorously rather than just observed — establishing that device type isn't a meaningful variable here helps narrow down what *is* worth modeling in Courses 4–6 (regression and machine learning), where the focus shifts to behavioral variables like driving distance and frequency instead.
