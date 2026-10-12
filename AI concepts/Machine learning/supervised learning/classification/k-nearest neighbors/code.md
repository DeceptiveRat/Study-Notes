
```python3
from sklearn.neighbors import KNeighborsClassifier
import numpy as np

x = np.array([[160, 60], [163, 60], [160, 64], [163, 54], [165, 61]])
y = np.array(['M', 'M', 'L', 'L', 'L'])

model = KNeighborsClassifier(n_neighbors=3)
model.fit(x, y)

y_pred = model.predict([[162, 61]])
y_pred_proba = model.predict_proba([[162, 61]])
print(y_pred)
print(y_pred_proba)
```
