# Telco-Customer-Churn

Telco Customer Churn — Step 1: Data Cleaning

This workspace contains the first notebook for a churn prediction project.

Files:
- `notebooks/01-data-cleaning.ipynb` — initial cleaning and encoding, saves cleaned CSV to `data/cleaned_telco_churn.csv`
- `notebooks/01-data-cleaning.ipynb` — initial cleaning and encoding, saves cleaned CSV to `data/cleaned_telco_churn.csv`
- `notebooks/02-eda.ipynb` — exploratory data analysis: distributions, churn rates by group, and figures saved to `reports/figures/`
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` — original dataset (source: public dataset used widely)

How to run:
1. Create a virtual environment and install requirements (see `requirements.txt`).
2. From the workspace root run `jupyter lab` or open `notebooks/01-data-cleaning.ipynb` in VS Code and run cells.

Notes:
- The notebook expects the CSV at the repository root. If you move files, update the path in the notebook.

Results from running `notebooks/01-data-cleaning.ipynb` (executed):

- Initial dataset shape: 7043 rows × 21 columns
- `TotalCharges` was read as object, converted to numeric. There were 11 blank-like values (0.16%) that became NaN.
- Because the missing fraction was small (<=5%), those 11 rows were dropped. New shape after handling `TotalCharges`: 7032 rows × 21 columns
- After trimming and one-hot encoding of categorical variables, the final cleaned dataset shape is 7032 rows × 47 columns
- Cleaned CSV saved to `data/cleaned_telco_churn.csv`