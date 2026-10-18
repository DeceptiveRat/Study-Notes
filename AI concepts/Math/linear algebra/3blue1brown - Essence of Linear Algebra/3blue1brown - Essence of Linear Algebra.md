1. basis vectors
![unnamed_bf73003de18c4c39a4794f0532d3bf40](unnamed_bf73003de18c4c39a4794f0532d3bf40.png)
- i-hat (x axis), j-hat (y axis) => basis vectors of the xy coordinate system

2. linear combination
- linear combination of vectors:
![unnamed_102ba335a85e43cf926e114f212b563d](unnamed_102ba335a85e43cf926e114f212b563d.png)

3. span
![unnamed_126516cbc6784f24b1c90ad580ef8eab](unnamed_126516cbc6784f24b1c90ad580ef8eab.png)
- span: set of all linear combinations

4. linearly dependent 
- at least one of the vectors can be expressed as a linear combination of the others
<=> linearly independent

5. linear transformation
- matrix vector multiplication
![unnamed_7cee90557c5f4513b913a6996ba7c43b](unnamed_7cee90557c5f4513b913a6996ba7c43b.png)
equivalent to moving i-hat to (a, c) and j-hat to (b, d), then seeing where (x, y) is moved to 
=> transformation

- matrix multiplication


![unnamed_37a99370e5034042b855f15ed75837ce](unnamed_37a99370e5034042b855f15ed75837ce.png)![unnamed_05ec9a186a6f467f89cae8ecf48b2d10](unnamed_05ec9a186a6f467f89cae8ecf48b2d10.png)![unnamed_89d88f51c9574d6c9d531fa7eb567be4](unnamed_89d88f51c9574d6c9d531fa7eb567be4.png)

6. determinant
- the factor by which a linear transformation changes any area (volume for 3d)

![unnamed_dec20e88fd5c4e95b474ccd6df153bbb](unnamed_dec20e88fd5c4e95b474ccd6df153bbb.png)![unnamed_69c1541746824eae8329cf97f297797c](unnamed_69c1541746824eae8329cf97f297797c.png)
6 is the determinant

- if orientation of space has been inverted, determinant is negative

![unnamed_57d7984a259e4a8b932ef5455bc28065](unnamed_57d7984a259e4a8b932ef5455bc28065.png)![unnamed_82b56899388649b28cb66aedbe647fa2](unnamed_82b56899388649b28cb66aedbe647fa2.png)
orientation inversion (2d)
use right hand rule for 3d. If after transformation, left hand has to be used, orientation inversion happened

- calculating determinant:
$$\det \begin{pmatrix}\begin{bmatrix}a&b\\c&d\end{bmatrix}\end{pmatrix} = ad-bc$$

![unnamed_8e1ca36ea764424ba677a84d90d70014](unnamed_8e1ca36ea764424ba677a84d90d70014.png)![unnamed_92fa099288e14681ac4bec8918218c58](unnamed_92fa099288e14681ac4bec8918218c58.png)

7. solving linear systems
![unnamed_cfc66de1d260421cb7728856c27d0b76](unnamed_cfc66de1d260421cb7728856c27d0b76.png)

8. inverse matrices and identity matrices
![unnamed_d7c7bac6e8bf4c959dbee80d84063a6e](unnamed_d7c7bac6e8bf4c959dbee80d84063a6e.png)
$$A^{-1}A = \begin{bmatrix}1&0\\0&1\end{bmatrix}$$
($A^{-1}$ is the inverse of matrix $A$ and $\begin{bmatrix}1&0\\0&1\end{bmatrix}$ is the identity matrix)

9. rank
- all vectors after transformation land in x dimension => x is the rank
- number of dimensions in the column space
- full rank => rank same as before transformation

10. column space
- set of all possible outputs

11. null space
- set of vectors that lands on the origin
- aka. kernel

12. nonsquare matrices
- 3x2 matrix
![unnamed_f730a4aa6486420491ea127e535af47a](unnamed_f730a4aa6486420491ea127e535af47a.png)
two columns mean two basis vectors
three rows mean landing spot is described with three coordinates

- transformations between dimensions