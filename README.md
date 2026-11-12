Saudi Student Dropout Prediction — CS316 Project
Project Overview
This machine learning project investigates student dropout patterns across Saudi Arabian universities using demographic, academic, personal, and social factors.

The project was developed for CS316: Introduction to AI and Data Science at Prince Sultan University.

The objective is to compare machine learning classification models, select a model using cross-validation on the training data, and evaluate the selected model on a separate test set. The work is intended for research and decision support, not automated decisions about individual students.
Dataset
- Original sample size: 4,560 student responses.
- Predictors: 25 variables.
- Target variable: Dropout (Yes / No).
- Data cleaning: Removed 37 exact duplicate rows and one record with a missing target.
- Cleaned sample size: 4,522 labeled records (3,506 non-dropout; 1,016 dropout).
- Split: 3,617 training records and 905 test records (80/20, stratified, random_state=42).
- Feature handling: All 25 predictors were treated as categorical features in the implemented preprocessing workflow.
Example features include GPA, study year, failed courses, academic warnings, employment status, university satisfaction, family/friends support, language barriers, psychological issues, health issues, and prior knowledge about the selected major.
Dataset Source
S. Albugami, A. Wali, and H. Almagrabi, "Predicting student dropout in Saudi Universities using machine learning and explainable AI," PeerJ Computer Science, 2026.

DOI: 10.7717/peerj-cs.3490
Project Pipeline
1. Data cleaning: Inspect column names, remove exact duplicates, and exclude records with missing target values.
2. Preprocessing: Use ColumnTransformer with categorical imputation and OneHotEncoder(handle_unknown="ignore"). The pipeline defines a numerical preprocessing branch, but no columns enter that branch for this dataset.
3. Train/test split: Use an 80/20 stratified split, keeping the test data separate from model selection.
4. Class imbalance: Apply SMOTE-ENN within the training pipeline so resampling is not applied to validation folds or test data.
5. Models: Compare Logistic Regression, Random Forest, and Support Vector Machine (SVM).
6. Validation and tuning: Use five-fold stratified cross-validation and GridSearchCV, refitting according to Macro-F1.
7. Final test: Select the model based on cross-validation and evaluate only that selected model on the independent test set.
8. Interpretation: Calculate permutation feature importance for the selected model.
Results
Five-fold Cross-Validation
Model	Initial Accuracy	Initial Macro-F1	Tuned Accuracy	Tuned Macro-F1
Logistic Regression	79.98%	0.753	80.18%	0.754
Random Forest	85.35%	0.792	85.51%	0.793
SVM	83.52%	0.782	83.83%	0.783


The tuning results come from GridSearchCV on the training split. Random Forest achieved the highest tuned cross-validated Macro-F1 and was selected for final evaluation.
Best Hyperparameters
Model	Selected settings
Logistic Regression	C=10, class_weight='balanced'
Random Forest	n_estimators=500, max_depth=15, max_features='sqrt', min_samples_leaf=1, class_weight=None
SVM	C=1, gamma=0.1, class_weight='balanced'


Independent Test Results — Selected Random Forest
- Test accuracy: 83.54%
- Test Macro-F1: 0.759
- Test records: 905
- Correctly identified non-dropout: 633
- Correctly identified dropout: 123
- False positives: 69
- False negatives: 80
Logistic Regression and SVM were not evaluated on the independent test set in the final notebook workflow. Their results above are cross-validation results only.

The dropout class remains harder to identify than the non-dropout class, so accuracy should be interpreted alongside Macro-F1, class-specific precision and recall, and the confusion matrix.
Feature Importance
Permutation importance for the selected Random Forest identified study year and GPA as the highest-ranked predictors, followed by family/friends support, failed courses, and faculty. These scores describe predictive reliance, not causal effects.
Evaluation Metrics
- Accuracy
- Precision
- Recall
- Macro-F1
- Confusion matrix
- Five-fold stratified cross-validation
- Permutation feature importance
Sustainability
SDG 4 — Quality Education
Student dropout can lead to lost educational opportunities and inefficient use of university resources. Studying dropout patterns may help universities identify areas where student support could be improved.

The model is intended for research and human-led decision support only.
Limitations and Ethical Considerations
- The dataset comes from voluntary survey responses and may contain response or sampling bias.
- The sample may not represent every university student in Saudi Arabia or future cohorts.
- The dropout class is less common, and the selected model still misses some dropout students.
- Some variables include personal or psychological information and require responsible handling.
- Predictions should not be used to punish students or automatically restrict educational opportunities.
- Model associations do not prove causation.
- Additional external and subgroup validation would be required before real-world deployment.
Requirements
Install the Python dependencies listed in the repository:
pip install -r requirements.txt
Main libraries include pandas, numpy, matplotlib, scikit-learn, and imbalanced-learn.
How to Run
1. Clone or download the repository.
2. Install dependencies with pip install -r requirements.txt.
3. Keep Saudi_Student_Dropout_Data.csv available alongside the notebook.
4. Open Saudi_Student_Dropout_Prediction.ipynb in Jupyter Notebook or Google Colab.
5. Run the notebook cells from top to bottom. Hyperparameter tuning may be computationally intensive.
6. Review the cross-validation scores, selected model, final evaluation, and feature-importance output.
Repository Structure
Saudi-Student-Dropout-Prediction/
├── Reports/
│   ├── CS316_Phase1_Project_Proposal Final.docx
│   └── CS316_Phase2_IEEE_Report.docx
├── README.md
├── Saudi_Student_Dropout_Data.csv
├── Saudi_Student_Dropout_Prediction.ipynb
├── [presentation file in repository root]
└── requirements.txt
Replace the presentation placeholder above with its exact filename as shown in GitHub.
Project Team
Prince Sultan University
CS316 — Introduction to AI and Data Science
- Abdullah Alrasheed
- Abdullah Altorifi
- Suliman Alyamany
Conclusion
The project demonstrates a machine learning workflow for studying student dropout in survey data collected from Saudi university students. Random Forest was selected using training-set cross-validation, achieving 85.51% tuned cross-validation accuracy and 0.793 tuned cross-validation Macro-F1. On the independent test set, it achieved 83.54% accuracy and 0.759 Macro-F1.

The results highlight the importance of considering class imbalance, evaluating minority-class performance, and treating predictive associations as tools for research rather than automatic academic decisions.
