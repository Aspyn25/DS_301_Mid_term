# **Credit Card Default Prediction - Mid Term Project**

## **📌 Project Overview**
This project aims to replicate and enhance the findings from the research paper:
**"The Comparisons of Data Mining Techniques for the Predictive Accuracy of Probability of Default of Credit Card Clients"** by I-Cheng Yeh & Che-hui Lien (2009).

We analyze the "Default of Credit Card Clients" dataset using multiple machine learning classification models to predict the probability of default. Our objective is to test different algorithms, optimize hyperparameters, and improve predictive accuracy.

## **📂 Dataset**
- **Name**: `default_credit_score`
- **Shape**: `(30000, 25)`
- **Source**: The dataset consists of credit card holders from a Taiwanese bank, containing demographic data, credit history, billing & payment amounts, and default payment status.

## **🔹 Machine Learning Models Implemented**
- **Logistic Regression (LR)**
- **K-Nearest Neighbors (KNN)**
- **Classification Trees (CTs)**
- **Support Vector Machine (SVM)**
- **XGBoost Classifier**

## **📊 Data Preprocessing & Feature Engineering**
- **Outlier Handling:**
  - Filtered `Credit Limit Amount` outliers (≥ 1,000,000) to the top 5%
  - Replaced negative values in `Bill Amount` (indicating overpayment) with `0`
  - Used Interquartile Range (IQR) method for `Bill Amount` & `Pay Amount` outliers
  - Merged unknown `EDUCATION` values (5,6) into category `4 (Others)`
- **Feature Scaling:** Applied `StandardScaler` for standardization.

## **📌 Reproduced Steps from the Paper**
### **1️⃣ Logistic Regression (LR)**
- Implemented as a baseline model.
- Applied `class_weight={0:1, 1:2}` to address class imbalance.
- **Performance:** `Accuracy = 0.80`, `AUC = 0.74`, `F1-score (minority class) = 0.48`

### **2️⃣ K-Nearest Neighbors (KNN)**
- Optimized `k` using hyperparameter tuning.
- Standardized features to improve distance calculations.
- Tested feature selection (Random Forest importance) but results remained unchanged.
- Applied `SMOTE` but performance declined due to KNN’s sensitivity to synthetic data.
- **Performance:** `Accuracy = 0.81`, `F1-score (minority class) = 0.41`

### **3️⃣ Classification Trees**
- **Hyperparameter tuning applied:**
  - `max_depth=4`: Prevent overfitting.
  - `min_samples_split=200`: Ensure node splitting occurs only with sufficient samples.
  - `min_samples_leaf=50`: Simplify model and improve generalization.
  - `random_state=42`: Ensure reproducibility.
- **Performance:** `Accuracy = 0.82`, `Recall (minority class) = 0.33`

## **📊 Model Performance Evaluation**
| Model | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-score (Class 1) | Error Rate | Area Ratio |
|---------|------------|-----------------|----------------|----------------|------------|-------------|
| **Logistic Regression** | 0.80 | 0.56 | 0.43 | 0.48 | 0.19 | 0.41 |
| **KNN (k=14)** | 0.81 | 0.65 | 0.30 | 0.41 | 0.18 | 0.68 |
| **Classification Trees** | 0.82 | 0.69 | 0.33 | 0.45 | 0.17 | 0.49 |
| **SVM** | 0.81 | 0.67 | 0.32 | 0.43 | 0.18 | 0.40 |
| **XGBoost** | 0.80 | 0.55 | 0.44 | 0.49 | 0.15 | - |

## **🚀 Key Contributions & Enhancements**
✅ **Explored Additional ML Models** beyond those in the original paper.<br>
✅ **XGBoost Implementation:** Applied gradient boosting for better class imbalance handling.<br>
✅ **SVM & Hyperparameter Tuning:** Optimized kernel functions and regularization parameters.<br>
✅ **Classification Tree Enhancements:**
- Used **GridSearchCV** for automatic hyperparameter tuning.
- **Optimized SSM (Sorting Smoothing Method) parameter tuning**.
- Improved model calibration (`R² = 0.8783` vs. paper’s `R² = 0.278`).

## **📌 Challenges & Lessons Learned**
🔹 **Class Imbalance Handling**:
  - **SMOTE caused overfitting**, so we used `scale_pos_weight` in XGBoost instead.
  - XGBoost **achieved AUC 0.82**, proving better for imbalanced classification.
🔹 **Overfitting in Classification Trees:**
  - Initial unpruned models performed poorly in validation.
  - **Pruning techniques (`max_depth=4`, `min_samples_leaf=50`) improved generalization.**
  
## **📌 How to Run the Project**
### **1️⃣ Clone the Repository**
```bash
git clone https://github.com/your-repo/DS_301_Mid_term.git
cd DS_301_Mid_term
```

## **📚 References**
- Research Paper: *The Comparisons of Data Mining Techniques for the Predictive Accuracy of Probability of Default of Credit Card Clients* – I-Cheng Yeh & Che-hui Lien (2009).
- Dataset: *Default of Credit Card Clients*.

---
📌 **Contributors:** Marcelo, Dana, Aspyn
📌 **Project Repo:** [GitHub Link](https://github.com/your-repo/DS_301_Mid_term)

🚀 *Happy Coding!*
