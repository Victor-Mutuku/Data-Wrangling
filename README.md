# Netflix Dataset Cleaning & Preprocessing

## Project Overview
This project focuses on **exploring, cleaning, and preprocessing a Netflix dataset** containing information about movies and TV shows. The dataset includes features such as title, director, cast, country, release year, rating, duration, genre, and description. The workflow demonstrates **data inspection, transformation, handling missing values, anomaly detection, and final dataset preparation for analysis or modeling**.

---

## Dataset
- **Source:** Kaggle Netflix Titles dataset (`netflix_titles.csv`)  
- **Rows:** 8,807  
- **Columns:** 12 (after preprocessing, 13 including `duration_value` and `duration_unit`)  

**Original Columns:**  
`show_id`, `type`, `title`, `director`, `cast`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, `description`  

---

## Workflow & Detailed Steps

### 1. Data Discovery
- Loaded dataset using **pandas**.
- Inspected dataset shape, column names, and data types.
- Checked for missing values and duplicate rows.  
- Found missing values in `director`, `cast`, `country`, `date_added`, `rating`, and `duration`.

### 2. Structuring the Data
- Converted `date_added` to **datetime** format.
- Separated `duration` into:
  - **duration_value** (numeric, e.g., `90` from `90 min`)  
  - **duration_unit** (string, e.g., `min` or `Seasons`)
- Converted `duration_value` to numeric for future calculations.

### 3. Cleaning the Data
- Removed duplicate rows.
- Dropped `description` column.
- Filled missing `director` using **cast-director mapping** for repeated pairs; remaining missing directors assigned "Not Given".
- Filled missing `country` values using **director-country mapping**; remaining missing countries assigned "Not Given".
- Dropped rows with missing `date_added`, `rating`, or `duration`.

### 4. Error Checking
- Verified `date_added` is not earlier than `release_year`.
- Dropped rows violating this condition.

### 5. Validation
- Dropped helper column `dir_cast`.
- Ensured:
  - `date_added` is of type datetime.
  - `duration_value` is numeric.
- Removed rows with `release_year` prior to 1997.
- Dropped rows with missing `title`, `release_year`, or `date_added`.
- Reset index after cleaning.
  
---

### 6. Publishing Cleaned Dataset
- Saved the cleaned dataset as CSV:  
  
## Skills Demonstrated

- **Data Analysis & Exploration:** Pandas, NumPy  
- **Data Cleaning & Preprocessing:** Handling missing values, duplicates, and anomalies  
- **Data Transformation:** Datetime conversion, extracting numeric values from text  
- **Error Checking & Validation:** Logical consistency between fields, anomaly detection  
- **Workflow & Pipeline Management:** End-to-end preprocessing for large datasets  
- **Data Publishing:** Saving clean datasets for reproducibility  

---

## Outputs & Visualizations

- **Cleaned Dataset CSV:** `cleaned_netflix.csv`  

**Features Added:**  
- `duration_value` (numeric duration)  
- `duration_unit` (unit of duration: min or seasons)  
- Dataset free of missing values in critical fields (`title`, `release_year`, `date_added`)  
- Logical errors resolved (e.g., `date_added` before `release_year` removed)  
- Dataset ready for visualization or predictive modeling
  
