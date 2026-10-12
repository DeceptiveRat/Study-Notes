
```python
#!/bin/python3 

from scipy.stats import chi2_contingency
from scipy.stats import chi2

#contingency table
table = [[200, 150, 50], [250, 300, 50]]
stat, p, dof, expected = chi2_contingency(table)
print(expected)

prob = 0.95
critical = chi2.ppf(prob, dof)
print("critical = %.3f, stat = %.3f" %(critical, stat))

if abs(stat) >= critical:
	print("reject H0")
else:
	print("fail to reject H0")
```
