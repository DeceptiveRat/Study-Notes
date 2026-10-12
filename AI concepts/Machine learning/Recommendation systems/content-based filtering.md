1. content-based filtering
- recommend items that are similar to ones user liked
- requires "content", i.e. information about users and items
- uses machine learning models

2. demonstration
![unnamed_30991aae5b844119b67359b8ed145628](unnamed_30991aae5b844119b67359b8ed145628.png)![unnamed_d8c76242166649478c0d4565280146cb](unnamed_d8c76242166649478c0d4565280146cb.png)
- normalize items matrix by dividing occurrence by square root of number of attributes - [1]
![unnamed_49e93232efae4cacb0c3b8e5a9ac8345](unnamed_49e93232efae4cacb0c3b8e5a9ac8345.png)

- generate user profiles via sum product
![unnamed_3fe741267d4a42599648592ea5cd6fd0](unnamed_3fe741267d4a42599648592ea5cd6fd0.png)

- sum product user vector with item vector and IDF vector
![unnamed_2b502b160b2740cd82eff0612eee9567](unnamed_2b502b160b2740cd82eff0612eee9567.png)

3. advantages
- no cold start
- no sparsity problems
- no need for data on other uses
- able to recommend unique tastes
- able to recommend new and unpopular items
- can provide explanation of recommended items - [2]

4. disadvantages
- requires content to be encoded as meaningful features
- users' tastes must be represented as learnable function
- unable to exploit quality judgement of other users

reference:
- Gachon University - Machine learning lecture

notes
[1]: square root is used because having 2 times as many attributes doesn't make each weigh 2 times as less
[2]: list content-features that caused item to be recommended