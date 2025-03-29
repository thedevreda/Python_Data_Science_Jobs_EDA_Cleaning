# A-Z Data Cleaning Guide

## A. Load the Data
1. **Import necessary libraries** (`pandas`, `numpy`, `seaborn`, `matplotlib`,`ast`,`warning` etc.).
2. **Load datasets** (CSV, Excel, API, etc.).
3. **Display basic info** (`df.info()`, `df.head()`, `df.shape()`).

## B. Data Inspection
4. **Check duplicates** (`df.duplicated().sum()`).
5. **Check missing values** (`df.isnull().sum()`, `df.isna().sum()`, `sns.heatmap(df.isnull())`).
6. **Check data types** (`df.dtypes`).
7. **Check unique values per column** (`df.nunique()`, `df['column'].unique()`).
8. **Check unique values per column** (`df.nunique()`, `df['column'].unique()`).


## C. Handle Duplicates
9. **Drop duplicate rows** (`df.drop_duplicates(inplace=True)`).
10. **Drop duplicates based on specific columns** (`df.drop_duplicates(subset=['col1', 'col2'], inplace=True)`).

## D. Handle Missing Data
11. **Fill numerical missing values with median or mean** (`df['column'].fillna(df['column'].median(), inplace=True)`).
12. **Fill categorical missing values with mode** (`df['column'].fillna(df['column'].mode()[0], inplace=True)`).
13. **Drop rows with too many missing values** (`df.dropna(thresh=threshold, inplace=True)`).
14. **Drop entire columns if they are mostly empty** (`df.drop(columns=['col_name'], inplace=True)`).

## E. Fix Data Types
15. **Convert dates** (`df['date_column'] = pd.to_datetime(df['date_column'])`).
16. **Convert categorical columns to category type** (`df['category_col'] = df['category_col'].astype('category')`).
17. **Convert numerical data stored as strings** (`df['num_col'] = pd.to_numeric(df['num_col'], errors='coerce')`).

## F. Standardize Text Formatting
18. **Trim extra spaces** (`df['col'] = df['col'].str.strip()`).
19. **Convert to lowercase** (`df['col'] = df['col'].str.lower()`).
20. **Remove special characters** (`df['col'] = df['col'].str.replace(r'[^\w\s]', '', regex=True)`).
21. **Fix typos and inconsistencies** (e.g., standardizing `yes/no`, `Y/N`, `true/false`).
22. **Rename columns** (`df.rename(columns={"A": "a", "B": "c"})`, `df.rename(index={0: "x", 1: "y", 2: "z"})`)


## H. Feature Engineering
24. **Extract date components** (`df['year'] = df['date_col'].dt.year`).
25. **Create new columns** (e.g., `df['full_name'] = df['first_name'] + ' ' + df['last_name']`).
26. **One-hot encode categorical variables**:
   ```python
   df = pd.get_dummies(df, columns=['category_col'], drop_first=True)
   ```

## J. Handle Unstructured Data (Optional)
29. **Clean phone numbers** (e.g., remove non-numeric characters, enforce format).
30. **Split addresses into street, city, zip**:
   ```python
   df[['Street', 'City', 'State_Zip']] = df['Address'].str.split(',', expand=True)
   ```
31. **Extract useful info from text fields (if applicable).**

## K. Save the Cleaned Dataset
32. **Save the cleaned dataset to a new file**:
   ```python
   df.to_csv("cleaned_data.csv", index=False)
   df.to_excel("cleaned_data.xlsx", index=False)
   ```

## Bonus Enhancements
✅ Automate repetitive tasks with functions.  
✅ Use `apply()` to optimize performance instead of loops.  
✅ Handle large datasets efficiently with `dask` or `polars`.  
✅ Document each transformation step in a markdown cell for better tracking.  

This structured approach will help systematically clean any dataset. 🚀

