# 1. Definition
Branch and bound is an algorithmic techique used to solve optimization problems. It is a systemic way of exploring all possible solutions to a problem by dividing the problem into smaller sub-problems and then applying bounds or constraints to eliminate certain subproblems into consideration

# 2. Characteristics
- optimal solution
Designed to find the optimal solution to an optimization problem by searching the solution space in a systemic way

- upper and lower bounds
Uses upper and lower bounds to reduce the size of the search space and eliminate subproblems

- pruning
Prunes the search tree by eliminating subproblems that cannot contain the optimal solution

- backtracking
Uses backtracking to return to a previous node in the search tree when a dead end is reached or a better solution found

# 3. Applications
- traveling salesman problem
- knapsack problem
- resource allocation
- network optimization
- game playing

# 4. Advantages
- optimal solution
- reduces search space
- proven performance
- incremental improvement: Starts with an initial lower bound and iterations improve it 

# 5. Disadvantages
- exponential time complexity
Worst-case time complexity is exponential in the size of the input, making it unsuited for handling complex issues

- memory-intensive
- sensitivity to problem-specific parameters
The quality of problem-specific constraints utilized determines how well the method performs

- limited scalability
Due to the exponential time complexity, may be unfit for some problems

---
reference:
(1) <https://www.geeksforgeeks.org/branch-and-bound-meaning-in-dsa/>