1. regression cost functions
- Sum of Squares due to Regression (SSR)
![unnamed_b5d236f7ce024755992fb77a127aa8d1](unnamed_b5d236f7ce024755992fb77a127aa8d1.png)
- Sum of Squares  of Error (SSE)
![unnamed_6593e663b1eb4f84b95bea3420fbcfbb](unnamed_6593e663b1eb4f84b95bea3420fbcfbb.png)
- Sum of Squares Total (SST)
![unnamed_f59d935bf2a34f8c8f7a429c1d77f877](unnamed_f59d935bf2a34f8c8f7a429c1d77f877.png)

2. R^2^
- R^2^ = 1 - (SSE/SST) = SSR/SST
- ranges from 1 to 0
- higher value means higher accuracy
- as features are added, never decreases => can set feature coefficient to 0 to ignore

3. improving regression models
- reduce variance => low test error - [1]
- filter out bad features

4. adjusted R^2^
- accounts for number of features (degree of freedom)
![unnamed_e2a953bd437140d09b25543bd5f2a2fe](unnamed_e2a953bd437140d09b25543bd5f2a2fe.png)

5. regularization
- constrains β coefficient estimates
- reduces variance 

notes
[1]: high variance => small changes in training data set leads to big changes in fitted model (overfitting)

reference:
- Gachon University - Machine learning lecture