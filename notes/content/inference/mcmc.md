# Markov chain Monte Carlo

Broad class of methods for drawing samples from posterior distribution. Do not need to compute costly normalizing factor (denominator in Bayes' theorem).

Creates Markov chains with samples that are eventually drawn from the exact posterior.

Want to compute expectation values and quantiles from a distribution, but that is hard. So instead we use samples to construct statistical estimators of these quantities.

## Problems

- How do you reach the stationary distribution quickly (i.e., become unbiased)?
- How can you pool information across multiple chains to speed up the above process?
  - ensemble chain adaptation {cite:p}`Hoffman2021,Hoffman2022`
- How can you deal with problematic geometry (ill-conditioned problems)?

  - **Riemannian HMC** {cite:p}`Girolami2011` uses a local geometry (i.e., empirical Fisher matrix) to define the mass matrix
    - has some problems (see [discussion](https://discourse.mc-stan.org/t/riemann-manifold-hmc-in-stan/19466/5))
      - numerical integrator can be unstable due to implementation and also due to geometry, fragility means that it requires hand-tuning by user
      - reparameterizing Euclidean HMC is equivalent to running Riemannian HMC
      - expensive to calculate Hessian in high dimensions ($n^2$ memory requirement)
        - quasi-Newton approximation methods {cite:p}`Zhang2022`
  - applying continuous mappings (transport map, normalizing flow) to transform MCMC proposals to more complex proposals
    - NeuTra HMC from {cite:t}`Hoffman2019` uses inverse autoregressive flows {cite:p}`Kingma2017` to learn the posterior geometry, then passes HMC samples (from a Gaussian) through the flow
      - they show that the dynamics of this method are equivalent to Riemannian HMC
    - can train a flow in conjunction with an MCMC sampler {cite:p}`Gabrie2022,Zhang2022a`
      - flow is trained with samples from MCMC and forward KLD (to avoid mode collapse), and the trained flow is used to warp space to improve MCMC proposals

## Temperature based methods

- parameterizes the posterior with some temperature $T$ as follows:
  \begin{align}
  \pi_T(\mathbf{x}) = [L(\mathbf{x})]^{1/T} \, p(\mathbf{x}),
  \end{align}
  where $\pi_T$ is the temperature-dependent modified posterior, $L$ is the likelihood, and $p$ is the prior
- at high temperatures ("hot chains"), the likelihood is flattened more, so low-density regions of the posterior can be explored more easily, and at low temperatures ("cold chains"), peaks in the likelihood/posterior are sampled more easily
- **simulated annealing** samples from a series of distributions of decreasing temperature, with the final temperature corresponding to the target distribution (i.e., $T=1$)
  - has no convergence guarantees unless we use infinite compute time
- **simulated tempering** is like simulated annealing, but the temperature is chosen randomly rather than systematically
  - need to define a joint distribution over the original parameter space and over temperature space, such that the joint distribution conditional on $T=1$ is the target distribution, and that the marginal distribution for $T$ is roughly uniform
- **parallel tempering** samples multiple modified posteriors in parallel, and then proposes swaps between chains so that states from hot chains inform cold chains
  - detailed balance is maintained by using a Metropolis-Hastings step to determine whether the swap is performed
  - swaps are usually done between adjacent chains to ensure that the acceptance probability is not tiny

## To Read

- parallel tempering [1](https://darrenjw.wordpress.com/2013/09/29/parallel-tempering-and-metropolis-coupled-mcmc/), [2](https://emcee.readthedocs.io/en/v2.2.1/user/pt/) {cite:p}`Neal1996`
- simulated annealing and annealed importance sampling {cite:p}`Neal1998,Midgley2022`
- [Unbiased MCMC with couplings](https://darrenjw.wordpress.com/2019/12/12/unbiased-mcmc-with-couplings/) {cite:p}`Jacob2019`
- avoiding detailed balance {cite:p}`Sohl-Dickstein2016`

## Misc

- **shadow Hamiltonian** models the errors of the numerical integration scheme; exact trajectory of the shadow Hamiltonian is the same as the approximate trajectory (approximate due to numerical errors) of the regular Hamiltonian
- **preconditioned Crank-Nicolson algorithm** has acceptance rate which is independent of the dimension, can use it to sample from infinite dimensional spaces {cite:p}`Hu2016`
- MCMC on Hilbert spaces {cite:p}`Beskos2011`

## References

```{bibliography}
  :filter: docname in docnames
```
