# Saudi Student Dropout Prediction — CS316 Project

## Project Overview
This machine learning project predicts student dropout risk across Saudi Arabian universities using demographic, academic, and well-being factors.

## Dataset
- **Sample Size:** 4,560 student records across 33 Saudi Arabian universities.
- **Features:** 25 predictive variables including GPA, failed courses, academic warnings, employment status, language barriers, and psychological/health issues.
- **Target Variable:** `Dropout` (`Yes` / `No`).

## Project Pipeline
1. **Data Cleaning & Preprocessing:** Duplicate removal, missing value imputation, and One-Hot Encoding for categorical features.
2. **Class Imbalance Management:** Applied `SMOTE-ENN` to balance class distribution without data leakage.
3. **Model Selection & Tuning:** Evaluated Logistic Regression, Random Forest, and Support Vector Machines (SVM) using 5-Fold Stratified Cross-Validation and GridSearchCV.
4. **Final Testing:** Model selection performed strictly using CV, keeping test data untouched until final evaluation.

## Requirements
To install dependencies locally:
```bash
pip install -r requirements.txt