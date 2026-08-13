# Ames Housing Data Cleaning

## Project Overview

This project analyzes the Ames housing dataset.

The dataset contains:

- 2,930 rows.
- 82 columns.
- Property characteristics.
- Sale price information.
- Numerical and categorical variables.
- Missing values that require cleaning.

The original DataFrame is named `df`. A separate copy named `clean_df` is used for data cleaning so the original dataset remains unchanged.

## Initial Data Validation

The dataset was checked for:

- Number of rows and columns.
- Missing values.
- Duplicate rows.
- Excel errors.
- Column names and data types.

Initial results:

```text
Rows: 2930
Columns: 82
Duplicate rows: 0
Excel errors: 0
```

## Create a Cleaning Copy

```python
clean_df = df.copy()
```

Creating a copy protects the original dataset from being changed during the cleaning process.

## Handle Missing Categorical Values

Some missing categorical values represent features that are not present on the property. For example, a missing garage, pool, fence, or fireplace may indicate that the property does not have that feature.

These missing values were replaced with `"None"`:

```python
none_columns = [
    "Alley",
    "Mas Vnr Type",
    "Bsmt Qual",
    "Bsmt Cond",
    "Bsmt Exposure",
    "BsmtFin Type 1",
    "BsmtFin Type 2",
    "Fireplace Qu",
    "Garage Type",
    "Garage Finish",
    "Garage Qual",
    "Pool QC",
    "Fence",
    "Misc Feature"
]

for column in none_columns:
    clean_df[column] = clean_df[column].fillna("None")
```

This preserves the meaning that the property does not have the feature instead of deleting the row.

Garage-related missing values commonly occur together when a property does not have a garage. [145]

## Handle Missing Numerical Values

Some numerical columns describe the size, quantity, or value of a feature. When the feature is not present, the missing value was replaced with `0`:

```python
zero_columns = [
    "Mas Vnr Area",
    "BsmtFin SF 1",
    "BsmtFin SF 2",
    "Bsmt Unf SF",
    "Total Bsmt SF",
    "Bsmt Full Bath",
    "Bsmt Half Bath",
    "Garage Yr Blt",
    "Garage Cars",
    "Garage Area"
]

for column in zero_columns:
    clean_df[column] = clean_df[column].fillna(0)
```

For `Garage Yr Blt`, the value `0` represents that the property does not have a garage. It does not represent an actual construction year.

## Handle Lot Frontage

`Lot Frontage` is a numerical measurement. Missing values were replaced with the overall median:

```python
clean_df["Lot Frontage"] = clean_df["Lot Frontage"].fillna(
    clean_df["Lot Frontage"].median()
)
```

Using the median helps reduce the effect of unusually large or small lot-frontage values.

## Handle Electrical

The `Electrical` column had one missing value. Since it is categorical, the missing value was replaced with the most common category:

```python
clean_df["Electrical"] = clean_df["Electrical"].fillna(
    clean_df["Electrical"].mode()
)
```

## Validate the Cleaned Data

Check the selected columns:

```python
clean_df[
    ["Alley", "Garage Cond", "Lot Frontage", "Mas Vnr Area"]
].isna().sum()
```

Expected result:

```text
Alley           0
Garage Cond     0
Lot Frontage    0
Mas Vnr Area    0
```

Check all columns for remaining missing values:

```python
remaining_missing = clean_df.isna().sum()

remaining_missing[remaining_missing > 0]
```

Check the total number of missing values:

```python
clean_df.isna().sum().sum()
```

Expected result:

```text
0
```

## Final Data Quality Check

```python
print("Rows and columns:", clean_df.shape)
print("Duplicate rows:", clean_df.duplicated().sum())
print("Total missing values:", clean_df.isna().sum().sum())
```

Expected result:

```text
Rows and columns: (2930, 82)
Duplicate rows: 0
Total missing values: 0
```

## Final Outcome

The cleaned dataset:

- Preserves all 2,930 rows.
- Keeps all 82 columns.
- Contains no remaining missing values.
- Contains no duplicate rows.
- Contains no Excel error values.
- Preserves the original data in `df`.
- Stores the cleaned data in `clean_df`.

The cleaned DataFrame is now ready for exploratory data analysis, visualization, and further analysis.# ames-housing-price-prediction
