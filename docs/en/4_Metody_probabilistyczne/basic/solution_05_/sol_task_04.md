# Task 4 — Geometric Distribution

## Problem Statement

The geometric distribution models the trial number on which the first success occurs in a sequence of independent Bernoulli trials with success probability $p \in (0,1)$.

---

## Subtask 0 — Probability Space and Random Variable

**Underlying experiment.** Perform independent Bernoulli trials, each with $P(\text{success}) = p$ and $P(\text{failure}) = 1 - p$. Stop at the first success.

**Sample space.** An elementary outcome describes the entire sequence of results up to and including the first success:

$$
\Omega = \{S,\ FS,\ FFS,\ FFFS,\ \ldots\}.
$$

More precisely, for each $k \geq 1$:

$$
\omega_k = (\underbrace{F, F, \ldots, F}_{k-1},\ S),
$$

which represents $k-1$ consecutive failures followed by a success on trial $k$. The sample space is countably infinite: $\Omega = \{\omega_1, \omega_2, \omega_3, \ldots\}$.

**Probability of an elementary outcome.** By independence:

$$
P(\{\omega_k\}) = (1-p)^{k-1} p.
$$

**Random variable.** Define $X : \Omega \to \mathbb{R}$ by:

$$
X(\omega_k) = k = \text{trial number on which the first success occurs}.
$$

**Support.** The possible values of $X$ are all positive integers:

$$
S_X = \{1, 2, 3, \ldots\} = \mathbb{N}.
$$

---

## Subtask 1 — PMF and CDF

**PMF of the Geometric Distribution.**

$$
P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \ldots
$$

**Validity:**

$$
\sum_{k=1}^{\infty} (1-p)^{k-1} p = p \sum_{k=0}^{\infty} (1-p)^k = p \cdot \frac{1}{1-(1-p)} = p \cdot \frac{1}{p} = 1. \checkmark
$$

This uses the geometric series $\sum_{k=0}^{\infty} r^k = \frac{1}{1-r}$ for $|r| < 1$.

**CDF of the Geometric Distribution.**

For integer $k \geq 1$:

$$
F(k) = P(X \leq k) = \sum_{j=1}^{k} (1-p)^{j-1} p = p \cdot \frac{1 - (1-p)^k}{1-(1-p)} = 1 - (1-p)^k.
$$

For $x \geq 1$ (non-integer values):

$$
F(x) = 1 - (1-p)^{\lfloor x \rfloor}.
$$

For $x < 1$: $F(x) = 0$.

**Complementary CDF (survival function):**

$$
P(X > k) = 1 - F(k) = (1-p)^k.
$$

---

## Subtask 2 — Support and Why It Is Infinite

The support $S_X = \{1, 2, 3, \ldots\}$ is infinite because there is no upper bound on the waiting time. For any finite $k$, there is a positive probability $(1-p)^k > 0$ that the first success has not yet occurred by trial $k$. Therefore no finite number can serve as the maximum of the support.

This reflects the nature of the experiment: the first success may in principle be delayed arbitrarily long (with decreasing but positive probability).

---

## Subtask 3 — Shape of the PMF

The PMF is strictly decreasing: since $0 < p < 1$, we have $0 < 1-p < 1$, so each successive term $(1-p)^{k-1} p$ is smaller than the previous one by a factor of $(1-p)$.

The mode is always at $k = 1$.

**Effect of $p$:**

- Large $p$ (e.g., $p = 0.8$): most mass is concentrated at small $k$; the PMF decays rapidly.
- Small $p$ (e.g., $p = 0.1$): the mass is spread over large $k$; the decay is slow.

---

## Subtask 4 — Shape of the CDF

The CDF $F(k) = 1 - (1-p)^k$ is an increasing concave function of $k$, starting near $0$ for small $k$ and approaching $1$ exponentially fast.

- Large $p$: $F$ reaches values close to $1$ very quickly.
- Small $p$: $F$ grows slowly; significant probability mass remains in the right tail for large $k$.

---

## Subtask 5 — Effect of Parameter Changes

As $p$ increases:

- The PMF becomes more concentrated at $k = 1$.
- The CDF rises steeply near the origin.
- The mean $E[X] = 1/p$ decreases.

As $p$ decreases:

