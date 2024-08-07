# Order Statistics

We have $n$ datapoints $\{x_1,\ldots,x_n\}$ drawn independently from a known continuous distribution with probability density function $f$ and cdf $F$.

Relabelling and ordering by value we have 
$\{x_{(1)},\ldots,x_{(n)}\}$, the *Order Statistics*.

To get the pdf and cdf of $X_{(1)}$ and $X_{(n)}$ is not hard.

$$
\mathbb{P}(X_{(1)} > x) = \mathbb{P}(\textrm{all} X_{i} > x) = (1-F(x))^n
$$
So
$$F_{X_{(1)}}(x) = 1 - (1-F(x))^n$$
and 
$$f_{X_{(1)}}(x) = nf(x)(1-F(x))^{n-1}$$

Similarly
$$F_{X_{(n)}}(x) = F(x)^n$$
and
$$f_{X_{(n)}}(x) = nf(x)F(x)^{n-1}$$

For computing the $ith$ order statistic cdf and pdf, it's easiest to proceeed by computing
$\mathbb{P}(x<X_{(i)} < x + \delta x)$, where we assume $\delta x$ so small that no other order statistic lies in the interval.

With that assumption the above probability works out as
$$
\frac{n!}{(i-1)!(n-i)!}F(x)^{i-1}(1-F(x+\delta x))^{n-i} (F(x+\delta x) - F(x))
$$
Letting $\delta x\rightarrow 0$, we derive
$$
f_{X_{i}}(x) = \frac{n!}{(i-1)!(n-i)!}F(x)^{i-1}(1-F(x)))^{n-i}f(x)
$$

## Speical case

An important special case is when $X\sim U(0,1)$, i.e., the original data points are drawn from the uniform distribution.

Plugging in values for $F$ and $f$, then shows 
$$
X_{(i)}\sim\textrm{Beta}(\alpha=i,\beta=n-i+1)
$$
So this has mean $i/(n+1)$

## Naive approach to using Order Statistics

Suppose we thought $X$ was well modelled with a normal distribution.
We might compute the MLE for the mean and variance to get $F$ and $f$ and then plug these into the order statistics formulae, to compute the expected value of the order statistics. We can then compare these to the observed values to see if they're 'reasonably close'.

Two main problems here:

  1. Functional form of pdf for order statistics is such that for most distributions (f) it can only be integrated numerically

  2. The plot of expected value vs. observed order stat is likely to be non-linear and assessing whether a good fit is hard.

These problems can be avoided with a transformation. See [The Probability Integral Transform](./probability_integral_transform.md)
