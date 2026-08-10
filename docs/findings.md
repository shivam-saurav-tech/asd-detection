# Project Findings & Observations

> This document is updated as the analysis progresses.  
> Last updated: May 2026

---

## Dataset

- **Source:** ASD Screening Dataset (UCI / Kaggle)
- **Records:** 1,104 subjects (adults)
- **Features:** 21 columns — 10 behavioral questions (A1–A10), demographics, screening score, and ASD classification
- **Target variable:** `Class/ASD` — Yes / No

---

## Preprocessing Steps

1. Loaded raw CSV and inspected shape, dtypes, and null values
2. Replaced `?` placeholder values with `NaN` and dropped or imputed accordingly
3. Encoded categorical variables (gender, ethnicity, country, relation) using label encoding
4. Converted binary behavioral responses (Yes/No) to integer (1/0)
5. Confirmed no duplicate records

---

## EDA Findings

### Class Distribution
- ASD Positive: 516 (46.7%)
- ASD Negative: 588 (53.3%)
- Dataset is reasonably balanced — no aggressive resampling needed

### Gender
- Male: 62% of ASD positive cases
- Female: 38% of ASD positive cases
- Consistent with clinical literature (approx. 4:1 male-to-female ratio)

### Age
- Age range: 17–64 years (adult dataset)
- ASD positive subjects tend to cluster in the 20–35 age bracket
- Older subjects (50+) show lower screening rates but similar positive ratios

### Screening Score
- Subjects scoring ≥ 7 out of 10: ASD positive rate > 85%
- Subjects scoring ≤ 4 out of 10: ASD positive rate < 10%
- Score alone is a strong pre-diagnostic signal

### Behavioral Questions (A1–A10)
| Question | Topic | Correlation with ASD |
|---|---|---|
| A1 | Social attention to others | High |
| A2 | Noticing small sounds | Medium |
| A3 | Multitasking focus | Medium |
| A4 | Switching tasks | Low-Medium |
| A5 | Pattern recognition | High |
| A6 | Reading social cues | Medium |
| A7 | Fictional perspective-taking | Low |
| A8 | Contextual understanding | High |
| A9 | Facial emotion recognition | Medium |
| A10 | Social engagement initiation | Medium |

### Family History
- Subjects with family history of ASD: 2.3× more likely to screen positive
- Strong indicator for risk stratification

---

## Next Steps (Planned)

- Train Logistic Regression, Random Forest, and XGBoost classifiers
- Evaluate using accuracy, precision, recall, F1, and ROC-AUC
- Apply SHAP for feature importance explainability
- Build Streamlit interface for interactive screening simulation

---

## References

- American Psychiatric Association. (2013). DSM-5
- Thabtah, F. (2017). ASD Screening Dataset. UCI Machine Learning Repository
- Maenner et al. (2023). Prevalence and Characteristics of Autism Spectrum Disorder. CDC MMWR
