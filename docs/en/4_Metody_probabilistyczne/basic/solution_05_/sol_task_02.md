# Task 2 — Discrete Distribution Given by a CDF Table

## Problem Statement

A discrete random variable $X$ is defined by the following cumulative distribution function (CDF), given at its jump points:

| $x$ | $-1$ | $0$ | $2$ | $4$ | $6$ |
|-----|------|-----|-----|-----|-----|
| $F(x)$ | $0.15$ | $0.35$ | $0.60$ | $0.85$ | $1.00$ |

The tasks are: reconstruct the PMF, construct a probability space, draw the graphs, and compute selected probabilities.

---

## Subtask 0 — Construction of a Probability Space

**Definition.** A finite probability space is a triple $(\Omega, \mathcal{F}, P)$ where $\Omega$ is a finite set of elementary outcomes, $\mathcal{F} = 2^\Omega$, and $P$ assigns non-negative weights summing to $1$.

**Construction.** The CDF has exactly five jump points, so there are five atoms of probability. Define:

$$
\Omega = \{\omega_1, \omega_2, \omega_3, \omega_4, \omega_5\}
$$

with probabilities (to be determined in Subtask 1) assigned as:

$$
P(\{\omega_i\}) = p(x_i), \quad x_1 = -1,\ x_2 = 0,\ x_3 = 2,\ x_4 = 4,\ x_5 = 6.
$$

Define $X : \Omega \to \mathbb{R}$ by $X(\omega_i) = x_i$.

**Underlying experiment.** One can think of selecting a number from the set $\{-1, 0, 2, 4, 6\}$ according to the distribution determined by the jump sizes of $F$.

**Sample space vs. support.** The sample space is $\Omega = \{\omega_1, \ldots, \omega_5\}$; its elements are abstract. The support of $X$ is $S_X = \{-1, 0, 2, 4, 6\}$.

---

## Subtask 1 — Reconstruction of the PMF

**Theorem.** For a discrete random variable, the PMF can be recovered from the CDF by computing the jump sizes:

$$
p(x_0) = P(X = x_0) = F(x_0) - F(x_0^-),
$$

where $F(x_0^-) = \lim_{x \nearrow x_0} F(x)$.

For the first support point, $F(x_1^-)$ is the value of $F$ just before the first jump, which equals $0$ (since $F(x) = 0$ for all $x < x_1$).

**Computation.**

$$
p(-1) = F(-1) - F(-1^-) = 0.15 - 0 = 0.15.
$$

$$
p(0) = F(0) - F(0^-) = 0.35 - 0.15 = 0.20.
$$

$$
p(2) = F(2) - F(2^-) = 0.60 - 0.35 = 0.25.
$$

$$
p(4) = F(4) - F(4^-) = 0.85 - 0.60 = 0.25.
$$

$$
p(6) = F(6) - F(6^-) = 1.00 - 0.85 = 0.15.
$$

**Reconstructed PMF table:**

| $x$ | $-1$ | $0$ | $2$ | $4$ | $6$ |
|-----|------|-----|-----|-----|-----|
| $P(X = x)$ | $0.15$ | $0.20$ | $0.25$ | $0.25$ | $0.15$ |

**Verification:**

$$
0.15 + 0.20 + 0.25 + 0.25 + 0.15 = 1.00. \checkmark
$$

All values are non-negative. The PMF is valid.

---

## Subtask 2 — Graph of the PMF

The PMF consists of five isolated spikes at the support points.

**Description of the graph.**

- At $x = -1$: spike of height $0.15$.
- At $x = 0$: spike of height $0.20$.
- At $x = 2$: spike of height $0.25$.
- At $x = 4$: spike of height $0.25$.
- At $x = 6$: spike of height $0.15$.

The distribution is symmetric: $p(-1) = p(6) = 0.15$ and $p(2) = p(4) = 0.25$, with a single intermediate value $p(0) = 0.20$. The two modes are $x = 2$ and $x = 4$.

---

## Subtask 3 — Graph of the CDF

The CDF is a right-continuous step function. The full piecewise definition is:

$$
F(x) =
\begin{cases}
0 & x < -1, \\
0.15 & -1 \leq x < 0, \\
0.35 & 0 \leq x < 2, \\
0.60 & 2 \leq x < 4, \\
0.85 & 4 \leq x < 6, \\
1.00 & x \geq 6.
\end{cases}
$$

**Description of the graph.**

