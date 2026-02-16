# Bulldozer Sale Price Prediction 🚜

This project focuses on predicting the sale price of bulldozers using machine learning. The goal is to build a regression model that can accurately estimate the auction price of a piece of heavy equipment based on its usage, configuration, and historical sale data. This is a time-series problem, as the goal is to predict future prices based on past data.

---

## 📝 Problem Definition

The objective is to predict the future sale price of a bulldozer, given its characteristics and historical sales data up to 2011.

**Evaluation Metric:** Root Mean Squared Log Error (RMSLE)

---

## 📊 Data

The dataset used in this project is the **Blue Book for Bulldozers** dataset from a Kaggle competition. It contains sales data and specifications for heavy equipment.

The data is split into the following files:

- **TrainAndValid.csv** — Contains training and validation data, including bulldozer specifications and sale prices up to 2011  
- **Test.csv** — Contains test data for which predictions need to be made (post-2011 sales)

---

## ⚙️ Methodology

The project follows a structured machine learning workflow from data exploration to model tuning and evaluation.

---

### 1️⃣ Exploratory Data Analysis (EDA)

- Dataset inspected for data types, missing values, and statistics
- Outliers detected in `YearMade` column (value = 1000)
- Erroneous YearMade values replaced with median year (1995)
- SalePrice distribution found to be right-skewed
- State-wise analysis showed Florida, Texas, and California as top sales states
- Time analysis showed:
  - Highest sales in 2008–2009
  - Peak sales months: February and March

---

### 2️⃣ Feature Engineering & Preprocessing

**Date Feature Extraction**

The `saledate` column was converted to datetime and expanded into:

- saleYear  
- saleMonth  
- saleDay  
- saleDayOfWeek  
- saleDayOfYear  

Original `saledate` column was then removed.

---

**Handling Missing Values**

Numerical Columns:
- Missing values filled using median
- Additional boolean indicator columns created (e.g., `auctioneerID_is_missing`)

Categorical Columns:
- Converted to category datatype
- Encoded using category codes + 1
- Missing indicators added for each categorical feature

This approach allows the model to learn missing-value patterns.

---

### 3️⃣ Modeling and Evaluation

**Time-Based Data Split**

- Training Set → Sales before 2012  
- Validation Set → Sales in 2012  

This preserves real-world time-series behavior.

---

**Models Evaluated**

- Ridge Regression  
- Lasso Regression  
- ElasticNet  
- RandomForestRegressor  

RandomForestRegressor performed best with lowest RMSLE.

---

### 🔧 Hyperparameter Tuning

Two-stage tuning was applied:

- RandomizedSearchCV — broad parameter search
- GridSearchCV — focused fine tuning around best parameters

Final optimized model trained on full training data with `max_samples=None`.

---

## ✨ Results

The final RandomForestRegressor model demonstrated strong predictive performance.

- **Validation RMSLE:** 0.247  
- **Validation R² Score:** 0.882  

---

## 📌 Feature Importance

Top features influencing bulldozer sale price:

- YearMade — Manufacturing year  
- ProductSize — Size classification  
- fiSecondaryDesc — Secondary model descriptor  
- saleYear — Year of sale  
- fiModelDesc — Primary model descriptor  

---

## 📈 Key Takeaways

- Time-aware splitting improves realistic validation
- Median imputation works well for skewed numeric features
- Missing-value indicators improve model learning
- Tree-based ensemble models handle mixed feature types effectively
- Feature engineering from dates significantly boosts performance

---
