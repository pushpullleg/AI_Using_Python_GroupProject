# Phase 4: Advanced Feature Engineering & Modeling Results

## Overview
We enhanced the dataset by adding **sport-specific** and **gender-specific** features to capture the true "athletics" context of the financial data. We then retrained our Random Forest and XGBoost models.

## New Features Added
*   **Gender Economics:** `Mens_Revenue_Share`, `Womens_Revenue_Share`, `Mens_Expense_Share`, `Womens_Expense_Share`.
*   **Sport Specifics:** `Football_Revenue_Share`, `Football_Expense_Share`, `Basketball_Revenue_Share`, `Basketball_Expense_Share`.
*   **Operational Metrics:** `Total_Athletes`, `Male_Athlete_Share`, `Revenue_Per_Athlete`, `Expense_Per_Athlete`.

## Model Performance Comparison

| Model | Baseline ROC-AUC | **Advanced ROC-AUC** | Change |
| :--- | :--- | :--- | :--- |
| **XGBoost** | 0.6831 | **0.6951** | +1.2% |
| **Random Forest** | 0.6803 | **0.6909** | +1.0% |

**Result:** The new features provided a **measurable improvement** in model performance.

## Key Drivers (Feature Importance)
1.  **Efficiency Ratio (`Efficiency_Mean_2yr`):** Still the #1 predictor. How well a school manages its money relative to expenses is the strongest signal.
2.  **Division:** Being in a specific NCAA division (or outside the main ones) is a major factor.
3.  **Gender Spending Balance:** `Mens_Expense_Share` and `Womens_Expense_Share` emerged as top 15 predictors, proving that *how* resources are allocated between men's and women's sports impacts financial stability.
4.  **Per-Athlete Metrics:** `Expense_Per_Athlete` and `Revenue_Per_Athlete` are valuable indicators of a program's scale and "luxury" level.

## Why didn't Football Share rank higher?
Interestingly, `Football_Revenue_Share` did not appear in the very top features globally. This is likely because:
*   **Dataset Diversity:** The dataset includes ~1,700 schools. Only a small fraction (~130) are big-time D1 Football Bowl Subdivision (FBS) schools where football prints money. For the vast majority of D2/D3 schools, football is just another expense, not a revenue driver.
*   **Correlation:** The financial impact of football is likely already captured by the `Grand Total Revenue` and `Efficiency Ratio` variables.

## Next Steps
1.  **Hyperparameter Tuning:** Squeeze more performance out of XGBoost.
2.  **Segmented Modeling:** Train a model *only* on Division 1 schools to see if Football/Basketball features become dominant there.
