1. collaborative filtering
- look only at ratings of like-minded users
- doesn't require information about users/items

2. collaborative filtering methods
- memory-based: use ratings to compute similarities between users or items
- model-based: use ratings to estimate or train a model to make rating predictions

3. advantages
- simple to implement
- doesn't require understanding of item content

4. disadvantages
- cold start: there must be enough users in system to find match
- sparse matrix leads to bad results
- can't recommend item that hasn't been previously rated
- popularity bias: cannot recommend items to someone with unique tastes

reference:
- Gachon University - Machine learning lecture