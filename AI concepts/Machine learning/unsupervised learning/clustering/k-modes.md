1. k-modes
- used for categorical data
- replace means with modes (most frequent value)
![unnamed_483b1d845233470bb993d4c6b648c76d](unnamed_483b1d845233470bb993d4c6b648c76d.png)
- centroids are represented by mode vectors
![unnamed_0990b422d3694ebdaed9bf153fb9aeed](unnamed_0990b422d3694ebdaed9bf153fb9aeed.png)
- minimize objective function
![unnamed_1a286f133c6f4b9bb5a3fdbde792454b](unnamed_1a286f133c6f4b9bb5a3fdbde792454b.png)
l: clusters
i: samples
j: attributes

2. process
- select k objects as initial modes
- repeat until no change
   - calculate distance between each object and mode vectors
   - assign objects to mode with shortest distance
   - select new mode for each cluster

3. distance function
- Hamming distance - number of different attribute values 
- can also use:

![unnamed_f2deb7c75c3e446581304d9470a63420](unnamed_f2deb7c75c3e446581304d9470a63420.png)![unnamed_c642c3d6df3540fdaf5025453114a786](unnamed_c642c3d6df3540fdaf5025453114a786.png)

reference:
- Gachon University - Machine learning lecture