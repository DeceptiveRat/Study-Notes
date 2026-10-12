1. matrix factorization
- an approximation of SVD
- considered one of the best single-model approach to CF
- prediction for user~i~ for item~j~ (r~ij~) can be obtained as dot product of U~i~ and V^T^~j~
- objective(loss) function must be minimized using various algorithms
![unnamed_6e8b4522725049e99435698395adfe46](unnamed_6e8b4522725049e99435698395adfe46.png)

2. matrix factorization visualized
![unnamed_9c619af3936846adb1b00de49aa2da63](unnamed_9c619af3936846adb1b00de49aa2da63.png)
A: 
- user-item matrix
U:
- user latent matrix
- row i is called embedding for user i
V^T^:
- item latent matrix
- row j is called embedding for item j

3. demonstration


![unnamed_f3da3da1f4b0458e934f8d46507118ae](unnamed_f3da3da1f4b0458e934f8d46507118ae.png)