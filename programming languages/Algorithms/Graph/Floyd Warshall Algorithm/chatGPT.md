The Floyd-Warshall algorithm is an efficient algorithm for finding the **shortest paths between all pairs of vertices** in a weighted graph. It works with both directed and undirected graphs and can handle negative edge weights (as long as there are no negative weight cycles). The algorithm is based on the principle of dynamic programming.

### Key Concepts:
- The algorithm computes the shortest paths between all pairs of vertices by considering whether a given vertex \( k \) can be used to find a shorter path between two vertices \( i \) and \( j \).
- It uses a 2D matrix \( D \) where \( D[i][j] \) represents the shortest distance from vertex \( i \) to vertex \( j \).
  
### Steps:
1. **Initialization:**
   - Create a 2D matrix \( D \) where each cell \( D[i][j] \) initially contains the weight of the edge between vertex \( i \) and vertex \( j \). If there is no edge, set \( D[i][j] \) to infinity (∞). Set \( D[i][i] = 0 \) for all \( i \), because the distance from any vertex to itself is 0.

2. **Algorithm Execution:**
   - For each vertex \( k \), consider whether it can be used as an intermediate point between any two other vertices \( i \) and \( j \).
   - For each pair of vertices \( i \) and \( j \), update the value of \( D[i][j] \) by checking if the path from \( i \) to \( j \) through \( k \) is shorter than the current value of \( D[i][j] \).
   
   The update rule is:
   \[
   D[i][j] = \min(D[i][j], D[i][k] + D[k][j])
   \]
   This checks if the path from \( i \) to \( k \) plus the path from \( k \) to \( j \) is shorter than the direct path from \( i \) to \( j \).

3. **Final Result:**
   - After considering all possible intermediate vertices, the matrix \( D \) will contain the shortest path distances between every pair of vertices.

### Example:

Let's consider a graph with 4 vertices and the following adjacency matrix representation (where a value of infinity (∞) indicates no direct path):

```
    0    3    ∞    7
    8    0    2    ∞
    5    ∞    0    1
    2    ∞    ∞    0
```

The matrix will be updated over three iterations, considering each vertex as an intermediate vertex.

#### Initialization:
The distance matrix \( D \) is initialized to the weights of the edges.

#### First iteration (consider vertex 1 as the intermediate vertex):
We check if paths that go through vertex 1 are shorter than the current paths.

#### Second iteration (consider vertex 2 as the intermediate vertex):
Update the matrix by checking if vertex 2 can serve as an intermediate vertex to shorten any path.

#### Third iteration (consider vertex 3 as the intermediate vertex):
Repeat the same process using vertex 3 as the intermediate vertex.

#### Final matrix:
After processing all intermediate vertices, the final matrix \( D \) will give the shortest distances between all pairs of vertices.

### Time Complexity:
- The time complexity of Floyd-Warshall is \( O(V^3) \), where \( V \) is the number of vertices. This makes it less efficient for very large graphs compared to algorithms like Dijkstra’s algorithm, which is better suited for finding the shortest path from a single source.

### Handling Negative Weight Cycles:
- If the algorithm detects that the shortest distance from a vertex to itself becomes negative (i.e., \( D[i][i] < 0 \)), it indicates the presence of a **negative weight cycle**. In this case, the shortest path problem has no solution because traversing the negative cycle indefinitely can decrease the path length without bound.

### Applications:
- **All-pairs shortest path**: For finding shortest paths between every pair of nodes in a graph.
- **Graph analysis**: Used in routing algorithms, network optimization, and in certain scheduling problems.

Would you like to see a code implementation of the Floyd-Warshall algorithm?