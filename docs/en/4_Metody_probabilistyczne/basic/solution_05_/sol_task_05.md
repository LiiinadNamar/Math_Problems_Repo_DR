# Task 5 — Poisson Distribution

## Problem Statement

The Poisson distribution models the number of random events occurring in a fixed interval of time or space, under assumptions of independence and constant average rate.

---

## Subtask 0 — Probability Space and Random Variable

**Underlying experiment.** Observe a telephone switchboard over a fixed one-hour interval. Calls arrive randomly and independently. The average number of calls per hour is $\lambda > 0$.

**Sample space.** An elementary outcome $\omega$ is a complete record of the arrival times of all calls during the hour:

$$
\omega = (t_1, t_2, \ldots, t_k) \in [0,1]^k, \quad k \in \{0, 1, 2, \ldots\}.
$$

A natural (though informal) description of the sample space is:

$$
\Omega = \bigcup_{k=0}^{\infty} [0,1]^k,
$$

where $[0,1]^0 = \{\emptyset\}$ represents the outcome of no arrivals. The rigorous construction uses the theory of Poisson point processes.

**Random variable.** Define:

$$
X(\omega) = \text{total number of calls during the hour} = k \text{ if } \omega \in [0,1]^k.
$$

**Support.** The possible values of $X$ are all non-negative integers:

$$
S_X = \{0, 1, 2, 3, \ldots\}.
$$

---

## Subtask 1 — PMF and Parameter

**PMF of the Poisson Distribution.**

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \ldots
$$

**Parameter.** The single parameter $\lambda > 0$ is the rate (expected number of events in the interval). It satisfies:

$$
E[X] = \lambda, \quad \mathrm{Var}(X) = \lambda.
$$

The Poisson distribution is characterized by the equality of its mean and variance.

**Validity:**

$$
\sum_{k=0}^{\infty} \frac{\lambda^k e^{-\lambda}}{k!} = e^{-\lambda} \sum_{k=0}^{\infty} \frac{\lambda^k}{k!} = e^{-\lambda} \cdot e^{\lambda} = 1. \checkmark
$$

This uses the Taylor series $e^{\lambda} = \sum_{k=0}^{\infty} \lambda^k / k!$.

---

## Subtask 2 — Support

The support of $X \sim \mathrm{Poisson}(\lambda)$ is:

$$
S_X = \{0, 1, 2, 3, \ldots\} = \mathbb{N}_0.
$$

It is countably infinite. There is no upper bound on the number of events: for any $k$, $P(X = k) > 0$. The probability decays super-exponentially as $k \to \infty$ (faster than any geometric decay).

---

## Subtask 3 — Shape of the PMF

**Mode.** The mode of $\mathrm{Poisson}(\lambda)$ is $\lfloor \lambda \rfloor$ (or both $\lfloor \lambda \rfloor$ and $\lfloor \lambda \rfloor - 1$ if $\lambda$ is a positive integer).

**Shape as $\lambda$ varies:**

- Small $\lambda$ (e.g., $\lambda = 0.5$): distribution is strongly right-skewed; most mass at $k = 0$ and $k = 1$.
- Moderate $\lambda$ (e.g., $\lambda = 3$): visibly right-skewed but with mass spread over several values.
- Large $\lambda$ (e.g., $\lambda = 10$): approximately symmetric and bell-shaped, approaching a normal distribution by the CLT.

**Consecutive ratio.** The ratio of successive PMF values is:

$$
\frac{P(X = k+1)}{P(X = k)} = \frac{\lambda}{k+1}.
$$

The PMF is increasing for $k < \lambda - 1$, achieves a maximum near $k = \lambda$, and is decreasing for $k > \lambda$.

---

## Subtask 4 — Cumulative Distribution Function

**Definition.** For $X \sim \mathrm{Poisson}(\lambda)$:

$$
F(k) = P(X \leq k) = e^{-\lambda} \sum_{j=0}^{k} \frac{\lambda^j}{j!}, \quad k = 0, 1, 2, \ldots
$$

There is no closed-form expression for general $k$; values are computed numerically.

The CDF is a right-continuous step function that increases from $0$ (at $x < 0$) to $1$ (as $k \to \infty$), with jumps of size $P(X = k)$ at each non-negative integer $k$.

---

## Subtask 5 — Effect of Increasing $\lambda$

As $\lambda$ increases:

- The mode shifts rightward (mode $\approx \lambda$).
- The distribution becomes more symmetric.
- The variance increases (since $\mathrm{Var}(X) = \lambda$), so the distribution spreads out.
- The CDF rises more gradually and its inflection point moves rightward.

