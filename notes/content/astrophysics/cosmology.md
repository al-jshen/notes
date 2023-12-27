# Cosmology

- common spectral features used to measure redshifts:
  - visible: Ca H and K, H-$\alpha$
  - millimeter: CO J transitions
  - radio: 21cm
  - xray: iron K
- for high redshifts, can use supernovae (can measure distances for these consistently)
- redshifts are measured relative to us, but for Hubble's law it doesn't matter where you measure it from (can come to same conclusion about expanding universe from any origin)
  - means that universe has no edge/is infinite (as far as we know) because if you have an edge then you can define a (special) center
- $H_0$ gives a characteristic time for the expansion of the universe
- to measure velocity of an object: $v = H_0 d + (\vec{v}_{pec} - \vec{v}_{pec,0}) \cdot \hat{d}$, with $\vec{v}_{pec} \cdot \hat{d}$ typically being a few hundred kilometers (so at high $z$, it is negligible, and velocity due to expansion dominates)

- cosmological principle: universe is homogeneous and isotropic
  - for stars, nearest star is $10^7$x further than the size of our Sun. for galaxies, nearest galaxy is ~20x further than the size of our Galaxy. so get more and more homogeneity at large scales.
- Minkowski metric: $ds^2 = c^2 dt^2 - (dx^2 + dy^2 + dz^2) = gu\nu dx^u dx\nu$
- general form under homogeneity and isotropy: $ds^2 = c^2 dt^2 - R^2(t) [f(r) dr^2 + g(r) (d\theta^2 + \sin^2 \theta d\phi^2)] = c^2 dt^2 - R^2(t) \ell^2$, where everything in the brackets is dimensionless (including $r$)

  - three forms, depending on curvature of space:
    - flat: $f = 1$, $g = r^2$
    - positively or negatively curved: $d\ell^2 = d\vec{x}^2 \pm du^2$ and $\vec{x}^2 \pm u^2 = \pm 1$, and $d\ell^2 = d\vec{x}^2 + (\vec{x}\dot d\vec{x})^2 / (1 \mp \vec{x}^2)$.
  - Friedmann-Robertson-Walker metric, $ds^2 = c^2 dt^2 - R^2(t) \times [\frac{dr^2}{1 - kr^2} + r^2 d\omega^2]$, with $k$ being curvature of the universe
    - $ds^2 = c^2 dt^2 - R^2(t) [d\chi^2 + S_k^2(\chi) d\omega^2]$ with $S_k = \sin, \chi, \sinh$ for $k = 1, 0, -1$
    - $\chi = c \int_{t_1}^{t_0} \frac{dt}{R(t)}$ has no time dependence
    - $\Delta x = c\frac{\Delta t_0}{R(t_0)} - \frac{c \Delta t_1}{R(t_1)} = 0 \implies \frac{\Delta t_0}{\Delta t_1} = \frac{R(t_0)}{R(t_1)} = \frac{\nu_1}{\nu_0} = \frac{\lambda_0}{\lambda_1} = 1 + z$, with $R$ being the scale size of the universe, so time dependent measurements (e.g., redshift) are directly proportional to the change in $R$
    - $R(t) = R_0 \frac{a(t)}{a(t_0)}$, with $a(t) = \frac{1}{1+z}$ being the scale factor, then $R_0 \chi = \int \frac{c dt}{a(t)}$ and $\frac{dt}{a} = \frac{dt}{da} \frac{da}{a} = \frac{a}{\dot{a}} \frac{da}{a^2} \implies \frac{\dot{a}}{a} = \frac{\dot{R}}{R} = H$
    - $R_0 \chi = \int \frac{c dt}{a(t)} = c \int_0^z \frac{dz}{H} = \frac{cz}{H_0}$, so for low $z$ we have $R(t_0) = \frac{c}{H_0}$ and $\chi = z$

