1. methods 
- elbow method
- silhouette index
- purity
- Dunn index
- Davies-Bouldin index

2. elbow method
- applied to results of K-means clustering
- find average distance of points in a cluster to its centroid and plot it
- pick k where average distance falls sharply
![unnamed_c6de843eca084213b06d3d1ef4888da6](unnamed_c6de843eca084213b06d3d1ef4888da6.png)

3. silhouette index
- applied to results of K-means clustering
- measure of how similar an object is to its own cluster compared to other clusters
- average of silhouette coefficients for all samples
![unnamed_d8ad1cf53ec445ea99b59565b58a8960](unnamed_d8ad1cf53ec445ea99b59565b58a8960.png)
a(i): average distance to all other points in cluster
b(i): average distance to all other points in other clusters
![unnamed_6e0939ea677447c8a823b5bd15094167](unnamed_6e0939ea677447c8a823b5bd15094167.png)

4. purity
![unnamed_77ca9b88801a4774b4030cdd4335609b](unnamed_77ca9b88801a4774b4030cdd4335609b.png)
- Ω is the set of clusters
- C is the set of classes

reference:
- Gachon University - Machine learning lecture