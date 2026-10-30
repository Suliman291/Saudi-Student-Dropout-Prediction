# Saudi Student Dropout Prediction — CS316 Project

## Project Overview

This machine learning project predicts student dropout risk across Saudi Arabian universities using demographic, academic, personal, and social factors.

The project was developed for **CS316: Introduction to AI and Data Science** at **Prince Sultan University**.

The main objective is to compare several machine learning classification models and determine which model performs best in predicting whether a student may drop out.

---

## Dataset

- **Sample Size:** 4,560 student responses.
- **Features:** 25 predictive variables.
- **Target Variable:** `Dropout` (`Yes` / `No`).
- The dataset includes students from multiple public and private universities across Saudi Arabia.

Example features include:

- GPA
- Academic year
- Failed courses
- Academic warnings
- Employment status
- University satisfaction
- Family and friends support
- Language barriers
- Psychological issues
- Health issues
- Previous knowledge about the selected major

### Dataset Source

The dataset was published with the following research article:

**S. Albugami, A. Wali, and H. Almagrabi,  
"Predicting student dropout in Saudi Universities using machine learning and explainable AI,"  
PeerJ Computer Science, 2026.**

DOI:

`10.7717/peerj-cs.3490`

---

## Project Pipeline

1. **Data Cleaning & Preprocessing**
   - Removed duplicate records.
   - Checked missing values.
   - Applied missing-value imputation when needed.
   - Used One-Hot Encoding for categorical features.
   - Standardized numerical variables.

2. **Train/Test Split**
   - Used an 80/20 train-test split.
   - Used stratification to preserve the class distribution.

3. **Class Imbalance Management**
   - Applied `SMOTE-ENN` to the training data.
   - The test set remained untouched to prevent data leakage.

4. **Model Training**
   - Logistic Regression
   - Random Forest
   - Support Vector Machine (SVM)

5. **Model Validation**
   - 5-Fold Stratified Cross-Validation.
   - Hyperparameter tuning using GridSearchCV.

6. **Final Testing**
   - Model selection was performed using cross-validation.
   - The independent test set was used only for final evaluation.

---

## Results

| Model | Test Accuracy | Macro F1 |
|---|---:|---:|
| Logistic Regression | 79.01% | 0.737 |
| Random Forest | **82.76%** | 0.750 |
| Support Vector Machine | 82.54% | **0.764** |

### Best Accuracy

The **Random Forest** model achieved the highest test accuracy:

**82.76%**

It also achieved approximately:

**85.35% Cross-Validation Accuracy**

Although Random Forest achieved the highest accuracy, SVM achieved a slightly higher Macro F1 score.

Because the dataset is imbalanced, performance was evaluated using multiple metrics instead of accuracy alone.

---

## Evaluation Metrics

The following evaluation metrics were used:

- Accuracy
- Precision
- Recall
- Macro F1 Score
- Confusion Matrix
- Stratified Cross-Validation

---

## Sustainability

This project supports:

### SDG 4 — Quality Education

Student dropout can lead to lost educational opportunities and inefficient use of university resources.

Machine learning may help universities understand patterns associated with dropout and potentially support earlier student-support interventions.

The model is intended for **research and decision-support purposes only**.

---

## Limitations and Ethical Considerations

- The dataset is based on voluntary survey responses.
- The sample may not represent every university student in Saudi Arabia.
- The dataset contains fewer dropout students than non-dropout students.
- Some variables contain personal or psychological information and should be handled responsibly.
- Predictions should not be used to punish students or automatically restrict educational opportunities.
- Machine learning predictions show associations and do not prove causation.
- The system should support human decision-making rather than replace it.

---

## Requirements

Install the required Python libraries using:

```bash
pip install -r requirements.txt
```

Main libraries used:

- pandas
- numpy
- matplotlib
- scikit-learn
- imbalanced-learn

---

## How to Run

1. Download or clone this repository.
2. Install the required libraries using `requirements.txt`.
3. Make sure `Saudi_Student_Dropout_Data.csv` is available.
4. Open:

```text
Saudi_Student_Dropout_Prediction.ipynb
```

5. Run the notebook cells from top to bottom.

The notebook performs preprocessing, class-imbalance handling, model training, cross-validation, hyperparameter tuning, final evaluation, and feature analysis.

---

## Repository Structure

```text
Saudi-Student-Dropout-Prediction/
│
├── Presentation/
├── Reports/
├── README.md
├── Saudi_Student_Dropout_Data.csv
├── Saudi_Student_Dropout_Prediction.ipynb
└── requirements.txt
```

---

## Project Team

**Prince Sultan University**

**CS316 — Introduction to AI and Data Science**

- Abdullah Alrasheed
- Abdullah Altorifi
- Suliman Alyamany

---

## Conclusion

The project demonstrates that machine learning can be used to predict student dropout using data collected from Saudi university students.

Among the tested models, **Random Forest achieved the highest test accuracy of 82.76%**, exceeding the project's target of 80% accuracy.

The results also demonstrate the importance of considering class imbalance and using evaluation metrics such as Macro F1, precision, and recall in addition to accuracy.
