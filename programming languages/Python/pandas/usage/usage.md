- print first few data

```python
print(data.head())
```

- print columns

```python
print(data.columns)
```

- change column name

```python
data.rename(columns={"oldName": "newName", "AnotherOld": "AnotherNew"}, inplace=True)
```

- drop column

```python
data.drop(['column_name'], axis=1, inplace=True)
```

- one hot encoding

```python
import pandas as pd
from sklearn.preprocessing import OneHotEncoder

# Example
enc = OneHotEncoder(drop="first", sparse_output=False)  # drop first to avoid dummy trap
encoded = enc.fit_transform(data[['mainroad']])

# Get new column names from encoder
encoded_df = pd.DataFrame(encoded, columns=enc.get_feature_names_out(['mainroad']))

# Reset index to match original DataFrame
encoded_df.index = data.index  

# Drop original column and join new ones
data = data.drop('mainroad', axis=1).join(encoded_df)
```

- sort columns alphabetically

```python3
df = df[sorted(df.columns)]
```

- view unique values for column

```python3
df['column1'].unique()
```

- find indexes of rows with certain values

```python3
df[df['column'] == 'value'].index
```

- label encoding

```python3
df1['profilename_encoded'] = df1['review_profilename'].astype('category').cat.codes
df1.drop(columns=['review_profilename'], inplace=True)
```

   - astype('category'): convert column to category type
   - .cat.codes: assign each unique category a number

```python3
df1['beer_style'] = df1['beer_style'].astype('category')
df1['beer_style_encoded'] = df1['beer_style'].cat.codes
id_to_style = dict(enumerate(df1['beer_style'].cat.categories))
style_to_id = {v: k for k, v in id_to_style.items()}
df1.drop(columns=['beer_style'], inplace=True)

df2['beer_style_encoded'] = df2['beer_style'].map(style_to_id)
df2.drop(columns=['beer_style'], inplace=True)
```

   - create mappings and inverse mappings for future use
- get column B where column A is X

```python3
result = df.loc[df['A'] == 'x', 'B']
result = df.loc[df['A'] == 'x', ['B', 'C']]
```

- simple data normalization for multiple columns

```python3
df_normalized = df.apply(lambda col: (col - col.mean()) / col.std(), axis=0)
```

- efficient data normalization for multiple columns using groups

```python3
# Define the columns you want to normalize
review_cols = [
    'review_appearance', 
    'review_aroma', 
    'review_palate', 
    'review_taste', 
    'review_overall'
]

# Apply the z-score normalization ( (x - mean) / std ) 
# grouped by user, and assign it back to the original columns
df1[review_cols] = df1.groupby('profilename_encoded')[review_cols].transform(
    lambda x: (x - x.mean()) / x.std()
)
```
