# AI Impact on Jobs 2030 — Statistical Analysis in R

A semester-long data analytics project examining salary, automation risk, and AI exposure across 100 job roles, using descriptive statistics, correlation analysis, hypothesis testing, and simple linear regression in R.

**Course:** STAT 206 – Introduction to Data Analytics | Forman Christian College (A Chartered University), Spring 2026
**Instructor:** Dr. Shakila Bashir

## Overview

This project explores a real-world dataset on how artificial intelligence is projected to affect different job roles by 2030 — specifically looking at salary levels, years of experience, education, AI exposure, and automation risk. The goal was to apply a full introductory statistics pipeline end-to-end: explore the data, describe it, test relationships formally, and build a predictive model — then honestly report what the data does (and doesn't) support.

**Objectives:**
- Explore the distribution of salary, AI exposure, and automation risk
- Compare salaries across experience and education groups
- Test correlations between numeric variables
- Build a simple linear regression model to predict salary from experience

## Dataset

Source: [AI Impact on Jobs 2030](https://www.kaggle.com/datasets/khushikyad001/ai-impact-on-jobs-2030) by Yadav, K. (2024), via Kaggle.

The full dataset contains 3,000 observations and 18 variables. This project uses the first 100 observations and 7 selected variables: `Job_Title`, `Average_Salary`, `Years_Experience`, `Education_Level`, `AI_Exposure_Index`, `Automation_Probability_2030`, `Risk_Category`.

The raw CSV isn't included in this repo (it belongs to the original Kaggle uploader) — download it from the link above and place it in the same directory as the `.Rmd` to reproduce the analysis.

To reproduce the exact scope used in this analysis after downloading the raw dataset, slice the first 100 rows in R:

```r
raw_data <- read.csv("AI_Impact_on_Jobs_2030.csv")
analysis_data <- head(raw_data, 100)
```

## Methodology

| Stage | Techniques used |
|---|---|
| Data handling | Type conversion, missing value checks, factor releveling (ordinal vs nominal) |
| Descriptive statistics | Mean, median, SD, variance, IQR, coefficient of variation, frequency tables |
| Visualization | Histogram, boxplot, scatter plots, bar chart, custom multi-group ggplot2 chart |
| Correlation | Pearson, Spearman, Kendall, with significance testing (`cor.test`) |
| Hypothesis testing | Welch two-sample t-test, one-way ANOVA (F-test), Chi-square test of independence |
| Regression | Simple linear regression with diagnostic plots and confidence-interval predictions |

## Key Findings

The honest headline finding of this project is a null result — and that's reported as-is rather than reframed:

- **No variable tested had a statistically significant relationship with salary.** Correlations between salary and experience, AI exposure, and automation probability were all weak (|r| < 0.11, p > 0.05).
- **t-test, ANOVA, and Chi-square tests all failed to reject their null hypotheses** — salary didn't differ significantly by experience group or education level, and education level was independent of automation risk category.
- **The regression model (Salary ~ Years of Experience) had an R² of 0.0114** — experience explains about 1% of salary variation, meaning the model has essentially no predictive power on its own.
- Automation risk category did track logically with AI Exposure Index and Automation Probability, as expected, confirming the risk labels in the dataset are internally consistent even if they don't relate cleanly to salary.

**Practical takeaway:** in this dataset, salary appears to be driven by factors outside experience/education/AI-exposure alone — likely job-specific or industry-specific factors not captured here. That's a real, useful conclusion, not a shortcoming of the analysis.

![AI Exposure vs Automation Probability by Risk Category](images/ai_exposure_vs_automation_by_risk.png)

*Custom multi-group visualization: Risk Category tracks logically with both AI Exposure Index and Automation Probability, even though neither relates significantly to salary.*

## Repository Structure

```
├── ai_jobs_2030_analysis.Rmd   # Full R Markdown source (code + narrative)
├── ai_jobs_2030_analysis.pdf   # Knitted PDF report
├── images/
│   └── ai_exposure_vs_automation_by_risk.png   # Key chart, embedded in README
├── docs/
│   └── presentation.pdf        # Class presentation slides (exported from PowerPoint)
└── README.md
```

## Tools

R, ggplot2, base R statistical functions (`t.test`, `aov`, `chisq.test`, `lm`, `cor.test`), knitr/pdflatex for report generation.

## Limitations

- Cross-sectional snapshot; no time-series data to observe actual change toward 2030
- Automation probabilities are dataset-provided estimates, not observed outcomes
- Key variables likely driving salary (industry, specific role seniority, location) aren't in the selected feature set
- Only the first 100 of 3,000 available rows were used, per assignment scope

## Author

**Muhammad Haseeb Ul Hassan**
BSCS, Data Analytics & Mathematics Minors — Forman Christian College (A Chartered University)
[LinkedIn](https://www.linkedin.com/in/muhammad-haseeb-ul-hassan) · [GitHub](https://github.com/m-haseeb-ul-hassan)
