# Data-Cleaning-Project

## Project Overview

This project demonstrates a complete data cleaning workflow using Python and Pandas. The goal was to transform a messy transaction dataset into a clean, analysis-ready dataset.

## Dataset

The dataset contains transaction records with the following fields:

- Transaction ID
- Item
- Quantity
- Price Per Unit
- Total Spent
- Payment Method
- Location
- Transaction Date

## Data Cleaning Steps

- Checked for missing values
- Removed invalid values such as ERROR and UNKNOWN
- Applied median imputation to numerical columns
- Applied mode imputation to categorical columns
- Converted columns to correct data types
- Recalculated Total Spent using Quantity × Price Per Unit
- Detected potential outliers using the IQR method
- Performed final data quality validation

## Final Dataset

After cleaning:
- Rows: 9,540
- Columns: 8
- Missing values: 0

## Tools Used

- Python
- Pandas
- NumPy
- Jupyter Notebook