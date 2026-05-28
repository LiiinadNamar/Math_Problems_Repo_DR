# Problem 07 — Conditional Probability with Three Categories

## Problem Statement

From the three-category table, show that $H$, $M$, and $L$ form a partition, compute marginal and conditional probabilities, use the law of total probability for $P(R)$, and compute posteriors $P(H \mid R)$, $P(M \mid R)$, $P(L \mid R)$.

| Activity level | Renewed | Did not renew | Total |
| -------------- | ------: | ------------: | ----: |
| High           |      80 |            20 |   100 |
| Medium         |      90 |            60 |   150 |
| Low            |      30 |           120 |   150 |
| Total          |     200 |           200 |   400 |

$$
H = \text{high activity},\quad M = \text{medium activity},\quad L = \text{low activity},\quad R = \text{renewed}.
$$

---

## Definitions / Theory

**Partition.**
Events $H$, $M$, $L$ form a partition if they are disjoint and cover the whole sample space.

**Law of total probability.**

$$
P(R) = P(R \mid H) P(H) + P(R \mid M) P(M) + P(R \mid L) P(L).
$$

**Bayes' formula.**

$$
P(H \mid R) = \frac{P(R \mid H) P(H)}{P(R)}.
$$

---

## Step-by-Step Solution

### Part 1 — Why $H$, $M$, $L$ form a partition

Each customer belongs to exactly one activity level, so the events are disjoint and exhaustive. The totals add to 400, covering all customers.

---

### Part 2 — Compute $P(H)$, $P(M)$, $P(L)$

$$
P(H) = \frac{100}{400} = 0.25,
$$

$$
P(M) = \frac{150}{400} = 0.375,
$$

$$
P(L) = \frac{150}{400} = 0.375.
$$

---

### Part 3 — Compute $P(R \mid H)$, $P(R \mid M)$, $P(R \mid L)$

$$
P(R \mid H) = \frac{80}{100} = 0.80,
$$

$$
P(R \mid M) = \frac{90}{150} = 0.60,
$$

$$
P(R \mid L) = \frac{30}{150} = 0.20.
$$

---

### Part 4 — Use total probability to compute $P(R)$

$$
\begin{align}
P(R)
&= 0.80 \cdot 0.25 + 0.60 \cdot 0.375 + 0.20 \cdot 0.375 \\
&= 0.20 + 0.225 + 0.075 \\
&= 0.50.
\end{align}
$$

This matches the column total $200/400 = 0.50$.

---

### Part 5 — Compute $P(H \mid R)$, $P(M \mid R)$, $P(L \mid R)$

$$
P(H \mid R) = \frac{80}{200} = 0.40,
$$

$$
P(M \mid R) = \frac{90}{200} = 0.45,
$$

$$
P(L \mid R) = \frac{30}{200} = 0.15.
$$

---

### Part 6 — Interpret $P(R \mid H)$ vs $P(H \mid R)$

$P(R \mid H) = 0.80$ asks: among high-activity customers, what fraction renewed? $P(H \mid R) = 0.40$ asks: among customers who renewed, what fraction are high-activity. These are different denominators and different questions.

---

## Final Result

$$
P(H) = 0.25,\quad P(M) = 0.375,\quad P(L) = 0.375.
$$

$$
P(R \mid H) = 0.80,\quad P(R \mid M) = 0.60,\quad P(R \mid L) = 0.20.
$$

$$
P(R) = 0.50.
$$

$$
P(H \mid R) = 0.40,\quad P(M \mid R) = 0.45,\quad P(L \mid R) = 0.15.
$$

---

## Interpretation / Sanity Check

The renewal rate $P(R)$ is a weighted average of the three conditional rates and lies between 0.20 and 0.80. Posterior probabilities sum to 1: $0.40 + 0.45 + 0.15 = 1$.

---

## Common Mistakes

- Forgetting to verify that $H$, $M$, $L$ are disjoint and exhaustive.
- Confusing $P(R \mid H)$ with $P(H \mid R)$.
