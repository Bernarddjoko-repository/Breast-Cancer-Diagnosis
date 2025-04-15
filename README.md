![Screenshot 2025-04-15 110020](https://github.com/user-attachments/assets/8a89b115-b0e1-4c46-9d69-bad8a2094a32)


## 📌 Project Description: Breast Cancer Classification using ML Pipeline<br>

This project demonstrates a comprehensive machine learning pipeline for binary classification of breast tumors (benign vs malignant) using the **Breast Cancer Wisconsin (Diagnostic)** dataset from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(diagnostic)).<br>
It simulates a real-world healthcare use case and includes **end-to-end stages**: from data loading, preprocessing, and class balancing, to model training, evaluation, interpretation, and visualization.<br>

---

## 🛠️ Step-by-Step Workflow<br>

### ✅ Step 1: Data Loading and Cleaning<br>
- Dataset with 569 rows and 32 columns (ID, Diagnosis, and 30 numerical features)<br>
- Dropped ID column, mapped `Diagnosis` to binary labels (`M`=1, `B`=0)<br>
- Verified no missing values<br>
- Handled moderate class imbalance (Malignant ≈ 37%, Benign ≈ 63%)<br>

### ✅ Step 2: Exploratory Data Analysis (EDA)<br>
- Visualized class distribution and feature histograms<br>
- Detected strong correlations among `radius`, `area`, `perimeter`, etc.<br>
- Identified high predictive separation between malignant and benign for key features<br>

### ✅ Step 3: Feature Engineering<br>
- Applied **StandardScaler** to normalize all features<br>
- Created an engineered feature: `area_ratio = area_mean / perimeter_mean`<br>
- Applied **SMOTE** to balance training data (post split)<br>
- Used **Random Forest** to rank features and selected **Top 10** most important<br>

### ✅ Step 4: Model Training<br>
Trained three supervised classifiers:<br>
- **Decision Tree**<br>
- **K-Nearest Neighbors (KNN)**<br>
- **Support Vector Machine (SVM)**<br>

Workflow:  
`Data → Train/Test Split → SMOTE (Train only) → Training → Evaluation`<br>

### ✅ Step 5: Evaluation and Cross-Validation<br>

| Model           | Accuracy | Precision | Recall | F1 Score |
|----------------|----------|-----------|--------|----------|
| Decision Tree  | 0.93     | 0.89      | 0.93   | 0.91     |
| **KNN**        | **0.97** | **0.98**  | 0.95   | **0.96** |
| SVM            | 0.96     | 0.95      | 0.95   | 0.95     |<br>

- **KNN performed best overall**, with the highest F1-score and lowest error rates<br>
- **Cross-validation** confirmed KNN's robustness (mean accuracy: 94.4%, std dev: 1.8%)<br>
- Visualized results using:<br>
  - Confusion matrices<br>
  - Decision boundaries (via PCA)<br>
  - Bar plots of evaluation metrics and cross-validation scores<br>

---

## ⚠️ Challenges Faced<br>

- **Class Imbalance**: Addressed using SMOTE, which successfully balanced the dataset without overfitting.<br>
- **Feature Redundancy**: High correlation among features required careful feature selection to reduce dimensionality.<br>
- **Interpretability**: Balancing model performance with explainability — KNN and SVM were favored for both.<br>

---

## 💡 Key Takeaways and Recommendations<br>

- **KNN** is recommended for deployment in clinical support tools, given its:<br>
  - High precision (reduces false positives)<br>
  - High recall (reduces false negatives — critical in cancer detection)<br>
  - Robust performance across cross-validation<br>

- Future work may include:<br>
  - Testing on external/clinical datasets<br>
  - Adding explainability tools like **SHAP** or **LIME**<br>
  - Exploring ensemble models (Random Forest, Gradient Boosting)<br>

