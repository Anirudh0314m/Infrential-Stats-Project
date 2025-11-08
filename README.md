

#  Predictive Modeling Case Study: Extramarital Affairs Prediction

**Course:** *Inferential Statistics and Predictive Analytics (21AIC401T)*

This project applies predictive modeling techniques, model validation, and deployment principles to the **Fair Extramarital Affairs Dataset**. The goal is to build, compare, and operationalize a robust classification model that identifies key factors influencing the likelihood of an extramarital affair.

---

##  1. Project Objective and Key Findings

###  **Objective**

To move beyond initial inferential analysis (T-tests, ANOVA) and develop a reliable **Logistic Regression** model for predicting the binary outcome *(had_affair = Yes/No)*.
The project validates model generalization using rigorous data partitioning and comparison against a rule-based model.

###  **Key Findings**

| **Metric**   | **Selected Model: Logistic Regression**           |
| ------------ | ------------------------------------------------- |
| **AUC-ROC**  | 0.7272 *(Superior discriminatory power)*          |
| **F1 Score** | 0.4609 *(Better balance of precision and recall)* |

**Conclusion:**
The Logistic Regression model was selected. Its performance indicates that the relationship between key factors (e.g., marriage satisfaction) and the probability of an affair is strongly **linear in the log-odds space**.

**Primary Driver:**

* **Marriage Satisfaction (rate_marriage)** is the most significant predictor.

---

##  2. Methodology Overview (5-Step Framework)

The analysis follows the **five-step framework** mandated by the course assignment:

### **Step 1: Data Preparation and EDA**

* **Data Source:** Fair Extramarital Affairs Dataset (N = 6366)
* **Target Variable:** `had_affair` *(Binary: 1 = Yes, 0 = No)*
* **Preprocessing:**

  * One-Hot Encoding for categorical features
  * Removed the source variable `affairs` to prevent data leakage
* **Validation Setup:**

  * 80/20 **Stratified Train-Test Split** to handle class imbalance (~25% positive class)
* **EDA Insights:**

  * Inverse relationship between `rate_marriage` and affair likelihood
  * Longer `yrs_married` duration observed among positive class individuals

---

### **Step 2: Model Development and Rule Induction**

* **Model:** Decision Tree Classifier (CART) — used as an equivalent to the CHAID Rule Induction algorithm.
* **Purpose:** Extract interpretable rules for high-risk profiles.
* **Key Rule:**

  * A **low Marriage Satisfaction Rating (≤ 2.5)** is the primary criterion predicting a positive affair outcome.

---

### **Step 3: Model Comparison and Evaluation**

* **Models Compared:**

  * Logistic Regression (Linear Baseline)
  * Decision Tree (CART) (Rule-Based)
* **Selection:**

  * Logistic Regression achieved **superior AUC-ROC** and **F1-Score**, proving its effectiveness despite its simplicity.

---

### **Step 4: Model Deployment and Updating**

* **Deployment:**

  * Final Logistic Regression model serialized using **joblib** for integration into a real-time scoring API.
* **Monitoring:**

  * Continuous tracking of **AUC-ROC** and **F1 Score** to detect model drift.
* **Updating Strategy:**

  * Full retraining every **6–12 months** using new data to counter concept drift due to the dataset’s age.

---

##  3. Repository Contents

| **File / Folder**                   | **Description**                                                              |
| ----------------------------------- | ---------------------------------------------------------------------------- |
| `README.md`                         | This document                                                                |
| `predictive_analysis.py`            | Primary source code (data prep, model training, rule extraction, evaluation) |
| `fair_affairs_cleaned.csv`          | Pre-processed dataset used for modeling                                      |
| `eda_satisfaction_bar.png`          | Bar chart illustrating affair rate vs. marriage satisfaction                 |
| `eda_yrs_married_density.png`       | Density plot showing yrs_married distribution by affair status               |
| `final_affair_prediction_model.pkl` | Serialized model file for deployment simulation                              |

---

##  4. Environment and Setup

### **Required Libraries**

* `pandas`
* `numpy`
* `scikit-learn`
* `statsmodels`
* `matplotlib`
* `seaborn`
* `joblib`

### **Running the Project**

1. **Clone the Repository**

   ```bash
   git clone <repository-url>
   cd extramarital-affairs-prediction
   ```

2. **Install Dependencies**

   ```bash
   pip install pandas numpy scikit-learn statsmodels matplotlib seaborn joblib
   ```

3. **Run the Main Script**

   ```bash
   python predictive_analysis.py
   ```

4. **View Results**

   * Model outputs, EDA visuals, and serialized files will be generated automatically in the project directory.

---

##  5. Conclusion

The study successfully demonstrates the end-to-end application of **Predictive Modeling** techniques, from data cleaning and exploratory analysis to model training, evaluation, and deployment.

The **Logistic Regression model** not only outperformed the rule-based alternative but also provided interpretable insights into behavioral predictors of extramarital affairs — with **marriage satisfaction** emerging as the most influential factor.

---

**Thank you for reviewing the Predictive Modeling Case Study.**


