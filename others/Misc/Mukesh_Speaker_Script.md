# Mukesh Ravichandran - Speaker Script
**CSCI 538 Final Project Presentation**

---

## SLIDE 1: Title Slide
**Time: ~30 seconds**

**Talking Points:**
- "Good [morning/afternoon]. I'm Mukesh Ravichandran, and this is our final project for CSCI 538."
- "We're presenting our work on predicting NCAA athletic program financial trajectories using machine learning with temporal validation."
- "I'll be covering the introduction, data overview, results, and conclusions. Abner will present our methodology, model implementation, and predictions."

---

## SLIDE 2: Problem Statement & Research Question
**Time: ~1.5 minutes**

**Talking Points:**
- "Our project addresses a critical challenge: predicting the financial trajectory of over 1,700 NCAA athletic programs."
- "This is important because athletic directors and administrators need early warning systems to allocate resources and plan for sustainability."
- "We're solving a three-class prediction problem: will a program's finances be Improving, Stable, or Declining?"
- **Research Question**: "Specifically, we ask: Can we accurately predict whether an NCAA athletic program will experience an Improving, Stable, or Declining financial trajectory using historical financial and operational data?"
- "Our approach uses temporal validation methodology for time series prediction, engineers features using only historically available information, and generates honest, actionable predictions."

---

## SLIDE 3: Why Temporal Validation?
**Time: ~1 minute**

**Talking Points:**
- "For time series prediction, models must predict the future using only past information—this is fundamental temporal causality."
- "Random train-test splits violate this principle—they allow future data to influence training on past predictions."
- "Our methodology uses temporal validation: we split data chronologically, train on past data, validate on intermediate periods, test on recent data, and predict on true future data."
- "This ensures realistic performance estimates that will hold up in production deployment."
- "This approach is supported by Bergmeir & Benítez (2012) and Tashman (2000), who established that temporal validation is essential for time series forecasting."

---

## SLIDE 4: Data Overview
**Time: ~1 minute**

**Talking Points:**
- "Our data comes from the NCAA Equity in Athletics Disclosure Act database—EADA requires all institutions to report annual financial and participation data."
- "We have 17,220 total records from 1,722 institutions spanning 10 years, from 2014 to 2023."
- "The original dataset had 580 features, but through careful feature engineering, we distilled this down to 14 historically-derived features."
- "Our target variable is Financial Trajectory: Improving means revenue is up and expenses are controlled, Stable means no significant change, and Declining means revenue is down or expenses are outpacing revenue."

**[TRANSITION TO ABNER]**: "Now I'll turn it over to Abner, who will explain our temporal validation methodology, feature engineering, and model selection."

---

## SLIDE 8: Results - Model Performance
**Time: ~1.5 minutes**

**Talking Points:**
- "We evaluated our models on a 2022 holdout test set—this was the first and only time we used this data for evaluation."
- "Our best performing model was Logistic Regression, achieving 57.3% accuracy with a weighted F1 of 0.563 and macro F1 of 0.487."
- "Random Forest achieved 54.6% accuracy, and XGBoost achieved 53.7%."
- "While these numbers may seem modest, they represent genuine predictive value—I'll show you why in the next slide."

---

## SLIDE 9: Results - Baseline Comparison
**Time: ~1.5 minutes**

**Talking Points:**
- "The question is: Is 57.3% good? Let's put it in context."
- "Random guessing for a three-class problem would give us 33.3% accuracy."
- "A most-frequent-class baseline—always predicting 'Stable'—achieves only 28.3% accuracy."
- "Our model at 57.3% represents a 29 percentage point improvement over this baseline."
- "For a challenging three-class financial prediction problem, this demonstrates genuine predictive value."
- "Most importantly, this is honest accuracy that stakeholders can trust—we're not inflating performance with unrealistic splits."

---

## SLIDE 10: Results - Visualizations
**Time: ~1 minute**

**Talking Points:**
- "Our visualizations tell a comprehensive story of model performance."
- "Confusion matrices show us per-model performance breakdown—where each model succeeds and where it struggles."
- "The model comparison chart provides side-by-side accuracy comparison across all three algorithms."
- "Feature importance analysis reveals which of our 14 features are most predictive."
- "And the temporal split diagram visualizes how we divided our data chronologically."

---

## SLIDE 14: Conclusions
**Time: ~2 minutes**

**Talking Points:**
- "Let me summarize what we accomplished."
- "We developed a complete machine learning system for financial trajectory prediction."
- "We implemented temporal validation methodology for realistic evaluation—this ensures our results will hold up in production."
- "We engineered 14 historically-derived features from 10 years of data."
- "We achieved 57.3% accuracy, which is a 29% improvement over baseline—meaningful for this challenging problem."
- "We generated actionable predictions for all 1,722 institutions for 2023."
- "And we verified our methodology through 7 independent validation checks."
- **Main Takeaway**: "Temporal validation enables trustworthy predictions that stakeholders can use for real-world decision-making in financial forecasting."
- **For Athletic Administrators**: "This serves as an early warning system for financial decline. It's a decision support tool—not a replacement for judgment—but those 45 high-confidence cases we identified warrant priority attention."

**[TRANSITION TO ABNER]**: "Abner will now present our 2023 predictions and discuss limitations."

---

## SLIDE 15: References & Q&A
**Time: ~3 minutes**

**Talking Points:**
- "Before we open for questions, I want to acknowledge the key references that informed our work."
- "Bergmeir & Benítez on time series cross-validation methodology, Tashman on rolling-origin evaluation, foundational work on Random Forests by Breiman, XGBoost by Chen & Guestrin, SMOTE for class imbalance by Chawla and colleagues, and financial prediction research by Gu and colleagues."
- "Our data comes from the NCAA EADA database."
- **"Thank you for your attention. We're now happy to take questions."**

---

## TIMING SUMMARY
- **Total Time**: ~13 minutes
- **Slides 1-4**: ~4 minutes (Introduction & Data)
- **Slides 8-10**: ~4 minutes (Results)
- **Slide 14**: ~2 minutes (Conclusions)
- **Slide 15**: ~3 minutes (Q&A)

---

## KEY REMINDERS
- ✅ Speak clearly and maintain eye contact
- ✅ Emphasize the research question early
- ✅ Highlight 29% improvement over baseline
- ✅ Stress "honest accuracy" and "trustworthy predictions"
- ✅ Smooth transitions to Abner (Slides 5-7, 11-13)
- ✅ Stay within time limits—be crisp and focused

