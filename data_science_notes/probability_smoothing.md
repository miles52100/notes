# Probability Smoothing


## Laplace or additive smoothing
A statistical technique to increase the probability of less likely elements
by increasing the count of all elements in the dataset by one.

Smoothing is very important in NLP where some words may have zero or close to zero probabilities such as out-of-vocabulary words

More precisely Laplace, Lidstone or additive smoothing is a technique applied to smooth categorical data. 
Given a set of observations $x=(x_1,\ldots, x_d)$ from a $d$-dimensional multinomial distribution with $N$ trials, a smoothed version of the counts gives the estimator

  $$
  \hat{\theta} = \frac{x_i+\alpha}{N+d\alpha}
  $$

  The *smoothed* count is $N\theta_i$, and the pseudocount $\alpha>0$ is the smoothing parameter.

Additive smoothing is a type of [shrinkage](./shrinkage.md#shrinkage) estimator.


There are several critiques of additive smoothing. The original Laplacian idea was in connection with the [sunrise problem](https://en.wikipedia.org/wiki/Sunrise_problem). 
Laplace himself undertsood that it was a misapplication of the rule of succession, because the approach fails to take into account all the additional evidence available to conclude the probability (IMHO uncomputable) of the sun rising tomorrow is far higher than the rule would indicate.
So the real issue is knowing when it's applicable.

The Bayesian analysis of prior distribution and what this should be when in total ignorance is illuminating.
See [Rule of succession](https://en.wikipedia.org/wiki/Rule_of_succession) and in particular the observation that the rule implicity takes into account before any observations one success and one failure (hence the $s+1$ and $n+2$ values). This implicitly implies that $p$ could be $0$ or $1$, but that is knowledge total ignorance would not have. The article by [here](https://www.phil.cmu.edu/projects/carnap/editorial/latex_pdf/1945-3.pdf) and [Noninformative stats](http://www.stats.org.uk/priors/noninformative/Smith.pdf) help justify a totally ignorant prior on a probability $p$ being the improper prior of $\propto \frac{1}{p(1-p)}$ (it's easier to work with the success:failure ratio $X=\frac{S}{N-S}$ where the prior is $\propto\frac{1}{X}$)



## References

 * [Generalized Probability Smoothing](https://arxiv.org/pdf/1712.02151v1.pdf)
 