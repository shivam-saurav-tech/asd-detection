# ASD Detection System 🧩

> **Status: 🚧 Work in Progress** — This project is actively being developed. Contributions, feedback, and suggestions are welcome.

An exploratory data analysis and behavioral pattern detection system for Autism Spectrum Disorder (ASD) using Python. The project analyses behavioral screening datasets to identify key patterns and features that contribute to ASD classification insights.

---

## 📌 Project Overview

Autism Spectrum Disorder affects an estimated 1 in 100 people worldwide. Early and accurate screening is critical — yet access to formal diagnosis remains limited in many regions. This project explores whether behavioral screening data alone can surface meaningful patterns to support early identification.

| Phase | Tool | Status |
|---|---|---|
| Data Preprocessing | Python, Pandas | ✅ Done |
| Exploratory Data Analysis | Pandas, Matplotlib, Seaborn | ✅ Done |
| Feature Analysis | Correlation, Chi-square | ✅ Done |
| Visualization | Matplotlib, Seaborn | ✅ Done |
| ML Model Development | Scikit-learn | 🚧 In Progress |
| Web Interface | Flask / Streamlit | 🔜 Planned |
| Model Evaluation & Tuning | Cross-validation, ROC-AUC | 🔜 Planned |

---

## 📁 Project Structure

```
asd-detection/
├── data/
│   ├── raw/                  # Original unmodified dataset
│   └── processed/            # Cleaned and preprocessed data
├── notebooks/
│   └── eda.ipynb             # Exploratory Data Analysis notebook (add yours here)
├── outputs/
│   └── figures/              # Generated charts and plots
├── docs/
│   └── findings.md           # Key findings and observations
├── requirements.txt          # Python dependencies
├── .gitignore
├── CONTRIBUTING.md
└── README.md
```

---

## 📊 What's Been Done So Far

- Loaded and cleaned the ASD behavioral screening dataset (1,104 records)
- Handled missing values, encoded categorical variables
- Performed feature-level correlation analysis across all 10 behavioral questions (A1–A10)
- Identified top discriminative features: **A1, A5, A8** (social attention, pattern recognition, contextual understanding)
- Visualised age distribution, gender split, ethnicity breakdown, and screening score distribution
- Observed that subjects scoring **≥7 on the screening test** show ASD positive rates above 85%
- Found family history increases likelihood of positive screening by **2.3×**

---

## 💡 Key Findings

- **Screening score ≥ 7** is the strongest single predictor of ASD classification
- **Male subjects** account for 62% of ASD positive cases — consistent with the known 4:1 clinical ratio
- **A1, A5, A8** behavioral questions carry the highest predictive signal individually
- **Family history** of ASD is a statistically significant risk factor

---

## 🔜 What's Coming Next

- [ ] Build and evaluate classification models (Logistic Regression, Random Forest, XGBoost)
- [ ] Perform cross-validation and hyperparameter tuning
- [ ] Generate ROC-AUC curves and confusion matrices
- [ ] Build an interactive prediction interface (Streamlit or Flask)
- [ ] Add SHAP-based feature importance explanation
- [ ] Write full project report in `docs/findings.md`

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/shivam-saurav-tech/asd-detection.git
cd asd-detection

# Install dependencies
pip install -r requirements.txt

# Add your dataset to data/raw/ then open the notebook
jupyter notebook notebooks/eda.ipynb
```

**Dataset:** [ASD Screening Data — UCI / Kaggle](https://www.kaggle.com/datasets/faizunnabi/autism-screening)

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3** | Core language |
| **Pandas** | Data loading, cleaning, manipulation |
| **Matplotlib / Seaborn** | Visualisation and EDA plots |
| **Scikit-learn** | ML models (coming soon) |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 🤝 Contributing

This project is open to contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

---

## ⚠️ Disclaimer

This project is for **educational and research purposes only**. It is not a clinical diagnostic tool and should not be used as a substitute for professional medical evaluation.

---

## 👤 Author

- Vinay Singh : [@exclamedvinay](https://github.com/exclamedvinay)
- Shivam Saurav : [shivam-saurav-tech](https://github.com/shivam-saurav-tech)
---

## 📄 License

MIT License — free to use, modify, and distribute with attribution.
