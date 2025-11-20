# Phase 4: Final Optimization Report

## 1. Hyperparameter Tuning Results
We performed a randomized search to optimize the **XGBoost** model using the advanced feature set.

### Best Parameters Found
*   `n_estimators`: 300
*   `max_depth`: 3 (Shallower trees prevent overfitting)
*   `learning_rate`: 0.05 (Slower learning for better generalization)
*   `subsample`: 0.7
*   `colsample_bytree`: 0.9
*   `min_child_weight`: 3

### Performance Comparison (ROC-AUC)

| Model Stage | ROC-AUC | Notes |
| :--- | :--- | :--- |
| **Baseline (Initial Features)** | 0.6831 | Standard financial metrics only |
| **Advanced (New Features)** | 0.6951 | Added Sport/Gender/Per-Athlete metrics |
| **Tuned (Optimized)** | **0.6992** | Hyperparameters optimized |

**Total Improvement:** +2.4% from baseline.

## 2. Final Model Selection
The **Tuned XGBoost** model is the best performing model.

*   **Strengths:** Best at ranking institutions by risk (highest ROC-AUC). Robust to overfitting due to conservative parameters (`max_depth=3`).
*   **Weaknesses:** Like all models in this experiment, it struggles with the "Improving" class (low precision). This suggests that "financial turnarounds" are hard to predict solely from past financial data—they likely depend on external factors (new coach, big donation, conference realignment) not in the dataset.

## 3. Key Findings for Stakeholders
1.  **Efficiency is King:** The `Efficiency Ratio` (Revenue/Expenses) is consistently the strongest predictor of future trajectory. Schools that spend efficiently today are stable tomorrow.
2.  **Division Matters:** Financial dynamics vary significantly by NCAA Division.
3.  **Gender & Sport Allocation:** How a school balances spending between Men's and Women's sports is a significant predictor of financial health, more so than just "having a football team."
4.  **Predictability Ceiling:** The models top out at ~70% ROC-AUC. This indicates a significant amount of "noise" or unmeasured variance in athletic finance (e.g., donor behavior, unexpected team success).

## 4. Recommendations
*   **Deploy the Tuned XGBoost model** for risk scoring.
*   **Focus on Efficiency:** Advise struggling institutions to focus on the `Efficiency Ratio` metric.
*   **Future Data Collection:** To break the 70% ceiling, collect data on **Donations/Endowments** and **Team Performance (Wins/Losses)**, as these likely drive the unexplained variance in revenue.
