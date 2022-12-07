# INLA (integrated nested Laplace approximation)

- used to do approximate inference for latent Gaussian models (LGM; models with a latent Gaussian random field)
  - includes a broad range of models, including GLMs and spatio-temporal models
- approximates the marginals of the posterior rather than the full joint posterior distribution
- marginals are often almost-normal, so a Laplace approximation (Taylor expansion around the mode) can be very good
- very fast and accurate (see [this comparison to Stan](https://www.martinmodrak.cz/2018/02/02/a-gentle-stan-vs.-inla-comparison/))

<!-- prettier-ignore -->
The setup of a LGM consists of three parts:
\begin{align}
&\textrm{Hyperparameters} &\quad &\boldsymbol{\theta} \sim \pi_\theta(\boldsymbol{\theta}) \\
&\textrm{Latent Gaussian field} &\quad &\boldsymbol{x} | \boldsymbol{\theta} \sim \mathcal{N}(\boldsymbol{\mu(\theta}), \boldsymbol{Q(\theta)}^{-1}) \\
&\textrm{Observations} &\quad &y_i | x_i, \boldsymbol{\theta} \sim \pi_y(y_i | x_i, \boldsymbol{\theta}),\,i=1, \ldots, n \\
\end{align}

INLA calculates the posterior marginals.
For the hyperparameters, this is

<!-- prettier-ignore -->
\begin{align}
  \pi(x_i | \boldsymbol{y}) = \int \pi(x_i | \boldsymbol{y, \theta}) \pi(\boldsymbol{\theta} | \boldsymbol{y}) d\boldsymbol{\theta},
\end{align}
and for the latent field $\boldsymbol{x}$, this is
\begin{align}
  \pi(\theta_j | \boldsymbol{y}) = \int \pi(\boldsymbol{\theta} | \boldsymbol{y}) d\boldsymbol{\theta}_{-j}.
\end{align}
Note that you need to calculate the posterior marginals of the hyperparameters before you can calcuate the posterior marginals of the latent field (nested!).

- try to keep the dimensionality of the hyperparameters small since INLA does a grid integration