- Horizontal segment at $y = 0$ for $x < -1$.
- At $x = -1$: upward jump to $y = 0.15$. The point $(-1, 0.15)$ is filled; the open circle is at $(-1, 0)$ from the left.
- Horizontal segment at $y = 0.15$ on $[-1, 0)$.
- At $x = 0$: jump to $y = 0.35$.
- Horizontal segment at $y = 0.35$ on $[0, 2)$.
- At $x = 2$: jump to $y = 0.60$.
- Horizontal segment at $y = 0.60$ on $[2, 4)$.
- At $x = 4$: jump to $y = 0.85$.
- Horizontal segment at $y = 0.85$ on $[4, 6)$.
- At $x = 6$: jump to $y = 1.00$.
- Horizontal segment at $y = 1.00$ for $x \geq 6$.

---

## Subtask 4 — Points of Jump

The CDF $F$ is discontinuous at exactly five points: $x \in \{-1, 0, 2, 4, 6\}$.

These are precisely the elements of the support $S_X$. At every other point, $F$ is constant and continuous.

---

## Subtask 5 — Why the Jump Size Equals the Probability

**Proof sketch.** By definition of the CDF:

$$
F(x_0) - F(x_0^-) = P(X \leq x_0) - P(X < x_0) = P(X = x_0).
$$

The first equality follows from the definition of $F$ and its left limit. The second equality is a consequence of the formula:

$$
P(X < x_0) = P(X \leq x_0) - P(X = x_0),
$$

which holds for any random variable. For discrete distributions, $P(X = x_0) > 0$ at support points, which produces a visible jump of that magnitude.

---

## Subtask 6 — Computation of Probabilities

Let $a = 2$ and $b = 4$ for the computations below.

**Cumulative probability (read directly from CDF):**

$$
P(X \leq 2) = F(2) = 0.60.
$$

**Strict inequality (left-hand limit):**

$$
P(X < 2) = F(2^-) = 0.35.
$$

**Probability of a single value (jump size):**

$$
P(X = 2) = F(2) - F(2^-) = 0.60 - 0.35 = 0.25.
$$

**Interval probability:**

$$
P(2 < X \leq 4) = F(4) - F(2) = 0.85 - 0.60 = 0.25.
$$

**Tail probability:**

$$
P(X > 2) = 1 - F(2) = 1 - 0.60 = 0.40.
$$

---

## Subtask 7 — Comparison with Task 1

| Aspect | PMF given (Task 1) | CDF given (Task 2) |
|--------|-------------------|-------------------|
| Immediate information | $P(X = x_0)$ for each support point | $P(X \leq x_0)$ for each support point |
| Requires derivation | CDF: accumulate sums | PMF: compute jump differences |
| Interval prob. $P(a < X \leq b)$ | Requires summing relevant $p(x)$ values | Requires only $F(b) - F(a)$ |
| Individual prob. $P(X = x_0)$ | Read directly from table | Requires computing $F(x_0) - F(x_0^-)$ |

**Conclusion.** The two representations carry the same information. The PMF is the natural representation when individual probabilities are of primary interest. The CDF is the natural representation for cumulative and interval probabilities, and it generalizes more naturally to continuous distributions.

---

## Final Result

The PMF recovered from the CDF is:

$$
p(-1) = 0.15, \quad p(0) = 0.20, \quad p(2) = 0.25, \quad p(4) = 0.25, \quad p(6) = 0.15.
$$

Selected computed probabilities (with $a = 2$, $b = 4$):

$$
P(X \leq 2) = 0.60, \quad P(X < 2) = 0.35, \quad P(X = 2) = 0.25,
$$

$$
P(2 < X \leq 4) = 0.25, \quad P(X > 2) = 0.40.
$$

---

## Interpretation and Sanity Check

All probabilities lie in $[0,1]$. The CDF is non-decreasing, right-continuous, with $F(-\infty) = 0$ and $F(+\infty) = 1$. The reconstructed PMF sums to $1$.

The distribution is nearly symmetric around $x = 2.5$: the masses at $-1$ and $6$ are equal ($0.15$), and the masses at $2$ and $4$ are equal ($0.25$). The distribution has two modes at $x = 2$ and $x = 4$.

---

## Common Mistakes

- Using $F(b) - F(a)$ to compute $P(a \leq X \leq b)$: the correct formula is $F(b) - F(a^-)$, not $F(b) - F(a)$, when the left endpoint is included.
- Forgetting that $F$ is right-continuous: the value $F(x_0)$ already includes the mass at $x_0$.
- Attempting to recover the PMF without computing left-hand limits explicitly.

---

## Note on Visualization

The PMF and CDF graphs described above are to be implemented in the interactive application (HTML/JavaScript) prepared as a companion tool to this problem set. The mathematical model is fully specified here; the graphical rendering is handled separately.
