# Optimisation

A very broad class of techniques aimed at roughly solving the following problem

*The problem*

Given an *objective function* $g:\mathbb{R}^p\rightarrow\mathbb{R}$, find a *minimizer* $\omega^{\star}$ of $g$, defined by

$$
g(\omega^{\star}) = \min_{\omega\in\mathbb{R}^p} g(\omega)
$$

The minimizer may or maynot be unique.
In some cases the minimum value $g(\omega^{\star})$ may be of interest, but more often it is finding the (a) minimizer, $\omega^{\star}$, that is the aim.

## Newton-Raphson method for finding zeros

Start with a guess, $\omega^1$, iterate to hopefully better approximations

$$
\omega^{t+1} = \omega^{t} - \frac{g(\omega^t)}{g'(\omega^{t})}
$$

## Newton-Raphson method for finding Optimisation

Given a differentiable $g$, optimise by finding a zero of $\nabla g$.
With $\nabla g$, the gradient and $\nabla^2g$ the Hessian, we start with an initial point $\omega^1\in\mathbb{R}^p$. We mimic the basic Newton-Raphson approach with an iteration formula

$$
\omega^{t+1} = \omega^{t} - \rho\left(\nabla^{2}(g(\omega^t)\right)^{-1}\nabla g(\omega^{t})
$$

Here $\rho\in(0,1]$ is a parameter, called the *learning rate*, which can be used to limit the step size of the iteration.

### Remarks

  1. Computing the inverse of the Hessian is:
     1. expensive
     2. numerically unstable
  2. Away from a local minimum, the Hessian may not be positive definite - so $g(\omega^{t+1})$  may be larger for all values of $\rho$
  3. Heuristically it's faster to perform more iterations of an approximate version of the Newton-Raphson method, such methods are called *quasi-Newton methods*.

## Gradient Descent

This is the quasi-Netwon method when we approximate the Hessian by the identity matrix, so the update simplifies to

$$
\omega^{t+1} = \omega^{t} - \rho\nabla g(\omega^{t})
$$

### Remarks

Slow to converge when:
  1. $\omega^1$ is not near a zero of the gradient or
  2. is in regions of domain of $g$ where $||\nabla g||$ is small but no zero of $\nabla g$ is nearby.
  3. The *stochastic* version of gradient descent seems to be the *de facto* standard algorithm for training neural networks.

## The BFGS Algorithm

## Modified to Quasi-Newton methods

## The Nelder-Mead Algorithm

## Simulated Annealing

## Genetic Algorithms

## Particle Swarm Optimisation

