# Task 1 — Discrete Distribution Given by a PMF Table

## Problem Statement

A discrete random variable $X$ is defined by the following probability mass function (PMF):

| $x$ | $-2$ | $0$ | $1$ | $3$ | $5$ |
|-----|------|-----|-----|-----|-----|
| $P(X = x)$ | $0.10$ | $0.25$ | $0.30$ | $0.20$ | $0.15$ |

The tasks are: construct a probability space, verify validity of the distribution, derive and graph the CDF, and compute selected probabilities.

---

## Subtask 0 — Construction of a Probability Space

**Definition.** A finite probability space is a triple $(\Omega, \mathcal{F}, P)$ where $\Omega$ is a finite sample space, $\mathcal{F} = 2^\Omega$ is the power set (all subsets), and $P$ is a probability measure.

**Construction.** Define:

$$
\Omega = \{\omega_1, \omega_2, \omega_3, \omega_4, \omega_5\}
$$

with probabilities assigned to elementary outcomes:

$$
P(\{\omega_1\}) = 0.10, \quad
P(\{\omega_2\}) = 0.25, \quad
P(\{\omega_3\}) = 0.30, \quad
P(\{\omega_4\}) = 0.20, \quad
P(\{\omega_5\}) = 0.15.
$$

Define the random variable $X : \Omega \to \mathbb{R}$ by:

$$
X(\omega_1) = -2, \quad
X(\omega_2) = 0, \quad
X(\omega_3) = 1, \quad
X(\omega_4) = 3, \quad
X(\omega_5) = 5.
$$

Then $P(X = x_i) = P(\{\omega_i\})$ for each $i$, which recovers the given table exactly.

**Underlying experiment.** One can think of spinning a wheel divided into five sectors of sizes proportional to the given probabilities, and assigning the value of $X$ according to which sector is selected.

**Sample space vs. support.** The sample space is $\Omega = \{\omega_1, \omega_2, \omega_3, \omega_4, \omega_5\}$; its elements are abstract outcomes. The support of $X$ is $S_X = \{-2, 0, 1, 3, 5\} \subset \mathbb{R}$; these are the values taken by $X$.

---

## Subtask 1 — Verification of Validity

**Requirements for a valid PMF.** A function $p : \mathbb{R} \to [0,1]$ is a valid PMF if and only if:

1. $p(x) \geq 0$ for all $x \in \mathbb{R}$,
2. $\displaystyle\sum_{x \in S_X} p(x) = 1$.

**Verification.**

All listed probabilities are non-negative:

$$
0.10 \geq 0, \quad 0.25 \geq 0, \quad 0.30 \geq 0, \quad 0.20 \geq 0, \quad 0.15 \geq 0. \checkmark
$$

Their sum:

$$
0.10 + 0.25 + 0.30 + 0.20 + 0.15 = 1.00. \checkmark
$$

Both conditions are satisfied. The table defines a valid probability distribution.

---

## Subtask 2 — Graph of the PMF

The PMF consists of five isolated spikes at the support points. At each $x \in S_X$, a vertical segment (or filled dot) of height $p(x)$ is drawn. Elsewhere, $p(x) = 0$.

**Description of the graph.**

- At $x = -2$: spike of height $0.10$.
- At $x = 0$: spike of height $0.25$.
- At $x = 1$: spike of height $0.30$ (the mode).
- At $x = 3$: spike of height $0.20$.
- At $x = 5$: spike of height $0.15$.

The horizontal axis carries no mass between these points.

---

## Subtask 3 — Cumulative Distribution Function

**Definition.** The CDF of a random variable $X$ is:

$$
F(x) = P(X \leq x), \quad x \in \mathbb{R}.
$$

For a discrete distribution with PMF $p$:

$$
F(x) = \sum_{\{k \in S_X \,:\, k \leq x\}} p(k).
$$

**Construction.**

For $x < -2$: no support point is $\leq x$, so $F(x) = 0$.

For $-2 \leq x < 0$: only $-2 \leq x$, so $F(x) = p(-2) = 0.10$.

For $0 \leq x < 1$: points $-2$ and $0$ are $\leq x$, so $F(x) = 0.10 + 0.25 = 0.35$.

For $1 \leq x < 3$: points $-2, 0, 1$ are $\leq x$, so $F(x) = 0.35 + 0.30 = 0.65$.

For $3 \leq x < 5$: points $-2, 0, 1, 3$ are $\leq x$, so $F(x) = 0.65 + 0.20 = 0.85$.

For $x \geq 5$: all support points are $\leq x$, so $F(x) = 0.85 + 0.15 = 1.00$.

**Summary table of the CDF:**

| Interval | $F(x)$ |
|----------|--------|
| $x < -2$ | $0$ |
| $-2 \leq x < 0$ | $0.10$ |
| $0 \leq x < 1$ | $0.35$ |
| $1 \leq x < 3$ | $0.65$ |
| $3 \leq x < 5$ | $0.85$ |
| $x \geq 5$ | $1.00$ |

---

## Subtask 4 — Graph of the CDF

The CDF is a right-continuous step function.

**Description of the graph.**

