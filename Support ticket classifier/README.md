# Goal
Automatically classify support tickets into:
 - High priority
 - Medium
 - Low

# Models Trained
LogisticRegression (with TF-IDF for text)
RandomForestClassifier!

# Tradeoffs
Detailed Model Performance & Error Analysis
Priority Level	Logistic Regression (TF-IDF)	Random Forest	Comparison
High Priority	80% Recall (Caught 8/10)	90% Recall (Caught 9/10)	RF captures +10% more urgency
Medium Priority	66% Recall (Caught 10/15)	73% Recall (Caught 11/15)	RF is more consistent
Low Priority	75% Recall (Caught 12/16)	87% Recall (Caught 14/16)	RF filters noise better
False Alarms	1 (Incorrectly flagged)	1 (Incorrectly flagged)	Tie
The Technical & Business Tradeoffs
1. Text (TF-IDF) vs. Structured Features
The Problem: Standard features like "User Location" or "Ticket Category" don't tell the whole story. A "Billing" ticket could be a simple question or a total payment failure.
The Text Advantage: By using TF-IDF, the model identifies high-impact tokens like "urgent," "unable to," "security," and "critical." This is the only reason we caught 90% of High-Priority tickets—the model is "reading" the frustration and technical severity in the message body.
2. Recall Sensitivity (The "Safety Net" Tradeoff)
In this system, a False Negative (missing a High-Priority ticket) means an angry customer and a potential breach of contract (SLA).
A False Positive (flagging a Low ticket as High) just means a support agent spends 2 minutes checking a ticket that wasn't actually urgent.
Conclusion: The Random Forest is a better "safety net" because its ensemble logic (multiple decision trees) is better at spotting the complex patterns that define a "High" priority ticket compared to the linear logic of Logistic Regression.
Final Decision & Implementation Strategy
Selected Model: Random Forest Classifier
I am moving forward with the Random Forest because it maximized our most important metric: High-Priority Recall.
Next Steps for Production:
Threshold Adjustment: Even though RF caught 9/10, I will look into lowering the probability threshold to catch that final 10th ticket.
Feature Engineering: I plan to add "Account Age" or "Plan Tier" (Free vs. Pro) to the model to see if we can push the Medium Priority accuracy higher without losing our grip on the High-Priority alerts.
