# 📱 Used Device Price Prediction (ReCell Project)

A machine learning project that predicts the normalized resale price of used and refurbished mobile devices. Built for **ReCell**, this project supports dynamic pricing strategies using linear regression and data-driven insights.

---
![Devices](https://github.com/user-attachments/assets/f5ac57a5-26ca-4856-8bc0-f701a6773c80)
---
## 📌 Table of Contents

- [Business Context](#business-context)
- [Problem Statement](#problem-statement)
- [Dataset Overview](#dataset-overview)
- [Project Objectives](#project-objectives)
- [Approach & Workflow](#approach--workflow)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Modeling](#modeling)
- [Evaluation](#evaluation)
- [Key Insights & Recommendations](#key-insights--recommendations)
- [Technologies Used](#technologies-used)
- [Author](#author)

---

## Business Context

The used and refurbished mobile device market is growing rapidly, with an estimated global worth of over $50 billion. Consumers are increasingly opting for cost-effective devices that retain quality. The impact of the COVID-19 outbreak may further boost this segment as consumers cut back on discretionary spending and buy phones and tablets only for immediate needs.
ReCell, a tech startup, aims to tap into this market by building a pricing engine to predict the value of used devices based on their features and condition.

---

## Problem Statement

> Given a dataset of used and refurbished devices, **Analyze** the data provided and **build** a linear regression model to predict the price of a used phone/tablet and **identify** factors that significantly influence it

---

## Dataset Description

The data contains the different attributes of used/refurbished phones and tablets. The detailed data dictionary is given below:

- `brand_name`: Name of manufacturing brand
- `os`: Operating Sytem on which the device runs
- `4g`: Whether 4G is available or not
- `5g`: Whether 5G is available or not
- `screen_size`: Size of the screen in cm
- `main_camera_mp`: Resolution of the rear camera in megapixels
- `selfie_camera_mp`: Resolution of the front camera in megapixels
- `ram`: Amount of RAM in GB
- `int_memory`: Amount of internal memory (ROM) in GB
- `battery`: Energy capacity of the device battery in mAh
- `weight`: Weight of the device in grams
- `release_year`: Year when the device model was released
- `days_used`: Number of days the used/refurbished device has been used
- `normalized_new_price`: Normalized price of a new device of the same model in euros
- `normalized_used_price`: Normalized price of the used/refurbished device in euros ~ *(Target Variable)*

---

## Project Objectives

- Understand the relationship between device specs and resale price
- Handle missing values and outliers effectively
- Build a predictive model using Linear Regression
- Evaluate model performance with appropriate metrics
- Identify features that influence used prices
- Make business-driven recommendations for ReCell

---

## 🔄 Approach & Workflow

1. **Data Cleaning**  
   - Group-wise imputation for missing values  
   - Outlier detection using IQR and boxplots  

2. **Exploratory Data Analysis (EDA)**  
   - Distribution of prices  
   - Correlation heatmap  
   - Groupby summaries by brand, OS, 5G, etc.  

3. **Feature Engineering**  
   - `device_age = 2021 - release_year`  
   - One-Hot Encoding for `brand_name`, `os`, `4g`, `5g`

4. **Model Building**  
   - Linear Regression with train/test split  
   - Performance evaluation using R² and MSE  
   - Coefficient interpretation

---

## Exploratory Data Analysis (EDA)

- Devices with **higher RAM**, **newer release years**, and **5G support** tend to retain better value.
- `days_used` negatively correlates with price (expected depreciation).
- iOS devices have a consistently **higher average resale value** than Android or others.
- Significant price drops seen for devices with small battery or no 4G/5G support.

---

## Modeling

- **Model Used:** Linear Regression
- **Train-Test Split:** 80/20
- **Feature Encoding:** One-Hot Encoding
- **Target:** `normalized_used_price`

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
```

## Evaluation

| Metric | Value    |
|--------|----------|
| R²     | **0.8356** |
| MSE    | **0.0533** |

✅ The model explains **83.56% of the variance** in used prices.  
✅ Error is low and predictions are consistent with real values.

---

## 💡 Key Insights & Recommendations

- Devices with **higher RAM**, **recent release years**, and **5G support** retain more value.
- Devices with longer `days_used` depreciate faster — this feature strongly impacts the model.
- iOS devices consistently have a **higher resale price** than Android and others.
- Pricing strategy should prioritize:
  - Battery capacity over 3500mAh
  - Devices released within the last 2–3 years
  - Brands with high resale loyalty (e.g., Apple)

---

## 🛠 Technologies Used

- Python
- Pandas & NumPy
- Matplotlib & Seaborn
- Scikit-learn
- Jupyter Notebook

---

## 👩🏽‍💻 Author
**Eniola Hannah**  
Data Scientist | Tech Innovator  
📍 Nigeria  
🔗 [LinkedIn](https://www.linkedin.com/in/eniolahannah)  
💻 [GitHub](https://github.com/eniolahannah)

---

> 📁 *This project was built as part of a data science case study for ReCell, focused on predictive modeling and business insights.*
