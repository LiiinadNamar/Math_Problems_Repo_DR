# Problem 02 — Four Regions of a Sample Space

## Problem Statement

From the given two-way table, compute the four region probabilities, verify they sum to 1, compute two unions, and compare conditional probabilities to decide whether the ticket type affects the probability of being solved on first contact.

| Ticket type   | Solved during first contact | Not solved during first contact | Total |
| ------------- | --------------------------: | ------------------------------: | ----: |
| Technical     |                          90 |                              60 |   150 |
| Non-technical |                         160 |                              40 |   200 |
| Total         |                         250 |                             100 |   350 |

$$
T = \text{ticket is technical},
$$

$$
S = \text{ticket was solved during the first contact}.
$$

---

## Definitions / Theory

**Four-region decomposition.**

$$
\Omega = (T \cap S) \cup (T \cap S^c) \cup (T^c \cap S) \cup (T^c \cap S^c).
$$

**Union from complement.**

$$
P(T \cup S) = 1 - P(T^c \cap S^c),
$$

$$
P(T^c \cup S) = 1 - P(T \cap S^c).
$$

**Conditional probability.**

$$
P(S \mid T) = \frac{P(T \cap S)}{P(T)}.
$$

---

## Step-by-Step Solution

### Part 1 — Four disjoint regions

Total $n = 350$:

$$
P(T \cap S) = \frac{90}{350} = \frac{9}{35} \approx 0.2571,
$$

$$
P(T \cap S^c) = \frac{60}{350} = \frac{6}{35} \approx 0.1714,
$$

$$
P(T^c \cap S) = \frac{160}{350} = \frac{16}{35} \approx 0.4571,
$$

$$
P(T^c \cap S^c) = \frac{40}{350} = \frac{4}{35} \approx 0.1143.
$$

---

### Part 2 — Verify they sum to 1

$$
\frac{9}{35} + \frac{6}{35} + \frac{16}{35} + \frac{4}{35} = \frac{35}{35} = 1.
$$

---

### Part 3 — Compute $P(T \cup S)$ and $P(T^c \cup S)$

$$
P(T \cup S) = 1 - P(T^c \cap S^c) = 1 - \frac{4}{35} = \frac{31}{35} \approx 0.8857,
$$

$$
P(T^c \cup S) = 1 - P(T \cap S^c) = 1 - \frac{6}{35} = \frac{29}{35} \approx 0.8286.
$$

---

### Part 4 — Compute $P(S \mid T)$ and $P(S \mid T^c)$

$$
P(S \mid T) = \frac{90}{150} = 0.60,
$$

$$
P(S \mid T^c) = \frac{160}{200} = 0.80.
$$

---

### Part 5 — Does being technical change the probability?

Yes. The first-contact resolution rate drops from 80% (non-technical) to 60% (technical). Therefore, ticket type affects the probability of being solved on first contact.

---

## Final Result

$$
P(T \cap S) = \frac{9}{35},\quad P(T \cap S^c) = \frac{6}{35},\quad P(T^c \cap S) = \frac{16}{35},\quad P(T^c \cap S^c) = \frac{4}{35}.
$$

$$
P(T \cup S) = \frac{31}{35},\quad P(T^c \cup S) = \frac{29}{35}.
$$

$$
P(S \mid T) = 0.60,\quad P(S \mid T^c) = 0.80.
$$

---

## Interpretation / Sanity Check

All probabilities lie in $[0, 1]$ and sum to $1$. The conditional probability is lower for technical tickets, indicating reduced first-contact resolution compared to non-technical tickets.

---

## Common Mistakes

- Using row or column totals without dividing by $n$.
- Mixing up $P(S \mid T)$ with $P(T \mid S)$.
- Assuming a union probability is the sum of marginals without subtracting the intersection.
