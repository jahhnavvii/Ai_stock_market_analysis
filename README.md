# AI Stock Market Analysis 📈

## 📌 Project Overview
This project performs Exploratory Data Analysis (EDA) and preprocessing on an AI-related stock market dataset to prepare it for machine learning modeling.

---

## 📂 Dataset Description
The dataset contains stock-level, sector-level, and market-level information along with market phase indicators and a Post-ChatGPT flag.

---

## ⚙️ Data Preprocessing Steps
- Handling missing values using statistical imputation
- Outlier treatment using IQR-based refilling
- Handling class imbalance using SMOTE
- Encoding categorical variables:
  - Sector → One-Hot Encoding
  - Industry → Target-Guided Encoding
- Feature scaling using StandardScaler
- Date features excluded from scaling

---

## 📊 Exploratory Data Analysis
- Target distribution analysis
- Feature distribution visualization
- Boxplots for outlier validation
- Correlation heatmap
- Market phase comparison before and after ChatGPT

---

## 🧠 Target Variable
**Market_Phase**
- 1 → Bear
- 2 → Neutral
- 3 → Bull

---

## 🛠️ Tools & Libraries
- Python
- Pandas
- NumPy
- Seaborn
- Matplotlib
- Scikit-learn
- Imbalanced-learn

---

## 🚀 Outcome
A clean, balanced, and fully numerical dataset ready for machine learning models.
