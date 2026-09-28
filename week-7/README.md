# Week-7 -Student Performance Analysis & Exploratory Data Analysis (EDA)

This project performs exploratory data analysis (EDA) and summary statistics on a student performance dataset (`StudentsPerformance.csv`) using Python in Google Colab. The analysis evaluates academic performance across math, reading, and writing scores relative to demographic and social factors.

---

## 📋 Overview

The primary goal of this notebook is to clean, inspect, and analyze student test performance metrics, including:
- **Demographics & Background:** Gender, Race/Ethnicity, Parental Level of Education, Lunch Type, Test Preparation Course
- **Core Scores:** Math Score, Reading Score, Writing Score
- **Calculated Performance:** Total Score, Overall Percentage

---

## 🗂️ Dataset Overview

- **Total Records:** 1,000 students
- **Total Features:** 8 primary attributes (+ 2 engineered features)
- **Data Quality:** 0 missing values, 0 duplicate entries

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `gender` | `object` | Gender of the student (`female`, `male`) |
| `race/ethnicity` | `object` | Demographic group (`group A`, `group B`, `group C`, `group D`, `group E`) |
| `parental level of education` | `object` | Highest education level of parents (e.g., `bachelor's degree`, `some college`, `master's degree`, `high school`) |
| `lunch` | `object` | Type of school lunch received (`standard`, `free/reduced`) |
| `test preparation course` | `object` | Completion status of test preparation (`none`, `completed`) |
| `math score` | `int64` | Math test score (out of 100) |
| `reading score` | `int64` | Reading test score (out of 100) |
| `writing score` | `int64` | Writing test score (out of 100) |

---

## 🛠️ Project Workflow

1. **Environment Setup & Data Import**
   - Import core data science libraries (`pandas`, `numpy`, `matplotlib.pyplot`, `seaborn`).
   - Mount Google Drive and load `StudentsPerformance.csv`:
     ```python
     df = pd.read_csv("StudentsPerformance.csv")
     ```

2. **Data Inspection & Cleaning**
   - View top and bottom records using `df.head()` and `df.tail()`.
   - Check dataset dimensions (`(1000, 8)`).
   - Confirm complete data integrity with `df.isnull().sum()` and `df.duplicated().sum()`.

3. **Statistical Analysis**
   - Calculate summary statistics (Mean, Median, Mode, Quartiles, Min, Max) for core test scores (`math score`, `reading score`, `writing score`).

4. **Feature Engineering**
   - **`total score`**: Sum of scores across all three subjects (Math + Reading + Writing).
   - **`Percentage`**: Overall percentage score computed as:
     $$\text{Percentage} = \left( \frac{\text{total score}}{300} \right) \times 100$$

---

## 📊 Summary Statistics Highlights

| Subject | Mean | Median | Mode | 25% (Q1) | 75% (Q3) | Min | Max |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Math Score** | 66.09 | 66.0 | 65 | 57.00 | 77.0 | 0 | 100 |
| **Reading Score** | 69.17 | 70.0 | 72 | 59.00 | 79.0 | 17 | 100 |
| **Writing Score** | 68.05 | 69.0 | 74 | 57.75 | 79.0 | 10 | 100 |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.x installed along with the required dependencies:

```bash
pip install pandas numpy matplotlib seaborn
