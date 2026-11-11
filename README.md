# Exploratory_Data_Analysis
# Sales Transaction Data Cleaning & Exploratory Data Analysis (EDA)

This repository contains the complete data preprocessing, exploratory data analysis (EDA), and cleaned datasets for sales transaction records. The project standardizes messy raw data, handles missing values and outliers, and generates key visual insights for downstream machine learning modeling (e.g., Linear Regression).

---

## 📁 Repository Structure

| File Name | Description |
| :--- | :--- |
| `EDA-External.ipynb` | Google Colab / Jupyter notebook containing all Python code for cleaning, EDA, and data visualizations. |
| `sales_transactions_regression.csv` | Raw, uncleaned dataset containing missing values, duplicates, and inconsistent categorical entries. |
| `sales_transactions_regression_preprocessed.csv` | Cleaned and preprocessed dataset ready for analysis and machine learning models. |

---

## 🛠️ Data Preprocessing & Cleaning Pipeline

The raw dataset underwent the following data cleaning steps using `pandas`:

1. **Redundant Feature Removal:** Dropped duplicate product ID columns (`product_id.1`, `product_id.2`, `product_id.3`).
2. **Missing Value Imputation:**
   * **Numerical Columns (`sales_amount`, `units_sold`, `unit_price`, `discount_pct`):** Imputed missing values using column medians.
   * **Categorical & Identifiers:**
     * Imputed missing `store_id` values using the mode (`S1`).
     * Filled missing dates using forward fill (`ffill`).
     * Sequentially auto-generated missing `transaction_id`s starting from `T50028`.
     * Mapped missing `product_id` values using store-level mode grouping.
3. **Categorical Standardization:** Standardized regional typos (`WST`, `EST`, `NOTH`, etc.) into four uniform regions (`West`, `East`, `South`, `North`) and cleaned store IDs into consistent codes (`S1`–`S4`).
4. **Outlier Handling:** Applied Interquartile Range (IQR) clipping (`.clip()`) on extreme `sales_amount` values to prevent distortion during statistical modeling.

---

## 📊 Key EDA Findings & Insights

* **Balanced Regional Volume:** Transactions are distributed evenly across all four regions (**West**, **East**, **South**, and **North**).
* **Store Contribution:** Store **S1** leads in total transaction volume, followed closely by **S2**, **S3**, and **S4**.
* **Revenue Drivers:** Total `sales_amount` is primarily driven by `unit_price` rather than `units_sold` (which consistently stays between 1–9 units per order).
* **Feature Relationships:** Numerical variables show expected linear relationships and clean distributions ready for machine learning.

---

