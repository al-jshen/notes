# Talks

## 9 Nov 2022 - Charles Margossian @ Columbia

- continuous time approximation: MCMC approximates Langevin diffusion process
- warmup phase serves to decrease bias
  - first few samples are drawn from prior distribution instead of target distribution and are thus heavily biased, so we throw them away
- sampling phase serves to decrease variance of Monte Carlo estimators by increasing effective sample size
- can run thousands of chains in parallel with modern hardware, if algorithm is GPU-friendly
- R-hat compares within-chain variance to between-chain variance
- if you run many chains in parallel, then the number of chains sets a lower bound on your effective sample size, so in theory you can take just a single sample per chain during the sampling phase
- how do you diagnose convergence in this many-chains regime?
- R-hat gives a diagnostic for a single chain in the limit of infinite length, but doesn't say anything about having multiple chains
- **nested R-hat** generalizes R-hat
  - group chains into size K "superchains"
    - for K=1 groups, we recover classical R-hat
  - have the same initialization for all chains within a superchain to avoid the problem that when you have all independent chains, nested R-hat can be made arbitrarily close to 1 by increasing K
  - can decompose nested R-hat measurement into two terms
    1. violation of stationarity, which is the variance of the conditional expectation, which measures how well chains have forgotten where they started from and goes to 0 if the expected value of the chain does not depend on the initialization
    2. persistent variance, which is the expected conditional variance, which is independent of whether your chains are stationary, but goes to 0 as you increase the the number chains
  - ![nrhat](../figures/nrhat.png)
  - violation is a proxy for squared bias, since they both decay with warmup at the same rate
  - larger K (and using fewer superchains/initializations) has higher variance before reaching stationarity
- benefit of running many chains is to achieve target precision more quickly (not just achieve precision that is as small as possible)

## Sept. 5, 2023: Ting Li @ IAS

- stellar streams science: is DM cold or warm? what is the shape of the MW potential? what is the mass of the MW? where do metal poor stars come from? can use to infer existence/flyby of DM subhalos
- to determine distance of GC, scan (metal-poor) isochrone in distance and find distance with maximum overdensity of stars (e.g., Drlica-Wagner, Shipp+ 2018 DESI)
- S5: DES photometry + Gaia DR2 PMs + low-res spectrograph on Anglo-Australian Telescope + high-res spectrograph on Magellan
- Phoenix stream: more metal poor than any known GC, tells you about metallicity floor
- infall of LMC -> MW halo not in dynamical equilibrium. fit data to determine mass of MW, including effects of LMC (Koposov+23 Orphan-Chenab stream).

## Sept. 12, 2023: Will Farr @ IAS

- for GW, distances are easy (energies are all typically $c^5/G ~ 10^{59}~{\rm erg\,s^{-1}}$) but redshifts are hard ($m_{obs} = m(1+z)$, if you can measure $m$ then you can measure $z$)
- BH mass function is not smooth, large bumps at 10 and 35 solar masses
- at low core masses, heavier core -> heavier BH, but at ~40 solar masses, core gets hot enough for pair instability (premature thermonuclear detonation) which kills the BH and prevents it from getting to even higher masses
- can "hear" the shape of a drum if it has a smooth boundary but not if it doesn't
- BH ringdown frequency uniquely determined by Kerr mass and spin, can validate GR, precision will get higher and higher with more and more data/BHs

```{bibliography}
  :filter: docname in docnames
```
