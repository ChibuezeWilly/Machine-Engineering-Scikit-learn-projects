Project Strategy: Prioritizing Recall to Mitigate Revenue Loss
Goal: Develop an early-warning system to identify high-risk customers before they churn.
Model Comparison & Performance Metrics
Metric	Logistic Regression	Random Forest Classifier	Winner
Accuracy	93%	95%	Random Forest
Recall (Churn Class)	94%	88%	Logistic Regression
Actual Churners Caught	17 / 18	16 / 18	Logistic Regression
False Positives	3	1	Random Forest
The Tradeoff Analysis
While the Random Forest model achieved higher overall Accuracy (95%), it struggled with the minority class, missing 2 out of 18 actual churners. In a business context, these False Negatives represent lost revenue and missed opportunities for retention.
Conversely, the Logistic Regression model achieved a superior Recall of 94%. It successfully identified 17 out of 18 churning customers. While it produced 3 False Positives (flagging safe customers as at-risk), the cost of sending an unnecessary retention offer is significantly lower than the cost of losing a customer entirely.
Final Decision: Production Selection
I have selected the Logistic Regression model for production. In churn forecasting, Recall is the primary KPI because the goal is to capture as much risk as possible. By correctly identifying nearly all at-risk customers, this model maximizes the effectiveness of our retention strategies and provides the highest protection for company revenue.
