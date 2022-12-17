# INLA (integrated nested Laplace approximation)

- used to do approximate inference for latent Gaussian models (LGM; models with a latent Gaussian random field)
  - includes a broad range of models, including GLMs and spatio-temporal models
- approximates the marginals of the posterior rather than the full joint posterior distribution
- marginals are often almost-normal, so a Laplace approximation (Taylor expansion around the mode) can be very good
- very fast and accurate (see [this comparison to Stan](https://www.martinmodrak.cz/2018/02/02/a-gentle-stan-vs.-inla-comparison/))

<!-- prettier-ignore -->
The setup of a LGM consists of three parts:
\begin{align}
&\textrm{Hyperparameters} &\quad &\boldsymbol{\theta} \sim \pi_\theta(\boldsymbol{\theta}),\,\boldsymbol{theta}=(\boldsymbol{\theta_1, \theta_2}) \\
&\textrm{Latent Gaussian field} &\quad &\boldsymbol{x} | \boldsymbol{\theta_2} \sim \mathcal{N}(\boldsymbol{\mu(\theta_2}), \boldsymbol{Q(\theta_2)}^{-1}) \\
&\textrm{Observations} &\quad &\boldsymbol{y} | \boldsymbol{x, \theta_1} \sim \prod_{i=1}^{N} \pi_y(y_i | x_i, \boldsymbol{\theta_1}),\,i=1, \ldots, n \\
\end{align}

<!-- prettier-ignore -->
The joint posterior for the latent field and the hyperparameters is
\begin{align}
\pi({\boldsymbol{x, \theta} | \boldsymbol{y}}) \propto \pi(\boldsymbol{y} | \boldsymbol{x, \theta}) \pi(\boldsymbol{x, \theta}) \propto \prod_{i=1}^N \pi(y_i | x_i, \boldsymbol{\theta}) \pi(\boldsymbol{x} | \boldsymbol{\theta}) \pi(\boldsymbol{\theta}).
\end{align}

<!-- prettier-ignore -->
INLA calculates the posterior marginals. For the hyperparameters, this is
\begin{align}
  \pi(\theta_j | \boldsymbol{y}) = \int \pi(\boldsymbol{\theta} | \boldsymbol{y}) d\boldsymbol{\theta}_{-j}, \; j=1, \ldots, m
\end{align}
and for the latent field $\boldsymbol{x}$, this is
\begin{align}
  \pi(x_i | \boldsymbol{y}) = \int \pi(x_i | \boldsymbol{y, \theta}) \pi(\boldsymbol{\theta} | \boldsymbol{y}) d\boldsymbol{\theta},\,i=1,\ldots,n.
\end{align}
Note that you need to calculate the posterior marginals of the hyperparameters before you can calcuate the posterior marginals of the latent field (nested!).

- try to keep the dimensionality of the hyperparameters $\boldsymbol{\theta}$ small since INLA does a grid integration
- dimension of the latent field can be extremely large ($10^6$)
- approximations are exact if the observation probability $\pi(\boldsymbol{y} | \boldsymbol{x, \theta})$ is Gaussian

# Resources

- https://www.precision-analytics.ca/articles/a-gentle-inla-tutorial/
- https://faculty.washington.edu/jonno/SISMIDmaterial/2-RINLA.pdf
