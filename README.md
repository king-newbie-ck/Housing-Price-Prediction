# House Price Prediction: Data Cleaning, Modeling & Visualization

A comprehensive end-to-end data science project focused on transforming raw, messy housing data into clean data, performing exploratory visual analysis, and training a predictive machine learning model.

## 📌 Project Overview
Real-world data is rarely clean. This project works with an intentionally flawed dataset containing missing values, duplicates, outliers, and messy text entries to simulate an authentic data engineering and analytics workflow.

### The Dataset (`house_prices.csv`)
* **Size:** 532 rows across 6 Indian cities.
* **Features:** Area, Bedrooms, Bathrooms, Age, City, Furnishing, Parking, MainRoad, Price.
* **Flaws Addressed:** 
  * 12 exact duplicate rows.
  * 28 missing `Bathrooms` entries, 21 missing `Furnishing` entries.
  * Inconsistent text casing (`Furnished`, `furnished`, `FURNISHED`, ` Furnished `).
  * Mixed Boolean inputs (`Y`, `yes`, `YES`).
  * 6 extreme price outliers.

---

## 🛠️ The Data Pipeline

### Part 1: Data Cleaning & Preprocessing
* **Inspection:** Assessed data integrity via `.head()`, `.info()`, and missing/duplicate aggregations.
* **Deduplication:** Dropped exact copies using `.drop_duplicates()`.
* **Text Standardization:** Applied `.str.strip().str.title()` to collapse duplicate categorical variants into structured classes.
* **Imputation:** Filled numerical gaps with column medians (robust against outliers) and categorical gaps using the column mode.
* **Outlier Removal:** Used the Interquartile Range (IQR) method to eliminate entries sitting further than 1.5× the IQR beyond the central 50% distribution.

### Part 2: Exploratory Data Visualization
Using `Matplotlib` and `Seaborn`, the following analysis visuals were generated:
1. **Histogram of Price:** Evaluates overall price distribution and density.
2. **Box Plot (Price by City):** Captures geographic variance and localized spreads across the 6 Indian cities.
3. **Scatter Plot (Area vs Price):** Visualizes structural relationships and scales between pricing and real estate size.
4. **Correlation Map (Heatmap):** Explores multi-collinearity and linear relationships between numeric vectors.
5. **Bar Chart (Average Price by Furnishing):** Tracks how furnishing states skew average listing values.

### Part 3: Predictive Machine Learning
* **Categorical Encoding:** Converted non-numeric categorical attributes (`City`, `Furnishing`, `MainRoad`) into numeric structures using `pd.get_dummies()`.
* **Data Splitting:** Held back an independent 20% test partition via `train_test_split()` for unbiased evaluation.
* **Model Training:** Fit a **Linear Regression** model to map dependencies between property attributes and valuations.

---

## 📈 Performance & Evaluation

The model demonstrates high explanatory predictive capabilities, capturing roughly **95.1%** of pricing variation.

| Metric | Value | Interpretation |
| :--- | :--- | :--- |
| **R² Score** | **0.951** | The model explains 95.1% of the variation in housing prices. |
| **Mean Absolute Error (MAE)** | **₹952,021** | On average, predictions deviate from actual values by ~₹9.52 Lakhs. |
| **Root Mean Squared Error (RMSE)** | **₹1,231,689** | Standard deviation of the residuals, penalizing larger errors. |

### Diagnostic Metrics
* **Actual vs. Predicted Plot:** Evaluated data points closely hug the perfect diagonal line, verifying strong fit accuracy.
* **Residual Plot:** Errors distribute randomly around zero without visible patterns, confirming linear modeling assumptions hold true.

## Documents Added
House_Price_Prediction.ipynb
house_prices.csv

## Charts Included in this Project
1. Price Distribution Chart
   Image = chart1_price_distribution.png
2. Price By City
   Image - chart2_price_by_city.png
3. Area vs Price
   Image = chart3_area_vs_price.png
4. Correlation
   Image - chart4_clustermap.png
5. Average Price by Furnishing
   Inage - chart5_avg_price_by_furnishing.png
   

---