For large $\lambda$, by the Central Limit Theorem:

$$
\frac{X - \lambda}{\sqrt{\lambda}} \xrightarrow{d} N(0, 1).
$$

---

## Subtask 6 — Computation of Probabilities

Let $\lambda = 3$, $k = 2$, $a = 1$, $b = 4$.

**Probability of exactly $k$ events:**

$$
P(X = 2) = \frac{3^2 e^{-3}}{2!} = \frac{9 e^{-3}}{2} \approx \frac{9 \cdot 0.04979}{2} \approx 0.2240.
$$

**Cumulative probability:**

$$
P(X \leq 2) = e^{-3}\left(\frac{3^0}{0!} + \frac{3^1}{1!} + \frac{3^2}{2!}\right) = e^{-3}(1 + 3 + 4.5) = 8.5 e^{-3} \approx 0.4232.
$$

**Upper tail:**

$$
P(X \geq 2) = 1 - P(X \leq 1) = 1 - e^{-3}(1 + 3) = 1 - 4e^{-3} \approx 1 - 0.1991 = 0.8009.
$$

**Interval probability:**

$$
P(1 \leq X \leq 4) = F(4) - F(0) = P(X \leq 4) - P(X = 0).
$$

$$
P(X = 0) = e^{-3} \approx 0.0498.
$$

$$
P(X \leq 4) = e^{-3}\left(1 + 3 + \frac{9}{2} + \frac{27}{6} + \frac{81}{24}\right) = e^{-3}(1 + 3 + 4.5 + 4.5 + 3.375) = 16.375\, e^{-3} \approx 0.8153.
$$

$$
P(1 \leq X \leq 4) = 0.8153 - 0.0498 = 0.7655.
$$

---

## Subtask 7 — CDF vs. Direct Summation

**Via PMF (direct summation):**

$$
P(X \leq 2) = P(X=0) + P(X=1) + P(X=2) = e^{-3}(1 + 3 + 4.5) \approx 0.4232.
$$

**Via CDF:**

$$
P(X \leq 2) = F(2) \approx 0.4232.
$$

The two approaches are identical in exact arithmetic. In practice, the CDF is read from a table or computed numerically. For interval probabilities, the CDF form $F(b) - F(a-1)$ is more efficient than summing individual PMF values.

---

## Subtask 8 — Practical Applications

**Telecommunications.** Modelling the number of phone calls arriving at a switchboard per unit time.

**Queueing theory.** Modelling customer arrivals at a service counter (basis of the $M/M/1$ queue).

**Epidemiology.** Modelling the number of disease cases per unit area or time in a population with low incidence.

**Astronomy.** Modelling the number of photons hitting a detector per unit time from a distant source.

**Insurance.** Modelling the number of claims submitted to an insurance company per year.

**Traffic engineering.** Modelling the number of vehicles passing a checkpoint per unit time under low-traffic conditions.

**Radioactive decay.** Modelling the number of decay events from a radioactive sample in a fixed time window.

---

## Final Result

The PMF of $X \sim \mathrm{Poisson}(\lambda)$ is:

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \ldots
$$

The mean and variance are both equal to $\lambda$.

For $\lambda = 3$:

$$
P(X = 2) \approx 0.2240, \quad P(X \leq 2) \approx 0.4232,
$$

$$
P(X \geq 2) \approx 0.8009, \quad P(1 \leq X \leq 4) \approx 0.7655.
$$

---

## Interpretation and Sanity Check

With $\lambda = 3$, the expected number of events is $3$. The mode is at $k = 3$ (or $k = 2$ and $k = 3$ both qualify since $\lambda = 3$ is an integer). The computed $P(X \leq 2) \approx 0.42$ is less than $0.5$, consistent with the median being slightly above $2$. All probabilities lie in $[0,1]$.

---

## Common Mistakes

- Treating $\lambda$ as an integer: $\lambda$ can be any positive real number.
- Using the formula for $k < 0$: the Poisson PMF is defined only for $k = 0, 1, 2, \ldots$
- Confusing $P(X \geq k) = 1 - F(k-1)$ with $1 - F(k)$: the former includes $k$ in the event, the latter does not.
- Applying the Poisson model when events are not independent or the rate is not constant over the interval.

---

## Note on Visualization

PMF and CDF graphs for multiple values of $\lambda$ (with a slider) are to be implemented in the interactive application. The mathematical model is fully specified here.
