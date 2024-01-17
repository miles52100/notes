# Hypothesis Testing

This is concerned with making decisions about a parameter $\Theta$ based on observation of data $\textbf{y}$.


The ususal set-up is a *null hypothesis*, $H_0$ and an *alternative hypothesis*, $H_1$.

Usually this is framed as 
$$
H_0: \Theta\in\bf{\Theta_0}
$$
$$
H_1: \Theta\in\bf{\Theta_1}
$$

When $\Theta$ can take a range of values under the hypothesis it's known as a *composite hypothesis*.

Where only one value is considered it's referred to as a *simple hypthesis*

$$
H_0: \Theta=\bf{\Theta_0}
$$
$$
H_1: \Theta=\bf{\Theta_1}
$$

This is an **important special case** which illuminates the approach and this is also the domain of the famous Neymann-Pearson Lemma.

Whatever the hypotheses it's important to state that they should be framed in a way the reflects the belief that

 * $H_0$ and $H_1$ are *mutually exclusive*, only one hypothesis can actually hold.
 * $H_0$ and $H_1$ are *exhaustive*, they cover all possibilites.

 For hypthesis testing we need a *test statistic*, a.k.a *score*, $T$ say.

$T$ is a RV and in particular 
$T=T(\bf{Y},\Theta_0,\Theta_1)$,
a function of the data $\bf{Y}$ and parameter values under the hyptheses.

A realisation of the test statistic is
$t=t(\bf{y},\Theta_0,\Theta_1)$

With these preliminaries we can now frame the standard hypthesis testing test.
It will take the form

$$
\textit{Accept\;} H_0 \it{\;if\;} T\in A, \it{ else\;reject\;} H_0
$$

Here the set $A$ is called the *Acceptance Region*.

So a test is defined by two quantities $\{T,A\}$.

So far we have just setup a generic framework for hypothesis testing.
There are two general approaches that differ, known as *Classical* and *Bayesian*

# Classical Hypothesis Testing

Recall the definitions:

$$
\alpha = \mathbb{P}(\textrm{Type I error}) = \mathbb{P}(T\not\in A\mid \Theta=\Theta_0)
$$
Called the *significance level* of the test, it's the probability we reject $H_0$ when it's true.

$$
\beta = \mathbb{P}(\textrm{Type II error}) = \mathbb{P}(T\in A\mid \Theta=\Theta_1)
$$
The probability we fail to reject $H_0$ when it's false.
The *power* of the test is $1-\beta$.

Ideally we'd want to minimize $\alpha$ and maximise the power. But clearly we can't do both independently.
Typically *we fix* the significance level, traditionally $\alpha\sim 0.05$ and then find a test that maximizes the power.

For simple hypothesis,we can construct the most powerful test given a significance level. This is 

*The Neymann-Pearson Lemma*

*For a fixed significance level $\alpha$, the most powerful test statistic is*
$$
T(\bf{Y},\Theta_0,\Theta_1) = \frac{f_Y(\bf{Y}\mid \Theta_0)}{f_Y(\bf{Y}\mid \Theta_1)}
$$
*and the the acceptance region $A=(C_{\alpha},\infty)$, where $C_{\alpha}$ is given by*

$$
\mathbb{P}(T<C_{\alpha}\mid \Theta=\Theta_0) = \alpha
$$

Basically this says, when comparing two simple hyptheses, the most powerful, MP, test is to threshold on the likelihood ratio.

**Example**

Assume $\bf{Y}$ is indepedently generated from a normal distribution with unknown $\mu,\sigma^2$. Suppose we happen to know that $\mu\in\{\mu_0,\mu_1\}$ (w.l.o.g $\mu_0>\mu_1$).
Then our hypotheses are
$$
H_0: \mu=\mu_0
$$
$$
H_1: \mu=\mu_1
$$

