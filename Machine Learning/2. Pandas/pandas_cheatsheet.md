# Pandas and ML Cheat Sheet

## Table of Contents

 1. [Installation](#installation)
 2. [Creating DataFrames](#creating-dataframes)
 3. [Inspecting Data](#inspecting-data)
 4. [Selecting](#selecting)
 5. [Modifying Data](#modifying-data)
 6. [Handling Missing Data](#handling-missing-data)
 7. [Sorting and Grouping](#sorting-and-grouping)
 8. [Merging and Joining DataFrames](#merging-and-joining-dataframes)
 9. [Exporting Data](#exporting-data)
 10. [References](#references)

## Installation

```bash
pip install pandas
```

```python
import pandas as pd
```

## Creating DataFrames

```python
# From a dictionary
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35]
    }
df = pd.DataFrame(
    data,
    index=[1,2,3])

# From an array
data = [
    ['Alice', 25],
    ['Bob' , 30],
    ['Charlie' , 35]]
df = pd.DataFrame(
    data,
    index=[1,2,3],
    columns=['Name', 'Age'])

# From a CSV file
df = pd.read_csv("data.csv")

# From an Excel file
df = pd.read_excel("data.xlsx")
```

## Inspecting Data

```python
df.head()  # First rows
df.tail()  # Last rows
df.sample()  # Random row selection
df.info()  # Summary of DataFrame
df.dtypes  # Data Types
df.describe()  # Summary statistics
df.shape  # Dimensions
df.columns  # Columns
df['sex'].value_counts()  # Unique values repeat count
df['sex'].value_counts(normalize=True) * 100  # Percentage
pd.crosstab( titanic_data.sex, titanic_data.survived)
# tip: normalize="index" or "columns" or "all"
```

## Selecting

```python
df['Age']  # Select a column
df[['Name', 'Age']]  # Select multiple columns
df.iloc[0]  # Select first row by index
df.loc[0, 'Name']  # Select specific value
df[df['Age'] > 25]  # Filter rows
df[0:10]
```

## Modifying Data

```python
df['Age'] = df['Age'] + 1  # Modify a column
df['NewColumn'] = df['Age'] * 2  # Add a new column

# Remove column
df.drop(columns=['NewColumn'], inplace=True)
# Rename a column
df.rename(columns={'Age': 'Years'}, inplace=True)
```

## Handling Missing Data

```python
df.dropna()  # Remove missing values
df.fillna(0)  # Fill missing values with 0
df.isna().sum()  # Count missing values per column
```

## Sorting and Grouping

```python
df.sort_values('Age', ascending=False)  # Sort by Age descending
df.groupby('Name').mean()  # Group by Name and compute mean
```

## Merging and Joining DataFrames

```python
df1.merge(df2, on='ID', how='inner')  # Inner join
df1.merge(df2, on='ID', how='left')  # Left join
df1.append(df2, ignore_index=True)  # Append rows
```

## Exporting Data

```python
df.to_csv("output.csv", index=False)  # Save as CSV
df.to_excel("output.xlsx", index=False)  # Save as Excel
```

## References

- [Pandas Documentation](https://pandas.pydata.org/docs/)

