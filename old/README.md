# A/B Test Analysis for E-Commerce Conversion Optimization

**Project Goal:**
Analyze an A/B test for an e-commerce website to determine whether a new landing page increases user conversions, and recommend whether to implement the new page, keep the old page, or extend the experiment.

**Dataset:**
- `ab_data.csv` - 294,478 rows: user IDs, timestamps, group assignment (control/treatment), landing page shown, and conversion outcome.
- `countries.csv` - user country (US / UK / CA), joined in for the regression section.

**Methodology:**
1. Data cleaning and validation: removed rows where `group` and `landing_page` were mismatched (3,893 rows) plus one duplicated user, leaving 290,584 unique users.
2. Exploratory analysis of conversion rates by group.
3. Hypothesis testing (H0: p_new - p_old <= 0) using a simulated sampling distribution (10,000 bootstrap draws) and the `statsmodels` proportions z-test.
4. Logistic regression on page type, then extended with country effects and page x country interaction terms.

**Key Findings:**
- Overall conversion rate: 11.96%
- Conversion rate (control / old page): 12.04%
- Conversion rate (treatment / new page): 11.88%
- Observed difference (new - old): -0.16 percentage points
- p-value: 0.905 (simulation), 0.905 (proportions z-test, z = -1.31), 0.190 (logistic regression on page type)
- Country (US/UK/CA) and page x country interaction terms were not statistically significant.

**Recommendation: Keep the old page.** At a 0.05 significance level we fail to reject the null hypothesis (p = 0.905): the data shows no evidence that the new page converts better, and the observed difference slightly favors the old page.

**Repo Contents:**
- `Analyze_ab_test_results_notebook.ipynb` - full analysis (Jupyter Notebook)
- `Analyze_ab_test_results_notebook.html` - exported report
- `ab_data.csv`, `countries.csv` - datasets
- Four screenshots of key code and outputs

**Skills & Tools:**
- Python (pandas, NumPy, statsmodels)
- A/B testing & hypothesis testing (sampling distributions, z-tests)
- Logistic regression
- Jupyter Notebook & data visualization
