1. random forest
- combines output of multiple decision trees to reach a single result

2. ensemble methods
- made up of a set of classifiers
- predictions are aggregated to identify most popular result
- well-known methods:
   - bagging
   - boosting

3. random forest algorithm
- extension of bagging method
- utilizes both bagging and feature randomness to create an uncorrelated forest of decision trees
- only selects a subset of features

4. how it works
- 3 main hyperparameters need to be set before training:
   - node size
   - number of trees
   - number of features sampled
- each tree is comprised of a data sample drawn from a training set with replacement
- feature bagging adds more diversity to dataset and reduces correlation among decision trees
- regression => decision trees will be averaged
- classification => majority vote

5. benefits
- reduced risk of overfitting
- flexibility
- easy to determine feature importance

6. challenges
- time-consuming process
- requires more resources
- more complex

reference:
<https://www.ibm.com/think/topics/random-forest>