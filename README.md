# Airplane Disaster Dataset – Cleaning & Preprocessing

This project focuses on cleaning and preparing a historical dataset of airplane accidents (1919–2023) for further analysis and visualization. The dataset contains various inconsistencies, missing values, and mixed formats, especially in temporal and categorical fields. The notebook provided performs all necessary operations in a clear, reproducible, and logically ordered pipeline.

## 📌 Dataset Source

The dataset is a CSV file containing aviation accident records from 1919 to 2023. It includes fields such as `date`, `year`, `location`, `country`, `operator`, `fatalities`, and `type`.

## ✅ Cleaning Workflow Summary

### 1. Import & Initial Setup
- Imported core libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, etc.
- Mounted Google Drive (in Colab) and loaded the raw CSV file.

### 2. Standardizing Missing Values
- Defined a regex-based dictionary to replace non-standard missing values such as `'unknown'`, `'unk'`, `'n/a'`, `'-'`, `'?'`, etc. with `np.nan`.
- Applied this cleaning globally across the dataset using `.replace()` with regex.

### 3. Dropping Incomplete Records
- Removed rows with less than **60% non-null values** to ensure data reliability.

### 4. Handling Categorical Fields
- For the following columns:
  - `country`, `operator`, `type`, and `cat`
- Filled missing values (`NaN`) with `'Unknown'`.
- Converted them to appropriate data types (`string` or `category`).

### 5. Date & Temporal Cleaning
- Converted the `date` column to datetime format using `pd.to_datetime()` with format `'%d-%b-%Y'` and `errors='coerce'`.
- For entries with a missing `date` but a valid `year`, a synthetic date `'01 Jan <year>'` was imputed.
- If `year` was missing but `date` was valid, it was extracted from `date`.
- Ensured `year` and `fatalities` were stored as nullable integers (`Int64`).

### 6. Final Output
- The cleaned DataFrame `df_cleaned` is now ready for analysis.
- Missing value statistics and structure (`.info()` and `.isnull().sum()`) were printed for inspection.
- The cleaning operations are organized into logical code blocks to support maintainability and further extension.

## 📁 Output

The cleaned notebook is saved as:

```
Airplane_Disaster_Cleaning_Final.ipynb
```

You can directly open it in Google Colab or Jupyter Notebook.

## ✅ Next Steps

- Perform exploratory data analysis (EDA)
- Visualize trends by country, operator, fatalities over time, etc.
- Apply geospatial analysis if needed (e.g., accident distribution by country)
