# Task 3 — Binomial Distribution $\mathrm{Bin}(n, p)$

## Problem Statement

The binomial distribution models the number of successes in $n$ independent Bernoulli trials, each with success probability $p$. The task is to write the PMF and CDF, analyse the graphs under different parameter choices, compute probabilities, and identify applications.

---

## Subtask 0 — Probability Space and Random Variable

**Underlying experiment.** Perform $n$ independent trials. Each trial results in either success ($S$) or failure ($F$), with $P(\text{success}) = p$ and $P(\text{failure}) = 1 - p$, where $p \in (0, 1)$.

**Sample space.** An elementary outcome is a sequence of $n$ symbols from $\{S, F\}$:

$$
\Omega = \{S, F\}^n = \{\omega = (\omega_1, \omega_2, \ldots, \omega_n) : \omega_i \in \{S, F\}\}.
$$

The cardinality is $|\Omega| = 2^n$.

**Probability of an elementary outcome.** Since the trials are independent:

$$
P(\{\omega\}) = p^{k(\omega)} (1-p)^{n - k(\omega)},
$$

where $k(\omega)$ is the number of $S$ symbols in $\omega$.

**Random variable.** Define $X : \Omega \to \mathbb{R}$ by:

$$
X(\omega) = \sum_{i=1}^{n} \mathbf{1}[\omega_i = S] = \text{number of successes in } \omega.
$$

**Support.** The possible values of $X$ are $S_X = \{0, 1, 2, \ldots, n\}$.

**Note on the Bernoulli case.** For $n = 1$, the support is $\{0, 1\}$ and $X$ reduces to a Bernoulli random variable $\mathrm{Ber}(p)$. Thus $\mathrm{Ber}(p) = \mathrm{Bin}(1, p)$.

---

## Subtask 1 — Probability Mass Function

**Derivation.** The event $\{X = k\}$ consists of all sequences $\omega \in \Omega$ containing exactly $k$ successes and $n - k$ failures. The number of such sequences is $\binom{n}{k}$. Each has probability $p^k (1-p)^{n-k}$.

**PMF of $\mathrm{Bin}(n, p)$:**

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \ldots, n.
$$

where $\binom{n}{k} = \dfrac{n!}{k!\,(n-k)!}$ is the binomial coefficient.

**Validity.** By the binomial theorem:

$$
\sum_{k=0}^{n} \binom{n}{k} p^k (1-p)^{n-k} = (p + (1-p))^n = 1^n = 1. \checkmark
$$

---

## Subtask 2 — Support

The support of $X \sim \mathrm{Bin}(n, p)$ is:

$$
S_X = \{0, 1, 2, \ldots, n\}.
$$

It is a finite set of $n+1$ consecutive non-negative integers. The minimum $0$ corresponds to no successes; the maximum $n$ corresponds to all trials being successes.

---

## Subtask 3 — Shape of the PMF under Different Parameters

**Effect of $p$ (fixed $n$).**

For $p < 0.5$: the distribution is right-skewed; the mode is near $\lfloor (n+1)p \rfloor$.
For $p = 0.5$: the distribution is symmetric around $n/2$.
For $p > 0.5$: the distribution is left-skewed.

As $p$ increases from $0$ to $1$, the mass shifts from left to right.

**Effect of $n$ (fixed $p$).**

For fixed $p$, increasing $n$ spreads the distribution and shifts the mode to the right (since the mean equals $np$). The distribution becomes more bell-shaped as $n$ increases, reflecting the Central Limit Theorem.

**Mode.** The mode of $\mathrm{Bin}(n, p)$ is $\lfloor (n+1)p \rfloor$ (or one of two adjacent values if $(n+1)p$ is an integer).

---

## Subtask 4 — Cumulative Distribution Function

**Definition.** For $X \sim \mathrm{Bin}(n, p)$:

$$
F(k) = P(X \leq k) = \sum_{j=0}^{k} \binom{n}{j} p^j (1-p)^{n-j}, \quad k = 0, 1, \ldots, n.
$$

For $k < 0$: $F(k) = 0$. For $k \geq n$: $F(k) = 1$.

The CDF is a right-continuous step function with $n+1$ jumps of size $P(X = k)$ at each $k \in S_X$.

**Remark.** There is no closed-form expression for $F(k)$ in general; it is computed by summing the PMF values up to $k$, or via the regularized incomplete beta function:

