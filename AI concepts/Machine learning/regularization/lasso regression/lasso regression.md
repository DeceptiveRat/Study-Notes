1. lasso
- Least Absolute Shrinkable Selector Operator
- uses L1 regularization => coefficient become zero more easily => feature selection
- minimizes
![unnamed_5086908bee474432aefaf12a613193cf](unnamed_5086908bee474432aefaf12a613193cf.png)
- limitations
   - large p, small n => selects at most n variables before it saturates
   - selects only one out of highly correlated variables group => lower accuracy

![unnamed_3e55644644f04475b7bef98a819ecf46](unnamed_3e55644644f04475b7bef98a819ecf46.png)

reference:
- Gachon University - Machine learning lecture