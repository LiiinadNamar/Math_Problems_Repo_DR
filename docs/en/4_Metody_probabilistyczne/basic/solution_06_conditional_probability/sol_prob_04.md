# Problem 04 — Inclusion-Exclusion and Double Counting

## Problem Statement

Given counts for two tools and their overlap, compute probabilities of events and regions, use inclusion-exclusion for the union, compute conditional probabilities, and explain the double counting in $P(A) + P(B)$.

Total employees: $200$.

* 130 use Tool A,
* 90 use Tool B,
* 60 use both tools.

$$
A = \text{employee uses Tool A},
$$

$$
B = \text{employee uses Tool B}.
$$

---

## Definitions / Theory

**Inclusion-exclusion.**

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B).
$$

**Set differences.**

$$
P(A \setminus B) = P(A \cap B^c), \quad P(B \setminus A) = P(A^c \cap B).
$$

**Conditional probability.**

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}.
$$

---

## Step-by-Step Solution

### Part 1 — Compute $P(A)$, $P(B)$, $P(A \cap B)$

$$
P(A) = \frac{130}{200} = 0.65,
$$

$$
P(B) = \frac{90}{200} = 0.45,
$$

$$
P(A \cap B) = \frac{60}{200} = 0.30.
$$

---

### Part 2 — Compute $P(A \cup B)$

$$
P(A \cup B) = 0.65 + 0.45 - 0.30 = 0.80.
$$

---

### Part 3 — Remaining regions

$$
P(A \setminus B) = \frac{130 - 60}{200} = \frac{70}{200} = 0.35,
$$

$$
P(B \setminus A) = \frac{90 - 60}{200} = \frac{30}{200} = 0.15,
$$

$$
P(A^c \cap B^c) = 1 - P(A \cup B) = 0.20.
$$

---

### Part 4 — Conditional probabilities

$$
P(A \mid B) = \frac{0.30}{0.45} = \frac{2}{3} \approx 0.6667,
$$

$$
P(B \mid A) = \frac{0.30}{0.65} = \frac{6}{13} \approx 0.4615.
$$

---

### Part 5 — Why $P(A \cup B) \neq P(A) + P(B)$

Adding $P(A)$ and $P(B)$ counts employees who use **both** tools twice. Inclusion-exclusion corrects this by subtracting $P(A \cap B)$.

---

### Part 6 — Which group is counted twice?

Employees who use both Tool A and Tool B, i.e., the group $A \cap B$.

---

## Final Result

$$
P(A) = 0.65,\quad P(B) = 0.45,\quad P(A \cap B) = 0.30.
$$

$$
P(A \cup B) = 0.80.
$$

$$
P(A \setminus B) = 0.35,\quad P(B \setminus A) = 0.15,\quad P(A^c \cap B^c) = 0.20.
$$

$$
P(A \mid B) = \frac{2}{3},\quad P(B \mid A) = \frac{6}{13}.
$$

---

## Interpretation / Sanity Check

The three disjoint regions $A \setminus B$, $B \setminus A$, and $A \cap B$ sum to $0.80$, so 80% of employees use at least one tool. The remaining 20% use neither tool.

---

## Common Mistakes

- Forgetting to subtract $P(A \cap B)$ when computing $P(A \cup B)$.
- Confusing $P(A \mid B)$ with $P(B \mid A)$.
