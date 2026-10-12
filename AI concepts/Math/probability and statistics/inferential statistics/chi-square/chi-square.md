1. chi-square
- test for significant relationship between two categorical variables in bivariate table
- requires no assumption about shape of population distribution 
- requires random sampling
- formula
![unnamed_0d8390cbd7614506bef2b3a2b1c4910e](unnamed_0d8390cbd7614506bef2b3a2b1c4910e.png)
- limitations
   - doesn't give information about strength of relationship
   - sensitive to sample size
   - sensitive to small expected frequencies in table

2. illustration
- add rows and columns
![unnamed_7d6f899d282f4a1a832e02982bc0f1ee](unnamed_7d6f899d282f4a1a832e02982bc0f1ee.png) 
- compute expected value(row total * column proportion) for each cell
![unnamed_07276d9e333644fc841aff4e64445b9b](unnamed_07276d9e333644fc841aff4e64445b9b.png)
- subtract expected from actual, square it, and divide by expected

![unnamed_bc5beb7dde8046968384dd4dbb87134e](unnamed_bc5beb7dde8046968384dd4dbb87134e.png)![unnamed_f92cbbb073884f3a829e617875e62060](unnamed_f92cbbb073884f3a829e617875e62060.png)
- sum values
1.099 + 0.918 + 1.136 + 0.949 = 4.102 = chi-value
- get critical value or convert chi-value to p value
![unnamed_d22b85650a0e4ff582bb9633265734f8](unnamed_d22b85650a0e4ff582bb9633265734f8.png)
critical value = 3.841
or
chisq.dist.rt(4.102,1) => p=0.04283
- compare values
4.102 > 3.841 => calculated value > critical value
0.04283 < 0.05 => p value < level of significance 
=> reject H~0~

3. chi-square distribution
![unnamed_00ab348cfbf641d58b9df75cb594c311](unnamed_00ab348cfbf641d58b9df75cb594c311.png)
- positively skewed
- as df increases chi-square distribution becomes symmetrical

4. chi-square test in machine learning
- use to select features dependent on response
- can determine relationship between predictor categorical feature and response categorical feature

reference:
- Gachon University - Machine learning lecture