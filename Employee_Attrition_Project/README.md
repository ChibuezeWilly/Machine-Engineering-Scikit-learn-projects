# Employee Retention: Predictive Churn Analysis

## Project Goal
The primary objective of this project is to build a reliable **Early Warning System** that predicts whether an employee is likely to **stay** or **leave** the company.

In the corporate world, unplanned attrition is expensive—costing thousands in recruitment and training for every person who leaves. This project leverages machine learning to transform HR data into actionable insights, allowing leadership to intervene before high-value talent walks out the door.

## Core Objectives
*   **Predictive Modeling**: Compare multiple classification algorithms (Logistic Regression vs. Random Forest) to identify the most accurate predictor of churn.
*   **Business Optimization**: Prioritize **Recall** to ensure that the "miss rate" for departing employees is as low as possible.
*   **Feature Insight**: Identify key drivers—such as work-life balance, salary, or tenure—that contribute most to an employee's decision to exit.

## Technical Implementation

### **Data Preparation**
*   **Preprocessing**: Leveraged `ColumnTransformer` for automated feature scaling and encoding.
*   **Algorithm Comparison**: Evaluated Logistic Regression against Random Forest to determine the best fit for this specific dataset.

### **Hyperparameter Tuning**
I utilized `GridSearchCV` to optimize the Random Forest model, evaluating performance based on Precision, Recall, and F1-Score.
*   **Findings**: The search revealed a tie in the top-ranking parameters. Both `max_depth: 10` and `max_depth: 15` (with `n_estimators: 20`) yielded identical scores.
*   **Refit Strategy**: I chose to refit the final model using **Recall** as the primary metric. In a retention context, it is more valuable to "flag" a potential leaver (even if they stay) than to miss someone who is actually walking out the door.

## The Trade-off: Model Selection
While Random Forest is a more complex ensemble method, the final evaluation via Classification Reports and Confusion Matrices favored the Logistic Regression model for production.

### **Performance Comparison**

**| Metric | Logistic Regression (Winner)**
| :--- | :--- |
|![Logistic Regression Confusion Matrix](<img width="538" height="432" alt="logistic_regression" src="https://github.com/user-attachments/assets/8a52eba3-d4d1-4d30-8fe6-1ec537277064" />
)
| **Correctly Predicted: "Stayed"** | **17 / 18** 
| **Missed Leavers (False Negatives)** | **1 (Lower Risk)** 
| **Correctly Caught: "Leaving"** | **11 / 12** 

**| Metric | Random Forest Classifier**
| :--- | :--- |
|![Logistic Regression Confusion Matrix](<img width="538" height="438" alt="random_forest_employee_project" src="https://github.com/user-attachments/assets/f2ec3412-0dc4-4949-9175-ed885c3cbe9b" />
)
| **Correctly Predicted: "Stayed"** | **16 / 18** 
| **Missed Leavers (False Negatives)** | **2 (Higher Risk)** 
| **Correctly Caught: "Leaving"** | **10 / 12** 

### **The "Why" Behind the Decision**
I selected **Logistic Regression** for production based on three critical factors:
1.  **Lower Business Risk**: It missed only 1 employee who actually left, whereas Random Forest missed 2. Minimizing False Negatives is vital for effective retention strategies.
2.  **Superior Sensitivity**: Logistic Regression correctly identified **91% (11/12)** of employees at risk, providing a more reliable warning system for HR.
3.  **Model Parsimony**: Logistic Regression is more **interpretable**. In a business setting, being able to explain *why* a model flagged an employee is often as important as the prediction itself.

## Key Takeaways
This project highlights that **higher complexity does not always equal higher business value.** By prioritizing the metric that reflects real-world impact—**Recall**—I successfully delivered a model that maximizes the opportunity for HR intervention and talent preservation.

**The Bottom Line:** This isn't just about labels; it's about helping HR departments move from reactive hiring to proactive talent management.
