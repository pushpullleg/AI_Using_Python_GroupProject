# Phase 3: Initial Model Evaluation Summary

## Overview
We have successfully trained and evaluated three machine learning models to classify the financial trajectory of NCAA athletic departments. The models were trained on the `trajectory_ml_ready.csv` dataset with **12,054 rows** and **20 features**, covering the years 2016-2022.

## Model Performance
We evaluated Logistic Regression, Random Forest, and XGBoost using **SMOTE** to handle class imbalance.

| Model | Accuracy | Macro F1-Score | ROC-AUC |
| :--- | :--- | :--- | :--- |
| **Logistic Regression** | 51% | 0.44 | 0.6766 |
| **Random Forest** | 52% | 0.48 | 0.6803 |
| **XGBoost** | 52% | 0.47 | 0.6831 |

## Key Observations
1.  **Performance Baseline:** All models perform significantly better than random guessing (33%), with ROC-AUC scores around 0.68. This indicates that the features contain predictive signal, but the problem is challenging.
2.  **Class Imbalance Challenges:**
    *   **"Declining" (Class 0):** Logistic Regression struggles to identify this class (Recall 0.17), while Tree models perform better (Recall ~0.40).
    *   **"Improving" (Class 2):** This is the minority class (~14%). Models have low precision (~0.26) for this class, meaning they generate many false positives when predicting improvement.
    *   **"Stable" (Class 1):** This is the majority class. Models perform best here, with F1-scores around 0.64-0.68.
3.  **Model Comparison:**
    *   **XGBoost** achieved the highest ROC-AUC (0.6831), suggesting it ranks predictions best.
    *   **Random Forest** achieved the best balance of Precision/Recall (Macro F1 0.48).
    *   **Logistic Regression** is the least effective at capturing the minority classes, likely due to non-linear relationships in the data.

## Recommendations for Phase 4 (Optimization)
1.  **Hyperparameter Tuning:** The current models use default parameters. Tuning `max_depth`, `n_estimators`, and `learning_rate` (for XGBoost) could improve performance.
2.  **Feature Selection:** We should analyze feature importance and remove noisy features to reduce overfitting.
3.  **Threshold Moving:** Adjusting the classification threshold could help improve Recall for the "Improving" or "Declining" classes, depending on which is more critical to predict.
4.  **Advanced Ensembling:** Stacking models might yield a small performance boost.
