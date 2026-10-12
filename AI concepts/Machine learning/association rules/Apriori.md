1. Apriori
- rules originating from same itemset have same support => consider only frequent itemsets
- may generate a large number of candidate itemsets
- requires many scans of database

2. generating frequent itemsets
- get minimum support threshold
- generate a list of one-itemset
- prune items that don't meet threshold
- generate list of two-itemset
- prune
- repeat until k-itemset is pruned

3. walkthrough

| TID | items |
| --- | --- |
| T1 | i1, i3, i4 |
| T2 | i2, i3, i5 |
| T3 | i1, i2, i3, i5 |
| T4 | i2, i5 |

- support threshold: 50%
- confidence threshold: 80%
- k = 3
- one-itemset pruning
![unnamed_a97df720b7334746b13e8b0d3b8e4e27](unnamed_a97df720b7334746b13e8b0d3b8e4e27.png)
drop i4

- two-itemset pruning
![unnamed_80b6eaaa4c04421591ce5bd5ac7431d1](unnamed_80b6eaaa4c04421591ce5bd5ac7431d1.png)

- three-itemset pruning
![unnamed_d8951a09d078436f807642717f2b67dc](unnamed_d8951a09d078436f807642717f2b67dc.png)

- generate candidate rules from itemset and prune
![unnamed_29c887054ede4a9fb9d230098c083dbb](unnamed_29c887054ede4a9fb9d230098c083dbb.png)

reference:
- Gachon University - Machine learning lecture