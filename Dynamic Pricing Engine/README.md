# Dynamic Pricing Engine (E-commerce / Ride / Delivery)

# Goal

Predict the final price for a product/service based on demand, competition, and context.

# Models:
LinearRegression
RandomForestRegressor
GradientBoostingRegressor

# Metrics
Prioritizing Precision over Stability
Model	Predicted Price	Error (vs. $6.85)	Verdict
Random Forest	$6.85	$0.00	Winner: Highest Accuracy.
Linear Regression	$7.36	$0.51	Baseline: Slightly overpriced.
Gradient Boosting	$9.92	$3.07	Outlier: Aggressively overpriced.

# TradeOffs 
MAE vs R²

MAE (Mean Absolute Error) vs. R²: In pricing, we prioritize MAE because we need to know the actual dollar amount we are off by. A high R² is useless if the model consistently misses the mark by $2.00, as that error directly erodes profit margins or drives customers away.
Overpricing vs. Underpricing: This is the "Sweet Spot" challenge. Overpricing (like Gradient Boosting at $9.92) creates a high profit per sale but kills volume because customers switch to competitors. Underpricing move units but leaves "money on the table," potentially leading to a net loss after operating costs.
Model Accuracy: Since the Random Forest predicted $6.85—the closest value to the actual historical final price, it proved it can navigate complex market variables better than the simpler Linear model or the over-aggressive Boosting model.

# Final Decision
I am selecting the Random Forest Regressor for production.
It achieved the lowest MAE, meaning it is the most reliable at hitting the "Sweet Spot." By accurately predicting the $6.85 price point, it maximizes revenue without crossing the threshold that triggers customer churn. It successfully balances the need for competitive pricing with the necessity of maintaining healthy profit margins.