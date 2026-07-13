# Heart Failure Prediction — EDA Insights Report

Exploratory data analysis of the Heart Failure Prediction dataset (918 patient records, 12 clinical features), summarized into a stakeholder-ready PDF report.

## Contents

| File | Description |
|---|---|
| `HeartFailure_EDA_Insights_Report.pdf` | Final deliverable — 5-page insights report with charts, key findings, data quality notes, and recommendations |
| `Heart_Failure_Prediction.ipynb` | Source Jupyter notebook containing the original EDA (univariate, bivariate, multivariate analysis, preprocessing) |

## Dataset

- **Source:** `heart.csv` (UCI / Kaggle Heart Failure Prediction dataset)
- **Size:** 918 rows × 12 columns
- **Target variable:** `HeartDisease` (1 = disease present, 0 = absent)
- **Features:** Age, Sex, ChestPainType, RestingBP, Cholesterol, FastingBS, RestingECG, MaxHR, ExerciseAngina, Oldpeak, ST_Slope

## What the analysis covers

1. **Data overview** — shape, dtypes, summary statistics
2. **Univariate analysis** — distributions of Age, Sex, Chest Pain Type
3. **Bivariate / multivariate analysis** — Chest Pain Type × Sex × Age, correlation matrix, feature correlation with the target
4. **Preprocessing** — null check, duplicate check, column rename (`Sex` → `Gender`)
5. **Data quality notes** — flags implausible zero-values in `Cholesterol` and `RestingBP`
6. **Key insights & recommendations** — top predictive features and next steps for modeling

## Key takeaways

- Dataset is clean: **0 missing values, 0 duplicates**
- Balanced target: **55.3%** positive for heart disease
- Sex is imbalanced: **79% male / 21% female**
- Strongest correlates with heart disease: **MaxHR (r = -0.40)**, **Oldpeak (r = 0.40)**, Age (r = 0.28), FastingBS (r = 0.27)
- **ASY (asymptomatic) chest pain** is the most common presentation (54%) and most associated with a positive diagnosis
- Zero-value entries in Cholesterol/RestingBP likely represent missing data and should be cleaned before modeling

## How to reproduce

1. Place `heart.csv` in the working directory (update the file path in the notebook's first cell)
2. Run `Heart_Failure_Prediction.ipynb` top to bottom
3. Regenerate the PDF report from the notebook's computed outputs (charts + narrative)

## Suggested next steps

- Impute or exclude zero-value Cholesterol/RestingBP entries
- Build a baseline classification model (logistic regression) using MaxHR, Oldpeak, Age, and ChestPainType as leading features
- Collect additional female patient records to reduce sex imbalance
- Validate the ASY–heart disease relationship with odds ratios or a stratified analysis