- The PMF decays more slowly.
- The CDF rises gradually.
- The mean $1/p$ increases, reflecting longer expected waiting times.

---

## Subtask 6 — Computation of Probabilities

Let $p = 0.3$, $k = 4$, $a = 2$, $b = 5$.

**Probability of exactly $k$ trials:**

$$
P(X = 4) = (1-0.3)^{3} \cdot 0.3 = (0.7)^3 \cdot 0.3 = 0.343 \cdot 0.3 = 0.1029.
$$

**Cumulative probability:**

$$
P(X \leq 4) = 1 - (0.7)^4 = 1 - 0.2401 = 0.7599.
$$

**Upper tail:**

$$
P(X > 4) = (0.7)^4 = 0.2401.
$$

**Interval probability:**

$$
P(2 \leq X \leq 5) = F(5) - F(1) = (1 - 0.7^5) - (1 - 0.7^1) = 0.7 - 0.7^5 = 0.7 - 0.16807 = 0.53193.
$$

---

## Subtask 7 — Interpretation of Tail Probabilities

The survival function $P(X > k) = (1-p)^k$ represents the probability that the first success has not yet occurred after $k$ trials. This is simply the probability of $k$ consecutive failures.

For example, with $p = 0.3$:

$$
P(X > 10) = (0.7)^{10} \approx 0.0282.
$$

Only about $2.8\%$ of the time does a player wait more than $10$ trials for the first success. As $k \to \infty$, the tail probability decays to $0$ exponentially.

**Memoryless property.** The geometric distribution is the only discrete distribution with the memoryless property:

$$
P(X > m + n \mid X > m) = P(X > n), \quad m, n \in \mathbb{N}.
$$

Given that no success has occurred in the first $m$ trials, the distribution of the remaining waiting time is the same as the original. This follows directly from:

$$
P(X > m + n \mid X > m) = \frac{P(X > m+n)}{P(X > m)} = \frac{(1-p)^{m+n}}{(1-p)^m} = (1-p)^n = P(X > n).
$$

---

## Subtask 8 — Practical Applications

**Reliability engineering.** $X$ models the number of trials until the first failure of a component, where each trial results in failure with probability $p$.

**Telecommunications.** $X$ models the number of transmission attempts until a packet is successfully received, where each attempt fails with probability $1 - p$.

**Epidemiology.** $X$ models the number of contacts a contagious individual must make until infecting a susceptible person, assuming constant transmission probability $p$ per contact.

**Quality control.** $X$ models the number of items inspected until the first defective one is found.

**Gambling.** $X$ models the number of rounds played until a player wins for the first time.

---

## Final Result

The PMF and CDF of $X \sim \mathrm{Geom}(p)$ are:

$$
P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \ldots
$$

$$
F(k) = 1 - (1-p)^k, \quad k = 1, 2, 3, \ldots
$$

The mean is $E[X] = 1/p$ and the variance is $\mathrm{Var}(X) = (1-p)/p^2$.

For $p = 0.3$:

$$
P(X = 4) = 0.1029, \quad P(X \leq 4) = 0.7599, \quad P(X > 4) = 0.2401,
$$

$$
P(2 \leq X \leq 5) \approx 0.5319.
$$

---

## Interpretation and Sanity Check

With $p = 0.3$, the expected waiting time is $E[X] = 1/0.3 \approx 3.33$ trials. The computed $P(X \leq 4) \approx 0.76$ confirms that roughly $76\%$ of experiments terminate within the first four trials, consistent with the mean. All probabilities lie in $[0, 1]$.

---

## Common Mistakes

- Using the formula $(1-p)^{k-1} p$ for $k$ starting at $0$ instead of $1$: the support is $\{1, 2, 3, \ldots\}$, not $\{0, 1, 2, \ldots\}$. (An alternative convention defines $X$ as the number of failures before the first success, giving support $\{0, 1, 2, \ldots\}$; the two conventions must not be mixed.)
- Forgetting the memoryless property when computing conditional probabilities.
- Confusing $P(X > k) = (1-p)^k$ with $P(X \geq k) = (1-p)^{k-1}$.

---

## Note on Visualization

The PMF and CDF for several values of $p$ are to be displayed in the interactive application. The mathematical model is fully specified here.
