# 🫀 Heart Disease Prediction with Machine Learning
 
> **Can we catch heart disease before it catches the patient?**
> This project uses classical ML to predict heart disease from clinical markers — achieving **91% recall** on the positive class, meaning 9 out of 10 at-risk patients are correctly identified.
 
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
 
---
 
## 🎯 Problem Statement
 
Heart disease remains the leading cause of death globally. Early prediction based on routine clinical data can dramatically improve patient outcomes.
 
We frame this as a **binary classification** task:
 
| Label | Meaning |
|-------|---------|
| `0` | No heart disease detected |
| `1` | Heart disease present |
 
**Dataset:** UCI Cleveland Heart Disease — 303 patients, 14 clinical features.
 
---
 
## 📊 Key Results
 
| Model | Accuracy | Recall (Class 1) | F1-Score | CV Accuracy |
|---|---|---|---|---|
| **SVM (RBF)** 🏆 | **0.87** | **0.91** | **0.88** | 0.843 |
| Logistic Regression | 0.84 | 0.88 | 0.85 | 0.860 |
| KNN | 0.82 | 0.84 | 0.83 | 0.827 |
| Decision Tree | 0.75 | 0.78 | 0.77 | 0.744 |
 
**Why recall matters here:** In medical diagnostics, a false negative (telling a sick patient they're healthy) is far more dangerous than a false positive. The SVM model minimizes exactly that risk.
 
---
 
## 🔍 What We Discovered
 
- **`oldpeak`** (ST depression induced by exercise) and **`thalach`** (max heart rate) emerged as the strongest predictors — confirming our initial hypothesis that cardiac stress markers outweigh demographics.
- **Cholesterol is overrated** — despite its reputation, `chol` showed high variance and heavy overlap between healthy and diseased groups, making it unreliable as a standalone predictor.
- **Scaling is non-negotiable** — without `StandardScaler`, KNN accuracy dropped below 65% because features like `chol` (range 126–564) completely dominated `oldpeak` (range 0–6).
---
 
## 🛠 Tech Stack & Pipeline
 
```
Raw Data → Imputation → One-Hot Encoding → Standard Scaling → Model Training → Evaluation
```
 
**Preprocessing:**
- Missing values: median imputation (`ca`), mode imputation (`thal`)
- Categorical encoding: one-hot (`cp`, `restecg`, `slope`, `thal`)
- Feature scaling: `StandardScaler` on all numerical features
**Models compared:**
- Logistic Regression — interpretable baseline
- K-Nearest Neighbors — local pattern detection
- Decision Tree — non-linear boundaries & feature importance
- SVM with RBF Kernel — high-dimensional non-linear classification
---
 
## ⚠️ Honest Limitations
 
We believe in transparency about what the model *can't* do:
 
- **Small dataset** (n=303) — results show high variance; changing `random_state` can shift accuracy by ±5%.
- **Edge cases** — patients with asymptomatic chest pain but otherwise normal vitals are consistently misclassified.
- **Decision Tree overfitting** — high training accuracy but significant test-set drop, classic memorization on a small dataset.
---
 
## 🚀 Future Work
 
- **Nested Cross-Validation** for more robust performance estimates
- **Random Forest / Gradient Boosting** to reduce the variance of tree-based methods
- **SHAP values** for model-agnostic interpretability
- Validation on a larger, more diverse clinical dataset
---
 
## 👥 Team

- Abenov Altair
- Akzhigitov Abilkaiyr
- Abdygalykov Dinmukhamed
 
---
 
<p align="center">
  <i>Built with scikit-learn, curiosity, and a genuine concern for patient outcomes.</i>
</p>
