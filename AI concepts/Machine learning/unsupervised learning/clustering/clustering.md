1. clustering
- groups unlabeled data based on similarities
- process raw data into groups

2. types
- exclusive clustering
   - data point can exist only in one cluter
   - e.g. k-means clustering
- overlapping clustering
   - allows data points to belong to multiple clusters
   - e.g. fuzzy k-means clustering
- hierarchical clustering
   - agglomerative clustering
      - bottoms-up approach
      - data points initially isolated
      - merged together iteratively based on similarity
      - similarity measurement methods:
         - ward's linkage: distance between two clusters is defined by increase in the sum of squared after clusters are merged
         - average linkage: mean distance between two points in each cluster
         - complete linkage: max distance between two points in each cluster
         - single linkage: min distance between two points in each cluster
   - divisive clustering
      - top-down approach
      - single data cluster is divided based on differences between data points
- probabilistic clustering
   - data points are clustered based on the likelihood that they belong to a particular distribution
   - e.g. Gaussian Mixture Model (GMM):
      - made up of an unspecified number of probability distribution functions => mixture model
      - leveraged to determine which Gaussian, or normal, probability a given data point belongs to