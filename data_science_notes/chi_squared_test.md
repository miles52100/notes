# The $\chi^{2}$-Test

An important classical test. See also the $t$-test [here](./chi_squared_test.md)

Suppose we have $n$ events that can occur in trial and we record the vector of counts
$(X_1,\ldots, X_n)$, so $X_i$ is the number of times we see event $i$ in $N$ trials say. We have $\sum_{i=1}^{n}X_i=N$.

Suppose our unknown parameter is $(\theta_1\ldots,\theta_n)$ where $\sum_{i=1}^n\theta_i=1$, $\theta_i$ being the probability of event $i$ occuring.

Then the likelihood is the multinomial probability
$$
\mathbb{P}(X_1=x_1,\ldots,X_n=x_n\mid\theta_1,\ldots,\theta_n)=\frac{N!}{x_1!x_2!\cdots x_n!}\theta_{1}^{x_1}\cdots\theta_{n}^{x_n}
$$

Consider the hypotheses

$$
H_0:\;\; \theta_1=p_1,\theta_2=p2,\ldots,\theta_n=p_n;
$$

$$
H_1:\;\;\textrm{one or more }\theta_i\neq p_i
$$

Then the $\chi^{2}$-test uses the test statistic
$$
K=\sum_{i=1}^{n}\frac{X_i-E_i)^2}{E_i}
$$
and the rejection region $(C_{\alpha},\infty)$, where $E_i=Np_i$ is the ecpected number of occurences of event $i$ in $N$ trials, when the null holds.
For a given significance level $\alpha$ we can set the rejection regiond using the following result

**Theorem**

*For large* $N$, $K$ *is approximately distributed as* $\chi^{2}_{(n-1)}$

This has a simple proof when $n=2$.
We note that the marginal distribution of $X_1$ is $B(N,p_1)$. We can the use the normal approcimation to the binomial to give us $X_1\sim N(Np_1,Np_1(1-p_1))$.
Then, because the square of a standard normal RV has a chi-squared distribution we have

$$
\frac{(X_1-Np_1)^2}{Np_1(1-p_1)}
\sim\chi^{2}_{(1)}
$$

It's also easy to show that
$$
K=\frac{(X_1-Np_1)^2}{Np_1}+\frac{(X_2-Np_2)^2}{Np_2}=\frac{(X_1-Np_1)^2}{Np_1(1-p_1)}
$$
using $X_1+X_2=N$ and $1=p_1+p_2$, from which it follows that $K\sim\chi^{2}_{(1)}$.
Unfortunately this argument cannot be made to generalise and the general proof is more complicated.
The most interesting proof shows that the $\chi^2$ test is asymptotically a Likelihood Ratio test, i.e. $K\approx -2\log\lambda$ for large $N$, where
$$
\lambda=\frac{p_{1}^{x_1}\cdots p_{n}^{x_n}}\max_{\theta1,\ldots,\theta_n}{\theta_{1}^{x_1}\cdots\theta_{n}^{x_n}}
$$
and the result then follows, noting the degrees of freedom are $n-1$ rather than $n$ as $H_0$ is only about $n-1$ linearly independent parameters.


## Examples

### Testing monographic roughness
We have an $n$ letter alphabet and a sample of $N$ characters, each character equals the $i^{th}$ letter with probability $\theta_i$.
We're interested in testing

$$
H_0:\;\; \theta_1=1/n\;\;\textrm{for all } i;
$$

$$
H_1:\;\;\textrm{one or more }\theta_i\neq 1/n
$$
If $x_i$ is observed occurence of letter $i$, the test statistic is
$$
K=\sum_{i=1}^{n}\frac{(X_i-N/n)^2}{N/n}
$$
and $K\sim\chi^{2}_{(n-1)}$ under $H_0$.
The actual test at significance level $\alpha$ is to reject $H_0$ if $K\geq C_{\alpha}$ where $C_{\alpha}$ is given by

$$
\mathbb{P}(K\geq C_{\alpha}\mid K\sim\chi^{2}_{(n-1)})=\alpha
$$

### Goodness of fit test

Suppose we have observations $y_1\ldots,y_N$ and want to test

$$
H_0:\;\;\textrm{The observations are an indepedent sample from a distribution with density }f_X(x)
$$
$$
H_1:\;\;\textrm{They're not}
$$

If the density has support on interval $[a,b]$ then we split this into $n$ intervals $[a,a_1],(a_2,a_3],\ldots,(a_n,b]$ such that $\mathbb{P}(X\in(a_{i-1},a_i])=1/n$
Count the observations that fall into each of these intervals and call the counts $x_1,\ldots,x_n$. Then, under $H_0$, these counts should be a sample from a multinomial distribution with aprameters $(1/n,\ldots,1/n)$ and so the appropriate test statistic is once again

$$
K=\sum_{i=1}^{n}\frac{(X_i-N/n)^2}{N/n}
$$
and $K\sim\chi^{2}_{(n-1)}$ under $H_0$.

*Remarks*

  1. It's not necessary to use the intervals above, you could use any set as long as you replace the expected counts above with ones appropriate to the intervals used.

  2. Recall the distribution $K$ is only asymptotically $\chi^2$ so the expected count in each interval should be reasonably large, as a rule of thumb each $x_i\geq 5$

