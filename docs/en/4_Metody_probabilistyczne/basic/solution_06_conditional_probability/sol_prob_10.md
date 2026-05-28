# Problem 10 — Comprehensive problem: event algebra, conditioning, independence, and Bayes

## Problem Statement

A company studies whether users complete an online onboarding process. Users are divided into two groups: those who received a tutorial and those who did not. The task integrates all major tools of event algebra and conditional probability: four-region decomposition, marginal and joint probabilities, conditional probabilities in both directions, independence testing, and verbal interpretation.

| Group             | Completed onboarding | Did not complete onboarding | Total |
| ----------------- | -------------------: | --------------------------: | ----: |
| Received tutorial |                  180 |                          70 |   250 |
| No tutorial       |                  120 |                         130 |   250 |
| Total             |                  300 |                         200 |   500 |

**Events defined:**

$$
T = \text{the user received the tutorial},
$$

$$
C = \text{the user completed onboarding}.
$$

---

## Definitions / Theory

**Four-region decomposition.**
Two events $T$ and $C$ divide the sample space into four disjoint regions:

$$
\Omega = (T \cap C) \cup (T \cap C^c) \cup (T^c \cap C) \cup (T^c \cap C^c).
$$

Probabilities are obtained by dividing cell counts by $n = 500$.

**Marginal probability from the decomposition:**

$$
P(T) = P(T \cap C) + P(T \cap C^c), \qquad P(C) = P(T \cap C) + P(T^c \cap C).
$$

**Inclusion-exclusion:**

$$
P(T \cup C) = P(T) + P(C) - P(T \cap C).
$$

**Conditional probability:**

$$
P(C \mid T) = \frac{P(T \cap C)}{P(T)}, \qquad P(T \mid C) = \frac{P(T \cap C)}{P(C)}.
$$

**Independence:**
$T$ and $C$ are independent if and only if

$$
P(T \cap C) = P(T) \cdot P(C).
$$

Equivalently, $T$ and $C$ are independent if and only if $P(C \mid T) = P(C)$.

---

## Step-by-Step Solution

### Part 1 — Four disjoint regions

Divide each cell count by $n = 500$:

$$
P(T \cap C) = \frac{180}{500} = 0.36,
$$

$$
P(T \cap C^c) = \frac{70}{500} = 0.14,
$$

$$
P(T^c \cap C) = \frac{120}{500} = 0.24,
$$

$$
P(T^c \cap C^c) = \frac{130}{500} = 0.26.
$$

**Verification:** The four probabilities must sum to $1$:

$$
0.36 + 0.14 + 0.24 + 0.26 = 1.00. \checkmark
$$

---

### Part 2 — Compute $P(T)$, $P(C)$, $P(T \cup C)$

**Marginal probability of receiving the tutorial:**

$$
P(T) = P(T \cap C) + P(T \cap C^c) = 0.36 + 0.14 = 0.50.
$$

This agrees with the row total: $250/500 = 0.50$.

**Marginal probability of completing onboarding:**

$$
P(C) = P(T \cap C) + P(T^c \cap C) = 0.36 + 0.24 = 0.60.
$$

This agrees with the column total: $300/500 = 0.60$.

**Probability of receiving tutorial or completing onboarding (or both):**

$$
P(T \cup C) = P(T) + P(C) - P(T \cap C) = 0.50 + 0.60 - 0.36 = 0.74.
$$

Equivalently, using the complement:

$$
P(T \cup C) = 1 - P(T^c \cap C^c) = 1 - 0.26 = 0.74. \checkmark
$$

---

### Part 3 — Compute $P(C \mid T)$ and $P(C \mid T^c)$

**Completion rate among users who received the tutorial.**

The reference population is the 250 tutorial users. Among them, 180 completed onboarding:

$$
P(C \mid T) = \frac{P(T \cap C)}{P(T)} = \frac{0.36}{0.50} = 0.72.
$$

**Completion rate among users who did not receive the tutorial.**

The reference population is the 250 non-tutorial users. Among them, 120 completed onboarding:

$$
P(C \mid T^c) = \frac{P(T^c \cap C)}{P(T^c)} = \frac{0.24}{0.50} = 0.48.
$$

---

### Part 4 — Compute $P(T \mid C)$ and $P(T \mid C^c)$

**Fraction of tutorial recipients among users who completed onboarding.**

The reference population is the 300 users who completed onboarding. Among them, 180 had received the tutorial:

$$
P(T \mid C) = \frac{P(T \cap C)}{P(C)} = \frac{0.36}{0.60} = 0.60.
$$

**Fraction of tutorial recipients among users who did not complete onboarding.**

The reference population is the 200 users who did not complete onboarding. Among them, 70 had received the tutorial:

