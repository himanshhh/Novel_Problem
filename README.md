# 📊 Crime & Property Price Analysis in Ireland

This project explores the relationship between recorded crime rates and property prices in Ireland using public datasets. The goal is to understand correlations, engineer meaningful features, and predict average property sale prices using machine learning models.

---

## 🧪 Tools & Libraries

| Category           | Libraries Used                                      |
|--------------------|-----------------------------------------------------|
| Data Manipulation  | `pandas`, `numpy`                                   |
| Visualization      | `matplotlib`, `seaborn`                             |
| Preprocessing      | `StandardScaler`, `OneHotEncoder`, `ColumnTransformer` |
| Modeling           | `RandomForestRegressor`, `GradientBoostingRegressor`, `LinearSVR` |
| Evaluation         | `mean_squared_error`, `mean_absolute_error`, `r2_score` |
| Optimization       | `Pipeline`, `GridSearchCV`, `train_test_split`     |

---

## 📁 Dataset Description

Two main datasets were merged:

- **[Recorded Crime in Ireland (Kaggle)](https://www.kaggle.com/datasets/zazaucd/recorded-crime-in-ireland)**  
  Contains crime counts by type, county, and time period.

- **[Property Price Register Ireland (Kaggle)](https://www.kaggle.com/datasets/erinkhoo/property-price-register-ireland)**  
  Contains property sale prices with details like date, property type, and location.

**Final merged dataset columns:**
- `Year`, `Quarter`, `COUNTY`
- `PROPERTY_DESC` (New or Second-Hand House/Apartment)
- `Type of Offence`, `Total_Crimes`
- `Avg_Sale_Price`

---

## 🔍 Exploratory Data Analysis (EDA)

- **Time-based Trends**:
  - Crime rates dropped sharply during COVID-19 (2019–2021).
  - Average sale prices rose significantly post-2016, peaking during 2019–2022.

- **Offence Type Analysis**:
  - Only offences with >6000 reports were visualized for better clarity.
  
- **Price Distribution**:
  - New residential units are priced higher than second-hand ones.
  - Dublin has the highest average property prices and crime rates.

- **County-Level Insights**:
  - Slight positive correlation observed between crime rate and property prices.
  - Outlier: Dublin (high in both price and crime).

---

## 🛠️ Feature Engineering

- **Class Balancing**: Upsampled minority classes in `PROPERTY_DESC`.
- **Preprocessing**:
  - Categorical variables: One-hot encoded
  - Numerical variable (`Total_Crimes`): Standardized
- **Pipeline**: Used `scikit-learn`’s `Pipeline` and `ColumnTransformer` to automate preprocessing and modeling steps.

---

## 🤖 Modeling

Three regression models were trained and optimized using `GridSearchCV`:

| Model              | Time Taken | Best Metrics (on Test Set) |
|-------------------|------------|-----------------------------|
| Random Forest      | ~28 mins   | Good RMSE & R²              |
| Gradient Boosting  | ~5 mins    | Best overall (MAE, R²)      |
| Linear SVM         | ~2 mins    | Fastest but less accurate   |

**Evaluation Metrics:**
- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R² Score

**Best Model:** ✅ Gradient Boosting Regressor — balances speed, accuracy, and variance explanation.

---

## 📈 Results Summary

- Gradient Boosting achieved the best trade-off between RMSE, MAE, and R².
- Normalized RMSE was kept below 5–10%, which is acceptable for real estate price prediction.

---

## 📌 Key Takeaways

- Property prices and crime rates show a weak but observable relationship at the county level.
- Dublin is an outlier with both high crime and high property values.
- Proper feature engineering and class balancing improve model performance significantly.

---

## 🚀 Future Improvements

- Include spatial mapping for geospatial crime vs. property pricing.
- Explore deep learning models (e.g., XGBoost, CatBoost).
- Incorporate additional features (e.g., interest rates, amenities, GDP).

---
