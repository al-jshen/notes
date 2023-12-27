# Theory

## Explaining and Harnessing Adversarial Examples {cite:p}`Goodfellow2015`

- NNs are susceptible to adversarial examples (AEs), which are inputs that are almost identical to the original inputs but cause the NN to misclassify the input
- susceptibility means that using Euclidean distance as a proxy for perceptual similarity is not a good idea
- linear models which are easy to optimize/designed to be linear (e.g., ReLU, LSTMs, and sigmoid networks which are tuned to spent most of their time in the non-saturating linear regime) are most susceptible to adversarial attacks
- fast gradient sign method generates adversarial examples given an input $\mathbf{x}$, target $y$, loss function $\ell(\theta, \mathbf{x}, y)$ as $\mathbf{x'} = \mathbf{x} + \epsilon \text{sign}(\nabla_{\mathbf{x}} \ell(\theta, \mathbf{x}, y))$ which is a linear perturbation in the direction that most increases the loss
- can do **adversarial training** by augmenting the training set with adversarial examples $(\mathbf{x'}, y)$ which smooths predictive distributions by decreasing the loss in some $\epsilon$-neighbourhood of $\mathbf{x}$
- only networks with a non-linearity can be made robust to adversarial examples

## Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles {cite:p}`Lakshminarayanan2017`

- **deep ensembles** are a collection of independently trained NNs with the same architecture and loss function but different initializations
- for regression, make each NN predict the mean and variance of a Gaussian, then optimize negative log-likelihood
- train a bunch of NNs with different initializations, then combine as a uniformly-weighted mixture model

<!-- prettier-ignore -->
\begin{align}
    \mu_{*}({\mathbf{x}}) &= \frac{1}{N} \sum_{n=1}^N \mu_{\theta_n}(\mathbf{x}) \\
    \sigma_{*}^{2}(\mathbf{x}) &= \frac{1}{N} \sum_{n=1}^N [\sigma_{\theta_n}^2(\mathbf{x}) + \mu_{\theta_n}^2(\mathbf{x}) - \mu_*^2(\mathbf{x})]
\end{align}

```{bibliography}
  :filter: docname in docnames
```
