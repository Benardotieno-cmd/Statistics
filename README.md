# Statistics: FinAccess 2024 Household Financial Access (Kenya)

A comprehensive statistics analyzing the FinAccess 2024 dataset — a household-level survey on financial access and inclusion in Kenya. The notebook works through descriptive statistics, distributions, correlation, and hypothesis testing, answering a structured set of questions (Q1–Q28) with accompanying code, plots, and written interpretation.

## Project Overview

This is an applied statistics exercise rather than a predictive modeling project. Each section poses conceptual and analytical questions about the dataset, then answers them with the relevant statistical method, visualization, and a written interpretation grounded in a financial-inclusion policy context (e.g., what a finding implies for designing financial products or understanding access gaps).

## Dataset

- **File:** `finaccess2024_datasprint.xlsx`
- **Key variables used throughout the analysis:**
  - `monthly_income` — household monthly income (right-skewed, contains outliers)
  - `household_size`
  - `fl_score` — financial literacy score (categorical)
  - `prodsum1` — count of financial products used by a household
  - `education_level`, `location_type` (urban/rural), `Age`, `Sex`
  - `Savings_formal`, `mobile_money_access`, `formal_service_use`, `financial_status`, `experienced_shock`

## Structure

The notebook is organized into 9 sections, each built around specific guided questions:

1. **Section 1 — Central Tendency:** Mean, median, and mode for `monthly_income`, `household_size`, and `fl_score`; comparing income across `location_type`.
2. **Section 2 — Measures of Dispersion:** Range, IQR, standard deviation; comparing variability in income and financial product usage across groups.
3. **Section 3 — Outliers:** IQR-based outlier detection for `monthly_income` and `household_size`, and how to handle them.
4. **Section 4 — Data Distributions:** Skewness of income, log transformation, Poisson vs. negative binomial fit for `prodsum1`, normality checks (histogram, Q-Q plot) for `household_size`.
5. **Section 5 — Correlation:** Income vs. product uptake (Pearson), a Spearman correlation matrix/heatmap, chi-square test of independence and Cramér's V for categorical associations (education, location, savings), and the correlation-vs-causation distinction.
6. **Section 6 — Hypothesis Testing Framework:** Setting up hypotheses (mobile money access by location), interpreting p-values and significance levels, Type I/Type II errors.
7. **Section 7 — Parametric Tests:** One-sample Wilcoxon test against a national income benchmark, Mann-Whitney U test (income by sex), Kruskal-Wallis/Welch's ANOVA with Games-Howell post-hoc (income by age group), one-proportion z-test (formal savings usage vs. 50%).
8. **Section 8 — Chi-Square Tests:** Test of independence (sex vs. savings behavior; mobile money access vs. location), chi-square goodness-of-fit (financial status categories vs. equal distribution).
9. **Section 9 — Non-Parametric Tests:** Mann-Whitney U (product usage: urban vs. rural; income: shock vs. no shock), Kruskal-Wallis (product usage across education levels).

## Requirements

```
numpy
pandas
scipy
matplotlib
seaborn
statsmodels
scikit-learn
plotly
pingouin
openpyxl
scikit-posthocs
```

Install dependencies with:

```bash
pip install numpy pandas scipy matplotlib seaborn statsmodels scikit-learn plotly pingouin openpyxl scikit-posthocs
```

## Usage

1. Place `finaccess2024_datasprint.xlsx` in your data directory and update the file path in the data-loading cell.
2. Open `Statistics.ipynb` in Jupyter Notebook or JupyterLab.
3. Run the cells in order — later sections (correlation, hypothesis tests) depend on cleaning steps done earlier (e.g., standardized `education_level` categories).

## Key Findings (as derived in the notebook)

- Household monthly income is strongly right-skewed (mean ≫ median), so the median is used as the "typical" value rather than the mean.
- The most common household size is 1.
- `prodsum1` (financial product count) shows overdispersion (variance > mean), suggesting a negative binomial fit is more appropriate than Poisson.
- Education level is significantly associated with formal savings usage, but location type is a likely confounder in that relationship.
- Median monthly income is significantly below a KES 50,000 benchmark (one-sample Wilcoxon test).
- Several categorical associations (education vs. location, mobile money access vs. location, sex vs. savings behavior) were tested via chi-square, with effect sizes reported using Cramér's V.

## Notes

- This notebook is written as an assignment response: markdown cells contain the interpretive answers to guided questions, alongside the code that produces the supporting statistics and plots.
- Some cells define hardcoded IQR values (e.g., `Q1 = 2500`, `Q3 = 10000`) earlier in the notebook before being recomputed from the data later on — worth reconciling if reused elsewhere.