$$
P(T \mid C^c) = \frac{P(T \cap C^c)}{P(C^c)} = \frac{0.14}{0.40} = 0.35.
$$

---

### Part 5 — Test for independence

Check whether $P(T \cap C) = P(T) \cdot P(C)$:

$$
P(T) \cdot P(C) = 0.50 \times 0.60 = 0.30.
$$

$$
P(T \cap C) = 0.36.
$$

Since $0.36 \neq 0.30$, the events $T$ and $C$ are **not independent** — they are **dependent**.

An equivalent check: $P(C \mid T) = 0.72 \neq 0.60 = P(C)$. Knowing that a user received the tutorial increases the probability of completion, so the two events are not independent.

---

### Part 6 — Does receiving the tutorial appear to change the probability of completing onboarding?

$$
P(C \mid T) = 0.72, \qquad P(C \mid T^c) = 0.48, \qquad P(C) = 0.60.
$$

The completion rate among tutorial recipients (72%) is substantially higher than among non-recipients (48%). **Yes, receiving the tutorial is associated with a higher probability of completing onboarding.** The difference of 24 percentage points suggests the tutorial has a meaningful effect.

Note: this is an observational analysis from a table. It shows association, not necessarily causation.

---

### Part 7 — Difference between $P(C \mid T)$ and $P(T \mid C)$

| Expression | Value | Reference population | Question answered |
|---|---|---|---|
| $P(C \mid T)$ | $0.72$ | All tutorial recipients | What fraction of tutorial recipients completed onboarding? |
| $P(T \mid C)$ | $0.60$ | All users who completed onboarding | What fraction of completers had received the tutorial? |

$P(C \mid T) = 0.72$ describes the **effect of the tutorial**: among those who received it, 72% completed onboarding.

$P(T \mid C) = 0.60$ describes the **composition of the completion group**: 60% of users who completed onboarding happened to have received the tutorial.

The two quantities answer entirely different questions. They share the numerator $P(T \cap C) = 0.36$ but differ in the denominator ($P(T) = 0.50$ versus $P(C) = 0.60$). Neither value implies the other.

---

### Part 8 — Short verbal interpretation

Among users who received the tutorial, **72%** completed the onboarding process, compared to only **48%** among those without a tutorial. The overall completion rate is **60%**. Tutorial recipients are thus 24 percentage points more likely to complete onboarding than non-recipients. Among all users who completed onboarding, **60%** had received the tutorial — reflecting both the high completion rate and the fact that the two groups are equal in size.

---

## Final Result

$$
P(T \cap C) = 0.36, \quad P(T \cap C^c) = 0.14, \quad P(T^c \cap C) = 0.24, \quad P(T^c \cap C^c) = 0.26.
$$

$$
P(T) = 0.50, \quad P(C) = 0.60, \quad P(T \cup C) = 0.74.
$$

$$
P(C \mid T) = 0.72, \quad P(C \mid T^c) = 0.48.
$$

$$
P(T \mid C) = 0.60, \quad P(T \mid C^c) = 0.35.
$$

**$T$ and $C$ are dependent. Receiving the tutorial is associated with a substantially higher completion rate.**

---

## Interpretation / Sanity Check

All probabilities lie in $[0, 1]$. The four region probabilities sum to $1$.

The overall completion rate $P(C) = 0.60$ lies between $P(C \mid T) = 0.72$ and $P(C \mid T^c) = 0.48$, consistent with the law of total probability:

$$
P(C) = P(C \mid T) \cdot P(T) + P(C \mid T^c) \cdot P(T^c) = 0.72 \times 0.50 + 0.48 \times 0.50 = 0.36 + 0.24 = 0.60. \checkmark
$$

---

## Common Mistakes

**Mistake 1: Confusing $P(C \mid T)$ with $P(T \mid C)$.**
These quantities have the same numerator but different denominators. They answer entirely different questions and must not be substituted for each other.

**Mistake 2: Concluding independence because both groups are equal in size.**
The equal group sizes ($P(T) = P(T^c) = 0.50$) are irrelevant to independence. Independence requires $P(T \cap C) = P(T) \cdot P(C)$, which fails here.

**Mistake 3: Interpreting association as causation.**
The finding that $P(C \mid T) > P(C \mid T^c)$ establishes an association between tutorial receipt and completion. It does not by itself establish that the tutorial *causes* higher completion, since users who receive the tutorial may differ from others in additional ways.

**Mistake 4: Using only conditional probabilities to check independence.**
It is sufficient to check one of $P(C \mid T) = P(C)$ or $P(T \cap C) = P(T) \cdot P(C)$. Both lead to the same conclusion, but one must be checked explicitly.
