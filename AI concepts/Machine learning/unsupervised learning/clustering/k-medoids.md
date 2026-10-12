1. k-medoids
- cluster center is existing object => useful against outliers
- algorithms
   - PAM
   - CLARA
   - CLARANS
- each data point is a vector 
- can include numerical and categorical data

2. Partitioning Around Medoids (PAM)
- choose k objects as medoids
- repeat until no change
   - assign each object to cluster with nearest medoid
   - randomly select non-medoid and swap with medoid if it has less cost
- works only for small datasets

3. Clustering Large Applications (CLARA)
- draw multiple random samples of dataset and apply PAM on each
- efficiency depends on sampling
- may not find best clustering

4. Clustering Algorithm based on Randomized Search (CLARANS)
- 

reference:
- Gachon University - Machine learning lecture