The test statistic is
$$
T(\bf{Y}) =\frac{f_{\bf{Y}}(\bf{Y}\mid \mu=\mu_0)}{f_{\bf{Y}}(\bf{Y}\mid \mu=\mu_1)}
=\exp\left\{
-\frac{1}{2}\sum_{i=1}^{n}\left(\frac{Y_i-\mu_0}{\sigma} \right)^2
+\frac{1}{2}\sum_{i=1}^{n}\left(\frac{Y_i-\mu_1}{\sigma} \right)^2\right\}
$$
which is an increasing function of $\overline{Y}$ if $\mu_o>\mu_1$.
Thresholding on $T$ is equivalent to thresholding on $\overline{Y}$ so the MP test at $\alpha=0.05$ is to reject $H_0$ if $\overline{Y}<C_{0.05}$.

To set this *critical value*, $C_{0.05}$, note the distribution of $\overline{Y}$ under $H_0$ is $N(\mu_o,\sigma^2/n)$, so

$$
0.05=\mathbb{P}(\overline{Y}<C_{0.05}\mid \overline{Y}\sim N(\mu_0,\sigma^2/n))
$$
which gives us $C_{0.05}=\mu_0-1.645\frac{\sigma}{\sqrt{n}}$, so we reject $H_0$ if

$$\overline{Y}<\mu_0 - 1.645\frac{\sigma}{\sqrt{n}}$$

## Construcing Tests for Composite Hyotheses

We now face the prospect that the probabilities of Type I and II errors are now functions of the parameter $\theta$


$$
\mathbb{P}(\textrm{Type I error}) = \mathbb{P}(T\not\in A\mid \Theta=\Theta_0)=\alpha(\theta),\;\;\theta\in\Theta_0
$$

$$
\mathbb{P}(\textrm{Type II error}) = \mathbb{P}(T\in A\mid \Theta=\Theta_1)=\beta(\theta),\;\;\theta\in\Theta_1
$$

Focusing on the composite null, we might try to fix $\max_{\theta\in\Theta_0}\alpha(\theta)$. This is called the *size* of the test. So we might want the size to be fixed at 0.05 or 0.01 say.
We're in effect replacing the composite null by the simple null $H_0:\theta=\theta^{\prime}$, where $\theta^{\prime}$ achives the maximum for $\alpha(\theta)$ - in some sense it's the worst case value of $\theta\in\Theta_0$.

We can only set the size if we have chosen our test statistic $T$. Unfortunately we don't have an explicit form of the Neymann-Pearson lemma to give us $T$ when the alternative $H_1$ is composite.
But we can still use it to suggest a sensible test statistic.

Let $\textrm{pow}(\theta)=1-\beta(\theta)$ be the *power function* of the test.
A highly desirable property of the test is that it be *Uniformly Most Powerful* (UMP)

**UMP Definition**

*A Test $\{T^{\star},A^{\star}\}$ of size $\alpha^{\star}$ with associated power function $\textrm{pow}^{\star}(\theta)$ is said to be Uniformly Most Powerful if*
$$
\textrm{pow}^{\star}(\theta)\geq \textrm{pow}(\theta)
$$
*for all $\theta\in\Theta_1$ and for all power functions $\textrm{pow}$*


If a UMP test exists we can easily find it using the Neymann-Pearson lemma to give the best test statistic for $H_0:\theta=\theta^{\prime}$ against $H_1:\theta=\theta_1$ for any $\theta_1\in\Theta_1$: if the resulting MP test **does not** depend on particular $\theta_1$ then **it is the UMP test**.

This is best illustrated with an example. 
Suppose we do a value of $\pi$ experiment, say using Buffon's needles to generate an estimate for $\pi$.
Let's suppose in our experiment we want to test 

$$
H_0: \pi\geq 3.14
$$
$$
H_1: \mu<3.14
$$

If we took any simple hypotheses in place $H_0$ and $H_1$, i.e.,

$$
H_0: \pi=\pi_0\textrm{ for a given $\pi_0\in[3.14,\infty)$}
$$
$$
H_1: \pi=\pi_1\textrm{ for a given $\pi_1\in(-\infty,3.14]$}
$$

The from our earlier example, the MP at $\alpha=0.05$ is to accept $H_0$ if $\overline{Y}>C_{0.05}$, because $\pi_0$ is always greater than $\pi_1$.
This immediately tells us we have the UMP test, because for all values of $\pi<3.14$ the test is MP. To set $C_{0.05}$ note

