# AI Stock Market Exploratory Data Analysis (EDA) Report

## 1. Introduction

The objective of this project is to perform a complete Exploratory Data Analysis (EDA) and data preprocessing pipeline on an AI-related stock market dataset. The primary goals are:

* To clean and prepare the dataset for machine learning.
* To understand market behavior across different **Market Phases** (Bear, Neutral, Bull).
* To analyze structural changes in the market before and after the introduction of **ChatGPT**, represented by the `Post_ChatGPT` indicator.

This report documents **what was done, why it was done, the results obtained**, and **what conclusions can be drawn**, especially regarding the impact of ChatGPT on stock market behavior.

---

## 2. Dataset Overview

The dataset contains time-series and categorical information related to AI and technology stocks. Key components include:

* **Numerical features**: prices, returns, volume, rolling volatility, and technical indicators.
* **Categorical features**: Sector, Industry, Ticker.
* **Target variable**: `Market_Phase` (ordinal, multi-class).
* **Binary indicator**: `Post_ChatGPT` (0 = pre-ChatGPT era, 1 = post-ChatGPT era).
* **Temporal feature**: Date.

### Target Variable Encoding

`Market_Phase` was encoded as an ordinal variable:

* 1 → Bear
* 2 → Neutral
* 3 → Bull

This encoding preserves the natural ordering of market conditions.

---

## 3. Missing Value Handling

### What was done

* Missing values in numerical columns were identified.
* Appropriate statistical imputation was applied:

  * Mean or median for continuous numerical features, depending on skewness.

### Why

* Machine learning models cannot handle missing values directly.
* Statistical imputation preserves dataset size and overall distribution.

### Outcome

* All missing values were successfully handled.
* No rows were dropped, ensuring maximum data retention.

---

## 4. Outlier Treatment

### What was done

* Outliers were detected using the **Interquartile Range (IQR)** method.
* Instead of removing rows, outliers were **refilled (capped)** at the lower and upper IQR fences.

### Why

* Financial data naturally contains extreme values.
* Removing outliers could distort market behavior and reduce dataset representativeness.

### Outcome

* Extreme values were controlled without losing information.
* Boxplots after treatment showed stable and reasonable feature ranges.

---

## 5. Handling Class Imbalance

### What was done

* The target variable `Market_Phase` showed class imbalance.
* **SMOTE (Synthetic Minority Oversampling Technique)** was applied.
* Only numerical features were used during SMOTE, and `Market_Phase` was treated as the sole target.

### Why

* Imbalanced classes can bias machine learning models toward majority classes.
* SMOTE creates synthetic samples to balance all classes equally.

### Outcome

* Balanced representation of Bear, Neutral, and Bull market phases.
* Improved readiness for classification models.

---

## 6. Encoding Categorical Variables

### Sector (Nominal)

* **One-Hot Encoding** was applied.
* Reason: Low cardinality and no inherent ordering.

### Industry (High Cardinality)

* **Target-Guided Encoding** was used.
* Each industry was replaced with the mean of `Market_Phase` for that industry.

### Ticker

* High cardinality and stock-specific.
* Dropped to avoid dimensional explosion and overfitting.

### Why this strategy

* Encoding was chosen based on **semantic meaning** and **cardinality**, not blindly.

### Outcome

* All features converted to meaningful numerical representations.
* Dataset dimensionality remained manageable.

---

## 7. Feature Scaling and Transformation

### What was done

* **StandardScaler (Z-score normalization)** was applied to continuous numerical features.
* Target (`Market_Phase`) and binary (`Post_ChatGPT`) columns were excluded from scaling.
* Date column was excluded from scaling.

### Why

* Features existed on different scales (prices, volumes, returns).
* Scaling ensures fair contribution of each feature in ML models.

### Outcome

* Scaled features showed mean ≈ 0 and standard deviation ≈ 1.
* Dataset became fully compatible with distance- and gradient-based algorithms.

---

## 8. Final Exploratory Data Analysis (EDA)

### Key Visual Analyses Performed

* **Target distribution plots** confirmed balanced classes after SMOTE.
* **Histograms** showed normalized feature distributions post-scaling.
* **Boxplots** verified successful outlier treatment.
* **Correlation heatmap** revealed relationships among returns, volatility, and market phase.
* **Market Phase vs Post-ChatGPT plots** highlighted structural differences between periods.

---

## 9. Impact of ChatGPT on Stock Market Behavior

### Observations from EDA

* The `Post_ChatGPT` period shows a **higher concentration of Neutral-to-Bull market phases**.
* Volatility-related features exhibit noticeable pattern changes post-ChatGPT.
* AI-related sectors and industries show relatively stronger market phases in the post-ChatGPT era.

### Interpretation (Important)

* These results indicate a **structural shift in market sentiment and behavior** after the introduction of ChatGPT.
* The rise of generative AI appears to have increased investor interest and optimism in AI-linked stocks.

⚠️ **Note**: This analysis establishes **association, not causation**. While trends align with the emergence of ChatGPT, external macroeconomic factors may also contribute.

---

## 10. Conclusion

This project successfully implemented a full EDA and preprocessing pipeline:

* The dataset is clean, balanced, encoded, and scaled.
* All preprocessing decisions were made based on data characteristics and best practices.
* EDA revealed meaningful insights into market phases and the post-ChatGPT market environment.

### Final Outcome

The final dataset is **machine-learning ready**, and the analysis suggests that the post-ChatGPT era corresponds with observable changes in stock market behavior, particularly within AI-related sectors.

---


**End of Report**
