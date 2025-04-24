
#  Transfer Market Value Prediction

##  Project Overview

This project investigates the key factors influencing the **transfer market value of professional football players**, using data science techniques including EDA, hypothesis testing, and regression modeling.

By analyzing variables such as **FIFA ratings, age, position, and injury history**, the project aims to determine whether these attributes significantly impact player valuation and to build a model that estimates transfer fees.

---

##  Objectives

- Explore how **performance**, **age**, **position**, and **injury records** affect player valuation.
- Conduct **exploratory data analysis** and **statistical hypothesis testing**.
- Build a **linear regression model** to predict transfer fees.
- Gain hands-on experience with real-world data science workflows.

---

##  Datasets Used

| File Name             | Description                                         |
|------------------------|-----------------------------------------------------|
| `players.csv`          | Player demographic info (name, birthdate, etc.)     |
| `transfers.csv`        | Historical transfers and market values              |
| `appearances.csv`      | Player performance stats (goals, assists, minutes)  |
| `dataset.csv`          | Injury history (number of days missed)             |
| `player_stats.csv`     | FIFA-based skill ratings (e.g., passing, dribbling) |
| `clubs.csv`            | Club ID and matching info                          |

---

##  Data Analysis

### 🔍 Exploratory Data Analysis (EDA)
- **Scatter Plot**: FIFA Rating vs Transfer Fee
- **Bar Chart**: Effect of injury (>30 days) on average transfer fee
- **Correlation Heatmap**: `rating`, `age`, `injury`, and `transfer_fee`

###  Hypothesis Testing
- **Injury Effect:** Does injury duration significantly reduce player value?
- **Age Effect:** Do younger players command significantly higher fees?

###  Machine Learning Model
- **Model Used:** Linear Regression
- **Features:** `custom_rating`, `age`, `position` (encoded)
- **Performance:**
  - R² Score: **0.032**
  - RMSE: **€6.59 million**

> The model reveals that FIFA-based performance and position slightly influence transfer values, but market value depends on many unobserved variables.

---

##  Tools and Technologies

- **Python (Pandas, NumPy)** – Data wrangling and preprocessing  
- **Seaborn & Matplotlib** – Visualization  
- **Scikit-learn** – Modeling and evaluation  
- **Jupyter Notebook** – Interactive development  
- **GitHub** – Version control and documentation

---

##  Conclusion

- Players with higher **FIFA ratings** tend to have higher transfer values.
- **Injury history** (especially >10 days) is associated with **lower market value**.
- **Age** did not show statistically significant effect in this dataset.
- The model achieved basic predictive capabilities, but further improvements are needed.

---

##  Future Work

- Apply **Random Forest or XGBoost** for improved non-linear modeling.
- Integrate **club-level financial data** and **player contract information**.
- Use **log-transformed target variable** to reduce outlier impact.
