# Steiner Tree and the Steiner Tree Problem, STP

> Given a graph and a subset of vertices in the graph, a Steiner tree spans through the given subset. The Steiner Tree may contain some vertices which are not in the given subset but are used to connect the vertices of the subset. The given set of vertices is called Terminal Vertices and other vertices that are used to construct the Steiner tree are called Steiner vertices. The Steiner Tree Problem is to find the minimum cost of Steiner Tree. 

## Complexity

> The Steiner Tree Problem is known to be NP-hard, which means that it is unlikely that there is an efficient algorithm that can solve the problem for large instances. However, there are several approximation algorithms that can provide a suboptimal solution with a guarantee on the quality of the solution.

## Minimum Spanning Tree, MST

> MST is a minimum weight tree that spans through all vertices. If the given subset (or terminal) vertices are equal to the set of all vertices in the Steiner Tree problem, then the problem becomes the Minimum Spanning Tree problem. And if the given subset contains only two vertices, then it is the shortest path problem between two vertices. Finding out Minimum Spanning Tree is polynomial-time solvable, but the Minimum Steiner Tree problem is NP-Hard and the related decision problem is NP-Complete.

## Applications

> Any situation where the task is to minimize the cost of connection among some important locations like VLSI Design, Computer Networks, etc.

### Approximate solutions

>Since the Steiner Tree problem is NP-Hard, there are no polynomial-time solutions that always give optimal cost. Therefore, there are approximate algorithms to solve the same. Below is one simple approximate algorithm.
>
>1) Start with a subtree T consisting of 
>   one given terminal vertex
>2) While T does not span all terminals
>   a) Select a terminal x not in T that is closest 
>      to a vertex in T.
>   b) Add to T the shortest path that connects x with T
>
>The above algorithm is (2-2/n) approximate, i.e., it guarantees that the solution produced by this algorithm is not more than this ratio of optimized solution for a given graph with n vertices. There are better algorithms also that provide a better ratio.

The Viterbi algorithm can be used to approximate solutions to the STP.

The Viterbi algorithm is a dynamic programming algorithm commonly used in the field of computational linguistics, speech recognition, and error-correcting codes. However, it can also be applied to solving the Steiner Tree Problem, which is a well-known problem in computer science and graph theory.

The Viterbi algorithm can be used to compute the cost of the minimum-cost tree that spans a subset of the vertices in the graph. Specifically, given a set of vertices to be spanned by the tree, the Viterbi algorithm can be used to compute the cost of the minimum-cost tree that spans those vertices and any additional vertices required to create a connected tree.

This approach is useful because it provides an approximation to the Steiner Tree Problem that is guaranteed to be within a constant factor of the optimal solution. The runtime of the algorithm is polynomial in the size of the graph and the number of vertices to be spanned by the tree, making it an efficient and practical solution for large instances of the problem.