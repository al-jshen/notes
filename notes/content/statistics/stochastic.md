# Stochastic Calculus

## Stochastic Processes

A stochastic process is a collection of random variables, given by
\begin{align}
X = \{X_t(\omega) \mid t \in T, \omega \in \Omega\},
\end{align}
where $T$ is the **index set** and $\Omega$ is the **sample space**. Each time/index-dependent random variable $X_t(\omega)$ may also be written as $X(t, \omega)$ to make clear that it is a function of two variables $t$ and $\omega$.

For a fixed point $t \in T$, you have a random variable $X_t = X_t(\omega)$. For a fixed point $\omega \in \Omega$, you take a single point for every $X_t$ in the stochastic process, and then you have a sample function (also called a sample path or a trajectory)
\begin{align}
X(\cdot, \omega): T \rightarrow S
\end{align}
that maps points from the index set $T$ (e.g., time) to the sample space $S$ (e.g., $\mathbb{R}^n$).

```{admonition} Gaussian processes
If the distributions of all the $X_t$ are multivariate Gaussian, then the stochastic process is called a Gaussian process.
```

<!-- prettier-ignore -->
A stochastic process $X$ is called **stationary** all $X_t$ have the same distribution. That is,
\begin{align}
X_i \overset{d}{=} X_j \text{ for all } i, j \in T.
\end{align}
Similarly, $X$ has **stationary increments** if
\begin{align}
X_i - X_j \overset{d}{=} X_{i+h}, X_{j+h} \text{ for all } i, j \in T \text{ and $h$, with } i+h, j+h \in T.
\end{align}

<!-- prettier-ignore -->
A stochastic process $X$ has **independent increments** (and is called **homogeneous**) if for all $i \in T$,
\begin{align}
X_2 - X_1, \ldots, X_n - X_{n - 1}
\end{align}
are independent random variables.

```{admonition} Poisson processes
A stochastic process $(X_t, t \in [0, \infty))$ is a (homogeneous) Poisson process with rate $\lambda > 0$ if it satisfies the following conditions:
- it has stationary, independent increments
- $X_0 = 0$
- $X_t \sim \mathrm{Poisson}(\lambda t) \text{ for } t > 0$
```

<!-- prettier-ignore -->
A stochastic process is said to be **self-similar of index $\gamma$** if it satisfies the following condition:

```{margin}
Self-similar processes are nowhere differentiable.
```

\begin{align}
\forall a \ge 0, \exists \gamma \ge 0 \text{ s.t. } (X\_{at}, t \ge 0) \overset{d}{=} (a^\gamma X_t, t \ge 0)
\end{align}

## Brownian Motion

<!-- prettier-ignore -->
A stochastic process $W = (W_t, t \in [0, \infty])$ is called a **Wiener process** or **Brownian motion** if it satisfies the following conditions:

```{margin}
Note that $W$ is a Gaussian process.
```

- it has stationary, independent increments
- $W_0 = 0$
- it has Gaussian increments: $W_t \sim \mathcal{N}(0, t) \text{ for } t > 0$, or equivalently, $W_{t+s} - W_{t} \sim \mathcal{N}(0, s)$
- it has continuous sample paths (no jumps): $W_t$ is continuous in $t$

A Wiener process has the following properties:

- mean: $\mathbb{E}[W_t] = \mathbb{E}[W] = 0 \text{ for } t \ge 0$
- variance: $\mathrm{Var}(W_t) = t$
- covariance: $\mathrm{cov}(W_s, W_t) = \mathrm{min}(s, t)$
- correlation: $\mathrm{corr}(W_s, W_t) = \sqrt{\frac{\mathrm{min}(s, t)}{\mathrm{max}(s, t)}}$

A Wiener process is 0.5-self-similar, which also implies that it has sample paths that are nowhere differentiable. This property means that to simulate Brownian motion on some interval $[0, T]$, you can simulate Brownian motion $B_t$ on $[0, 1]$ and then stretch it out with $W_t = \sqrt{T} B_{t / T}$ for $t \in [0, T]$.

<!-- prettier-ignore -->
Brownian motion sample paths have infinite (unbounded) 2-variation. This means that for some finite interval $[0, T]$, taking the supremum over all possible partitions of that interval $\tau = t_0 < \ldots < t_n = T$, we have
\begin{align}
  \underset{\tau}{\mathrm{sup}} \sum_{i=1}^{n} \left| W_{t_i} - W_{t_{i - 1}}\right| = \infty.
\end{align}

```{margin}
Remember that a Wiener process can be stretched out arbitrarily, so this actually generalizes to any interval $[0, T]$.
```

