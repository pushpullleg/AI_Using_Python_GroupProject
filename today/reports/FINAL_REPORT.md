# NCAA Financial Trajectory Classification - Final Project Report

## 1. Executive Summary
This project developed a machine learning model to predict the future financial trajectory ("Improving", "Stable", or "Declining") of NCAA athletic departments. Using a dataset of over 12,000 annual reports from 2016-2022, we engineered advanced features capturing sport-specific economics and gender allocation.

**Key Result:** The final XGBoost model achieves an **ROC-AUC of 0.70**, successfully identifying key drivers of financial stability such as operational efficiency and gender spending balance.

## 2. Problem Statement
NCAA athletic departments face significant financial volatility. Predicting whether a program is on a path to financial distress ("Declining") or growth ("Improving") allows for proactive management.

*   **Objective:** Classify schools into three trajectories based on future revenue/expense trends.
*   **Target Variable:**
    *   **Improving:** Revenue Growth > 3% AND Expenses growing slower than Revenue.
    *   **Declining:** Revenue shrinking OR Expenses growing >3% faster than Revenue.
    *   **Stable:** Status quo.

## 3. Data Processing & Feature Engineering
We processed the raw EADA dataset to meet the coursework requirement of >10,000 rows and >10 features.

### Key Features Created
1.  **Financial Trends:** 2-year CAGR and 1-year growth rates for Revenue and Expenses.
2.  **Efficiency Metrics:** `Efficiency_Mean_2yr` (Revenue / Expenses ratio).
3.  **Volatility:** Standard deviation of financial metrics over a rolling window.
4.  **Advanced "Athletic" Features:**
    *   **Gender Balance:** `Mens_Expense_Share`, `Womens_Expense_Share`.
    *   **Sport Specifics:** `Football_Revenue_Share`, `Basketball_Revenue_Share`.
    *   **Operational:** `Revenue_Per_Athlete`, `Total_Athletes`.

## 4. Modeling Approach
We evaluated multiple algorithms (Logistic Regression, Random Forest, XGBoost) and addressed class imbalance using SMOTE.

### Model Evolution
| Phase | Model | Features | ROC-AUC | Key Insight |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline** | Logistic Regression | Basic Financials | 0.53 | Linear models failed to capture complexity. |
| **Intermediate** | Random Forest | Basic Financials | 0.68 | Non-linear models performed significantly better. |
| **Advanced** | XGBoost | + Sport/Gender Features | 0.695 | Domain-specific features added predictive power. |
| **Final** | **Tuned XGBoost** | Optimized Params | **0.70** | Hyperparameter tuning squeezed out max performance. |

## 5. Key Findings
1.  **Efficiency is Paramount:** The ratio of Revenue to Expenses is the single strongest predictor of future trajectory.
2.  **Context Matters:** The "Division" a school belongs to fundamentally changes its financial dynamics.
3.  **Gender Allocation Signal:** The proportion of budget allocated to men's vs. women's sports is a significant predictor, likely acting as a proxy for Title IX compliance status or institutional priorities.

## 6. Deployment
The final model has been saved as `final_trajectory_model.joblib`. A prediction script `predict_trajectory.py` allows users to query any school to assess its risk profile.

## 7. Future Work
*   **External Data:** Incorporate endowment data and team win/loss records.
*   **Text Analysis:** Analyze the text of financial footnotes for warning signs.
*   **Time-Series Deep Learning:** Use LSTM networks if longer historical sequences become available.
