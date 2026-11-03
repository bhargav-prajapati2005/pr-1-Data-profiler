# Customer Churn Data Preprocessing & Feature Engineering

A beginner-friendly data analytics project focused on inspecting, cleaning, transforming, and exploring a customer churn dataset before machine-learning use.

## Project Overview

The dataset contains customer demographic details, income, purchase activity, spending, recency, and a churn label. The project can be used to practice:

- Data loading with Pandas
- Data profiling and quality checks
- Handling missing values and duplicate records
- Exploratory Data Analysis (EDA)
- Feature engineering and preprocessing
- Preparing data for machine-learning models

## Repository Files

| File | Description |
|---|---|
| `customer_churn_dataset(1).csv` | Main customer churn dataset |
| `customer.db` | SQLite database file supplied with the project |
| `README.md` | Project documentation |

## Dataset Details

The CSV contains **203 rows and 8 columns**.

| Column | Description |
|---|---|
| `CustomerID` | Customer identifier |
| `Age` | Customer age |
| `Gender` | Customer gender |
| `Income` | Customer income |
| `Purchases` | Number of purchases |
| `TotalSpending` | Total customer spending |
| `DaysSinceLastPurchase` | Days since the customer's last purchase |
| `Churn` | Target variable: `1` = churned, `0` = not churned |

## Initial Data Quality Findings

The initial inspection found:

- 4 missing values in `Age`
- 3 missing values in `Gender`
- 5 missing values in `Income`
- Repeated `CustomerID` values are present; investigate them before deciding whether they are true duplicate records.
- The target column `Churn` is binary (`0` or `1`).

Do not remove or fill values blindly. First inspect the affected records and document the cleaning decisions.

## SQLite Database Note

The supplied `customer.db` currently contains a table named `customers` with the columns `id`, `name`, and `city`. It contains one record. This schema is different from the customer churn CSV schema, so the database should not be assumed to contain the CSV dataset.

## Suggested Workflow

1. Load the CSV using Pandas.
2. Inspect the dataset with `head()`, `info()`, `describe()`, and `shape`.
3. Check missing values with `isnull().sum()`.
4. Check duplicate rows and repeated customer IDs.
5. Handle missing values using a justified strategy.
6. Encode categorical features such as `Gender`.
7. Scale numerical features if required by the selected model.
8. Perform EDA using charts and summary statistics.
9. Separate features (`X`) and target (`y = Churn`).
10. Save the cleaned dataset for later modelling.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- SQLite
- Jupyter Notebook

## Quick Start

Install the commonly used Python libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Load the dataset:

```python
import pandas as pd

df = pd.read_csv("customer_churn_dataset(1).csv")

print(df.head())
print(df.info())
print(df.isnull().sum())
```

Inspect the SQLite database:

```python
import sqlite3
import pandas as pd

connection = sqlite3.connect("customer.db")

customers = pd.read_sql_query("SELECT * FROM customers", connection)
print(customers.head())

connection.close()
```

## Project Objective

The objective is to produce a clean, well-understood dataset that is suitable for further analysis and customer churn prediction. Any preprocessing decisions should be recorded so that the workflow is reproducible.

## Author

BHARGAV PRAJAPATI

