1. decision tree
- split based on attributes to reach decision
![unnamed_d63b7af2273a46c6868bf38e071ba4cb](unnamed_d63b7af2273a46c6868bf38e071ba4cb.png)
- advantages
   - inexpensive to construct for small datasets
   - fast at classifying unknown records
   - easy to interpret for small trees
   - can handle continuous and categorical variables
   - can handle classification and regression tasks
- disadvantages
   - error-prone with too many targets
   - expensive to train
   - greedy => no global optimization

2. selecting the best node split
- compute Gini index of parent
![unnamed_778a4a6709494f6a9553586c23ab3948](unnamed_778a4a6709494f6a9553586c23ab3948.png)
- compute Gini index of each partition
![unnamed_ad94aedc3f4c48d499d9c7709fe1a113](unnamed_ad94aedc3f4c48d499d9c7709fe1a113.png)
- compute weighted Gini index
![unnamed_dc5266bbc85e411cbe51f5ee1afa999e](unnamed_dc5266bbc85e411cbe51f5ee1afa999e.png)
- compute Gini gain
![unnamed_4df877b8967e4694ae0bed6e69e487c1](unnamed_4df877b8967e4694ae0bed6e69e487c1.png)
- select split with highest Gini gain

3. selecting best splitting value for continuous attribute
- sort attribute values
- choose split position as intermediate between two values
- compute Gini index for each position
- chose position with least Gini index
![unnamed_9fed424efffc4fed9ee21c25d75d3b37](unnamed_9fed424efffc4fed9ee21c25d75d3b37.png)

4. classification (miscalculation error)
- simpler than Gini index
![unnamed_926c7e4989d34ab1b0bc6277de3afc05](unnamed_926c7e4989d34ab1b0bc6277de3afc05.png)
- illustration
![unnamed_a2e7a7a29f05435c93a5b56b5c0d20d2](unnamed_a2e7a7a29f05435c93a5b56b5c0d20d2.png)

5. pruning
- pre-pruning
   - stop subtree construction at some nodes
   - set early-stopping conditions
- post-pruning
   - remove nodes bottom-up or top-down
   - if classification error does not become worse after removing subtree, replace subtree with leaf node

reference: 
- Gachon University - Machine learning lecture