$$
\alpha(\pi) = \mathbb{P}(\overline{Y}<C_{0.05}\mid\pi) = \Phi(\frac{C_{0.05}-\pi}{\sigma/\sqrt{n}})
$$
For $\pi\geq 3.14$ this is maximised at $\pi=3.14$, so we want

$$
0.05=\max_{\pi\geq 3.14}\alpha(\pi) =  \Phi(\frac{C_{0.05}-3.14}{\sigma/\sqrt{n}})
$$

which gives us $C_{0.05}=3.14-1.645\frac{\sigma}{\sqrt{n}}$ and the UMP size 0.05 test is to accept $H_0$ if $\overline{Y}>3.14-1.645\frac{\sigma}{\sqrt{n}}$

The above makes it clear why we think of 3.14 as the 'worst' value under the null that $\pi$ could take when trying to discriminate between $H_0$ and $H_1$.


Of course it is **not always the case that a UMP test exists**. 
Consider the following hyptheses

$$
H_0: \pi= 3.14
$$
$$
H_1: \pi\neq3.14
$$

This looks very odd for any continuous parameter (not just $\pi$). If we were Bayesians and believed $\pi$ to be a RV, then $H_0$ would always have probability zero of being true.
This leads to a contradiction between classical and Bayesian tests called the *Lindley paradox*.

Ignoring such issues and continuing the classical analysis.
The natural test is to accept $H_0$ if $\overline{Y}< C_{0.05}$  under $H_1:\pi>3.14$ but the MP test under $H_1:\pi<3.14$ is to accept $H_0$ if  $\overline{Y}> C_{0.05}$.

Clearly we have an inconsistency when considering $H_1$ that covers both sides of $H_0$.

As with most of statistics, the reasonable resolution is to consider conider an inteval for the acceptance of the nul.
Accept $H_0$ if 
$$3.14-C_{0.05}<\overline{Y}<3,14+C_{0.05}$$

Typically this simple resolution is then complicated by giving it a long name.

This test is called a *Uniformly Most Powerful Unbiased* (UMPU) test.
Formally defined by

**Definition**

*A test is said to be a size $\gamma$ uniformly most powerful unbiased test if*

$$
\begin{align*}
(i)\;\;&  \textrm{pow}(\theta)\leq\gamma\;\;\forall\theta\in\Theta_0\\
(ii)\;\;&  \textrm{pow}(\theta)\geq\gamma\;\;\forall\theta\in\Theta_1\\
\end{align*}
$$
*and $\textrm{pow}(\theta)\geq\textrm{pow}^{\star}(\theta)$ for all $\theta\in\Theta_1$ and for all power functions $\textrm{pow}^{\star}$ satisfying (i) and (ii)*

These conditions define an unbiased test and guarantee the probability of making the right decision is always larger than the probability of making the wrong decision.

In practice, it may not be possible to construct a UMP or UMPU test (the normal distribution particularly lends itself to being able to do so). We might have to settle for finding a sensible test statistic whose distribution we can at least approximate.
We do need some habdle on the test statistic distribution in order to set q significance level and fix acceptance region.

Often  one resorts to a *Likelihood Ration Test* (LRT) sometimes known as *Maximum Likelihood Test*.
If we were testing between two composite hypotheses then the LR test statistic is 
$$
\lambda=\frac{\max_{\theta\in\Theta_0} f_{\bf{Y}}(\bf{y}\mid\theta)}{max_{\theta\in\Theta} f_{\bf{Y}}(\bf{y}\mid\theta)}
$$
where $\Theta=\Theta_0\cup\Theta_1$ and the test protocol is to accept $H_0$ if $\lambda\geq C_{\alpha}$.

A key advantage in using $\lambda$ is we know its approximate distribution

**Theorem**

*Under mild regularity conditions, for a large sample size,*
$$
-2\log\lambda\sim \chi^{2}_{(r)}
$$
*where* $H_0$ *and* $H_1$ *specify hypotheses for r independent parameters. This result is used to derive the distribution of the well known* $\chi^2$ *statistic, see link*