- FRW: $ds^2 = c^2 dt^2 - R_0^2 a^2(t) [\chi^2 + S_k^2(\chi) dw^2]$, where $R_0 = R(t_0) = c/H_0$, $S_k(\chi) = {\sin\chi, \chi, \sinh\chi}$ for $k = {+1, 0, -1}$ and comoving distance $R_0 \chi = c \int_{t_1}^{t_0} dt/a(t)$, all the geometry is in the square brackets and all the time dependence is in the $R_0^2 a^2(t)$ term
- small angle formula: $\theta = \frac{s}{d}$, with $s$ being the size of the object and $d$ being the distance to the object, note here that $\theta$ is an "observable" (is directly measured just by looking at the size of the object in the sky)
- angular diameter distance: $d_A = R_0 a(t) S_k(\chi) = \frac{R_0 S_k(\chi)}{1 + z}$
- other way to get distance is the luminosity distance: $F = \frac{L}{4\pi d_L^2} = \frac{L}{4\pi R_0^2 S_k^2(\chi) (1 + z)^2}$, with $d_L = S_k(\chi) R_0 (1 + z)$
- surface brightness is the brightness per solid angle, at small redshifts this is constant, and at large redshifts it is given by $\frac{b}{(\Delta \theta)^2} \propto \frac{1}{d_L^2} d_A^2 \propto \frac{1}{(1 + z)^4}$, so the same object at high redshift has a much lower surface brightness
- over a ride range of redshifts, $6~{\rm kpc}$ subtends 1 arcsec on the sky, which is also roughly the limit of how well ground-based telescopes can resolve things due to the atmosphere, which means that galaxies are generally going to be resolved (and not confused with stars)
- Einstein field equation: $R_{\mu \nu} - \frac{1}{2} g_{\mu \nu} R = \frac{8\pi G}{c^4} T_{\mu \nu}$ where $g_{\mu \nu}$ is the GR metric, $R_{\mu \nu}$ is the Ricci tensor, and $T_{\mu \nu}$ is the stress-energy tensor
- plugging FRW into Einstein field equation: $T_{\mu \nu} = {\rm diag}(\rho c^2, -p, -p, -p)$ and LHS of Friedmann becomes ${\rm diag}(\frac{3}{c^2} (\frac{\dot{a}}{a})^2 + \frac{kc^2}{a^2}, \frac{1}{c^2} (2 \frac{\ddot{a}}{a} + (\frac{\dot{a}}{a})^2 + \frac{kc^2}{a^2}), ...)$ where the last 3 terms in the diagonal are the same, so if we set LHS=RHS, then we just end up with a system of two equations
- Friedmann equation #1: $\dot{R} - \frac{8\pi R^2 \rho G}{3} = -kc^2$
  - assuming matter only flat universe, get $\frac{dR}{dt} \propto R^{-1/2}$, solve to find that $R \propto t^{2/3} \implies R = R_0 (\frac{t}{t_0)})^{2/3}$, and the age of the universe is $t_0 = \frac{2}{3} \frac{1}{H_0}$
- Friedmann equation #2: $\ddot{R} = \frac{-4\pi RG}{3} (\rho + \frac{3p}{c^2})$

- $(\frac{\dot{a}{a}})^2 - \frac{8\pi G \rho}{3} = -\frac{kc^2}{R_0^2 a^2}$, where if $k = 0$ then we can solve for the critical density $\rho = \rho_{crit} = \frac{3H^2}{8\pi G}$
- equation of state: $p = w \rho c^2$, where $w = 0$ for (non-relativistic) matter, $w = 1/3$ for radiation/relativistic matter, and $w = -1$ for dark energy
- cosmological constant: new energy component that is constant in time and space, $p = -\rho c^2$ (i.e., vacuum itself has non-zero energy density), defined as $\Lambda = \frac{3\pi G}{3} \frac{\rho_V}{c^2}$
- density is given by $\rho = \rho_m + \rho_\gamma + \rho_\Lambda = \rho_{m,0} a^{-3} + \rho_{\gamma, 0} a^{-4} + \rho_\Lambda = \rho_{crit,0} (\Omega_{m,0} a^{-3} + \Omega_{\gamma,0} a^{-4} + \Omega_{\Lambda,0})$
- can write differential equation to find the time dependence of $a$: $\frac{1}{H_0^2} (\frac{\dot{a}}{a})^2 = \Omega_{m} a^{-3} + \Omega_{\gamma} a^{-4} + \Omega_{\Lambda} - \frac{kc^2}{R_0^2 H_0^2 a^2}$
- number density of photons is $\sim 410~{\rm cm^{-3}}$, and of protons is $\sim 2.4\times 10^{-7}~{\rm cm^{-3}}$, but to find the dominant source of energy, need to find the energy density by multiplying by the typical energy of a photon ($2.7~{\rm K} \simeq 10^{-3}~{\rm eV}$) or proton ($10^{9}~{\rm eV}$)

- if randomly distributed, distribution of galaxies is $dP = n dV$, where $n$ is the number density of galaxies and $dV$ is the volume element
- with excess, $dP = n(1 + \xi(r)) dV$, where $\xi(r)$ is the fractional excess
- bias is defined as $b^2 = \frac{\xi_{G}(r)}{\xi_{DM}(r)}$, where $\xi_{G}(r)$ is the excess probability of galaxies and $\xi_{DM}(r)$ is the excess probability of dark matter
- centrals: one galaxy per halo, basically just a step function at some halo mass
- satellites: multiple galaxies per halo, usually a power law

- to get good photo-z can look for breaks (Lyman, Balmer/4000A) which are broader features, or Lyman alpha (biased sample which is very star forming, low mass, low dust (because Lyman alpha is in UV band which is susceptible to dust))

### Resources

### Formulas

- redshift: $z = (\lambda - \lambda_0) / \lambda_0 = v/c$
- Hubble's law: $v = H_0 d$
