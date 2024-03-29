# Measure Theory

## $\sigma$-Algebra

<!-- prettier-ignore -->
```{prf:definition} σ-algebra
:nonumber:

A **$\sigma$-field** or **$\sigma$-algebra**, $\mathcal{A}$, on the set $\Omega$ is a collection of subsets of the power set $\mathcal{P}(\Omega)$, called the **measurable sets**, with the following properties:

- it is not empty: $\emptyset, \Omega \in \mathcal{A}$
- it is closed under complement: $A \in \mathcal{A} \implies A^c \in \mathcal{A}$
- it is closed under countable unions and intersections: for $A_i \in \mathcal{A}, i \in \mathbb{N}$, we have $\cup_{i=1}^{\infty} A_i \in \mathcal{A}$ and $\cap_{i=1}^{\infty} A_i \in \mathcal{A}$
```

<!-- prettier-ignore -->
For a given (general) subset $M \subseteq \mathcal{P}(\Omega)$, there is a smallest $\sigma$-algebra that contains the set $M$. We call this the **$\sigma$-algebra generated by $M$**, and it is defined as
\begin{align}
\sigma(M) = \bigcap_{\substack{{M \subseteq \mathcal{A}}\\{\mathcal{A}~\text{$\sigma$-algebra}}}} \mathcal{A}.
\end{align}

An important $\sigma$-algebra is the **Borel $\sigma$-algebra**, which is the $\sigma$-algebra generated by all open sets (or equivalently, all closed sets). The elements it contains are called **Borel sets**, which are the sets that can be formed from open (closed) sets through unions, intersections, and (relative) complements.

For a random variable $X$, the **$\sigma$-algebra generated by the random variable $X$** contains all of the inverse images $X^{-1}(B)$ of all the Borel sets $B \subset \mathbb{R}$. That is, it contains the set of all points $\omega \in \Omega$ where $X(\omega) \in B$ for some Borel set $B \in \mathcal{B}(\mathbb{R})$.

For a stochastic process $X = (X_t, t \in T, \omega \in \Omega)$, the $\sigma$-algebra $\sigma(X)$ is the smallest $\sigma$-algebra containing all sets of the form $\{\omega: X_t(\omega) \in C\}$ for any Borel sets $C$. For a "nice" function $f$ acting on $X$, $\sigma(f(X)) \subset \sigma(X)$. That is, $f$ does not provide any new information about the structure of $X$.

## Measures

For a set $X$ and a $\sigma$-algebra $\mathcal{A}$ defined on $X$, the tuple $(X, \mathcal{A})$ is called a **measurable space**.

````{prf:definition} Measure
:nonumber:

We can define a function $\mu: \mathcal{A} \rightarrow [0, \infty]$, which we call a **measure** if it satisfies the following conditions:

- $\mu(\emptyset) = 0$
- $\forall A \in \mathcal{A}, \mu(A) \geq 0$
- $\mu(\cup_{i = 1}^{\infty} A_i) = \sum_{i=1}^{\infty} A_i$ for all $A_i \in \mathcal{A}$ with $i \in \mathbb{N}, A_i \cap A_j = \emptyset, i \neq j$ (i.e., disjoint sets in $\mathcal{A}$)

```{admonition} Extended real line $[0, \infty]$
:class: dropdown
Note that the codomain of a measure includes $\infty$. It is called the [extended real line](https://en.wikipedia.org/wiki/Extended_real_number_line). In this set $[0, \infty]$, calculations work as follows:

- $\forall x \in [0, \infty], x + \infty = \infty$
- $\forall x \in (0, \infty], x * \infty = \infty$
- $0 * \infty = 0$ (in most cases in measure theory)
```
````

The tuple $(X, \mathcal{A}, \mu)$ is called a **measure space**. Given a measure space, a subset $A \in \mathcal{A}$ is called **$\mu$-null** or a **null set** if $\mu(A) = 0$. If some property holds for all points $x \in X$ except on a null set, then we say that the property holds **$\mu$-almost everywhere** or **almost everywhere**. That is, the measure of the set of points for which the property does not hold is 0.

```{prf:example} ReLU is almost-everywhere differentiable
:class: dropdown
:nonumber:

The ReLU function is given by a function $f: \mathbb{R} \rightarrow \mathbb{R}$ defined as
\begin{align}
f(x) = \rm{max}(0, x) =
\begin{cases}
x & \text{if } x > 0 \\
0 & \text{otherwise}
\end{cases}
\end{align}
Its derivative is given by
\begin{align}
f'(x) =
\begin{cases}
1 & \text{if } x > 0 \\
0 & \text{if } x < 0
\end{cases}
\end{align}

Note that the ReLU is differentiable everywhere except for the subset $\{0\}$, which is a null set, so we say that ReLU is almost-everywhere differentiable.
```

Measurable spaces can be connected by a **measurable map**, which is defined below.

```{prf:definition} Measurable map
:nonumber:

For two measurable spaces $(X_1, \mathcal{A}_1), (X_2, \mathcal{A}_2)$, we define a **measurable map** to be a map $f: X_1 \rightarrow X_2$ satisfying the condition that
\begin{align}
\forall A_2 \in \mathcal{A}_2, f^{-1}(A_2) \in \mathcal{A}_1.
\end{align}
```

For two measurable functions $f$ and $g$ on the measurable spaces $(\Omega, \mathcal{A}), (\mathbb{R}, \mathcal{B}(\mathbb{R}))$, the following combinations are also measurable:

