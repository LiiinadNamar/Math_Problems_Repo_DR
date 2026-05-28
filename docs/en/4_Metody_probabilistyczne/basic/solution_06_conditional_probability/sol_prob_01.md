# Problem 01 — Event Algebra from a Two-Way Table

## Problem Statement

From the given two-way table, compute the four disjoint region probabilities, then use them to find marginal, union, and conditional probabilities. Decide whether the events are mutually exclusive or independent, and interpret the conditional probabilities.

| Student type               | Submits homework on time | Does not submit on time | Total |
| -------------------------- | -----------------------: | ----------------------: | ----: |
| Attends lectures regularly |                       48 |                      12 |    60 |
| Does not attend regularly  |                       22 |                      18 |    40 |
| Total                      |                       70 |                      30 |   100 |

$$
A = \text{student attends lectures regularly},
$$

$$
B = \text{student submits homework on time}.
$$

---

## Definitions / Theory

**Four-region decomposition.**
Two events $A$ and $B$ split the sample space into four disjoint regions:

$$
\Omega = (A \cap B) \cup (A \cap B^c) \cup (A^c \cap B) \cup (A^c \cap B^c).
$$

**Marginal and union probabilities.**

$$
P(A) = P(A \cap B) + P(A \cap B^c),
$$

$$
P(B) = P(A \cap B) + P(A^c \cap B),
$$

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B).
$$

**Conditional probability.**

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}.
$$

**Independence.**
Events $A$ and $B$ are independent iff $P(A \cap B) = P(A) P(B)$.

---

## Step-by-Step Solution

### Part 1 — Four disjoint regions

Total $n = 100$. Divide each cell by 100:

$$
P(A \cap B) = \frac{48}{100} = 0.48,
$$

$$
P(A \cap B^c) = \frac{12}{100} = 0.12,
$$

$$
P(A^c \cap B) = \frac{22}{100} = 0.22,
$$

$$
P(A^c \cap B^c) = \frac{18}{100} = 0.18.
$$

Check: $0.48 + 0.12 + 0.22 + 0.18 = 1$.

---

### Part 2 — Compute $P(A)$, $P(B)$, $P(A \cup B)$

$$
P(A) = 0.48 + 0.12 = 0.60,
$$

$$
P(B) = 0.48 + 0.22 = 0.70,
$$

$$
P(A \cup B) = 0.60 + 0.70 - 0.48 = 0.82.
$$

Alternative check: $P(A \cup B) = 1 - P(A^c \cap B^c) = 1 - 0.18 = 0.82$.

---

### Part 3 — Compute $P(A \mid B)$ and $P(B \mid A)$

$$
P(A \mid B) = \frac{0.48}{0.70} = \frac{48}{70} = \frac{24}{35} \approx 0.686,
$$

$$
P(B \mid A) = \frac{0.48}{0.60} = 0.80.
$$

---

### Part 4 — Mutually exclusive?

No. $P(A \cap B) = 0.48 > 0$, so the events can occur together.

---

### Part 5 — Independent?

$$
P(A) P(B) = 0.60 \times 0.70 = 0.42 \neq 0.48 = P(A \cap B).
$$

So $A$ and $B$ are **not independent**.

---

### Part 6 — Interpretation

$P(A \mid B) \approx 0.686$ means: among students who submit homework on time, about 68.6% attend lectures regularly.

$P(B \mid A) = 0.80$ means: among students who attend lectures regularly, 80% submit homework on time.

---

## Final Result

$$
P(A \cap B) = 0.48,\quad P(A \cap B^c) = 0.12,\quad P(A^c \cap B) = 0.22,\quad P(A^c \cap B^c) = 0.18.
$$

$$
P(A) = 0.60,\quad P(B) = 0.70,\quad P(A \cup B) = 0.82.
$$

$$
P(A \mid B) = \frac{24}{35} \approx 0.686,\quad P(B \mid A) = 0.80.
$$

Events are **not mutually exclusive** and **not independent**.

---

## Interpretation / Sanity Check

All probabilities lie in $[0, 1]$ and the four-region probabilities sum to $1$. The conditional probabilities are consistent with the row and column totals (48 out of 70, and 48 out of 60).

---

## Common Mistakes

- Using raw counts instead of dividing by the total.
- Confusing $P(A \mid B)$ with $P(B \mid A)$.
- Concluding independence because both events occur together; independence requires $P(A \cap B) = P(A) P(B)$.
