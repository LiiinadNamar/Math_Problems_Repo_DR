# Problem 05 — Independence from Data

## Problem Statement

A streaming platform records whether users hold a premium account and whether they watched a movie during the last weekend. The task is to compute marginal and conditional probabilities from the given two-way table, then determine whether account type and movie-watching behavior are independent events.

| Account type | Watched a movie | Did not watch a movie | Total |
| ------------ | --------------: | --------------------: | ----: |
| Premium      |              84 |                    36 |   120 |
| Free         |              56 |                    24 |    80 |
| Total        |             140 |                    60 |   200 |

**Events defined:**

$$
A = \text{the user has a premium account},
$$

$$
M = \text{the user watched a movie during the weekend}.
$$

---

## Definitions / Theory

**Sample space and four-region decomposition.**
Given two events $A$ and $B$, the sample space decomposes into four disjoint regions:

$$
\Omega = (A \cap B) \cup (A \cap B^c) \cup (A^c \cap B) \cup (A^c \cap B^c).
$$

Their probabilities are obtained by dividing each cell count by the total number of observations $n$.

**Marginal probability.**
The probability of a single event is obtained by summing over the relevant row or column total:

$$
P(A) = \frac{\text{row total for } A}{n}.
$$

**Conditional probability.**
If $P(B) > 0$, then

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}.
$$

Conditioning on $B$ restricts the reference population to outcomes inside $B$.

**Independence.**
Events $A$ and $B$ are **independent** if and only if

$$
P(A \cap B) = P(A) \cdot P(B).
$$

An equivalent formulation: $A$ and $B$ are independent if and only if

$$
P(A \mid B) = P(A),
$$

provided $P(B) > 0$. Independence means that knowing whether $B$ occurred provides no information about whether $A$ occurred.

---

## Step-by-Step Solution

### Part 1 — Compute $P(A)$, $P(M)$, $P(A \cap M)$

Divide each relevant count by the total $n = 200$.

**Marginal probability of premium account:**

$$
P(A) = \frac{120}{200} = 0.60.
$$

**Marginal probability of watching a movie:**

$$
P(M) = \frac{140}{200} = 0.70.
$$

**Joint probability (premium and watched a movie):**

$$
P(A \cap M) = \frac{84}{200} = 0.42.
$$

---

### Part 2 — Compute $P(M \mid A)$ and $P(M \mid A^c)$

**Conditional probability of watching a movie given premium account.**

The reference population is restricted to the 120 premium users. Among them, 84 watched a movie:

$$
P(M \mid A) = \frac{P(A \cap M)}{P(A)} = \frac{84/200}{120/200} = \frac{84}{120} = 0.70.
$$

**Conditional probability of watching a movie given free account.**

The reference population is restricted to the 80 free users. Among them, 56 watched a movie:

$$
P(M \mid A^c) = \frac{P(A^c \cap M)}{P(A^c)} = \frac{56/200}{80/200} = \frac{56}{80} = 0.70.
$$

---

### Part 3 — Decide whether $A$ and $M$ are independent

**Method 1: Compare $P(A \cap M)$ with $P(A) \cdot P(M)$.**

$$
P(A) \cdot P(M) = 0.60 \times 0.70 = 0.42.
$$

$$
P(A \cap M) = 0.42.
$$

Since $P(A \cap M) = P(A) \cdot P(M)$, the events $A$ and $M$ are **independent**.

**Method 2: Compare $P(M \mid A)$ with $P(M)$.**

$$
P(M \mid A) = 0.70 = P(M).
$$

Conditioning on $A$ does not change the probability of $M$. This confirms independence.

---

## Final Result

$$
P(A) = 0.60, \quad P(M) = 0.70, \quad P(A \cap M) = 0.42.
$$

$$
P(M \mid A) = 0.70, \quad P(M \mid A^c) = 0.70.
$$

**The events $A$ and $M$ are independent.**

---

## Interpretation / Sanity Check

All computed values lie in $[0, 1]$, as required for probabilities.

The two conditional probabilities $P(M \mid A)$ and $P(M \mid A^c)$ are both equal to $0.70$, which is exactly the marginal $P(M)$. This means that **account type carries no information about weekend movie-watching behavior**. Premium and free users watch movies at exactly the same rate.

Independence here is an empirical observation from the data in this particular table. It is not a logical necessity — in a different dataset, account type and viewing behavior could easily be dependent.

---

## Common Mistakes

**Mistake 1: Concluding dependence because the counts look different.**
The numbers 84 and 56 are different, but they come from groups of different sizes (120 and 80). What matters for independence is the *rate*, not the raw count.

**Mistake 2: Confusing independence with disjointness.**
Disjoint events cannot occur together: $P(A \cap M) = 0$. Independent events *can* occur together, but the occurrence of one does not affect the probability of the other. These are fundamentally different concepts.

**Mistake 3: Checking only one condition.**
It is sufficient to verify $P(A \cap M) = P(A) \cdot P(M)$, but checking both $P(M \mid A) = P(M)$ and $P(M \mid A^c) = P(M)$ provides additional confirmation and deeper understanding.
