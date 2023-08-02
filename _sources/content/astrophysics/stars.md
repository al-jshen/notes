# Stars

## Timescales

- nuclear >> Kelvin-Helmholtz >> diffusion >> dynamical >> collision
- nuclear (lifetime with current mass (i.e., fuel) and current luminosity): $t_{nuc} = \frac{aM_\odot c^2}{L_\odot} \approx 10^{11}~{\rm yr}$, where $a$ is the energy fraction released during fusion
- Kelvin-Helmholtz (time to radiate away all gravitational energy): $t_{KH} = \frac{GM_\odot^2 / R_\odot}{L_\odot} \approx 10^{7}~{\rm yr}$
- diffusion (time for photon to random walk out of the star): $t_{diff} = N t_{\gamma} \approx 10^{4}~{\rm yr}$
- dynamical (time for kinetic events to occur (e.g., response time to perturbations, time taken for sound wave to travel across star)): $t_{dyn} = R / v_{esc} = \sqrt{R^3 / 2GM} \approx 1600~{\rm s}$
- collision (time between photon collisions): $t_{\gamma} = \frac{\lambda}{c} \approx 10^{-10}~{\rm s}$, where $\lambda$ is the mean free path

## Polytropes

- approximate stellar structure with self-gravitating spherically symmetric blob of gas
- parameterized by polytropic index $n$ or $\gamma = 1 + 1/n$
- polytropes are solutions to the Lane-Emden equations, which are parameterized by length/radius $\xi$ and temperature $\theta$

Relations:

- $P = K\rho^{\gamma}$
- $\rho = \rho_c \theta^n$
- $P = P_c \theta^{n + 1}$

Lane Emden: $\frac{1}{\xi^2} \frac{\rm d}{{\rm d}\xi} \left(\xi^2 \frac{{\rm d}\theta}{{\rm d}\xi} \right) = -\theta^{n}$, with boundary conditions $\theta = 1$, ${\rm d}\theta / {\rm d}\xi = 0$ at the center ($\xi = 0$)

Common cases:

- $n = 0$: rocky planet with constant density
- $n = 1.5$: convective stars, gas giants (e.g., Jupiter), brown dwarfs, non-relativistic degenerate matter (e.g., low-mass white dwarfs)
- $n = 3$: main sequence stars, relativistic degenerate matter (e.g., high-mass white dwarfs)
- $n = 5$: infinite radius

## Convection

- occurs when heat flux is high
- formal requirement for instability to convection is that the temperature gradient is steeper than adiabatic: $\Delta > \Delta_{\rm ad}$ (superadiabatic), which means that the Brunt-Väisälä frequency $N$ satisfies $N^2 < 0$
- very efficient, so in most convective parts of the star $\Delta \approx \Delta_{\rm ad}$ (temperature gradient is close to adiabatic, which means that $F_{conv} \rightarrow 0$, so flux due to convection is/becomes small)

## Fusion

- in cooler stars, mostly pp-chain ($\varepsilon \propto T^4$), and in hotter stars, CNO cycle ($\varepsilon \propto T^{20}$)
- slowest reaction in the pp chain is the first one
- Gamow peak has roughly Gaussian shape and is the effective energy at which reactions occur
  - mean/peak is given by $E_0 = 1.22\,(Z_1^2 Z_2^2 T_6^2 (\mu / m_p))^{1/3}~{\rm keV}$, with $Z_1^2 Z_2^2 (\mu / m_p) = 1/2$ for the pp chain
  - width is given by $\Delta = 4/\sqrt{3}\,(E_0 kT)^{1/2}$
- energy released in fusion reaction is the difference between the binding energies of the reactants and the products (time efficiency, which for hydrogen to helium is 0.7%)
- nuclear mass given by semi-empirical mass formula
- nuclei with larger binding energies per nucleon are more stable; the most stable nuclei are all around the iron peak ($^{56}\text{Fe}$, $^{56}\text{Ni}$, $^{62}\text{Ni}$)

## Opacity

<!-- prettier-ignore -->
- types of opacity:
  - free-free (inverse Bremsstrahlung): electron passes near an ion and absorbs a photon of any wavelength
  - bound-free: photon is absorbed/used to eject an electron from a bound state of an atom, only works if photon has more energy than the ionization potential, and only exists in states with bound (i.e., unionized) systems (typically $T < 10^{6}~{\rm K}$)
  - bound-bound (spectral lines): absorption of a photon that causes an electron to jump energy levels, requires photon to be in a very narrow wavelength range for any particular spectral line, but is important because some atoms can have a large number of (closely spaced) lines that absorb lots of photons
  - Thomson (from Thomson scattering): non-relativistic, inelastic collision of low energy ($h\nu \ll m_e c^2$, which is typically the case for blackbodies at $T < 10^{8}~{\rm K}$) photon and electron, which causes the electron to oscillate (but not recoil, because photon was low energy) and emit a new photon with the same wavelength
  - negative hydrogen ion: electron passes near a neutral hydrogen atom and they turn into a $H^{-}$ ion, which requires availability of free electrons either due to ionized hydrogen (unlikely) or free electrons due to ionized metals (Na, K, Cs, Ca are very easy to ionize), but $H^{-}$ itself becomes ionized away at $T \sim 10^{4}~{\rm K}$, so this is important only in cool stars
- Rosseland mean opacity (free-free, bound-free, and bound-bound) can approximated using Kramers formula: $\kappa_{K} = 4\times 10^{25}\,(1+X)\,(Z+0.0001)\,(\rho / T^{3.5})~{\rm cm^{2}\,g^{-1}}$
  - free-free opacity most effective at high densities and low temperatures (e.g., in low mass stars)
- Thomson opacity given by $\kappa_{Th} = 0.2\,(1 + X)~{\rm cm^{2}\,g^{-1}}$
- $H^{-}$ opacity given by $\kappa_{H^{-}} = 2.5\times 10^{-31}\,(Z / 0.02)\,\rho^{0.5}\,T^{9}~{\rm cm^{2}\,g^{-1}}$

### Resources

- https://www.bartol.udel.edu/~owocki/phys633/14-opacity.pdf

## Formulas

- $F = -\left(\frac{4acT^3}{3\kappa \rho}\right) \frac{{\rm d}T}{{\rm d}r}$
