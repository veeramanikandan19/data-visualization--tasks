# Week-5 Healthcare Assessment & Exploratory Data Analysis (EDA)

This repository contains a data analysis and preprocessing workflow performed on patient admission data using Python in Google Colab. The notebook focuses on data validation, standardizing categorical attributes, datetime parsing, feature engineering (hospital stay duration), and descriptive statistical reporting.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Dataset Architecture](#-dataset-architecture)
- [Project Workflow & Data Pipeline](#-project-workflow--data-pipeline)
- [Key Insights & Statistical Summary](#-key-insights--statistical-summary)
- [Setup & Installation](#-setup--installation)
- [How to Run](#-how-to-run)
- [Tech Stack & Dependencies](#-tech-stack--dependencies)

---

## 📋 Overview

Healthcare operational efficiency relies heavily on understanding patient admission trends, lengths of stay, and billing metrics. This project conducts an end-to-end Exploratory Data Analysis (EDA) on 500 patient records (`healthcare_dataset.csv`) to establish clean data baselines for downstream analytical tasks or predictive modeling.

---

## 🗂️ Dataset Architecture

The dataset contains **500 rows** and **9 primary attributes**:

| Column Name | Data Type | Description | Example Value |
| :--- | :--- | :--- | :--- |
| `Patient_ID` | `object` | Unique alphanumeric patient identifier | `P1001` |
| `Gender` | `object` | Patient demographic gender | `Male`, `Female` |
| `Age` | `int64` | Patient age in years | `45` |
| `Medical_Condition` | `object` | Primary diagnosed health condition | `Hypertension`, `COPD`, `Stroke` |
| `Admission_Date` | `datetime64[ns]` | Date of patient admission | `2026-01-15` |
| `Admission_Type` | `object` | Categorical admission urgency (`routine`, `emergency`, `urgent`) | `urgent` |
| `Medical_Code` | `object` | Standardized ICD-10 diagnostic code | `ICD-10-I10` |
| `Billing_Amount` | `float64` | Total billed cost in USD ($) | `4500.0` |
| `Discharge_Date` | `datetime64[ns]` | Date of patient discharge | `2026-01-20` |

---

## 🛠️ Project Workflow & Data Pipeline

1. **Environment Setup & Data Import**
   - Import core Python data libraries (`pandas`, `matplotlib`, `seaborn`).
   - Load dataset directly from Google Drive path: `/content/drive/MyDrive/file/healthcare_dataset.csv`.

2. **Data Cleaning & Quality Checks**
   - Check missing value distributions across all columns using `isnull().sum()`.
   - Apply programmatic imputation across text/object columns using `.fillna('Unknown')`.
   - Normalize string attributes for consistency (e.g., lowercase conversion on `Admission_Type`).

3. **Datetime Conversion & Parsing**
   - Cast string date fields (`Admission_Date`, `Discharge_Date`) to pandas `datetime64[ns]` objects to enable temporal calculations.

4. **Feature Engineering**
   - **`Hospital_Stay_Days`**: Created by computing the exact day difference between discharge and admission dates:
     $$\text{Hospital\_Stay\_Days} = \text{Discharge\_Date} - \text{Admission\_Date}$$

5. **Statistical Distribution & Analysis**
   - Run aggregate metrics using `describe()` on continuous parameters (`Age`, `Billing_Amount`, `Hospital_Stay_Days`).
   - Evaluate categorical frequency distributions using `value_counts()` on `Admission_Type`.

---

## 📊 Key Insights & Statistical Summary

### Descriptive Overview

| Metric | Patient Age | Billing Amount ($) | Hospital Stay (Days) |
| :--- | :--- | :--- | :--- |
| **Count** | 500 | 500 | 500 |
| **Mean** | 50.11 years | $7,249.00 | 2.74 days |
| **Std Dev** | 15.33 years | $3,198.97 | 1.18 days |
| **Min** | 22 years | $2,300.00 | 1 day |
| **25% (Q1)** | 37 years | $4,400.00 | 2 days |
| **50% (Median)** | 50 years | $6,950.00 | 2 days |
| **75% (Q3)** | 63 years | $9,400.00 | 4 days |
| **Max** | 78 years | $14,200.00 | 10 days |

### Admission Type Breakdown
- **Routine:** 196 admissions (39.2%)
- **Emergency:** 188 admissions (37.6%)
- **Urgent:** 116 admissions (23.2%)

---

## 🚀 Setup & Installation

### Prerequisites
Make sure Python 3.8+ is installed on your local environment or execute directly in Google Colab.

### Install Required Libraries
```bash
pip install pandas matplotlib seaborn
