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
├── docs/
│   └── Project_Report.docx                 # problem statement, methodology, results template, discussion, limitations
├── notebooks/
│   └── ASD_Pipeline & Framework.ipynb      # pipeline runnable (data -> features -> training -> evaluation -> saved model)
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└──requirements.txt                         # Python dependencies
```

---

## 📊 What's Been Done So Far

Open `notebooks/ASD_Pipeline & Framework.ipynb` in Jupyter / Colab and run all cells top
to bottom. On first run it will:

1. Download ABIDE subjects and the Schaefer/AAL atlases.
2. Extract and cache connectivity features to `feature_cache/` (so re-runs are fast).
3. Run 10-fold cross-validation and print per-fold accuracy/AUC.
4. Train a final model on the full CV portion and evaluate once on a held-out test set.
5. Save the trained model, scaler, and PCA transform to `artifacts/`.
6. Report permutation feature importance for the final model.

---

## 💡 Key Findings

- **Features:** Regional time-series extracted with two brain atlases (Schaefer-2018, 100 ROIs, and AAL), converted to tangent-space functional connectivity matrices (`nilearn.connectome.ConnectivityMeasure`), and fused into a single feature vector per subject.
- **Model:** A compact feed-forward network (`Linear → LayerNorm → ReLU → Dropout → Linear → LayerNorm → ReLU → Linear`) trained with `BCEWithLogitsLoss` (class-imbalance weighted) and Adam.
- **Evaluation protocol:** A stratified hold-out test set is split off before any cross-validation; 10-fold stratified CV is run on the remaining data for a robust performance estimate; the final model is retrained on the full CV portion and scored once on the untouched hold-out set.

---
## 🎯 Results

| Metric | Cross-validation (mean ± std) | Hold-out test set |
|---|---|---|
| Accuracy | 66.67% (+/- 15.52) | 76.00% |
| AUC | 0.763 (+/- 0.156) | 0.819 |

---
## 🔜 What's Coming Next

- [ ] Scale to the full ABIDE release and/or combine with ABIDE II.
- [ ] Nested cross-validation for proper hyperparameter search.
- [ ] Generate ROC-AUC curves and confusion matrices.
- [ ] Map important PCA components back to anatomical connectivity edges for clinical interpretability.
- [ ] Package the saved model behind a small inference API (e.g. AWS SageMaker endpoint).
- [ ] Write full project report in `docs/findings.md`

---

## 🚀 How to Run

**1. Clone the repository**
```bash
git clone https://github.com/shivam-saurav-tech/asd-detection.git
cd asd-detection
```

**2. Create virtual environment**
```bash
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**Dataset :** [ABIDE (Autism Brain Imaging Data Exchange)](http://fcon_1000.projects.nitrc.org/indi/abide/), fetched via `nilearn.datasets.fetch_abide_pcp` (C-PAC preprocessing pipeline).

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

## 🚫 Known limitations

Stated here deliberately, as they're relevant to how the results should be read:

- Trained on 200 of ABIDE's ~1,100+ available subjects; a larger sample would give a
  more generalizable estimate.
- Threshold tuning uses an internal validation split per fold rather than nested
  cross-validation; hyperparameters (PCA components, learning rate, epochs) were set
  manually rather than searched.
- No external dataset validation (e.g. training on ABIDE I, testing on ABIDE II).
- Interpretability is limited to permutation importance on PCA components, not yet
  mapped back to specific brain regions/connections.

  ---

## 🤝 Contributing

This project is open to contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

---

## ⚠️ Disclaimer

This project is for **educational and research purposes only**. It is not a clinical diagnostic tool and should not be used as a substitute for professional medical evaluation.

---

## 👤 Author

- Shivam Saurav : [shivam-saurav-tech](https://github.com/shivam-saurav-tech)
- Vinay Singh : [@exclamedvinay](https://github.com/exclamedvinay)
---

## 📄 License

MIT — see [LICENSE](LICENSE).
