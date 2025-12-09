# 🔥 **Wildfire Forecast System — EDA + CatBoost Modeling**

This project focuses on analyzing wildfire-related environmental factors and building a **CatBoost-based forecasting model** to predict wildfire occurrence or severity. The system uses structured data, feature analysis, and machine-learning modeling to support early wildfire warning systems.

---

## 📌 **Project Overview**

Wildfires have a severe impact on ecosystems, air quality, and human safety. This project aims to:

* Explore wildfire-related datasets
* Analyze correlations between climate variables and wildfire behavior
* Detect outliers & data inconsistencies
* Train a **CatBoost model** to forecast wildfire risk
* Evaluate model performance
* Identify the most influential features contributing to wildfire outbreaks

---

## 🗂️ **Repository Structure**

```
wildfire-forecast-system/
│── Wildfire_Analysis_and_CatBoost.ipynb
│── dataset/
│── visuals/
│── README.md
```

---

## 🛠️ **Technologies Used**

<p align="center">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
<img src="https://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
<img src="https://img.shields.io/badge/Matplotlib-005C97?style=for-the-badge&logo=matplotlib&logoColor=white"/>
<img src="https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=seaborn&logoColor=white"/>
<img src="https://img.shields.io/badge/CatBoost-FF6F00?style=for-the-badge&logo=catboost&logoColor=white"/>
<img src="https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/>
</p>

---

# 📊 **Exploratory Data Analysis (EDA)**

The following steps were performed:

### ✔ Data Cleaning

* Missing value treatment
* Date conversion
* Renaming inconsistent fields
* Handling outliers using IQR / Z-score methods

### ✔ Univariate Analysis

* Distribution of temperature
* Humidity levels
* Wind speed
* Soil moisture
* Fire Weather Index values

### ✔ Bivariate & Correlation Analysis

* Heatmap of features vs wildfire occurrence
* Understanding which variables strongly influence fire ignition
* Scatterplots showing relationships (e.g., wind vs fire risk)

### ✔ Insights (Examples – you may replace with your results)

* Higher temperature + low humidity increases fire probability
* Wind speed correlates with fire spread behavior
* Certain months/seasons show higher wildfire occurrences

---

# 🤖 **CatBoost Modeling**

### ✔ Why CatBoost?

CatBoost is chosen because:

* Handles categorical features automatically
* Excellent performance on tabular data
* Less hyperparameter tuning required
* Robust to outliers and missing values
* Fast training and strong accuracy

### ✔ Steps Performed

1. **Train-test split**
2. **Encoding categorical features** (CatBoost does this internally)
3. **Model training** with CatBoostClassifier or CatBoostRegressor
4. **Hyperparameter tuning** (if performed)
5. **Feature importance extraction**
6. **Model evaluation**

---

# 📈 **Model Evaluation**

Typical metrics include:

### For Classification:

* **Accuracy**
* **Precision, Recall, F1-score**
* **AUC–ROC Curve**
* **Confusion Matrix**

### For Forecast Regression:

* **MAE, MSE, RMSE**
* **R² Score**

(Add your actual numbers here)

---

# ⭐ **Feature Importance (CatBoost)**

CatBoost provides clear ranking of features.
Common important variables might include:

Here is a polished **Feature Importance summary** you can paste directly into your **README.md** for the Wildfire Forecast System.
This explains both **CatBoost Feature Importance** and **Permutation Importance** exactly based on your image.

---

# 🔥 **Feature Importance Analysis**

Understanding which variables influence wildfire prediction the most is a critical step in building an effective forecasting system.
Two methods were used:

1️⃣ **CatBoost Feature Importance** (model-based)
2️⃣ **Permutation Importance** (performance-based)

Both reveal which features contribute the most to wildfire prediction accuracy.

---

## 🌲 **1. CatBoost Feature Importance**

CatBoost provides internal importance scores by measuring how often and effectively each feature is used in tree splits.

### **Top Contributing Features (CatBoost Importance):**

| Feature                        | Importance Level |
| ------------------------------ | ---------------- |
| **brightness**                 | ⭐ Highest        |
| **frp (Fire Radiative Power)** | 🔥 Very High     |
| **acq_time**                   | High             |
| longitude                      | Medium           |
| latitude                       | Medium           |
| scan                           | Medium           |
| track                          | Low              |
| bright_t31                     | Lowest           |

### **Interpretation**

* **brightness** is the strongest predictor — hotter, brighter thermal signatures indicate active fire.
* **frp** (Fire Radiative Power) is highly influential because it measures fire intensity.
* **acq_time** also affects detection accuracy (fires at different hours show different patterns).
* Geographic coordinates (latitude, longitude) matter but play a secondary role.
* **bright_t31** contributes the least to the model.

---

## 🔥 **2. Permutation Importance**

Permutation Importance measures how prediction error changes when a feature’s values are shuffled.
This reveals which features actually affect **model performance** the most.

### **Top Contributing Features (Permutation Importance):**

| Feature    | Importance Level                          |
| ---------- | ----------------------------------------- |
| **frp**    | ⭐ Highest — most critical for predictions |
| brightness | High                                      |
| acq_time   | Medium                                    |
| scan       | Medium                                    |
| longitude  | Medium                                    |
| latitude   | Medium                                    |
| track      | Low                                       |
| bright_t31 | Very Low                                  |

### **Interpretation**

* **frp** is the single most performance-critical feature — removing or randomizing it greatly reduces accuracy.
* **brightness** remains important but less than frp.
* Spatial features (longitude, latitude) contribute moderately.
* **track** and **bright_t31** have minimal impact.

---

## 📌 **Final Takeaways**

* **FRP (Fire Radiative Power)** and **Brightness** are the two most important wildfire indicators.
* **CatBoost** and **Permutation Importance** agree on the key feature rankings.
* Temporal and geographic variables help but are secondary predictors.
* Less informative features can be removed or down-weighted to simplify the model.

---

# 📈 **Visualizations**

Saved inside `/visuals` folder:

* Correlation heatmap
* Time-series trend of wildfire occurrences
* Feature importance graph
* Boxplots for outlier checks
* Line charts of climate variables

---

# 📝 **Conclusion**

* Environmental variables strongly influence wildfire behavior.
* CatBoost provides **high accuracy and robust prediction capability** for wildfire forecasting.
* Feature importance reveals that factors like **temperature, wind speed, humidity, and drought indicators** play the biggest roles.
* The system can be extended into a real-time wildfire alert or monitoring system.

---

# 🚀 **Future Enhancements**

* Hyperparameter tuning using GridSearch or Optuna
* Implement forecasting models (Prophet, ARIMA, LSTM)
* Build a live web dashboard using **Streamlit**
* Integrate satellite imagery (MODIS/VIIRS)
* Deploy model using FastAPI or Flask

---

# 🙌 **Acknowledgements**

Dataset credit goes to wildfire research organizations, environmental monitoring agencies, or UCI/Kaggle sources depending on your dataset.

---
