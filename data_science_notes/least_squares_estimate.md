# Least Squares Estimate

Suppose we have $n$ datapoints $\{(x_i,y_i)\}_{i=1}^n$
Viewed as a dot plot in the $x$-$y$-plane we want to approximate it with the best straight-line fit
$y=\alpha  + \beta x$.
You can perform the calculus and obtain the best estimates.

The result is cleaner if we model our best line $y=\alpha + \beta (x-\overline{x})$.

We then obtain

$$
\hat{\alpha} = \overline{y}
$$
$$

\hat{\beta} = \frac{\sum (x_i-\overline{x})(y_i-\overline{y})}{\sum (x_i-\overline{x})^2}
$$

### The simple linear regression model
Even better is to model it as 
$y_i=\alpha + \beta x_i + \epsilon_i$
with the errors $\epsilon_i$ taken as IIRV, with mean 0 and variance $\sigma^2$. Under *this assumption* the likelihood of the data is computed to be

$$
L = \left (\frac{1}{2\pi\sigma^2} \right)^{n/2}\exp\left\{-\frac{\sum (y_i-\alpha-\beta x_i)^2)}{2\sigma^2}\right\}`
$$

Clearly maximising this expression is equivalent to minimising the squared term in the exponent and hence equivalent to the least squares estimate.

To repeat, **assuming the errors are normally distributed** the MLE is equiavlent to the ordinary least squares estimator, OLS.

### Properties of OLS
The normality assumption of the errors $\epsilon_i$ allows more than to just calculate the estimates $\hat{\alpha}$ and $\hat{\beta}$. In fact we have

*Theorem*

$\hat{\alpha}$ and $\hat{\beta}$ *are unbiased*

*Proof*
    
$E[Y_i] = \alpha + \beta x_i$ and $E[\overline{Y}] = \alpha + \beta\overline{x}$. 

Using the formula for $\hat{\alpha}$ and $\hat{\beta}$ above we have

$$
E[\hat{\beta}] = \frac{\sum (x_i-\overline{x})(E[Y_i]-E[\overline{Y}])}{\sum (x_i-\overline{x})^2} = \beta
$$

Then $E[\hat{\alpha}]=E[\overline{Y}] -\beta\overline{x} = \alpha$

**Theorem**

Assuming the errors are normally distributed 

**Warning** originally I copied the variance of $\hat{\alpha}$ as
$$
\textrm{Var}(\hat{\alpha}) = \frac{\sigma^2\overline{x}^2}{\sum (x_i-\overline{x})^2}
$$
I don't think this is correct.
From books the correct variance is

$$
\textrm{Var}(\hat{\alpha}) = \frac{\sigma^2\sum x_{i}^2}{n\sum (x_i-\overline{x})^2}
$$

The rest are correct as copied

$$
\textrm{Var}(\hat{\beta}) = \frac{\sigma^2}{\sum (x_i-\overline{x})^2}
$$

$$
\textrm{Cov}(\hat{\alpha},\hat{\beta}) = -\frac{\sigma^2\overline{x}}{\sum (x_i-\overline{x})^2}
$$


**Theorem**

Define the Residual Sum of Squares (RSS) to be $\sum_{i=1}^n (y_i-\hat{\alpha} - \hat{\beta} x_i)^2$. Then 

$$
s^2 = \frac{\textrm{RSS}}{n-2}
$$
is an unbiased estimate of $\sigma^2$


The *residual* $e_i$ is defined as the individual components of $y_i-\hat{\alpha}-\hat{\beta}x_i$.


Under appropriate conditions these estimators converge in probability to the true values and have asymptotic normality allowing to construct confidence intervals.

**WARNING**

Once you have the above estimates from the data, you can make predictions with the simple linear model. The variance of the estimators might lead you to assume the variance, and hence standard error, of your predictor to follow from the variance of a sum of two RVs.
This is **wrong** and getting a prediction confidence interval is a bit more involved.



## Extension to Multiple Parameters

The above model is linear, not because it's linear in $x_i$, *but linear in $\alpha$ and $\beta$*.

**As long as  a model is linear in the parameters** we can easily generalise the theory to many parameters, with several variables transformed in several ways.

Suppose we consider a model of the form

$$
y_i = \sum_{j=0}^{p-1}\beta_jx_{ij} + \epsilon_i
$$
$\beta_0$ corresponds to $\alpha$, so $\textbf{x}_0$ is simply a vector of 1s.

Writing this in matrix form as $\textbf{Y}=\textbf{X}\beta$ then finding the least square estimate is equivalent to minimising
$$
S(\beta) = ||\textbf{Y}-\textbf{X}\beta||^2
$$

Differentiating w.r.t $\beta$ yields the *normal equations*

$$\textbf{X}^T\textbf{X}\beta=\textbf{X}^T\textbf{Y}$$

So the maximum likelihood/least square solution is 
$$
\hat{\beta} = (\textbf{X}^T\textbf{X})^{-1}\textbf{X}^T\textbf{Y}
$$

This solution *depends* on $\textbf{X}$ havgin full rank for invertibility.

Results from earlier have their multi-dimensional counterparts which we recall briefly

  1. $E[\hat{\beta}]=\beta$

  2. The variance-covariance matrix of $\hat{\beta}$ is $\sum_{\hat{\beta}\hat{\beta}}=\sigma^2(\textbf{X}^T\textbf{X})^{-1}$

  3. An unbiased estimate for the variance of the error term is 
$$
s^2=\frac{||\textbf{Y}-\textbf{X}\hat{\beta}||^2}{n-p}=\frac{\textrm{RSS}}{n-p}
$$

From these results we see that each of the $\hat{\beta_i}$ is a normally distributed RV with mean $\beta_i$ and variance $\sigma^2(\textbf{X}^T\textbf{X})^{-1}_{ij}$. Substituing from 3, we can compute the standard error of the estimate for $\hat{\beta}_{i}$ as 

$$
s_{\hat{\beta}_i} = s\sqrt{(\textbf{X}^T\textbf{X})^{-1}_{ii}}
$$

We then have, under normality assumptions,

$$

\frac{\hat{\beta_i}-\beta_i}{s_{\hat{\beta}_i}} \sim t_{n-p}
$$

This means we can test each parameter to see whether it sginificantly differs from 0. If it so then we may well conclude that the variable does not belong to the model and we can remove it and reestimate the other parameters.

Once we have done this we will have a *final* model, but importantly this model has been constructed *on the assumption of normality of the errors*.

We now need to test this assumption.

Plotting the residuals on a scatter diagram allows us to check there are no dependencies between the variables and the value of $x_i$ but **does not** check the normality assumption.

So we need to do a probability plot, using the probability transform approach, [here](./probability_integral_transform.md).

Assuming normality, the residuals have mean 0 and more matrix algebra shows the variance-covariance matrix to be 
$\sum_{\hat{e}\hat{e}} \sigma^2(\textbf{I}-\textbf{X}(\textbf{X}^T\textbf{X})^{-1}\textbf{X})$

We also find the $i^{th}$ standardized residual (mean 0, variance 1) to be:

$$
h_i=\frac{Y_i-(\textbf{X}\hat{\beta})_i}{s\sqrt{1-[\textbf{X}^T\textbf{X})^{-1}\textbf{X})]_{ii}}}
$$

Hence if we order the H_i$ and plot against the expected values of the order statistics of a $N(0,1)$ distribution we can finally determine whether the normality asssumption is warranted.
