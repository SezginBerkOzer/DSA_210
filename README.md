
#  DSA210 Term Project – Transfer Market Value Prediction

I am a student from Sabancı University, **Sezgin Berk Özer**, and this is my DSA210 term project.  
The aim of this project is to analyze how **performance metrics, age, injuries, and club-related features** impact the **market value of professional football players**, and to develop a machine learning model that predicts transfer fees.

---

#  Contents
- [Motivation](#motivation)
- [Project Goal](#project-goal)
- [Data Sources and Preprocessing](#data-sources-and-preprocessing)
- [Data Analysis](#data-analysis)
  - [EDA](#exploratory-data-analysis)
  - [Hypothesis Testing](#hypothesis-testing)
  - [Modeling](#machine-learning-modeling)
- [Findings](#findings)
- [Limitations and Future Work](#limitations-and-future-work)

---

##  Motivation

Player transfers in football involve multi-million euro decisions. Traditional valuation relies heavily on subjective judgment, club prestige, and incomplete performance stats. This project aims to **objectively evaluate how key metrics—such as age, injuries, and rating—impact player market value**, using historical data and data science techniques.

---

##  Project Goal

- Understand the impact of **FIFA-based skill ratings, age, injury duration, and player position** on market value.
- Build a **regression model** that can predict transfer value based on player attributes.
- Explore whether players from top clubs are **overvalued** compared to equally skilled players in smaller clubs.

---

##  Data Sources and Preprocessing

###  Dataset Summary

| File Name             | Description |
|----------------------|-------------|
| `players.csv`         | Player demographic data (name, date of birth, position) |
| `transfers.csv`       | Historical transfer records and fees |
| `player_valuations.csv` | Market value time series |
| `appearances.csv`     | Performance stats (goals, assists, minutes) |
| `dataset.csv`         | Injury history (days injured per season) |
| `player_stats.csv`    | FIFA player attributes (dribbling, vision, shooting...) |
| `clubs.csv`           | Club IDs and names |

Raw `.csv` data was preprocessed using `pandas`, merged on player names and cleaned. Missing values were dropped or imputed logically (e.g., missing injury duration = 0).

---

##  Data Analysis

###  Exploratory Data Analysis

- **Scatter Plot**: Custom FIFA rating vs Transfer Fee
- **Bar Chart**: Effect of injury (30+ days) on average market value
- **Correlation Heatmap**: Check strength of relationships between rating, age, injury, and market value

###  Hypothesis Testing

- **Injury Impact**: Do injured players have significantly lower transfer fees?
- **Age Impact**: Are younger players more expensive?
  - **p-values** were used to test significance at α = 0.05
  - Result: No significant difference found for injuries or age in current dataset

---

##  Machine Learning Modeling

- **Model Used**: Linear Regression
- **Features**: `custom_rating`, `age`, `position` (one-hot encoded)
- **Target**: `transfer_fee`
- **Performance**:
  - R² Score: 0.032
  - RMSE: €6.59 million

While basic, the model demonstrates how FIFA-based metrics and player demographics affect transfer value. Further improvements are discussed below.

---

##  Findings

- **FIFA custom rating** has a **positive correlation** with transfer value.
- **Injury and age** effects were **not statistically significant** in the current sample.
- **Position encoding** slightly improved the regression model.

---

##  Limitations and Future Work

### Limitations

- **Missing or inconsistent data** across datasets (e.g., injury durations, club valuations).
- **Transfer fees** vary due to club negotiations, agent effects, or media hype—not captured here.
- Only basic linear models used—**non-linear effects are likely**.

### Future Work

- Add **club market value**, **league tier**, and **contract duration**
- Use **Random Forest/XGBoost** for better modeling
- Apply **log transformation** to reduce impact of extreme fees
- Conduct **clustering** or **classification** to group player types

---

**Thank you for reading!** Full code and analysis notebooks are available in this repository.

