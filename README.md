<div style="font-size: 12px;">
# Breast Cancer Prediction & Analysis using ML Models
> Replicating & Extending Published Research on the Wisconsin Diagnostic Breast Cancer Dataset
> 
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-green?logo=scikitlearn)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Boosting-red)](https://xgboost.readthedocs.io/)
[![Dataset](https://img.shields.io/badge/Dataset-WDBC%20%28UCI%29-lightblue)](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Group Members:
Ashlesha Agrawal, Aashi Soni , Garv gupta
---
## Project Overview
This project replicates the analysis and insights from a published research paper on breast cancer classification using machine learning, working on the exact same dataset (Wisconsin Diagnostic Breast Cancer — WDBC). Beyond replication, it critically identifies the limitations of the original research and extends the work with additional experiments and a tuned model variant.
The goal of this work is to demonstrate:
- Ability to understand and reproduce research-grade ML pipelines
- Proficiency in exploratory data analysis (EDA) and feature engineering
- Hands-on experience with 9 different ML classifiers
- Critical thinking about research gaps and limitations

---
## Dataset
| Property | Value |
|---|---|
| Name | Wisconsin Diagnostic Breast Cancer (WDBC) |
| Source | UCI Machine Learning Repository |
| Records | 569 samples |
| Features | 30 numeric features + ID + Diagnosis |
| Target | Diagnosis: M = Malignant · B = Benign |
| Format | .xlsx |

### Feature Groups
The 30 input features are computed from digitized images of fine needle aspirate (FNA) of breast masses, describing characteristics of the cell nuclei:
- Mean values — radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension
- Standard error (SE) — same 10 characteristics
- Worst values — same 10 characteristics (largest mean of the three largest values)
---
## Research Replication
This notebook mirrors the methodology of the reference research paper, faithfully reproducing:
| Research Step | Description |
|---|---|
| EDA | Class distribution, feature correlations, statistical summaries |
| Preprocessing | Column renaming, label encoding (M=0, B=1), train/test split |
| Model Training | 9 classifiers trained on identical splits |
| Evaluation | Precision, Recall, F1-Score per class (Benign & Malignant) |
| Visualization | Replicated figures from the paper (distribution plots, heatmaps, bar charts) |

---
## ML Models Evaluated
| # | Model | Library |
|---|---|---|
| 1 | Support Vector Machine (SVM) | scikit-learn |
| 2 | Logistic Regression (LR) | scikit-learn |
| 3 | K-Nearest Neighbors (KNN) | scikit-learn |
| 4 | Naive Bayes (NB) | scikit-learn |
| 5 | Decision Tree (DT) | scikit-learn |
| 6 | Random Forest (RF) | scikit-learn |
| 7 | AdaBoost | scikit-learn |
| 8 | XGBoost | xgboost |
| 9 | Improved XGBoost (I-XGBoost) * | xgboost |

> * I-XGBoost is a tuned variant of XGBoost introduced as part of this extended analysis to address limitations found in the original research.

---

## Key Visualizations

The notebook reproduces and extends the following figures from the research:

- Fig. Distribution of Tumor Classes — Countplot of Benign vs Malignant samples
- Correlation Heatmap — Feature-level Pearson correlation matrix
- Fig. 9. Comparing various ML models — Side-by-side bar charts of Precision, Recall, and F1-Score for each model, broken down by Benign and Malignant classes

---

## Research Limitations Identified

After replicating the published research, several critical limitations were uncovered:

1. No Cross-Validation — The paper evaluates models on a single train/test split, making results susceptible to variance based on the random seed. A k-fold cross-validation approach would provide more robust and generalizable estimates.

2. No Hyperparameter Tuning — Most baseline models are run with default parameters, which may not yield optimal performance for this specific dataset. GridSearchCV or RandomizedSearchCV could significantly improve results.

3. Class Imbalance Ignored — The dataset is moderately imbalanced (357 Benign vs 212 Malignant). The paper does not apply any imbalance-handling strategy (SMOTE, class weighting, etc.), which can bias classifiers toward the majority class.

4. Accuracy Used Without Context — While accuracy is reported, it can be misleading on imbalanced datasets. AUC-ROC, Matthews Correlation Coefficient (MCC), or balanced accuracy would be more informative metrics.

5. No Feature Importance Analysis — The paper does not investigate which features contribute most to classification. Feature importance from tree-based models or SHAP values could provide valuable clinical interpretability.

6. No Statistical Significance Testing — Model comparisons are made without statistical tests (e.g., McNemar's test, Wilcoxon signed-rank test), making it unclear whether observed differences are meaningful or due to random chance.

7. Overfitting Risk in I-XGBoost — The improved XGBoost variant shows high performance but is evaluated on the same test set used for tuning decisions, potentially introducing data leakage.

---

## Tech Stack

```
Python 3.8+
├── pandas           — Data loading & manipulation
├── numpy            — Numerical operations
├── matplotlib       — Visualization
├── seaborn          — Statistical plots
├── scikit-learn     — ML models & evaluation
└── xgboost          — Gradient boosting models
```

---

## Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost openpyxl
```

### Run the Notebook

1. Clone this repository
   ```bash
   git clone https://github.com/AshleshaAgrawal012/Breast_Cancer_Prediction_and_Analysis_using_ML_Models.git
   cd Breast_Cancer_Prediction_and_Analysis_using_ML_Models
   ```

2. Launch Jupyter Notebook
   ```bash
   jupyter notebook breast_cancer_ml_analysis.ipynb
   ```

3. Run all cells — The notebook is self-contained and will execute the full pipeline end-to-end.

---

## Repository Structure

```
Breast_Cancer_Prediction_and_Analysis_using_ML_Models/
│
├── breast_cancer_ml_analysis.ipynb   ← Main analysis notebook
├── wdbc_dataset.xlsx                 ← Wisconsin Diagnostic Breast Cancer dataset
└── README.md                         ← This file
```

---

## Reference Paper
The analysis in this notebook is based on and extends the following published research:
> Abreastcancerriskpredication andclassification model with ensemble
learning andbigdatafusion
Varshali Jaiswala,1, Praneet Saurabhb,1, Umesh Kumar Lilhorec,1, Mayank Pathakd,1,
Sarita Simaiyac,1, Surjeet Dalale,∗,1
> The original paper is not included in this repository due to copyright. Please access it via the DOI link above or through your institution's library, ResearchGate, or Google Scholar.
---

## What This Project Demonstrates
| Skill | Evidence |
|---|---|
| Reading & Understanding Research Papers | Reproduced all figures and experiments from the original paper |
| Exploratory Data Analysis | Correlation heatmaps, class distribution, feature statistics |
| Machine Learning | 9 classifiers trained, tuned, and compared |
| Model Evaluation | Precision, Recall, F1-Score per class |
| Critical Thinking | 7 concrete research limitations identified |
| Python / Jupyter | End-to-end reproducible notebook |

</div>
