1. simple linear regression
- hypothesis
![unnamed_cf00ce3a443b4348924df2e6796d18b5](unnamed_cf00ce3a443b4348924df2e6796d18b5.png)
- cost function
![unnamed_ccbdbbd4249e45809e5362d790f036a6](unnamed_ccbdbbd4249e45809e5362d790f036a6.png)
- minimizing J(θ) is the goal
![unnamed_ef40b06fd52b422494e923bc8d0aa345](unnamed_ef40b06fd52b422494e923bc8d0aa345.png)

2. logistic regression
- hypothesis
![unnamed_466fa49fe5854ef6b85cda6e382576c1](unnamed_466fa49fe5854ef6b85cda6e382576c1.png)
- loss function
![unnamed_7514d773a01b4ff6a0cee941970f1031](unnamed_7514d773a01b4ff6a0cee941970f1031.png)
- cost function
![unnamed_b4cfeb09174f49eb8237ced42d6370af](unnamed_b4cfeb09174f49eb8237ced42d6370af.png)
- minimizing cost function is the goal

3. learning rate α
![unnamed_0503b4b6593342558e737f89d4f4453e](unnamed_0503b4b6593342558e737f89d4f4453e.png)
- automatically chosen with
   - Adam optimizer
   - AdaGrad
   - RMSProp

4. challenges
- computation time
- control learning rate => speed up convergence + minimize oscillations near local/global optima
![unnamed_190285a343ae40cab401585ff8072b8e](unnamed_190285a343ae40cab401585ff8072b8e.png)
- non-convex cost functions to optimize (i.e. saddle points)
![unnamed_9c9904ac895e4bcba2591e21bbd98574](unnamed_9c9904ac895e4bcba2591e21bbd98574.png)
- vanishing gradients
   - solution: use ReLU as activation function
![unnamed_6eb7696300aa42edbfae124eee7e1bd7](unnamed_6eb7696300aa42edbfae124eee7e1bd7.png)

5. variations
- batch gradient descent
   - compute gradient with entire training data
   - very slow
- stochastic gradient descent
   - compute gradient with single training data
   - much faster
- mini-batch gradient descent
   - compute gradient with small mini-batch

reference:
- Gachon University - Machine learning lecture