### Variants

Brownian Bridge
: a Wiener process $(W_t, t \in [0, 1])$ with the extra condition that $W(1) = 0$

Brownian motion with linear drift
: $X_t = \mu t + \sigma W_t$ for $t \ge 0$

```{margin}
This is also a Gaussian process since we are just rescaling and shifting the W, which is itself Gaussian.
```

Geometric Brownian Motion
: $X_t = \exp{(\mu t + \sigma W_t)}$ for $t \ge 0$

```{note}
For a standard normal random variable $Z$, we have $\mathbb{E}[e^{\lambda Z}] = e^{\lambda^2 / 2}$ for $\lambda \in \mathbb{R}$.
```

## Conditional Expectation

<!-- prettier-ignore -->
The **conditional expectation of $X$ given $B$** is given by
\begin{align}
\mathbb{E}[X \mid B] &= \frac{\mathbb{E}[X I_B]}{P(B)} \\
&= \frac{1}{P(B)} \int_{-\infty}^{\infty} x I_B f_X(x) dx \\
&= \frac{1}{P(B)} \int_B x f_X(x) dx.
\end{align}

The interpretation here is that you are taking the expectation of the random variable $X$, but restricting yourself to the cases of $X$ where $B$ has occurred. This is why you need to normalize by $P(B)$ and also why there is an extra indicator function factor (because you only care about the cases of $X$ which overlap with $B$).

The **conditional expectation of $X$ given $Y$**, where $Y$ is a discrete random variable, is itself a discrete random variable, defined as
\begin{align}
\mathbb{E}[X \mid Y](\omega) = \mathbb{E}[X \mid Y = y_i],~\text{with } \omega \in \{\omega : Y(\omega) = y_i \}
\end{align}

It has the following properties:

- linearity: $\mathbb{E}[c_1 X_1 + c_2 X_2 \mid Y] = c_1 \mathbb{E}[X_1 \mid Y] + c_2 \mathbb{E}[X_2 \mid Y]$
- $\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X \mid Y]]$
- if $X$ and $Y$ are independent: $\mathbb{E}[X \mid Y] = \mathbb{E}[X]$

## Measure Theory

### $\sigma$-Algebra

<!-- prettier-ignore -->
A **$\sigma$-field** or **$\sigma$-algebra** on the set $\Omega$ is a collection of subsets of $\mathbb{P}(\Omega)$, called the **measurable sets**, with the following properties:

- it is not empty: $\emptyset, \Omega \in \mathcal{F}$
- it is closed under complement: $A \in \mathcal{F} \implies A^c \in \mathcal{F}$
- it is closed under countable unions and intersections: for $A_i \in \mathcal{F}, i \in \mathbb{N}$, we have $\cup_{i=1}^{\infty} A_i \in \mathcal{F}$ and $\cap_{i=1}^{\infty} A_i \in \mathcal{F}$

<!-- prettier-ignore -->
For a given (general) subset $M \subseteq \mathbb{P}(\Omega)$, there is a smallest $\sigma$-algebra that contains the set $M$. We call this the **$\sigma$-algebra generated by $M$**, and it is defined as
\begin{align}
\sigma(M) = \bigcap_{\substack{{M \subseteq \mathcal{F}}\\{\mathcal{F}~\text{$\sigma$-algebra}}}} \mathcal{F}.
\end{align}

An important $\sigma$-algebra is the **Borel $\sigma$-algebra**, which is the $\sigma$-algebra generated by all open sets. The elements it contains are called **Borel sets**, which are the sets that can be formed from open sets through unions, intersections, and (relative) complements.

For a random variable $X$, the **$\sigma$-algebra generated by the random variable $X$** contains all of the inverse images $X^{-1}(B)$ of all the Borel sets $B \subset \mathbb{R}$. That is, it contains the set of all points $\omega \in \Omega$ where $X(\omega) \in B$ for some Borel set $B \subset \mathbb{R}$.

For a stochastic process $X = (X_t, t \in T, \omega \in \Omega)$, the $\sigma$-algebra $\sigma(X)$ is the smallest $\sigma$-algebra containing all sets of the form ${\omega: X_t(\omega) \in C}$ for any Borel sets $C$. For a "nice" function $f$ acting on $X$, $\sigma(f(X)) \subset \sigma(X)$. That is, $f$ does not provide any new information about the structure of $X$.

## Resources

- _Elementary Stochastic Calculus_ by Thomas Mikosch
- [A brief introduction to self-similar processes by J.C. Pardo](https://www.cimat.mx/~jcpardo/ssp1.pdf)