# Bayesian Hypothesis Testing

Bayesian hypothesis testing is perhaps simpler than its classical counterpart because we can now directly compute the posterior probabilities of the null and alternative, i.e.,

$$
p_0=\mathbb{P}(H_0\mid\bf{Y}),\;\;p_1=\mathbb{P}(H_1\mid\bf{Y})
$$
where $p_0+p_1=1$.

In practice we work with the *Posterior Odds* of $H_0$ being true, that is

$$
\frac{\mathbb{P}(H_0\mid\bf{Y})}{\mathbb{P}(H_1\mid\bf{Y})} = \frac{f(\bf{y}\mid H_0)}{f(\bf{y}\mid H_1)}\frac{\mathbb{P}(H_0)}{\mathbb{P}(H_1)}
$$

or sometimes the ratio of posterior and prior odds, called the *Bayes factor* (BF)

$$
BF = \frac{\mathbb{P}(H_0\mid{\bf{Y}})/\mathbb{P}(H_1\mid\bf{Y})}{\mathbb{P}(H_0)/\mathbb{P}(H_1)} = \frac{f(\bf{y}\mid H_0)}{f(\bf{y}\mid H_1)}
$$

To make a decision between $H_0$ and $H_1$ we threshold on the BF and quantify by giving the actual value of the BF for the posterior odds.

For the case where $H_0$ and $H_1$ are simple hypotheses, the BF is the same as the likelihood ratio in the Neymann-Pearson lemma, and so the decision in this case will be the same regardless of whether you're using Bayesian or classical methods.
Where the approaches differ is if at least one of the hypotheses is composite.

To compute the BF in this case, we need to put a prior distribution on $\theta$ given $H_0$ is true, say $p_0(\theta)$ and similarly assuming $H_1$ is true, $p_1(\theta)$ say.
We then have

$$
BF = \frac{f(\bf{y}\mid H_0)}{f(\bf{y}\mid H_1)} = \frac{\int_{\Theta_0}f(\bf{y}\mid\theta,H_0)p_0(\theta)d\theta}{\int_{\Theta_1}f(\bf{y}\mid\theta,H_1)p_1(\theta)d\theta}
$$
this somewhat rarely known as the *ratio of the averaged likelihoods*

Returning to our example where we wish to test
$$
H_0: \pi\geq 3.14
$$
$$
H_1: \mu<3.14
$$
If we take the priors to be (improper and) flat, so $p_i(\pi)\propto 1$ ($i=1,2$), representing total uncertainty about $\pi$ under both hypotheses.
Then the BF is

$$
BF = \frac{\int_{3.14}^{\infty}\exp\left\{-\frac{1}{2}\sum\left(\frac{y_i-\pi}{\sigma} \right)^2\right\}d\pi}{\int^{3.14}_{-\infty}\exp\left\{-\frac{1}{2}\sum\left(\frac{y_i-\pi}{\sigma} \right)^2\right\}d\pi}
$$

which gives 

$$
BF = \frac{1}{\Phi\left(\frac{3.14-\overline{y}}{\sigma/\sqrt{n}}\right)} -1
$$
The upshot is that thresholding on the BF is the same as thresholding on $\overline{y}$. Again we have the same form of test as given by the classical approach, the only difference is we now quantify our decision by the value of the BF rather than the significan level.

So far there's not seen a real difference between the two, and in part this is a reflection of chossing sensible hypotheses and selecting natural tests.
The real differences arise when we don't do that. Again picking up our example 

$$
H_0: \pi= 3.14
$$
$$
H_1: \pi\neq3.14
$$

As in the previous case, we must put priors on $\pi$ under $H_0$ and $H_1$. Because $H_0$ is simple, we'll just put a point mass $\rho_0$ at 3.14. Under $H_1$ we'll need a continuous density that integrates to $1-\rho$. A simple choice might be

$
p(\pi\mid H_1) = \frac{(1-\rho)}{2M}
$, if $\pi\in(3.14-M,3.14+M)$ and $0$ otherwise.

Substituting this into the BF gives
