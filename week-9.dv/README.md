# House Sales Data Understanding, Cleaning & Feature Engineering

An Exploratory Data Analysis (EDA), data cleaning, and feature engineering project built using Python to analyze real estate valuation patterns, detect anomalies, and engineer temporal and unit valuation metrics using historical house sales data from King County, Washington, USA.

---

## 📌 Problem Statement

Real-estate valuation involves analyzing various property characteristics, including the number of bedrooms and bathrooms, living area, lot size, construction year, renovation history, and geographical location. Raw property sales data often contains missing values, invalid entries, inconsistent date formats, and extreme valuations that impact the performance of downstream predictive models. 

This project establishes a robust data preparation pipeline to clean the raw dataset, derive meaningful property features, identify unusual valuation patterns, and examine factors influencing house prices.

---

## 📁 Dataset Overview

- **Dataset Source:** Kaggle
- **Dataset Name:** King County House Sales Dataset
- **Total Records:** 21,613 property sales
- **Total Attributes:** 21 original features

### Core Features Used

| Column Name | Description |
| :--- | :--- |
| `date` | Date of property sale (string format: `YYYYMMDDTHHMMSS`) |
| `price` | Sale price of the property ($) |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `sqft_living` | Interior living area in square feet |
| `sqft_lot` | Total land area in square feet |
| `grade` | Construction and design quality grade (1–13) |
| `condition` | Overall condition of the property (1–5) |
| `yr_built` | Year the property was constructed |
| `yr_renovated` | Year of renovation (0 if never renovated) |
| `waterfront` | Binary flag indicating waterfront access (0/1) |
| `lat` / `long` | Geographical coordinates |

### Derived / Engineered Features

| Feature Name | Description | Formula / Logic |
| :--- | :--- | :--- |
| `sale_year` | Year the property was sold | Extracted from `date` |
| `sale_month` | Month the property was sold | Extracted from `date` |
| `property_age` | Age of property at the time of sale | `sale_year` - `yr_built` |
| `is_renovated` | Renovation indicator flag | `1` if `yr_renovated > 0` else `0` |
| `years_since_renovation` | Years elapsed since last renovation | `sale_year - yr_renovated` (or `property_age` if non-renovated) |
| `price_per_sqft_living` | Valuation per living square foot | `price` / `sqft_living` |
| `price_per_sqft_lot` | Valuation per lot square foot | `price` / `sqft_lot` |

---

## 🛠️ Tools & Libraries Used

- **Language:** Python 3
- **Environment:** Google Colab / Jupyter Notebook
- **Data Manipulation:** `pandas`, `numpy`
- **Data Visualization:** `matplotlib`, `seaborn`

---

## 🚀 Project Workflow & Objectives

### 1. Data Collection & Inspection
- Loaded `kc_house_data.csv` via Google Drive.
- Inspected dataset shape (`21,613 rows × 21 columns`), data types, and verified **0 missing values** and **0 duplicate records**.

### 2. Data Cleaning & Pre-processing
- **Date Parsing:** Converted string date column into standard `datetime64` objects.
- **Zero-Value Treatment:** Identified zero counts in `bedrooms` (13 properties) and `bathrooms` (10 properties), imputing them with their respective dataset medians.
- **Logical Validation:** Inspected structural anomalies (e.g., flagging the 33-bedroom property record).

### 3. Temporal Feature Engineering
- Extracted `sale_year`, `sale_month`, `sale_day`, and `sale_hour`.
- Computed `property_age` relative to sale year.
- Derived renovation history variables (`is_renovated`, `years_since_renovation`).

### 4. Unit Valuation Metrics
- Calculated `price_per_sqft_living` and `price_per_sqft_lot`.
- Ensured zero values were safely handled to avoid division errors before calculating relative land and living area metrics.

### 5. Outlier Detection (IQR Method)
- Evaluated extreme values across house prices and unit valuation metrics using the Interquartile Range (IQR) technique:
  $$\text{IQR} = Q_3 - Q_1$$
  $$\text{Upper Bound} = Q_3 + 1.5 \times \text{IQR}$$
- Identified **1,146 price outliers** exceeding the upper statistical threshold, distinguishing luxury waterfront properties from true data errors.

---

## 📊 Data Visualizations Performed

1. **Price & Living Area Histograms:** Examined distribution skewness for property pricing and living square footage.
2. **Outlier Box Plots:** Identified extreme prices, `price_per_sqft_living`, and `price_per_sqft_lot`.
3. **Bedroom Count vs. Average Price Bar Chart:** Compared mean pricing across room count configurations.
4. **Living Area vs. Price Scatter Plot:** Evaluated the linear correlation between square footage and total sale price.
5. **Annual Price Trend Bar Chart:** Analyzed price growth across sale years (2014 vs. 2015).

---

## 💡 Key Findings & Insights

- **Living Area Correlation:** `sqft_living` is the primary linear driver of property valuation.
- **Renovation Impact:** Renovated properties command a significant price premium compared to non-renovated homes of similar age.
- **Skewed Valuations:** Property prices and price-per-sqft metrics exhibit right-skewed distributions due to high-value luxury real estate.

---

## 💻 How to Run the Project

1. Open the project in **Google Colab**.
2. Mount your Google Drive:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')

3.Place kc_house_data.csv in your Drive path (/content/drive/MyDrive/file/).

4.Execute code cells sequentially to run the processing pipeline and view output charts.

👤 Author
Name: [S.Veermanikandan]
