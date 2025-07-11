# Final Project – Customer Churn Analysis

**Author:** Ileana Jarquin
**Program:** TripleTen Data Science Bootcamp  
**Date:** July 2025

---

## 🔎 Project Overview

This repository contains my **Capstone Project** for the TripleTen Data Science Bootcamp—a comprehensive, end-to-end analysis that puts into practice the full data science workflow:

1. **Problem definition:** Predict customer churn for a telecom provider  
2. **Data engineering:** Ingest, clean, merge, and transform multiple real-world datasets  
3. **Feature engineering & EDA:** Create and explore tenure, billing, and service usage features  
4. **Modeling:** Train, tune, and evaluate multiple classification models using pipelines and GridSearchCV  
5. **Insights & business impact:** Extract actionable retention strategies from the final model

By completing this Capstone, I demonstrate mastery of Python, pandas, scikit-learn pipelines, and ML evaluation—culminating the skills acquired throughout the bootcamp.

---

## 🛠️ Tech Stack & Libraries

- **Python 3.9**  
- **JupyterLab** for interactive development  
- **Pandas** & **NumPy** for data manipulation  
- **Matplotlib** & **Seaborn** for visualization  
- **scikit-learn** for preprocessing, modeling, and evaluation  
  - `Pipeline`, `ColumnTransformer`, `GridSearchCV`  
  - **Logistic Regression**, **RandomForestClassifier**, **GradientBoostingClassifier**  

---

## 🚀 Project Steps

1. **Data Loading & Merging**  
   - Imported four CSV files (`personal.csv`, `contract.csv`, `internet.csv`, `phone.csv`)  
   - Merged into one DataFrame on `customer_id`

2. **Data Preprocessing**  
   - Renamed columns to snake_case  
   - Parsed `start_date` and `end_date` as datetime, created `churned` target  
   - Handled missing values (`total_charges` conversion, `active_days` imputation)

3. **Feature Engineering**  
   - Created `active_days` (tenure) from date fields  
   - Binarized `internet_service` → `fiber_optic`  
   - One-hot encoded contract and payment method categories  
   - Converted all boolean/categorical flags to numeric

4. **Exploratory Data Analysis (EDA)**  
   - Visualized churn distribution, service counts, and billing patterns  
   - Identified that most churn occurs in the first 6 months

5. **Model Training & Evaluation**  
   - Split into stratified train/test sets  
   - Addressed class imbalance with `class_weight='balanced'`  
   - Trained and tuned three models via `GridSearchCV` (AUC-ROC scoring)  
     - **Logistic Regression:** AUC = 0.818  
     - **Random Forest:** AUC = 0.830  
     - **Gradient Boosting:** AUC = 0.894 (final model)

6. **Feature Importance & Insights**  
   - Extracted top predictors from Gradient Boosting (`active_days`, `monthly_charges`, etc.)  
   - Mapped these insights back to business recommendations  

---

## 📈 Key Results & Recommendations

- **Final Model:** Gradient Boosting Classifier (AUC-ROC = 0.894)  
- **Top Predictors:**  
  1. **active_days** (tenure)  
  2. **monthly_charges**  
- **Retention Strategies:**  
  - **Early Engagement:** Onboarding programs and check-ins during first months  
  - **Bundling Offers:** Incentivize multi-service packages for lower-tenure customers  
  - **Value Communication:** Targeted discounts for high-bill customers at risk  