- For $x < -2$: the graph lies on the horizontal line $y = 0$.
- At $x = -2$: a jump upward to $y = 0.10$. Open circle on the left, filled circle on the right.
- Constant at $0.10$ on $[-2, 0)$.
- At $x = 0$: jump to $y = 0.35$.
- Constant at $0.35$ on $[0, 1)$.
- At $x = 1$: jump to $y = 0.65$.
- Constant at $0.65$ on $[1, 3)$.
- At $x = 3$: jump to $y = 0.85$.
- Constant at $0.85$ on $[3, 5)$.
- At $x = 5$: jump to $y = 1.00$.
- Constant at $1.00$ for $x \geq 5$.

---

## Subtask 5 — Jumps of the CDF and the PMF

**Theorem.** For any discrete distribution, the size of the jump of $F$ at a point $x_0$ equals the probability mass at that point:

$$
F(x_0) - F(x_0^-) = P(X = x_0),
$$

where $F(x_0^-) = \lim_{x \nearrow x_0} F(x)$ denotes the left-hand limit.

**Explanation.** The CDF accumulates probability from left to right. When $x$ crosses a support point $x_0$, the event $\{X \leq x\}$ gains the atom $\{X = x_0\}$, increasing $F$ by exactly $P(X = x_0)$.

**Verification for this example.**

$$
F(-2) - F(-2^-) = 0.10 - 0 = 0.10 = P(X = -2). \checkmark
$$

$$
F(0) - F(0^-) = 0.35 - 0.10 = 0.25 = P(X = 0). \checkmark
$$

$$
F(1) - F(1^-) = 0.65 - 0.35 = 0.30 = P(X = 1). \checkmark
$$

$$
F(3) - F(3^-) = 0.85 - 0.65 = 0.20 = P(X = 3). \checkmark
$$

$$
F(5) - F(5^-) = 1.00 - 0.85 = 0.15 = P(X = 5). \checkmark
$$

---

## Subtask 6 — Computation of Probabilities

Let $a = 1$ and $b = 3$ for the computations below.

**Direct from the PMF:**

$$
P(X = 1) = 0.30.
$$

**Using the CDF:**

$$
P(X \leq 1) = F(1) = 0.65.
$$

$$
P(X < 1) = F(1^-) = \lim_{x \nearrow 1} F(x) = 0.35.
$$

Note the distinction: $P(X < 1) = P(X \leq 0) = F(0) = 0.35$ since the support is discrete.

$$
P(1 < X \leq 3) = F(3) - F(1) = 0.85 - 0.65 = 0.20.
$$

$$
P(X \geq 1) = 1 - P(X < 1) = 1 - F(1^-) = 1 - 0.35 = 0.65.
$$

Alternatively, using the PMF directly:

$$
P(X \geq 1) = P(X=1) + P(X=3) + P(X=5) = 0.30 + 0.20 + 0.15 = 0.65. \checkmark
$$

---

## Subtask 7 — Comparison: PMF vs CDF

| Quantity | Easier from PMF | Easier from CDF |
|----------|----------------|----------------|
| $P(X = x_0)$ | Read directly | Compute jump $F(x_0) - F(x_0^-)$ |
| $P(X \leq b)$ | Sum all $p(x)$ for $x \leq b$ | Read $F(b)$ directly |
| $P(a < X \leq b)$ | Sum $p(x)$ for $x \in (a,b]$ | Compute $F(b) - F(a)$ |
| $P(X > a)$ | Sum $p(x)$ for $x > a$ | Compute $1 - F(a)$ |

**Conclusion.** The PMF is convenient for computing the probability of individual values and small finite sums. The CDF is more efficient for computing cumulative and interval probabilities via simple differences.

---

## Final Result

The PMF is valid. The CDF is the right-continuous step function tabulated above, with jumps of sizes $0.10, 0.25, 0.30, 0.20, 0.15$ at the points $-2, 0, 1, 3, 5$ respectively.

Selected computed probabilities (with $a=1$, $b=3$):

$$
P(X = 1) = 0.30, \quad P(X \leq 1) = 0.65, \quad P(X < 1) = 0.35,
$$

$$
P(1 < X \leq 3) = 0.20, \quad P(X \geq 1) = 0.65.
$$

---

## Interpretation and Sanity Check

All computed probabilities lie in $[0,1]$. The CDF is non-decreasing and approaches $0$ as $x \to -\infty$ and $1$ as $x \to +\infty$. The sum of all jump sizes equals $1$, confirming consistency between the PMF and CDF.

The value $x = 1$ carries the largest probability mass ($0.30$), making it the mode of the distribution. The distribution is slightly right-skewed, with more mass concentrated on the left portion of the support.

---

## Common Mistakes

- Confusing $P(X < a)$ with $P(X \leq a)$: for discrete distributions these differ by $P(X = a)$.
- Writing $P(a < X \leq b) = F(b) - F(a^-)$ instead of $F(b) - F(a)$.
- Forgetting that the CDF is right-continuous: $F(x_0) = P(X \leq x_0)$, not $P(X < x_0)$.
- Treating the sample space $\Omega$ and the support $S_X$ as the same object.

---

## Note on Visualization

The PMF and CDF graphs described above are to be implemented in the interactive application (HTML/JavaScript) prepared as a companion tool to this problem set. The mathematical model is fully specified here; the graphical rendering is handled separately.
