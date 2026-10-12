1. logistic regression
- used to fit a curve to data in which the dependent variable is binary 
- does not assume relationship between independent and dependent variables is linear
- does not assume dependent variable or error terms are distributed normally

2. when to use logistic regression
![unnamed_59ca0e6a1b2848e29787918acc46d3a1](unnamed_59ca0e6a1b2848e29787918acc46d3a1.png)
![unnamed_b3be5a0b8d9a41638ecd6b075ced74ec](unnamed_b3be5a0b8d9a41638ecd6b075ced74ec.png)
=> linear regression is not viable

- modify table

![unnamed_9f625c00e64943e296a69d9416b5a218](unnamed_9f625c00e64943e296a69d9416b5a218.png)![unnamed_9fcbd9ea4fc54daeb49f3d6970048f5c](unnamed_9fcbd9ea4fc54daeb49f3d6970048f5c.png)
=> we can use SIGMOID function

3. relation to logits
- in logistic regression we seek a model of:
logit(p) = a + bX
- can reduce logistic regression to linear regression with odds

![unnamed_231f7eeddf954a11bc867ce0494a694e](unnamed_231f7eeddf954a11bc867ce0494a694e.png)![unnamed_3ebe920698d24022b380efaa311f1357](unnamed_3ebe920698d24022b380efaa311f1357.png)

reference:
