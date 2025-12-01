# Abner Lusung - Speaker Script
**CSCI 538 Final Project Presentation**

---

## SLIDE 5: Temporal Validation Methodology
**Time: ~1.5 minutes**

**Talking Points:**
- "Thank you, Mukesh. I'll now walk you through how we implemented our temporal validation approach."
- "Our methodology uses chronological data splitting—we split by time, not randomly."
- **Point to diagram**: "From 2014 to 2016, we use data for lookback periods—this helps us create lag features."
- "From 2017 to 2019, we train our models—this is where patterns are learned."
- "2020 to 2021 is our validation set—we use this to tune hyperparameters."
- "2022 is our test set—this is the first and only time we evaluate final model performance."
- "And 2023 is reserved for true future predictions—we haven't seen these labels yet."
- **Key Principles**: "Temporal causality means we train only on past data. Our evaluation is realistic because we test on a future holdout set. And our 2023 predictions use only data from 2014 to 2022."

---

## SLIDE 6: Feature Engineering
**Time: ~1.5 minutes**

**Talking Points:**
- "We engineered 14 historically-derived features using only temporal information."
- "Current metrics include Efficiency Ratio, Revenue Per Athlete, and Total Athletes—these give us a snapshot of current operational efficiency."
- "One-year growth metrics capture Revenue Growth and Expense Growth over the past year."
- "Two-year trends include CAGR calculations for revenue and expenses, plus average efficiency over two years."
- "Volatility measures—we compute standard deviation of revenue and expenses over two years to capture financial stability."
- "We also include raw values: Grand Total Revenue and Grand Total Expenses."
- "And finally, Division as a categorical feature—D1, D2, D3, or Other."
- **Design Philosophy**: "All features are computed from historical data only—everything we use would be available at prediction time. These features capture financial trends, growth patterns, and operational efficiency."

---

## SLIDE 7: Model Selection
**Time: ~1 minute**

**Talking Points:**
- "We tested three algorithms: Logistic Regression, Random Forest, and XGBoost."
- "Logistic Regression used balanced class weights and the L-BFGS solver."
- "Random Forest had 100 trees with max depth of 10 and balanced sampling."
- "XGBoost used 100 estimators with max depth of 5."
- "To handle class imbalance, we used SMOTE—Synthetic Minority Over-sampling Technique—which generates synthetic examples of minority classes."
- "We also applied balanced class weights across all models."
- **Why Traditional ML?**: "With approximately 5,000 training samples, we're too small for deep learning. We also prioritized interpretability—we need to understand which features matter—and computational efficiency was important for our pipeline."

---

## SLIDE 11: 2023 Predictions
**Time: ~1.5 minutes**

**Talking Points:**
- "Using our best model—Logistic Regression—we generated predictions for all 1,722 institutions for 2023."
- "Our predictions show: 803 institutions, or 46.6%, are predicted to be Stable."
- "473 institutions, 27.5%, are predicted to be Declining."
- "And 446 institutions, 25.9%, are predicted to be Improving."
- **High-Confidence Cases**: "We identified 45 institutions with prediction confidence of 70% or higher."
- "For example, Thomas University has a 90% confidence prediction of declining trajectory."
- "University of Olivet has 89% confidence for declining."
- **Critical Point**: "These are TRUE predictions—the actual outcomes for 2023 don't exist yet. We can't verify these until 2024 data becomes available. This is what makes our work valuable—it's actionable now."

---

## SLIDE 12: Key Findings
**Time: ~1.5 minutes**

**Talking Points:**
- "Let me summarize our key findings."
- **Finding 1**: "Temporal validation produces realistic, trustworthy predictions. Our 57.3% accuracy represents genuine predictive value, and the 29% improvement over baseline demonstrates real utility."
- **Finding 2**: "Financial trajectory prediction is challenging but feasible. This is a three-class problem with inherent uncertainty, but modest accuracy is meaningful for decision support."
- **Finding 3**: "Our feature engineering successfully captures predictive signals. Just 14 features derived from historical trends are sufficient, and efficiency ratios and growth patterns are most informative."
- **Finding 4**: "Our 2023 predictions are ready for deployment. We have trajectory forecasts for all 1,722 institutions, with 45 high-confidence cases identified for priority attention."
- **Finding 5**: "Our methodology was verified through rigorous checks. Seven independent verification checks confirmed temporal integrity, and no data leakage was detected in our final pipeline."

---

## SLIDE 13: Limitations and Future Work
**Time: ~1.5 minutes**

**Talking Points:**
- "We want to be transparent about limitations."
- "External factors aren't modeled—economic conditions, policy changes, or unexpected events like COVID aren't captured."
- "Speaking of COVID, the 2020-2021 data period is impacted by pandemic disruptions, which may affect model performance."
- "Our data is self-reported through EADA filings, so data quality depends on institutional reporting accuracy."
- "And 57.3% accuracy means significant uncertainty remains—this is a decision support tool, not a crystal ball."
- **Future Work**: "We'd like to add macroeconomic indicators to capture external factors."
- "We could explore LSTM or Transformer models if we had more data."
- "An ensemble voting system combining our three models could potentially improve accuracy."
- "Most importantly, we plan to validate our 2023 predictions when 2024 data becomes available—this is true validation."
- "And we'd like to develop a real-time prediction API for practical deployment."

**[TRANSITION BACK TO MUKESH]**: "Mukesh will now present our conclusions."

---

## TIMING SUMMARY
- **Total Time**: ~8 minutes
- **Slides 5-7**: ~4 minutes (Methodology)
- **Slide 11**: ~1.5 minutes (Predictions)
- **Slides 12-13**: ~3 minutes (Findings & Limitations)

---

## KEY REMINDERS
- ✅ Point to diagrams and visualizations when speaking
- ✅ Emphasize "true predictions" for 2023
- ✅ Highlight the 45 high-confidence cases
- ✅ Be honest about limitations
- ✅ Smooth transitions to/from Mukesh
- ✅ Stay within time limits—be concise and clear

---

## QUICK REFERENCE: Slide Numbers
- **Slides 5-7**: Your methodology section
- **Slide 11**: Your predictions
- **Slides 12-13**: Your findings and limitations
- **Mukesh covers**: 1-4, 8-10, 14-15

