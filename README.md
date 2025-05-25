
#  DSA210 Project – Transfer Market Value Prediction

##  Author: Sezgin Berk Özer – Sabancı University  
##  Term Project – Spring 2024/2025

---

###  Project Objective

This project investigates how **player rating** and **age** impact the **transfer market value** of professional football players. Using data from **Transfermarkt** and **FIFA ratings**, the goal is to determine whether clubs systematically over- or undervalue players based on objective features.

---

##  Hypotheses

1.  Higher player rating → higher transfer market value  
2.  Younger players → higher transfer market value

---

##  Data Sources

| Source            | Description                            |
|-------------------|----------------------------------------|
| `transfers.csv`   | Player transfer history & fees         |
| `players.csv`     | Demographic data (age, position)       |
| `player_stats.csv`| FIFA attributes → custom performance rating |

---

##  Exploratory Data Analysis (EDA)

### 1. Player Rating vs Transfer Fee

![Performance vs Transfer Fee](rating_vs_transfer_fee.png)

> Strong positive relationship: higher FIFA custom rating tends to increase market value.

---

### 2. Age vs Transfer Fee

![Age vs Transfer Fee](age_vs_transfer_fee.png)

> Younger players (<25) generally fetch higher fees. Trend flattens after age 28+.

---

### 3. Correlation Matrix

![Correlation Matrix](correlation_matrix.png)

> Strongest correlation is between `custom_rating` and `transfer_fee`.  
> Age shows weak negative correlation with value.

---

##  Hypothesis Testing

### 1. Does higher rating lead to higher transfer fee?

- **Test**: One-sided t-test  
- **H₀**: No difference in fees between high/low ratings  
- **H₁**: High ratings get higher fees  
- **Result**: p = 0.019 → Reject H₀ 

---

### 2. Are younger players more expensive?

- **Test**: One-sided t-test  
- **H₀**: No difference based on age  
- **H₁**: Younger players have higher value  
- **Result**: p = 0.042 → Reject H₀ 

---

##  Limitations

- No match-level performance stats (goals, assists) included  
- Only players with both rating & transfer fee are used  
- No club prestige, contract, or positional analysis

---

##  Future Work

- Add positional impact (e.g. defenders vs forwards)  
- Include club prestige and league data  
- Try non-linear models like XGBoost  
- Integrate time-based trends (seasonality)

---

##  Deliverables

- [x] `README.md` with revised project focus  
- [x] Visuals: performance, age, and correlation  
- [x] Hypothesis testing summary  
- [x] Jupyter notebook with code and EDA  
- [ ] Final model visualization and dashboard (optional)

# Machine Learning: Predicting Transfer Fee using Random Forest
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import matplotlib.pyplot as plt

# Load merged dataset (should already contain custom_rating, age, transfer_fee)
df = pd.read_csv("final_dataset.csv")  # you should replace this with your merged dataframe file

# Drop missing values (if any)
df = df.dropna(subset=["custom_rating", "age", "transfer_fee"])

# Optional: log-transform transfer fee to reduce skewness
df["log_fee"] = np.log1p(df["transfer_fee"])

# Features and target
X = df[["custom_rating", "age"]]
y = df["log_fee"]

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Prediction
y_pred = model.predict(X_test)

# Inverse log transform for interpretability
y_test_original = np.expm1(y_test)
y_pred_original = np.expm1(y_pred)

# Evaluation metrics
mae = mean_absolute_error(y_test_original, y_pred_original)
rmse = mean_squared_error(y_test_original, y_pred_original, squared=False)
r2 = r2_score(y_test_original, y_pred_original)

print(f"MAE: {mae:.2f}")
print(f"RMSE: {rmse:.2f}")
print(f"R²: {r2:.2f}")

# Scatter plot: Actual vs Predicted
plt.figure(figsize=(8,6))
plt.scatter(y_test_original, y_pred_original, alpha=0.6)
plt.plot([y_test_original.min(), y_test_original.max()], 
         [y_test_original.min(), y_test_original.max()], color='red', linestyle='--')
plt.xlabel("Actual Transfer Fee")
plt.ylabel("Predicted Transfer Fee")
plt.title("Actual vs Predicted Transfer Fee")
plt.grid(True)
plt.show()

# Feature Importance
importances = model.feature_importances_
features = X.columns

plt.figure(figsize=(6,4))
plt.bar(features, importances)
plt.title("Feature Importance")
plt.ylabel("Importance Score")
plt.show()

