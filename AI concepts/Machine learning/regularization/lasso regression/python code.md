
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import cross_val_score
from sklearn.preprocessing import OneHotEncoder
from sklearn.model_selection import GridSearchCV
from sklearn.linear_model import Lasso

# read dataset
sample_size = 545
DATAPATH = "data/Housing.csv"
data = pd.read_csv(DATAPATH)
data.price = data.price/10000

# one hot encoding
enc=OneHotEncoder(sparse_output=False, drop="first")
encoded=enc.fit_transform(data[['mainroad', 'guestroom', 'basement', 'hotwaterheating', 'airconditioning', 'prefarea', 'furnishingstatus']])
encoded_df = pd.DataFrame(encoded, columns=enc.get_feature_names_out(['mainroad', 'guestroom', 'basement', 'hotwaterheating', 'airconditioning', 'prefarea', 'furnishingstatus']))
encoded_df.index = data.index
encoded_data = data.drop(['mainroad', 'guestroom', 'basement', 'hotwaterheating', 'airconditioning', 'prefarea', 'furnishingstatus'], axis=1).join(encoded_df)

data = data.drop(['mainroad', 'guestroom', 'basement', 'hotwaterheating', 'airconditioning', 'prefarea', 'furnishingstatus'], axis=1)

x_encoded = encoded_data.drop(['price'], axis=1)
x = data.drop(['price'], axis=1)
y = data['price'].values.reshape(-1,1)
cv_list = [5, 10, 15, 20, 500]
parameters = {'alpha':[1e-15, 1e-10, 1e-8, 1e-4, 1e-3, 1e-2, 1, 5, 10, 20]}

for cv_used in cv_list:
	print("cv used: ", cv_used)

	lasso = Lasso()
	lasso_regressor = GridSearchCV(lasso, parameters, scoring='neg_mean_squared_error', cv=cv_used)

	lasso_regressor.fit(x, y)
	print("features dropped: ")
	print("best parameter:")
	print(lasso_regressor.best_params_)
	print("best score:")
	print(lasso_regressor.best_score_)

	lasso_regressor.fit(x_encoded, y)
	print("features encoded: ")
	print("best parameter:")
	print(lasso_regressor.best_params_)
	print("best score:")
	print(lasso_regressor.best_score_)
	print()
```
