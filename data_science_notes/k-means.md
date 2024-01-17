# k-Means

Clustering method

## Setup

Data points $(x_1,\ldots,x_n)$, each $x_i\in\mathbb{R}^d$ for some $d$.

We want to group these $n$ points into $k$ clusters $\{C_i\}_{i=1}^k$, where $k\leq n$.

## Objective
Find clusters $C:=\{C_i\}, 1\leq i\leq k$, such that
$$
\textrm{arg-min}_{C}\sum_{i=1}^k\sum_{x\in C_i} ||x-\mu_i||^2
$$
is minimized.

Put another way we seek a cluster partition $C$ such that 
$$
\textrm{arg-min}_{C}\sum_{i=1}^k |C_i|\textrm{Var}(C_i)
$$
is minimized.

Because, for $x,y\in C_i$, $||x-y||^2=||x-\mu_i||^2 + ||y-\mu_i||^2$, it's easily seen that the above minimization is equivalent to minimizing the pairwise squared deiviations of points:

$$
\textrm{arg-min}_{C}\sum_{i=1}^k \frac{1}{|C_i|}\sum_{x,y\in C_i}||x-y||^2
$$
is minimized.

## Algorithm

Use iterative refinement technique.

Given initial set of $k$ means: $\mu_{1}^{(1)},\ldots,\mu_{k}^{(1)}$ -proceed in two steps:

  * **Assignment** 
  
    Starting at $t=1$.
    Assign each point $x$ to mean closest (Euclidean distance), so $x$ gets assigned to cluster $C_{i}^{(t)}$ if
    $||x-\mu_{i}^{(t)}||^2$ is smallest.

  * **Update** 

    Recompute centroids 
    $$\mu_{i}^{(t+1)} = \frac{1}{|C_{i}^{(t)}|}\sum_{x\in C_{i}^{(t)}} x$$

  * **Stop** 

    Algorithm converges or stops when updates no longer change anything.

This does crucially depend on the initialization step, i.e. choice of initial $k$ means $\{\mu_{i}^{(1)}\}$

## Comments

  * Originally from signal processing
  * Above simple version is aka *Lloyd's algorithm* or *naive k-means*
  * Not guaranteed to find optimum
  * Finding optimal solution is NP-hard (even for $k=2$)
