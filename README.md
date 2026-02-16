# Bulldozer Sale Price Prediction 🚜

This project focuses on predicting the sale price of bulldozers using machine learning. The goal is to build a regression model that can accurately estimate the auction price of heavy equipment based on usage, configuration, and historical sale data. This is a time-series problem, where future prices are predicted using past data.

---

## 📝 Problem Definition

The objective is to predict the future sale price of a bulldozer given its characteristics and historical sales data up to 2011.

**Evaluation Metric:** Root Mean Squared Log Error (RMSLE)

---

## 📊 Data

The dataset used in this project is the **Blue Book for Bulldozers** dataset from a Kaggle competition.

Files used:

- `TrainAndValid.csv` — Training and validation data
- `Test.csv` — Test data for prediction

---

## ⚙️ Methodology

### 1️⃣ Exploratory Data Analysis (EDA)

- Checked data types and missing values
- Fixed incorrect `YearMade = 1000` values → replaced with median (1995)
- Observed SalePrice distribution was right-skewed
- Top sales states: Florida, Texas, California
- Peak sales years: 2008–2009
- Peak months: February and March

---

### 2️⃣ Feature Engineering & Preprocessing

**Date Processing**
- Converted `saledate` to datetime
- Extracted:
  - saleYear
  - saleMonth
  - saleDay
  - saleDayOfWeek
  - saleDayOfYear
- Dropped original saledate column

**Missing Values**

Numerical:
- Filled with median
- Added `_is_missing` indicator columns

Categorical:
- Converted to category type
- Used category codes + 1

---

### 3️⃣ Modeling and Evaluation

**Data Split**
- Train → before 2012
- Validation → 2012

**Models Tested**
- Ridge
- Lasso
- ElasticNet
- RandomForestRegressor

**Best Model:** RandomForestRegressor

---

### 🔧 Hyperparameter Tuning

- RandomizedSearchCV
- GridSearchCV

**Final RMSLE:** 0.247

---

## ✨ Results

- **Validation RMSLE:** 0.247
- **Validation R² Score:** 0.882

---

## 📌 Feature Importance

Top predictors:

- YearMade
- ProductSize
- fiSecondaryDesc
- saleYear
- fiModelDesc

---

## 🚀 How to Use

Clone the repository:

```bash
git clone https://github.com/your-username/bulldozer-price-prediction.git
```

Open the Jupyter notebook:

```
bulldozer-price-prediction.ipynb
```

Run all cells to reproduce results.

---

## 👩‍💻 Author

Your Name Here
