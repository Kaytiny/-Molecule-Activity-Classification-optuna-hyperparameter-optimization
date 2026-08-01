# Molecule Activity Classification

A machine learning project for classifying the biological activity of chemical compounds based on molecular descriptors.

This repository implements a complete machine learning pipeline: data preprocessing, feature scaling, baseline model comparison (Random Forest, XGBoost), and hyperparameter optimization using Optuna.

---

## Data Description

The dataset consists of a vector of molecular descriptors (1776 features, `D1` – `D1776`) and a target variable, `Activity`:
* **`Activity`** (target): Biological activity of the compound (`0` or `1`).
* **`D1` – `D1776`** (features): Numerical features representing the physical and chemical properties of the molecule.

---

## Tech Stack

* **Python 3.x**
* **Pandas / NumPy** — Data loading, preprocessing, and manipulation
* **Scikit-Learn** — Dataset splitting (`train_test_split`), feature scaling (`StandardScaler`), evaluation metrics, and `RandomForestClassifier` baseline
* **XGBoost** — Gradient boosting with GPU acceleration support (`device='cuda'`)
* **Optuna** — Bayesian hyperparameter optimization

---

## Workflow Pipeline

1. **Data Splitting & Preparation:**
   * Split the raw dataset into training (`train`) and validation (`valid`) sets in an 80/20 ratio while preserving class balance (`stratify=y`).
   * Normalize features using `StandardScaler`.

2. **Baseline Model Evaluation:**
   * `RandomForestClassifier` (baseline)
   * `XGBClassifier` (GPU-accelerated)

3. **Hyperparameter Optimization:**
   * Automated hyperparameter tuning for `XGBClassifier` using **Optuna** (optimizing `n_estimators`, `learning_rate`, `max_depth`, `reg_alpha`, `reg_lambda`, etc.).

---

## Results and Metrics

Model performance was evaluated using **Accuracy**, **Precision**, **Recall**, and **F1-Score**.

| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **RandomForestClassifier** | ~0.7816 | ~0.7886 | ~0.8157 | ~0.8019 |
| **XGBClassifier (Baseline)** | ~0.7856 | ~0.7874 | ~0.8280 | ~0.8072 |
| **XGBClassifier + Optuna** | **~0.8156** | — | — | — |

*After hyperparameter optimization with Optuna, the best iteration achieved an accuracy improvement of up to **~81.56%**.*
