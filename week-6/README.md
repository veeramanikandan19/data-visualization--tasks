# Week - 5 -Healthcare Data Analysis & Exploratory Data Analysis (EDA)

This project performs exploratory data analysis (EDA) and data preprocessing on a large-scale healthcare dataset (`healthcare_dataset (1).csv`). The analysis focuses on patient admissions, billing summaries across medical conditions, and length of hospital stay calculations using Python and Google Colab.

---

## 📋 Overview

The notebook analyzes key administrative, clinical, and billing metrics across patient records, including:
- **Patient Demographics:** Name, Age, Gender, Blood Type
- **Clinical Attributes:** Medical Condition, Doctor, Hospital, Medication, Test Results
- **Admission & Billing Details:** Date of Admission, Discharge Date, Room Number, Insurance Provider, Billing Amount, Admission Type
- **Derived Metrics:** Length of Hospital Stay (`Hospital_Stays` in days)

---

## 🗂️ Dataset Overview

- **Total Records:** 55,500 entries
- **Total Features:** 15 columns
- **Data Completeness:** 0 missing values across all features

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Name` | `object` | Patient full name |
| `Age` | `int64` | Age in years |
| `Gender` | `object` | Patient gender |
| `Blood Type` | `object` | ABO/Rh blood group (`A+`, `A-`, `B-`, `O+`, `AB+`, etc.) |
| `Medical Condition` | `object` | Primary condition (e.g., Arthritis, Asthma, Cancer, Diabetes, Hypertension, Obesity) |
| `Date of Admission` | `datetime64[ns]` | Admission date |
| `Doctor` | `object` | Attending physician |
| `Hospital` | `object` | Healthcare facility name |
| `Insurance Provider` | `object` | Payer organization (e.g., Blue Cross, Medicare, Aetna) |
| `Billing Amount` | `float64` | Charged amount in USD ($) |
| `Room Number` | `int64` | Assigned hospital room |
| `Admission Type` | `object` | Categorical admission urgency (`Urgent`, `Emergency`, `Elective`) |
| `Discharge Date` | `datetime64[ns]` | Discharge date |
| `Medication` | `object` | Prescribed treatment (e.g., Paracetamol, Ibuprofen, Aspirin, Penicillin) |
| `Test Results` | `object` | Outcome indicator (`Normal`, `Inconclusive`, `Abnormal`) |

---

## 🛠️ Project Workflow

1. **Environment Setup & Data Import**
   - Import required analysis libraries (`pandas`, `matplotlib.pyplot`, `seaborn`).
   - Read dataset directly from Google Drive path:
     ```python
     df = pd.read_csv("/content/drive/MyDrive/file/healthcare_dataset (1).csv")
     ```

2. **Data Inspection & Integrity Verification**
   - Execute `.info()` to confirm schema structure and data types.
   - Run `.isnull().sum()` to verify dataset completeness (55,500 non-null values across all columns).

3. **Financial & Grouped Aggregations**
   - Group billing totals by `Medical Condition`:
     ```python
     billing = df.groupby("Medical Condition")["Billing Amount"].sum()
     ```
   - Segment billing by `Medical Condition` and `Gender` using `.unstack()`:
     ```python
     billing_by_gender = df.groupby(['Medical Condition', 'Gender'])['Billing Amount'].sum().unstack()
     ```
   - Visualize total billing metrics using stacked bar charts.

4. **Feature Engineering**
   - Convert string date fields to pandas datetime objects (`pd.to_datetime`).
   - Create `Hospital_Stays` column to compute exact length of stay in days:
     $$\text{Hospital\_Stays} = \text{Discharge Date} - \text{Date of Admission}$$

5. **Visualization**
   - Generate violin plots using `seaborn` to inspect the statistical distribution of hospital stays across medical conditions.

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python installed along with the required libraries:

```bash
pip install pandas matplotlib seaborn
