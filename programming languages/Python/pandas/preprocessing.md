Good question — this is an important first step before any preprocessing.

If you have your data in a CSV file, the first thing to do is to **load it into a DataFrame** (using pandas), then use pandas’ built-in methods to explore and inspect it. Here’s a practical summary:

---

### 🧭 1. Load the data

```python
import pandas as pd

df = pd.read_csv('your_file.csv')
```

---

### 🔍 2. View basic information and metadata

These commands help you understand the structure and health of your dataset.

#### **a. Overall info**

```python
df.info()
```

* Shows number of entries, column names, data types, and **non-null counts** (helps detect missing data).

#### **b. Summary statistics**

```python
df.describe()
```

* Gives mean, std, min, max, etc. for numeric columns.
* Use `df.describe(include='all')` to include categorical columns.

#### **c. Check for null values**

```python
df.isnull().sum()
```

* Shows how many nulls each column has.
* You can also check the **percentage of missing data**:

  ```python
  df.isnull().mean() * 100
  ```

#### **d. See shape and column names**

```python
df.shape      # (rows, columns)
df.columns    # column names
```

#### **e. View a few rows**

```python
df.head()     # first 5 rows
df.tail()     # last 5 rows
```

#### **f. Check data types**

```python
df.dtypes
```

* Useful for identifying categorical vs numerical columns.

#### **g. Detect duplicates**

```python
df.duplicated().sum()
```

#### **h. Count unique values per column**

```python
df.nunique()
```

---

If you want to go a bit deeper:

* Use **`df.value_counts()`** for frequency analysis on specific columns.
* Use **`df.corr()`** to see correlations between numeric features.

---

Would you like me to show the **next step** — how to handle missing values, duplicates, and inconsistent data (i.e., the actual preprocessing part)?
