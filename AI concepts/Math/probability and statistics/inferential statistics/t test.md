1. t test
- compares two averages and measures how different they are
- three main types
   - independent samples t test
   - paired samples t test
   - single sample t test

2. t score
- ratio between "the difference between two groups of sample data" and "difference within groups"
- larger t score means more difference between groups
=> more likely to be repeatable in population
- each has a p value associated

3. independent samples t test
- a.k.a two samples t test
- compare means of two different group samples
- null hypothesis: μ~1~ = μ~2~
![unnamed_59f7230be219466d8d1689ae3f92a017](unnamed_59f7230be219466d8d1689ae3f92a017.png)
![unnamed_0989dbabf6f04b9eafca2e9974271c7e](unnamed_0989dbabf6f04b9eafca2e9974271c7e.png)

4. paired samples t test
- a.k.a correlated pairs t test, dependent samples t test
- compares means from same group sample at different times
- null hypothesis: mean of difference between paired samples is zero
- steps:
   - calculate difference between two datasets
   - calculate mean difference, d~m~ (difference between mean of each dataset)
   - calculate SD of differences, s~d~
   - calculate standard error of mean difference, SE(d~m~) = ![unnamed_481e0c532c3745edaf8506b67a7f3d18](unnamed_481e0c532c3745edaf8506b67a7f3d18.png)
   - calculate t-statistic, t = d~m~/SE(d~m~)
   - use t-distribution table to find p value
   - test null hypothesis




![unnamed_3579ec54f7d944aa93ceadeea9a1b373](unnamed_3579ec54f7d944aa93ceadeea9a1b373.png)
![unnamed_9bd475a3563f482f9443685dbd82a55b](unnamed_9bd475a3563f482f9443685dbd82a55b.png)![unnamed_1919347a89dd4c27bb0816fca5bae22c](unnamed_1919347a89dd4c27bb0816fca5bae22c.png)![unnamed_2d21abc909c54098b796a0e0386d2b5e](unnamed_2d21abc909c54098b796a0e0386d2b5e.png)

5. single sample t test
- compare mean of single group against known mean (population mean)


![unnamed_fcb5e88be4ee4fc99fc59b42625dfb10](unnamed_fcb5e88be4ee4fc99fc59b42625dfb10.png)![unnamed_d36448e7de0240cb837070e8eeea0005](unnamed_d36448e7de0240cb837070e8eeea0005.png)

6. paired samples t test illustration
- calculate sum of difference (Σd~i~) and sum of squared differences (Σ(d~i~^2^))
![unnamed_3a53adf906d84c589cce8a2886b380df](unnamed_3a53adf906d84c589cce8a2886b380df.png)
- calculate t
![unnamed_b33ba025ee544f34bab286c16544be66](unnamed_b33ba025ee544f34bab286c16544be66.png)
- calculate p value
![unnamed_7c822aae80a748299228e0a59e5f4440](unnamed_7c822aae80a748299228e0a59e5f4440.png)
- p value is between 0.025 and 0.01
- reject null hypothesis

7. two-tailed vs one-tailed
- two-tailed: possibility of relationship in two directions i.e. significantly different
- one-tailed: possibility of relationship in one direction i.e. significantly less/more

8. paired samples t test illustration

![unnamed_02534f6e962a4658ac6d57c40a1f60f4](unnamed_02534f6e962a4658ac6d57c40a1f60f4.png)
t = 5.72 
t![unnamed_fcf214c5e7d743599bfc37d34c7cdb43](unnamed_fcf214c5e7d743599bfc37d34c7cdb43.png)~crit~ = 2.776
t > t~crit~
=> reject H0
X - Y, same room - different room should have a difference of 2.776 in either direction if to be 95% sure they are independent. But it has a difference of + 5.72, making same room significantly better than different room

9. t test in machine learning
- select learning model by comparing results of different learning models

reference:
- Gachon University - Machine learning lecture