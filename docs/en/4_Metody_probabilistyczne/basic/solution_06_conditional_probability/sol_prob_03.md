# Problem 03 — Conditional Probabilities Are Not Symmetric

## Problem Statement

From the two-way table, compute conditional probabilities in both directions and explain why they answer different questions. Decide which conditional probability is useful for measuring the effect of watching the lecture, and which is useful for describing those who passed the quiz.

| User behavior         | Passed quiz | Did not pass quiz | Total |
| --------------------- | ----------: | ----------------: | ----: |
| Watched lecture       |          72 |                18 |    90 |
| Did not watch lecture |          28 |                32 |    60 |
| Total                 |         100 |                50 |   150 |

$$
W = \text{user watched the lecture},
$$

$$
Q = \text{user passed the quiz}.
$$

---

## Definitions / Theory

**Conditional probability.**

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}.
$$

The condition determines the **reference population**. Switching the condition changes the denominator and typically changes the value.

---

## Step-by-Step Solution

### Part 1 — Compute $P(Q \mid W)$ and $P(W \mid Q)$

Among the 90 users who watched the lecture, 72 passed:

$$
P(Q \mid W) = \frac{72}{90} = 0.80.
$$

Among the 100 users who passed the quiz, 72 watched the lecture:

$$
P(W \mid Q) = \frac{72}{100} = 0.72.
$$

---

### Part 2 — Compute $P(Q \mid W^c)$ and $P(W \mid Q^c)$

Among the 60 users who did not watch the lecture, 28 passed:

$$
P(Q \mid W^c) = \frac{28}{60} = \frac{7}{15} \approx 0.4667.
$$

Among the 50 users who did not pass, 18 watched the lecture:

$$
P(W \mid Q^c) = \frac{18}{50} = 0.36.
$$

---

### Part 3 — Why $P(Q \mid W)$ and $P(W \mid Q)$ are different

$P(Q \mid W)$ uses all **lecture watchers** as the reference group and asks how many of them passed. $P(W \mid Q)$ uses all **quiz passers** as the reference group and asks how many of them watched the lecture. Different denominators mean different questions and different answers.

---

### Part 4 — Which probability is useful for measuring effect?

To assess whether watching the lecture helps, compare pass rates:

$$
P(Q \mid W) = 0.80 \quad \text{vs.} \quad P(Q \mid W^c) \approx 0.4667.
$$

So $P(Q \mid W)$ (and its comparison to $P(Q \mid W^c)$) is the relevant quantity.

---

### Part 5 — Which probability describes users who passed?

To describe the composition of quiz passers, use $P(W \mid Q) = 0.72$.

---

## Final Result

$$
P(Q \mid W) = 0.80,\quad P(W \mid Q) = 0.72,
$$

$$
P(Q \mid W^c) = \frac{7}{15} \approx 0.4667,\quad P(W \mid Q^c) = 0.36.
$$

Watching the lecture is associated with a higher pass rate, and 72% of quiz passers watched the lecture.

---

## Interpretation / Sanity Check

All values are in $[0, 1]$. The pass rate drops sharply from 0.80 to about 0.467 when users do not watch the lecture, indicating a strong association.

---

## Common Mistakes

- Treating $P(Q \mid W)$ and $P(W \mid Q)$ as interchangeable.
- Comparing raw counts (72 vs 28) instead of conditional rates (80% vs 46.7%).
