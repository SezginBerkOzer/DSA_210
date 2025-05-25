# Transfer Market Value Prediction Project
# Author: Sezgin Berk Özer – Sabancı University
# Term Project – DSA210 Spring 2024/2025

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import ttest_ind
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score, mean_squared_error, mean_absolute_error

# ------------------------
# Data Loading & Merging
# ------------------------

players = pd.read_csv("players.csv")
transfers = pd.read_csv("transfers.csv")
stats = pd.read_csv("player_stats.csv")

# Merge datasets on player_id
df = players.merge(stats, on="player_id").merge(transfers, on="player_id")
df = df.dropna(subset=["age", "custom_rating", "transfer_fee"])

# ------------------------
# Exploratory Data Analysis
# ------------------------

# 1. Rating vs Transfer Fee
plt.figure(figsize=(8, 5))
sns.scatterplot(x="custom_rating", y="transfer_fee", data=df)
plt.title("Player Rating vs Transfer Fee")
plt.xlabel("Custom FIFA Rating")
plt.ylabel("Transfer Fee (EUR)")
plt.grid(True)
plt.tight_layout()
plt.savefig("rating_vs_transfer_fee.png")
plt.show()

# 2. Age vs Transfer Fee
plt.figure(figsize=(8, 5))
sns.scatterplot(x="age", y="transfer_fee", data=df)
plt.title("Age vs Transfer Fee")
plt.xlabel("Age")
plt.ylabel("Transfer Fee (EUR)")
plt.grid(True)
plt.tight_layout()
plt.savefig("age_vs_transfer_fee.png")
plt.show()

# 3. Correlation Matrix
corr = df[["custom_rating", "age", "transfer_fee"]].corr()
plt.figure(figsize=(6, 4))
sns.heatmap(corr, annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Correlation Matrix")
plt.tight_layout()
plt.savefig("correlation_matrix.png")
plt.show()

# ------------------------
# Hypothesis Testing
# ------------------------

# Hypothesis 1: Higher ratings → higher fees
high_rating = df[df["custom_rating"] >= df["custom_rating"].median()]
low_rating = df[df["custom_rating"] < df["custom_rating"].median()]
t_stat1, p_val1 = ttest_ind(high_rating["transfer_fee"], low_rating["transfer_fee"], alternative='greater')

print("Hypothesis 1 – Rating:")
print("T-statistic:", t_stat1)
print("P-value:", p_val1)

# Hypothesis 2: Younger players → higher fees
young = df[df["age"] <= df["age"].median()]
old = df[df["age"] > df["age"].median()]
t_stat2, p_val2 = ttest_ind(young["transfer_fee"], old["transfer_fee"], alternative='greater')

print("\nHypothesis 2 – Age:")
print("T-statistic:", t_stat2)
print("P-value:", p_val2)

# ------------------------
# Machine Learning
# ------------------------

# Features and Target
X = df[["custom_rating", "age"]]
y = df["transfer_fee"]

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Linear Regression
lr = LinearRegression()
lr.fit(X_train, y_train)
y_pred_lr = lr.predict(X_test)

# Random Forest
rf = RandomForestRegressor(random_state=42)
rf.fit(X_train, y_train)
y_pred_rf = rf.predict(X_test)

# Evaluation Function
def evaluate(y_true, y_pred, model_name):
    print(f"\n{model_name} Performance:")
    print("R² Score:", r2_score(y_true, y_pred))
    print("MAE:", mean_absolute_error(y_true, y_pred))
    print("RMSE:", mean_squared_error(y_true, y_pred, squared=False))

# Evaluate models
evaluate(y_test, y_pred_lr, "Linear Regression")
evaluate(y_test, y_pred_rf, "Random Forest Regressor")

# Plot: Actual vs Predicted (Random Forest)
plt.figure(figsize=(6, 6))
plt.scatter(y_test, y_pred_rf, alpha=0.6)
plt.plot([y.min(), y.max()], [y.min(), y.max()], 'r--')
plt.xlabel("Actual Transfer Fee")
plt.ylabel("Predicted Transfer Fee")
plt.title("Actual vs Predicted Transfer Fee (Random Forest)")
plt.grid(True)
plt.tight_layout()
plt.savefig("actual_vs_predicted_rf.png")
plt.show()
