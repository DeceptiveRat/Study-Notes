# Backtracking:
A general algorithm for finding all the solutions to some computational problems, notably, constraint satisfaction problems, that incrementally builds possible candidates to the solutions and abandons candidates as soon as it is apparent they do not fit the constraint. 

It is an algorithmic-techique for solving problems recursively by trying to build a solution incrementally, one piece at a time.

# Branch and Bound:
B&B is an algorithm design paradigm for discrete and combinatoric optimisation problems.

It consists of a systematic enumeration of candidate solutions. That is, the set of candidate solutions is thought of as forming a rooted tree with the full set at the root. 


| Parameter | Backtracking | Branch and Bound |
| --- | --- | --- |
| Approach | Backtracking is used to find all possible solutions to a problem | Used to solve optimisation problems |
| Traversal | DFS | DFS of BFS |
| Function | feasibility function | bounding function |
| Problems | Decision problems | Optimisation problems |
| Searching | Searches the state space tree until a solution is obtained | Searches the whole state space tree |
| Efficiency | More efficient | Less efficient |
| Application | N-Queen problem, Sum of subset, Hamilton cycle problem, graph coloring problem | knapsack problem, travelling salesman problem |
| Solve | Can solve almost any problem | Can't solve some problems |
| Next move | Next move can lead to a bad choice | Next move is always towards a better solution |
| Solution | First solution found | Optimal solution |


---
reference:
<https://www.geeksforgeeks.org/difference-between-backtracking-and-branch-n-bound-technique/>