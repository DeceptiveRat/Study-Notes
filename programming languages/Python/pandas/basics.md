1. series
- saves data and indices

```python3
data=pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
print(data)
data['b']
```

![unnamed_4919edb1fa6743ad81e584ae9a4597d0](unnamed_4919edb1fa6743ad81e584ae9a4597d0.png)

2. DataFrame
![unnamed_30a072631fe342eb847feaddd7692e3a](unnamed_30a072631fe342eb847feaddd7692e3a.png)
- has rows and columns
- can perform operations on cells
- view size with shape()

3. read/write
- to_csv()
- to_excel()
- read_csv()
- read_excel()

4. pandas slicing
- loc(): uses column names
- iloc(): uses numbers

![unnamed_62723de948bb462eb4527f37cdf39bb9](unnamed_62723de948bb462eb4527f37cdf39bb9.png)![unnamed_56f3d45da70c4d5ea141a0d27852f399](unnamed_56f3d45da70c4d5ea141a0d27852f399.png)

5. data check
- isnull()
- notnull()
- dropna()
- fillna()

6. aggregate functions
- sum()
- mean()
- sort_values()

7. search for data
- query()

```python3
df_filter = df.query('age>=30')
```


8. apply function
- apply(func, axis=0, raw=False)
   - raw: pass parameter as array(True) or Series(False)

```python3
def sum_array(arr):
	return arr.sum()

sum_arrays = df.apply(sum_array, axis=0, raw=True)
```


reference:
- 가천대 - Python programming
