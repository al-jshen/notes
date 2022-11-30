# Variational inference

Big idea: choose a family of approximating distributions, then use optimization to find the approximating distribution that is closest to the target distribution. Very scalable.

## ELBO

We want to minimize the KL divergence (an asymmetric measure of difference between distributions). We can do this by maximizing the **evidence lower bound (ELBO)**, which tries to optimize for densities which balance between matching the target distribution well, while also being close to the prior distribution.

## Mean-field approximation

Makes the assumption that latent variables are mutually independent, so that we can factorize the likelihood as

\begin{align}
q(z) = \prod_i q_i(z_i)
\end{align}

- (relative) simplicity of the mean-field family of approximating distributions makes optimization easy (i.e., can apply it to large problems)
- does not model dependencies between latent variables
- tends to underestimates variances of parameters

## Normalizing Flows

- learn a flexible, bijective transformation from a simple base distribution that you can sample from and have an exact likelihood for to your target distribution

- for some invertible mapping $f$, random variable $z$ with base distribution $z \sim p_z(z)$, and some sample $x$ from the target distrbution $x \sim \pi(x)$ such that $x = f(z)$ and $z = f^{-1}(x)$, we have
  \begin{align}
  \pi(x) \approx p_x(x) = p_z(f^{-1}(x)) \left|\textrm{det}(\frac{\partial f^{-1}(x)}{\partial x})\right| = p_z(z) \left|\textrm{det}(\frac{\partial f(z)}{\partial z})\right|^{-1}
  \end{align}

- we can parameterize the mapping $f$ with a neural network, under the conditions that

  1. the mapping must be bijective (i.e., input and output dimensions are the same, and the mapping is invertible)
  2. the determinant of the Jacobian must be efficient and invertible

- to learn the target density given some samples, we simply maximize the likelihood of the data under our model likelihood by transforming the data samples to our base distribution, then calculating the likelihood
- to generate samples from a given target distribution, we generate samples from our base distribution, push them through our mapping into our approximate target distribution, then use a Monte Carlo estimate of the ELBO to make our variational distribution a good approximation for the target distribution

## References

```{bibliography}
  :filter: docname in docnames
```
