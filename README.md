# **Transfer Market Value Prediction - DSA210 Project**

## **Project Overview**  

This project aims to analyze how **age, performance, injuries, and current club value** impact the **market value of professional soccer players**. By using **historical transfer data, performance metrics, and club financials**, I will build a predictive model to estimate a player's transfer market value.  

By applying data science techniques such as **exploratory data analysis (EDA), visualization, hypothesis testing, and machine learning**, I will determine how these key factors influence player valuation. The findings will help in understanding **whether clubs overvalue or undervalue players based on their performance, injuries, or club prestige**.  

---

## **Objectives**  

1. **Understand Key Factors in Player Valuation**  
   - Determine how **age, performance, injuries, and current club value** affect market value.  

2. **Build a Predictive Model**  
   - Develop a machine learning model to estimate player value based on historical transfer data.  

3. **Data-Driven Insights for Transfers**  
   - Investigate whether **players at richer clubs are valued higher, even if performance is similar**.  

4. **Apply Data Science Skills**  
   - Use Python, machine learning, and statistical analysis to extract meaningful insights from real-world soccer data.  

---

## **Motivation**  

This project combines **my passion for soccer and data science**. Here’s why it matters:  

- **Understanding Player Valuation**  
  - Player transfers involve massive financial investments, and clubs need data-driven strategies to avoid overpaying.  

- **Data-Driven Scouting**  
  - Instead of relying on traditional subjective scouting, this project introduces **an objective approach** using statistical analysis.  

- **Real-World Application of Data Science**  
  - This project allows me to apply **machine learning, data visualization, and regression techniques** to a real-world topic.  

---

## **Dataset**  

The dataset for this project consists of **historical player transfers** and **performance data**. Here’s what will be included:  

- **Player Information:**  
  - Name, nationality, position, age at transfer.  

- **Performance Metrics:**  
  - Goals, assists, minutes played, match ratings, passes completed, tackles.  

- **Injury Data:**  
  - Number of injuries, games missed, injury severity, recovery time.  

- **Current Club Data:**  
  - Club market value, league ranking, Champions League/Europa League participation.  

- **Transfer Data:**  
  - Transfer fee, previous club, new club, contract length.  

### **Data Sources**  
- **[Transfermarkt](https://www.transfermarkt.com/)** – Transfer fees, club financial data, injury history.  
- **[FBref](https://fbref.com/en/)** – Player performance statistics (goals, assists, match ratings).  
- **[FIFA Ratings Data](https://www.kaggle.com/datasets/)** – Historical FIFA ratings and attributes.  

All data will be **collected, cleaned, and processed in Python (Pandas, NumPy, and Scikit-learn)**.  

---

## **Tools and Technologies**  

To analyze and visualize the data, I will use:  

- **Python** (for data processing and modeling)  
- **Pandas & NumPy** (for data cleaning and manipulation)  
- **Matplotlib & Seaborn** (for visualizing trends and relationships)  
- **Scikit-learn & XGBoost** (for predictive modeling)  
- **GitHub** (for version control and documentation)  

---

## **Analysis Plan**  

### **1. Data Collection & Cleaning**  
- Import data from **Transfermarkt, FBref, and FIFA datasets**.  
- Handle missing values, standardize transfer fees, and preprocess numerical/categorical features.  

### **2. Data Exploration & Visualization**  
- **Scatter Plots** – Analyze age vs. market value.  
- **Heatmaps** – Show correlations between player performance and market value.  
- **Bar Charts** – Compare market values based on club ranking.  

### **3. Hypothesis Testing**  
- **Null Hypothesis (H₀):** Age, performance, injuries, and club value have no significant effect on market value.  
- **Alternative Hypothesis (H₁):** One or more of these factors significantly influence player valuation.  

### **4. Machine Learning Model**  
- **Regression Models:**  
  - Linear Regression  
  - Decision Tree  
  - Random Forest  
  - XGBoost  

- **Evaluation Metrics:**  
  - **Mean Absolute Error (MAE)**  
  - **Root Mean Squared Error (RMSE)**  

### **5. Trend Analysis & Insights**  
- Investigate how **injuries, performance streaks, and club market value** affect player values.  
- Predict **which players might be overvalued or undervalued** based on historical data.  

---

## **Example Analysis**  

1. **Age vs. Market Value:**  
   - A **scatter plot** will show whether younger players have significantly higher market values.  

2. **Injury Impact:**  
   - Compare **injured players vs. non-injured players** to see if injuries significantly reduce a player’s transfer fee.  

3. **Club Influence:**  
   - Investigate whether **players at richer clubs are automatically valued higher**, even if their performance is the same as players at mid-table clubs.  

---

## **Results of the Analysis (Expected Outcomes)**  

### **Univariate Analysis**  
- **Market Value:**  
  - Histogram showing distribution of player values.  
- **Age:**  
  - Boxplot to analyze which age range is the most valuable.  

### **Bivariate Analysis**  
- **Scatter plot:** Age vs. Market Value.  
- **Heatmap:** Relationship between player performance and market value.  

### **Multivariate Analysis**  
- **Bar Chart:** Comparison of player values across different clubs.  
- **Correlation Heatmap:** Relationship between club value, injuries, and market value.  

### **Machine Learning Results (Expected)**  

| **Model**              | **Mean Squared Error (MSE)** | **R² Score**  |
|------------------------|---------------------------|---------------|
| **Linear Regression**  | **0.25**                   | **0.70**      |
| **Decision Tree**      | **0.38**                   | **0.55**      |
| **Random Forest**      | **0.30**                   | **0.65**      |
| **XGBoost**            | **0.22**                   | **0.75**      |

- **XGBoost is expected to perform the best**, as it handles non-linear relationships effectively.  

---

## **Findings (Expected Outcomes)**  

- **Younger players are likely to have higher market values**, especially under 25.  
- **Frequent injuries may decrease player market value significantly**.  
- **Players at high-value clubs may be overvalued compared to equally talented players at mid-table clubs**.  
- **Performance (goals, assists, match ratings) is expected to be the strongest predictor of market value**.  

---

## **Limitations & Future Work**  

### **Limitations**  
- Data **only includes players from top European leagues** – results may not generalize to smaller leagues.  
- Injury data might be **incomplete or inconsistent** across different seasons.  

### **Future Work**  
- Expand dataset to include **more leagues** (MLS, South American leagues, etc.).  
- Use **Deep Learning** for more advanced predictions.  
- Analyze **team-level transfers** to understand **club transfer policies**.  

---

## **Conclusion**  

This project will provide **a data-driven approach to analyzing soccer transfers**. By the end of this study, I aim to:  

- Identify the **strongest factors influencing player market value**.  
- Build an **accurate machine learning model** for player valuation.  
- Discover **if clubs are overvaluing certain players based on non-performance factors**.  

This project highlights how **data science and machine learning** can improve soccer analytics and **help clubs make better financial decisions** in the transfer market. 🚀⚽  

