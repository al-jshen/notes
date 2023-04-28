# Stars

## Timescales

nuclear >> Kelvin-Helmholtz >> diffusion >> dynamical >> collision

- nuclear (lifetime with current mass (i.e., fuel) and current luminosity): $t_{nuc} = \frac{aM_\odot c^2}{L_\odot} \approx 10^{11}~{\rm yr}$, where $a$ is the energy fraction released during fusion
- Kelvin-Helmholtz (time to radiate away all gravitational energy): $t_{KH} = \frac{GM_\odot^2 / R_\odot}{L_\odot} \approx 10^{7}~{\rm yr}$
- diffusion (time for photon to random walk out of the star): $t_{diff} = N t_{\gamma} \approx 10^{4}~{\rm yr}$
- dynamical (time for kinetic events to occur (e.g., response time to perturbations, time taken for sound wave to travel across star)): $t_{dyn} = R / v_{esc} = \sqrt{R^3 / 2GM} \approx 1600~{\rm s}$
- collision (time between photon collisions): $t_{\gamma} = \frac{\lambda}{c} \approx 10^{-10}~{\rm s}$, where $\lambda$ is the mean free path

## Polytropes

Approximate stellar structure with self-gravitating spherically symmetric blob of gas. Parameterized by polytropic index $n$ or $\gamma = 1 + 1/n$. Polytropes are solutions to the Lane-Emden equations, which are parameterized by length/radius $\xi$ and temperature $\theta$.

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

Occurs when heat flux is high. Formal requirement for instability to convection is that the temperature gradient is steeper than adiabatic: $\Delta > \Delta_{\rm ad}$ (superadiabatic), which means that the Brunt-Väisälä frequency $N$ satisfies $N^2 < 0$. Very efficient, so in most convective parts of the star $\Delta \approx \Delta_{\rm ad}$ (flux due to convection is small)