$$
F(k) = I_{1-p}(n-k,\, k+1),
$$

where $I_x(a, b)$ is the regularized incomplete beta function. In practice, numerical tools are used.

---

## Subtask 5 — Shape Changes

**As $p$ increases (fixed $n$):**

The PMF shifts to the right. The mode increases. For $p$ close to $1$, most mass is concentrated near $k = n$.

**As $n$ increases (fixed $p$):**

The mean $\mu = np$ increases linearly. The standard deviation $\sigma = \sqrt{np(1-p)}$ increases as $\sqrt{n}$. The PMF becomes more spread but also more symmetric (by CLT).

---

## Subtask 6 — Computation of Probabilities

Let $n = 10$, $p = 0.4$, $a = 3$, $b = 7$.

**PMF value:**

$$
P(X = 3) = \binom{10}{3}(0.4)^3(0.6)^7 = 120 \cdot 0.064 \cdot 0.0279936 \approx 0.2150.
$$

**Cumulative probability:**

$$
P(X \leq 3) = \sum_{k=0}^{3} \binom{10}{k}(0.4)^k(0.6)^{10-k} \approx 0.3823.
$$

**Upper tail:**

$$
P(X \geq 3) = 1 - P(X \leq 2) = 1 - \sum_{k=0}^{2}\binom{10}{k}(0.4)^k(0.6)^{10-k} \approx 1 - 0.1673 = 0.8327.
$$

**Interval probability:**

$$
P(3 \leq X \leq 7) = F(7) - F(2) \approx 0.9877 - 0.1673 = 0.8204.
$$

---

## Subtask 7 — PMF vs. CDF for Computation

For individual probabilities, compute directly from the PMF formula.
For cumulative and interval probabilities, use the CDF: $P(a \leq X \leq b) = F(b) - F(a-1)$, since $X$ is integer-valued.

Note the identity for integer-valued $X$:

$$
P(a \leq X \leq b) = F(b) - F(a-1) = \sum_{k=a}^{b} P(X = k).
$$

---

## Subtask 8 — Practical Applications

**Quality control.** $X$ counts the number of defective items in a batch of $n$ units, where each item is defective with probability $p$ independently.

**Clinical trials.** $X$ counts the number of patients responding to a treatment out of $n$ enrolled, assuming each patient responds independently with probability $p$.

**Opinion polling.** $X$ counts the number of respondents supporting a policy, out of $n$ surveyed, assuming each supports it independently with probability $p$.

**Network reliability.** $X$ counts the number of links that remain active in a network of $n$ independent links, each failing with probability $1-p$.

**Genetics.** In a diploid organism, each offspring independently inherits a trait with probability $p$; $X$ counts how many offspring in a litter of $n$ carry the trait.

---

## Final Result

The PMF of $X \sim \mathrm{Bin}(n, p)$ is:

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \ldots, n.
$$

The mean is $\mu = np$ and the variance is $\sigma^2 = np(1-p)$.

For $n = 10$, $p = 0.4$, $a = 3$, $b = 7$:

$$
P(X = 3) \approx 0.2150, \quad P(X \leq 3) \approx 0.3823,
$$

$$
P(X \geq 3) \approx 0.8327, \quad P(3 \leq X \leq 7) \approx 0.8204.
$$

---

## Interpretation and Sanity Check

With $n = 10$ and $p = 0.4$, the expected number of successes is $\mu = 4$. Most of the probability mass is near $k = 3, 4, 5$, consistent with the computed values. All probabilities lie in $[0,1]$.

---

## Common Mistakes

- Confusing $P(a \leq X \leq b) = F(b) - F(a-1)$ with $F(b) - F(a)$: since $X$ is integer-valued, $F(a-1) = P(X \leq a-1) = P(X < a)$.
- Applying the binomial model when trials are not independent (e.g., sampling without replacement from a small population — the hypergeometric model is appropriate instead).
- Using the formula for $p = 0$ or $p = 1$ without checking: $\mathrm{Bin}(n, 0)$ places all mass at $0$, and $\mathrm{Bin}(n, 1)$ places all mass at $n$.

---

## Note on Visualization

The PMF and CDF graphs for multiple parameter choices are to be displayed in the interactive application accompanying this problem set. The mathematical model is fully specified here.
