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

## References

```{bibliography}
  :filter: docname in docnames
```
