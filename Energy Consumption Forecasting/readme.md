# Energy Consumption Forecasting (Smart Buildings)

# Goal
Predict how much electricity a building will consume in the next hour/day.

# Models Trained
 - LinearRegression
 - RandomForestRegresso
 - GradientBoostingRegressor

# Metrics

This is a real-world problem. It helps companies reduce energy waste, plan usage better, and save costs.

I approached it as a regression problem and trained three different models.

Linear Regression performed the best:
R² score: 96.93%
On average, my prediction is off by: $323.74 (MAE)
RMSE: $509.96

Random Forest:
R² score: 95.91%
On average, my prediction is off by: 
$391.46 (MAE)
RMSE: $589.19

Gradient Boosting Regressor:
R² score: 94.95%
On average, my prediction is off by: 
$483.41 (MAE)
RMSE: $654.55


# TRADEOFFS
MAE vs RMSE
MAE → average error (easy to explain)
RMSE → punishes large mistakes (important for spikes)
Lag feature importance?


# FINAL DECISION
At first, I expected the more complex models like Random Forest or Gradient Boosting to perform better, but that wasn’t the case.

Linear Regression outperformed both of them.

The tradeoff here is clear. Linear Regression is simpler, faster, easier to explain, and in this case, more accurate. That tells me the relationship in the data is mostly linear, so adding complexity actually reduced performance.

Random Forest and Gradient Boosting are powerful and can capture complex patterns, but they come with more computation, more tuning, and sometimes unnecessary complexity when the data doesn’t need it. In this case, they introduced more error instead of reducing it.

So for a real production system, I would go with Linear Regression because it gives better predictions, is easier to maintain, and is more efficient.