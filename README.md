# Credit Scoring Model Fairness Analysis

![screenshot-localhost_8888-2025 04 04-13_37_35](https://github.com/user-attachments/assets/f31890b7-e101-43f7-a0a5-ebb62bd64a07)

### Overview

This project evaluates whether machine learning (ML) credit scoring models introduce more bias than traditional methods using the Give Me Some Credit dataset. It compares:

- Traditional logistic regression (interpretable scorecard)
- Random Forest
- Gradient Boosting

Key questions addressed:
- Do ML models improve predictive accuracy?
- Do they amplify biases against protected groups (e.g., minorities, women)?
- Which model offers the best balance of fairness and performance?

### Dataset

Target: SeriousDlqin2yrs (1 = default within 2 years, 0 = no default)

**Key Features Used**

- Feature Risk Impact
- RevolvingUtilizationOfUnsecuredLines (Hig)h
- TotalPastDue (engineered) (Very High)
- NumberOfTimes90DaysLate (High)
- MonthlyIncome (Medium)
- age (Low)


### Key Steps

1. Data Preparation
- Cleaning: Handles missing values, outliers, and feature engineering (e.g., TotalPastDue).
- Demographic Simulation: Generates synthetic race/gender attributes (real data lacks these due to privacy).

2. Model Training
- Traditional Scorecard: Logistic regression with score mapping (e.g., 600 base points).
- ML Models: Random Forest and Gradient Boosting, optimized for AUC-ROC.

3. Fairness Evaluation
Metrics:
- Disparate impact ratio (threshold: <0.8 indicates bias).
- Statistical tests (t-tests for score differences by demographic group).
Visualization: Score distributions, fairness gaps, and performance comparisons.

### Results Summary

- Model	Test AUC	Fairness Gap	Minority Score Gap (Δ)	Gender Score Gap (Δ)
- Traditional	0.857	0.007	-2.92*	+1.04*
- Random Forest	0.863	0.008	-3.86*	+1.30*
- Gradient Boosting	0.866	0.007	-1.63*	+0.65*
(*p < 0.05)

#### Insights:
- ML models (especially Gradient Boosting) improve accuracy without significantly increasing bias.
- All models show statistically significant disparities (minorities receive lower scores).
- No model violates regulatory thresholds (disparate impact > 0.8).

### Recommendations

1. For compliance: Use the traditional model (interpretable, similar fairness).

2. For performance: Adopt Gradient Boosting (highest AUC, smallest fairness gap).

3. Mitigate bias:
- Reweight training data for underrepresented groups.
- Apply post-processing fairness adjustments.

### Source

[Give Me Some Credit](https://www.kaggle.com/c/GiveMeSomeCredit
)

[Give Me Some Credit Dataset from Kaggle](https://www.kaggle.com/c/GiveMeSomeCredit)

https://www.kaggle.com/c/GiveMeSomeCredit
  

