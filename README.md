Predictive Modeling Case Study: Extramarital Affairs Prediction

Course: Inferential Statistics and Predictive Analytics (21AIC401T)

This project completes the Case Study Assignment by applying predictive modeling techniques, model validation, and deployment principles to the Fair Extramarital Affairs Dataset. The objective is to build, compare, and operationalize a robust classification model to identify the key factors influencing the likelihood of an extramarital affair.

1. Project Objective and Key Findings

Objective

To move beyond initial inferential analysis (T-tests, ANOVA) and develop a reliable Logistic Regression model for predicting the binary outcome (had_affair = Yes/No). The project validates model generalization using rigorous partitioning and comparison against a rule-based model.

Key Findings

Metric

Selected Model: Logistic Regression

AUC-ROC

0.7272 (Superior discriminatory power)

F1 Score

0.4609 (Better balance of precision and recall)

Conclusion

The Logistic Regression model was selected. Its performance indicates that the relationship between key factors (e.g., marriage satisfaction) and the probability of an affair is strongly linear in the log-odds space.

Primary Driver

Marriage Satisfaction (rate_marriage) is the most significant predictor.

2. Methodology Overview (5-Step Assignment Structure)

The analysis follows the five-step framework mandated by the course assignment:

Step 1: Data Preparation and EDA

Data Source: Fair Extramarital Affairs Dataset ($N=6366$).

Target Variable: had_affair (Binary: 1=Yes, 0=No).

Preprocessing: Performed One-Hot Encoding for categorical features and removed the source variable (affairs) to prevent data leakage.

Validation Setup: Applied an 80/20 Stratified Train-Test Split to handle class imbalance (approx. 25% positive class).

EDA Visuals: Confirmed the inverse relationship between rate_marriage and affair likelihood, and identified the prolonged duration of yrs_married in the positive class.

Step 2: Model Development and Rule Induction

Model: Decision Tree Classifier (CART). (Used as the equivalent of the CHAID Rule Induction algorithm.)

Purpose: To extract direct, interpretable rules for high-risk profiles.

Key Rule: The model's root split confirmed that a low Marriage Satisfaction Rating ($\leq 2.5$) is the primary criterion for predicting a positive outcome (Affair).

Step 3: Model Comparison and Evaluation

Models Compared: Logistic Regression (Linear Baseline) vs. Decision Tree (CART) (Rule-Based).

Selection: Logistic Regression achieved superior AUC-ROC and F1-Score, demonstrating its effectiveness as the optimal choice despite its simplicity.

Step 4: Model Deployment and Updating

Deployment: The final Logistic Regression model is serialized using joblib for integration into a real-time scoring API.

Monitoring: Designed a framework to continuously track performance metrics (AUC-ROC, F1 Score) to detect Model Drift.

Updating Strategy: Recommended Full Retraining every 6-12 months using new data to counter high risk of Concept Drift (given the age of the survey data). 

3. Repository Contents

This repository contains all necessary project files and outputs:

File / Folder

Description

README.md

This document.

predictive_analysis.py

Primary source code. Contains all steps: data prep, model training (LogReg, DT), rule extraction, and final evaluation.

fair_affairs_cleaned.csv

The pre-processed dataset used for modeling.

eda_satisfaction_bar.png

Bar chart illustrating affair rate vs. marriage satisfaction.

eda_yrs_married_density.png

Density plot showing yrs_married distribution by affair status.

final_affair_prediction_model.pkl

Demonstration file (serialized model saved for deployment simulation).

4. Environment and Setup

The project was executed using Python and requires the following libraries:

pandas
numpy
scikit-learn
statsmodels 
matplotlib 
seaborn
joblib


Running the Project

To replicate the analysis and generate the report outputs:

Clone the repository.

Install the required libraries: pip install pandas scikit-learn statsmodels matplotlib seaborn joblib

Run the main script: python predictive_analysis.py

Thank you for reviewing the Predictive Modeling Case Study.
