# Student Performance Data Analysis

An Exploratory Data Analysis (EDA) project using Python to analyze student performance metrics across math, reading, and writing subjects based on gender, demographic factors, test preparation, and parental education levels.

---

## 📁 Dataset Overview

The dataset used in this project is `StudentsPerformance.csv`. It contains **1,000 student records** with **8 attributes** (5 categorical features and 3 numerical score features).

### Feature Details
- **`gender`**: Gender of the student (`female`, `male`)
- **`race/ethnicity`**: Ethnic background group (`group A`, `group B`, `group C`, `group D`, `group E`)
- **`parental level of education`**: Highest education level attained by parents (`bachelor's degree`, `some college`, `master's degree`, `associate's degree`, `high school`, `some high school`)
- **`lunch`**: Type of lunch received (`standard`, `free/reduced`)
- **`test preparation course`**: Completion status of pre-exam course (`none`, `completed`)
- **`math score`**: Math examination score (0–100)
- **`reading score`**: Reading examination score (0–100)
- **`writing score`**: Writing examination score (0–100)

---

## 🛠️ Tools & Libraries Used

- **Language:** Python 3
- **Environment:** Google Colab
- **Data Manipulation:** `pandas`, `numpy`
- **Data Visualization:** `matplotlib`, `seaborn`

---

## 🚀 Key Analysis & Workflow

1. **Data Loading & Inspection**:
   - Loaded dataset into Pandas DataFrame via Google Drive (`/content/drive/MyDrive/file/StudentsPerformance.csv`).
   - Inspected numerical distribution using `df.describe()`.
   - Verified data types and checked missing values using `df.info()`.

2. **Categorical Feature Analysis**:
   - Extracted unique values across demographic factors (`gender`, `parental level of education`, `lunch`, `test preparation course`).

3. **Grouped Analysis**:
   - Computed average exam scores categorized by `parental level of education`.

4. **Bivariate Analysis & Visualizations**:
   - **Scatter Plots**: Analyzed relationships between pairs of exam subjects:
     - Math Score vs. Writing Score
     - Reading Score vs. Writing Score
   - **Heatmap**: Visualized correlation matrix across all numeric test scores.

---

## 📈 Key Insights & Findings

- **Strong Correlation**: Reading and writing scores show a very high positive correlation (**~0.95**), indicating that students who perform well in reading almost always score high in writing.
- **Math Performance Link**: Math scores also show strong positive correlations with both reading (**~0.82**) and writing (**~0.80**).
- **Parental Education Impact**: Students whose parents hold higher education degrees (master's/bachelor's) consistently perform better on average across all subjects.

---

## 💻 How to Run the Code

1. Mount Google Drive in Google Colab:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')

   👤 Author
Name: [S.Veeramanikandan]
