# The Probability Integral Transform
For motivation see [Order Statistics](./order_statistics.md)

Suppose $X$ is a random variable with pdf $f$ and strictly monotonic cdf $F$.

We consider the distribution of $F(X)$.

$$
\mathbb{P}(F(X))\leq y) = \mathbb{P}(X\leq F^{-1}(y)) = F(F^{-1}(y))=y
$$

In other words, irrespective of the exact distribution of $X$, $F(X)\sim U(0,1)$

$F(X)$ is called the **probability integral transform**

To conintue the discussion [here](./order_statistics.md#naive-approach-to-using-order-statistics)

we can now see that the transformed order statistics $F(x_{(1)}),\ldots,F(x_{(n)})$ should have expected values 
$1/(n+1),2/(n+1),\ldots,n/(n+1)$ resp.

In practice we draw points from $U$ and apply $F^{-1}$. More precisely we compute $F^{-1}(i/(n+1))$ as our expected value for the $ith$ order statistic.
Then if our model is correct, note this is our assumed choice of $F$, plotting these values against observed should be approximately a straight line.

### Two small examples
 
1. $X\sim$ exponential with parameter $\lambda$

    $$U=F(X)=1-e^{\lambda X}$$
    so 
    $$
    X = -\frac{1}{\lambda}\log(1-U)
    $$

    So plot $X_{(i)}$ against $\log(1-i/(n+1))$)

2. $X\sim$ Weibull with parameter $\rho,\kappa$

    $$U=F(X)=1-e^{(\rho X)^\kappa}$$
    so 
    $$
    \log(X) = \frac{1}{\kappa}\log(-\log(1-U)) - \log(\rho)
    
    $$

    So plot $\log(X_{(i)})$ against $\log(-\log(1-i/(n+1)))$
    Gradient and intercept provide rough estimates for the parameters.

**Warning** 
Even with substantial amounts of data, we can expect the end percentiles to deviate substantially from a straight line as experiments with X\sim N(0,1)$ will confirm.

