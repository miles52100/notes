# The $t$-test

Along with the $\chi^2$-test, see [here](./chi_squared_test.md), a standard classical test.

For a distribution with known variance $\sigma$, the CLT tells us 
$$
\frac{\sqrt{n}(\overline{X}-\mu)}{\sigma}\sim N(0,1)
$$

To test the hypothesis that $\mu=\mu_0$ we simplt compute the value of the above statistic at $\mu=\mu_0$ and check if appropriately small to accept the hypothesis.

This is known (somewhat pointlessly) as the $z$-test

What if we don't know $\sigma$ and have to estimate it?

Consider the statistic
$$
T=\frac{\sqrt{n}(\overline{X}-\mu)}{S}
$$
where $S$ is the estimated standard deviation (a.k.a standard error). 

As $n$ gets large, we know $S$ gets closer to $\sigma$, so we might hope $T$ converges to a normal distribution.

In fact for any $n$ this statistic has a $t$-distribution with $n-1$ degrees of freedom.

$$
\frac{\sqrt{n}(\overline{X}-\mu)}{S} \sim t_{(n-1)}
$$

The $t$-distribution is defined as 
$$\frac{N(0,1)}{\sqrt{\chi^{2}_{(n-1)}}}$$

And a simple analysis of the pdf shows $T\rightarrow N(0,1)$ as $n\rightarrow\infty$

*Remarks*

1. We used the traditional unbiased estimate $S=\sum (\overline{X}-X_i)^2/(n-1)$, not the maximum likelihood estimate, because this gives the required distribution for the above results

2. Tests are constructed in the obvious way: compute value of $T$ and compare to critical value from the appropriate $t$-distribution to decide if significant and whether to accept/reject the null.