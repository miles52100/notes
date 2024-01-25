# Simpson's paradox

Not a true paradox, but still very counter-intuitive.
I find it most naturally illustrated using 2-d vectors and the parallelogram rule for addition.

Take two people (things) X, Y say. X has $N_X$ events say and scores some value x say, so $x\leq N_X$. Similarly for $Y$.

Not it can happen that under this score $X$ 'beats' $Y$, $x>y$, however if we partition the events into two disjoint subsets, say they occured over two time periods, and you only look at events in the first or second time period.

Let's suppose $N_X=N_{X,1} + N_{X,2}$ etc.
Then $Y$ can beat $X$'s score in each time period, and yet when you combine them, $X$ beats $Y$.

Viewing the score of $X$ in time period one as the slope of the vector $(N_{X,1},x_1)$, etc. we see that we need $X's$ first slope to be less than $Y$'s and simliarly for the second slope. But we need $X$'s second slope to be bigger than $Y$'s first slope and other conditions for this 'paradox' to work.

**Example**

The smallest example, of game playing and counts of wins say.

Player X plays p games and wins q say in a time period. 
So $q\leq p$
Ditto for Y. We say one beats the other if they have a better score $= q/p$

|round | player | (p,q) | score | top scorer|
|------|--------|-------|-------|-------|
|1     | X      | (2,0) | 0%    | no    |
|      | Y      | (4,1) | 25%   | yes   |
|2     | X      | (4,3) | 75%   | no    |
|      | Y      | (1,1) | 100%  | yes   |
||
| 1+2  | X       | (6,3)  | 50% | yes   |
|      | Y       | (5,2)  | 40% | no    |

