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


## Causation and counterfactuals

In the AoS book, chapter 16, on Causal Inference, there's a discussion of Simpson's paradox.

There it's claimed that:

  1. There is no real paradox
  2. To properly explain 1. is almost impossible without using counterfactuals.

They give the example of a binary treatment variable $X$ and binary outxome $Y$. There's a third binary variable $Z$, could be gender say.

So it's a clinical set-up with a treatment that may or may not be given and a clear outcome. 
They suppose the joint probability distribution of $(X,Y,Z)$ is given by


|    | Y=1 | Y=0  | Y=1 | Y=0 |
|----|-----|------|-----|-----|
|X=1 |.15  |.225  |.1   |.025 |
|X=1 |.0375|.0875 |.2625|.1125|
|    | Z=1 | Z=1  | Z=0 | Z=0 |

The values sum to 1.

The marginal distribution for $(X,Y)$ is

|    | Y=1 | Y=0  |     | 
|----|-----|------|-----|
|X=1 |.25  |.25   |.5   |
|X=0 |.3   |.20   |.5   |
|    |.55  |.45   |1.0    |

From these tables we conclude:

$$
\mathbb{P}(Y=1\mid X=1) - \mathbb{P}(Y=1\mid X=0) = -0.1\;\;\textrm{treatment is harmful}
$$
$$
\mathbb{P}(Y=1\mid X=1,Z=1) - \mathbb{P}(Y=1\mid X=0,Z=1) = 0.1\;\;\textrm{treatment is beneficial to men}
$$
$$
\mathbb{P}(Y=1\mid X=1,Z=0) - \mathbb{P}(Y=1\mid X=0,Z=0) = 0.1\;\;\textrm{treatment is beneficial to women}
$$

Clearly the text conclusions are nonsense. You cannot have a treatment that is good for men and good for women but bad overall!

It's claimed that the problem is with the text description of the mathematical inequalities.

The top inequality **does not mean** the treatment is harmful.

That statement, mathematically, would be 
$$
\mathbb{P}(C_1=1)<\mathbb{P}(C_0=1)
$$
Where $C_0, C_1$ are random variables representing the outcome if the subject received the treatment or not. Put succinctly in the **consistency relationship**

$
Y=C_X$

The point being that $C_1$ (outcome when treated) has a value when $X=0$ (no treatment given) but we don't get to observe it. It's a counterfactual - what would have happened if this patient had been given the treatment even though they didn't get it.

This is related to the earlier discussion of *association* and *causation* (both mathematically defined) not being the same. **But** they go on to prove that if the subjects are randomly assigned to treatment then *association* and *causation* are the same.
In the above it seems confusing because with the distribution you inherently assume observations are indepedently drawn from $X$, according to the marginal distribution. But that's not where the numbers came from - they're empirical distributions from the observed values of $(X,Y,Z)$.
In other words and somewhat informally the observed value of $X$ is not random and independent.

TODO - think more about this, feels like there should be some test to demonstrate that $X$ has not been randomly assigned??

In any event with the variables $C_0,C_1$ identified as the variables we actually care about when we use the statements about treatment being beneficial or not, it's trivial to prove there cannot be a Simpson like paradox

Suppose we have 
$$\mathbb{P}(C_1=1\mid Z=z) > \mathbb{P}(C_0=1\mid Z=z)$$
So for each confounding outcome $z$, treatment gives better outcome (probabilistically)

Then

$$
\mathbb{P}(C_1=1)  = \sum_{z}\mathbb{P}(C_1=1\mid Z=z)\mathbb{P}(Z=z) > 
$$
$$
\;\;\;\;\;\;\;\;\sum_{z}\mathbb{P}(C_0=1\mid Z=z)\mathbb{P}(Z=z) = \mathbb{P}(C_0=1)
$$
