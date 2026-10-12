 1. ridge regression
- adds penalty term to cost function => force reduction of β
- uses L2 norm in penalty term => coefficients rarely become zero
- minimizes
![unnamed_27ac9340f92746c3995718135a2771eb](unnamed_27ac9340f92746c3995718135a2771eb.png)
- penalty term makes estimates biased but reduces variance
   - bias: difference between actual value and estimated value
   - variance: spread of estimated values
![unnamed_f8ac7a99069449e0b4733cf7c9b3ee9f](unnamed_f8ac7a99069449e0b4733cf7c9b3ee9f.png)
- limitations
   - retains features => complex to compute

2. RSS
![unnamed_6e406e6f3baf4cddaa7e0e4834976dda](unnamed_6e406e6f3baf4cddaa7e0e4834976dda.png)
RSS = |y - Xβ|^2^

3. λ
![unnamed_ab7ea4af33b1459e8bcc357f26f6f0e9](unnamed_ab7ea4af33b1459e8bcc357f26f6f0e9.png)
- a.k.a alpha
- determined through cross-validation
- as λ increases coefficients shrink towards zero
![unnamed_16c9e117730740b38f9d40bf07a24441](unnamed_16c9e117730740b38f9d40bf07a24441.png)


4. scaling
- coefficient estimates change significantly due to sum of squared coefficients term in penalty term
- standardize before applying ridge regression
![unnamed_387adb4f51ec46ae945d0db95a1cfe2c](unnamed_387adb4f51ec46ae945d0db95a1cfe2c.png)

reference:
- Gachon University - Machine learning lecture