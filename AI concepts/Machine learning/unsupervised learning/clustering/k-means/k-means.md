1. k-means
- close data are clustered into same group
- k is the number of clusters
- limitations
   - not applicable for categorical data
   - unable to handle outliers
   - need to specify k
- variations
   - selection of initial centroids
   - distance measure
   - calculating cluster means

2. process
- initialize k centroids 
   - random selection or initial centroid sampling methods
- assign centroid to data points
   - uses euclidean distance to find closest centroid
- assign new centroids
   - new centroids are assigned the mean of all points for each cluster
- repeats until centroid points converge