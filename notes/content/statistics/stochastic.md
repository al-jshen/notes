# Stochastic Calculus

## Stochastic Processes

A stochastic process is a collection of random variables, given by
\begin{align}
\{X_t(\omega) | t \in T, \omega \in \Omega\},
\end{align}
where $T$ is the **index set** and $\Omega$ is the **sample space**. Each time/index-dependent random variable $X_t(\omega)$ may also be written as $X(t, \omega)$ to make clear that it is a function of two variables $t$ and $\omega$.

For a fixed point $t \in T$, you have a random variable $X_t = X_t(\omega)$. For a fixed point $\omega \in \Omega$, you take a single point for every $X_t$ in the stochastic process, and then you have a sample function (also called a sample path or a trajectory)
\begin{align}
X(\cdot, \omega): T \rightarrow S
\end{align}
that maps points from the index set $T$ (e.g., time) to the sample space $S$ (e.g., $\mathbb{R}^n$).

```{admonition} Gaussian Processes
If the distributions of all the $X_t$ are multivariate Gaussian, then the stochastic process is called a Gaussian process.
```
