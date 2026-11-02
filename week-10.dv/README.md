# Week 10: Advanced Visualization & Real Estate Regression Analysis

An Exploratory Data Analysis (EDA) and introductory linear regression project built using Python to analyze property pricing drivers, spatial distributions, quality grades, waterfront premiums, and unit valuations using preprocessed real estate data from King County, Washington.

---

## 📌 Project Overview

This project focuses on visual data exploration and regression modeling to evaluate property valuation factors. Using Seaborn, Matplotlib, and Scikit-Learn, the analysis examines the relationship between living area square footage, property grade, waterfront status, geographic clusters, and final sale prices.

---

## 📁 Dataset Overview

- **Input File:** `Kc_house_data_preprocessed(10).csv`
- **Total Records:** 21,613 properties
- **Total Features:** 25 columns (including preprocessed & engineered attributes)

### Primary Features Analyzed

| Column Name | Description |
| :--- | :--- |
| `price` | Target variable — Sale price of the property ($) |
| `sqft_living` | Interior living area in square feet |
| `grade` | Construction and design quality grade (1–13) |
| `waterfront` | Binary indicator for waterfront access (0 = No, 1 = Yes) |
| `lat` / `long` | Geographic coordinates (latitude & longitude) |
| `Property_Age` | Engineered age of the property at time of sale |
| `Is Renovated` | Boolean flag indicating renovation status |
| `price_per_sqft` | Price per square foot of living area |

---

## 🛠️ Tools & Libraries Used

- **Language:** Python 3
- **Environment:** Google Colab
- **Data Manipulation:** `pandas`
- **Data Visualization:** `matplotlib`, `seaborn`
- **Machine Learning:** `scikit-learn` (`LinearRegression`)

---

## 🚀 Key Analysis & Visualizations

1. **Living Area vs. Property Price (`sns.regplot`)**:
   - Fitted a regression model to plot the linear trend between living square footage (`sqft_living`) and price (`price`).
   - Saved visualization as `living_area_vs_price.png`.

2. **Price Distribution Across Property Grades (`sns.boxplot`)**:
   - Analyzed price variability across construction quality ratings (`grade`). Higher grades demonstrate exponential growth in median home values.
   - Saved visualization as `price_by_grade.png`.

3. **Waterfront Impact Analysis (`sns.boxplot`)**:
   - Compared sale prices between waterfront properties and non-waterfront properties, identifying a significant price premium for waterfront access.
   - Saved visualization as `price_by_waterfront.png`.

4. **Geographic Price Distribution & Heatmap (`plt.scatter`)**:
   - Mapped property prices spatially using latitude and longitude coordinates with a colorbar gradient (`viridis` palette).
   - Saved visualization as `geographic_price_heatmap.png`.

5. **High-Value Location Clustering**:
   - Clustered properties by rounding coordinates (`lat` and `long` to 2 decimal places).
   - Aggregated location metrics (`property_count`, `average_price`, `median_price`, `average_living_area`) for clusters with $\ge 5$ properties.
   - Exported top clusters to `high_value_location_clusters.csv`.

---

## 📈 Real Estate Investment & Model Summary

Running the simple linear regression model ($Y = \text{Price}$, $X = \text{sqft\_living}$) yields the following baseline metrics:

```text
REAL ESTATE INVESTMENT SUMMARY
------------------------------------------
Properties Analyzed:                  21,613
Average Price:                        $540,088.14
Median Price:                         $450,000.00
Average Living Area:                  2,079.9 sq ft
Price Change per Additional Sq Ft:     +$280.62 / sq ft
Regression R-squared (R²):            0.493
How to Run the Code
Mount Google Drive in your Colab environment:

Python
from google.colab import drive
drive.mount('/content/drive')
Place Kc_house_data_preprocessed(10).csv in your Drive folder (/content/drive/MyDrive/file/).

Execute notebook cells sequentially to clean missing rows, generate interactive plots, export high-value cluster data, and view linear regression summary outputs.

👤 Author
Name: [S.Veeramanikandan]
