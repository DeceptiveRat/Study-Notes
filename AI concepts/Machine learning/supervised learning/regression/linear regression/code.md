manual:

```python3
import numpy as np
x=np.array([5, 7, 9])
y=np.array([16, 21, 24])

mx = np.mean(x)
my = np.mean(y)
print("mx", mx)
print("my", my)

divisor = 0
for i in x:
  divisor += (i-mx)**2

dividend = 0
for i in range(len(x)):
  dividend += (x[i]-mx)*(y[i]-my)
a = dividend/divisor
b = my-a*mx
xp = 6
y = a*xp + b
print("y value ", y)
```


using scikit-learn:

```python3
import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pylab as plt

x=np.array([5, 7, 9]).reshape(-1, 1)
y = np.array([16, 21, 24])

model = LinearRegression()
model.fit(x, y)

y_pred = model.predict([[6]])
print("y prediction: ", y_pred)
```
