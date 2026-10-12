1. association rule applications
- recommendation system
- telecommunication
- banking services
- medical treatment
- basketball game analysis

2. association rule terms
- transaction: set of items "purchased" together
- item
- itemset: group of item
- k-itemset: itemset with k items
- mine: generate frequent itemsets
- association rule: pattern of X->Y:
   - antecedent: X
   - consequent: Y
- support(X): fraction of transactions that contain X
- confidence(X->Y) = P(Y|X)
- lift(X->Y) = confidence(X->Y)/support(Y):
   - lift > 1: positive correlation
   - lift = 1: no correlation
   - lift < 1: negative correlation

3. frequent itemset generation
- brute force:
   - list all possible association rules
   - compute support and confidence for each rule
   - prune rules that fail min-support and min-confidence
   - computationally prohibitive
- Apriori
- Frequent Pattern (FP) growth

reference:
- Gachon University - Machine learning lecture