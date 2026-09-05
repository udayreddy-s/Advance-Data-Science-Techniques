 Data Importing and Basic Data Cleaning

 Project Overview

This project focuses on importing, auditing, cleaning, and preparing the Mall Customer Segmentation dataset for downstream analytics and machine learning tasks. The workflow handles structural inconsistencies, validates data integrity, standardizes column headers, and enforces appropriate data types using Python and pandas inside a Jupyter Notebook environment.

---

# Dataset Summary
- **Source File:** `Mall_Customers.csv`
- **Initial Shape:** 200 rows, 5 columns
- **Final Shape:** 200 rows, 5 columns
- **Attributes:**
  - `customer_id`: Unique identifier for each customer
  - `gender`: Biological sex (`Male`, `Female`)
  - `age`: Customer age in years
  - `annual_income_k`: Annual income in thousands of dollars ($k)
  - `spending_score`: Score assigned by the mall based on customer behavior and spend nature (1–100)


## Data Cleaning Steps Performed

### 1. Data Ingestion & Initial Exploration
- Loaded the raw dataset using `pd.read_csv('Mall_Customers.csv')`.
- Inspected the structure, non-null counts, and memory footprint using `.shape`, `.head()`, and `.info()`.

### 2. Column Standardization & Renaming
- Standardized all column labels to lowercase `snake_case` to eliminate whitespace and special characters.
- Fixed the typographical column error where gender was labeled as `Genre`.
  - `CustomerID` &rarr; `customer_id`
  - `Genre` &rarr; `gender`
  - `Age` &rarr; `age`
  - `Annual Income (k$)` &rarr; `annual_income_k`
  - `Spending Score (1-100)` &rarr; `spending_score`

### 3. Duplicate Records Removal
- Audited identical records across all features using `df.duplicated().sum()`.
- Verified that all 200 customer entries are unique; confirmed 0 duplicate rows.

### 4. Missing Value Identification & Handling
- Checked for null or missing values across every field using `df.isnull().sum()`.
- Verified that the raw dataset contained zero missing values.
- Applied `.dropna()` to ensure pipeline safety against unexpected null entries.

### 5. Categorical & String Standardization
- Stripped extraneous leading and trailing whitespace from the `gender` column.
- Capitalized categorical values to ensure consistent casing across entries (`Male`, `Female`).

### 6. Data Type Casting
- Assigned and converted columns to their optimal data types:
  - `customer_id`: `int64`
  - `gender`: `category` (converted from generic string object to optimize memory usage)
  - `age`: `int64`
  - `annual_income_k`: `int64`
  - `spending_score`: `int64`

### 7. Data Verification & Sanity Checks
- Verified numerical boundary ranges using `.min()` and `.max()`:
  - `age`: Range confirmed between 18 and 70 years.
  - `annual_income_k`: Range confirmed between 15k and 137k.
  - `spending_score`: Range confirmed strictly within the designated scale of 1 to 99 (valid [1–100] bound).
- Executed `.describe()` to review statistical distributions (mean, median, standard deviation, quartiles).

### 8. Data Export
- Exported the finalized, clean dataframe to CSV using `df.to_csv('cleaned_mall_customers.csv', index=False)`.

---

## Repository Structure

Data Cleaning/
├── README.md                  
├── Mall_Customers.csv           
├── cleaned_mall_customers.csv   
└── data_cleaning.ipynb          