# Markov chain Monte Carlo

Broad class of methods for drawing samples from posterior distribution. Do not need to compute costly normalizing factor (denominator in Bayes' theorem).

Creates Markov chains with samples that are eventually drawn from the exact posterior.

Want to compute expectation values and quantiles from a distribution, but that is hard. So instead we use samples to construct statistical estimators of these quantities.

## Problems

- How do you reach the stationary distribution quickly?
- How can you pool information across multiple chains to speed up the above process?
  - ensemble chain adaptation {cite:p}`Hoffman2021,Hoffman2022`
  - {cite}`Gabrie2022`
- How can you deal with problematic geometry (ill-conditioned problems)?

  - **Riemannian HMC** {cite:p}`Girolami2011`: use a local geometry (i.e., empirical Fisher matrix) to define the mass matrix
    - has some problems (see https://discourse.mc-stan.org/t/riemann-manifold-hmc-in-stan/19466/5)
      - numerical integrator can be unstable due to implementation and also due to geometry, fragility means that it requires hand-tuning by user
      - reparameterizing Euclidean HMC is equivalent to running Riemannian HMC
      - expensive to calculate Hessian in high dimensions ($n^2$ memory requirement)
        - quasi-Newton approximation (a la L-BFGS) possible?
  - applying continuous mappings to transform MCMC proposals to more complex proposals
    - NeuTra HMC from {cite:t}`Hoffman2019` uses inverse autoregressive flows {cite:p}`Kingma2017` to learn the posterior geometry, then passes HMC samples (from a Gaussian) through the flow
      - they show that the dynamics of this method are equivalent to Riemannian HMC

## References

```{bibliography}
  :filter: docname in docnames
```