- composition: $g \circ f = g(f(\cdot))$
- addition: $f + g$
- multiplication: $f * g$
- absolute value: $|f|$

```{prf:example} The Characteristic/Indicator Function 𝜒
:class: dropdown
:nonumber:

For two measurable spaces $(\Omega, \mathcal{A}), (\mathbb{R}, \mathcal{B}(\mathbb{R}))$, the characteristic function is defined as
\begin{align}
\chi_A: \Omega \rightarrow \mathbb{R}, \quad \chi_A(\omega) =
\begin{cases}
1 & \text{if } x \in A \\
0 & \text{if } x \notin A
\end{cases}
\end{align}

For all measurable set $A \in \mathcal{A}$, $\chi_A$ is a measurable map. We can show this by checking the preimages:

- $\chi_A^{-1}(\emptyset) = \emptyset$
- $\chi_A^{-1}(\mathbb{R}) = \Omega$
- $\chi_A^{-1}(\{1\}) = A$
- $\chi_A^{-1}(\{0\}) = A^c$

Note that all of these preimages are contained in the $\sigma$-algebra $\mathcal{A}$, meaning that $\chi_A$ is measurable.
```

## Lebesgue Integral

<!-- prettier-ignore -->
We can define a simple function as a function that can be represented as linear combinations of indicator functions over some subsets. That is, for $A_1, \ldots, A_n \in \mathcal{A}$ and $c_1, \ldots, c_n \in \mathbb{R}$, a **simple function** is one of the form
\begin{align}
f(x) = \sum_{i = 1}^{n} c_i \cdot \chi_{A_{i}}(x).
\end{align}

Since additions of measurable functions are themselves measurable, these simple functions are also measurable.

```{margin}
The restriction $c_i \geq 0$ is done to avoid the problem of subtracting infinite measures from other infinite measures (not defined). We then only need to add possibly infinite measures, which is fine.
```

We can restrict the coefficients $c_i$ to be non-negative, and then define the set of simple functions as
\begin{align}
\mathcal{S}^{+} = \{f: X \rightarrow \mathbb{R} \mid f \text{ simple}, f \geq 0\}.
\end{align}

```{prf:definition} The Lebesgue integral for simple functions
:nonumber:

The **Lebesgue integral** of a function $f$ with respect to some measure $\mu$ is given by
\begin{align}
\int_X f(x) d\mu(x) = \int_X f d\mu = I(f) \\
= \sum_{i = 1}^{n} c_i \mu(A_i) \quad \forall A_i \in \mathcal{A}.
\end{align}

Note that because $c_i, \mu(A_i) \geq 0$, we have $I(f) \in [0, \infty]$.
```

The Lebesgue integral for simple functions has the following properties:

- positive linearity: $I(\alpha f + \beta g) = \alpha I(f) + \beta I(g)$ for $\alpha, \beta \geq 0$
- monotonicity: $f \leq g \implies I(f) \leq I(g)$

The Lebesgue integral can be extended to more complicated functions. The idea is that even if we have a function that takes on an infinite number of possible values, we can approximate it with simple functions, and take finer and finer subdivisions of our function. Each of these simple functions is Lebesgue integrable, so in the limit, the Lebesgue integral of all the subdivisions/approximations will be the Lebesgue integral of the original function.

More formally, the general **Lebesgue integral** is defined as
\begin{align}
\int_X f d\mu = \mathrm{sup}\left\{\int_X s d\mu \mid s \in \mathcal{S}^{+}, 0 \leq s \leq f\right\}.
\end{align}

A function $f$ is called **$\mu$-integrable** if $\int_X f d\mu < \infty$.

### Monotone Convergence Theorem

```{prf:theorem} Monotone convergence theorem
:nonumber:

Consider a measure space $(X, \mathcal{A}, \mu)$, a sequence of functions $f_n: X \rightarrow [0, \infty]$ which are measurable for all $n \in \mathbb{N}$, and a measurable function $f: X \rightarrow [0, \infty)$.

If ${f_n}$ are monotonically increasing and they pointwise converge to $f$ $\mu$-a.e., i.e.:
\begin{align}
f_1 \leq f_2 \leq f_3 \leq \ldots \quad &\mu \text{-a.e.} \\
\text{and } \lim_{n \to \infty} f_n(x) = f(x) \quad &\mu \text{-a.e. with } x \in X,
\end{align}
then
\begin{align}
\lim_{n \to \infty} \int_X f_n d\mu = \int_X \lim_{n \to \infty} f_n d\mu.
\end{align}
```

<!-- prettier-ignore -->
One immediate application of the monotone convergence theorem is to a sequence of measurable, non-negative functions $(f_n)_{n \in \mathbb{N}}$. The partial sums $\sum_{n=1}^{\infty} f_n: X \rightarrow [0, \infty]$ form a monotonically increasing sequence of measurable functions, so 
\begin{align}
\int_X \sum_{n=1}^{\infty} f_n d\mu = \sum_{n=1}^{\infty} \int_X f_n d\mu.
\end{align}

## Resources

- [Measure Theory Youtube Series by The Bright Side of Mathematics](https://www.youtube.com/playlist?list=PLBh2i93oe2qvMVqAzsX1Kuv6-4fjazZ8j)
- <https://math.berkeley.edu/~brent/files/lebesgue_integral.pdf>
- Wikipedia is actually pretty good for this!
