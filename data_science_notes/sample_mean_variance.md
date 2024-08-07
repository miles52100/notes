# Sample Mean and Variance

Basic cooncepts in statistics

Let $X_1,x_2,\ldots X_n$ be random variables.

## Sample Mean

The **sample mean**, is defined by

$$
\overline{X}_n = \frac{1}{n}\sum_{i=1}^nX_i
$$

## Sample Variance

The **sample variance**, is defined by

$$
S_{n}^2 = \frac{1}{n-1}\sum_{i=1}^n(X_i-\overline{X}_n)^2
$$

We then have the basic

*Theorem*

Let $X_1,\ldots,X_n$ be IID and let
$\mu=\mathbb{E}(X_i)$, $\sigma^2=\mathbb{V}(X_i)$.
Then
$$
\mathbb{E}(\overline{X}_n)=\mu,
$$
$$
\mathbb{V}(\overline{X}_n)=\frac{\sigma^2}{n}
$$
and
$$
\mathbb{E}(S_{n}^{2})=\sigma^2
$$
