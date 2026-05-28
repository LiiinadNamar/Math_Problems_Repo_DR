# Problem 06 — Dependence from Data

## Problem Statement

A delivery company records whether a parcel is international and whether it is delayed. The task is to compute marginal, joint, and conditional probabilities from the two-way table, test for independence, and interpret the asymmetry between $P(D \mid I)$ and $P(I \mid D)$.

| Parcel type   | Delayed | Not delayed | Total |
| ------------- | ------: | ----------: | ----: |
| Domestic      |      24 |         376 |   400 |
| International |      36 |         164 |   200 |
| Total         |      60 |         540 |   600 |

**Events defined:**

$$
I = \text{the parcel is international},
$$

$$
D = \text{the parcel is delayed}.
$$

---

## Definitions / Theory

**Four-region decomposition.**
Given two events $I$ and $D$, the sample space splits into four disjoint regions:

$$
\Omega = (I \cap D) \cup (I \cap D^c) \cup (I^c \cap D) \cup (I^c \cap D^c).
$$

Probabilities are obtained by dividing cell counts by the total $n = 600$.

**Conditional probability.**
If $P(B) > 0$, then

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}.
$$

**Independence.**
Events $A$ and $B$ are independent if and only if

$$
P(A \cap B) = P(A) \cdot P(B).
$$

Equivalently, $A$ and $B$ are independent if and only if $P(A \mid B) = P(A)$.

If this equality does not hold, the events are **dependent**.

**Asymmetry of conditional probability.**
In general, $P(D \mid I) \neq P(I \mid D)$. The two expressions share the numerator $P(I \cap D)$ but have different denominators:

$$
P(D \mid I) = \frac{P(I \cap D)}{P(I)}, \qquad P(I \mid D) = \frac{P(I \cap D)}{P(D)}.
$$

---

## Step-by-Step Solution

### Part 1 — Compute $P(I)$, $P(D)$, $P(I \cap D)$

Total number of parcels: $n = 600$.

$$
P(I) = \frac{200}{600} = \frac{1}{3} \approx 0.3333.
$$

$$
P(D) = \frac{60}{600} = 0.10.
$$

$$
P(I \cap D) = \frac{36}{600} = 0.06.
$$

---

### Part 2 — Compute $P(D \mid I)$ and $P(D \mid I^c)$

**Conditional probability of delay given international parcel.**

The reference population is restricted to the 200 international parcels. Among them, 36 are delayed:

$$
P(D \mid I) = \frac{P(I \cap D)}{P(I)} = \frac{36/600}{200/600} = \frac{36}{200} = 0.18.
$$

**Conditional probability of delay given domestic parcel.**

The reference population is restricted to the 400 domestic parcels. Among them, 24 are delayed:

$$
P(D \mid I^c) = \frac{P(I^c \cap D)}{P(I^c)} = \frac{24/600}{400/600} = \frac{24}{400} = 0.06.
$$

---

### Part 3 — Test for independence

**Check whether $P(I \cap D) = P(I) \cdot P(D)$.**

$$
P(I) \cdot P(D) = \frac{1}{3} \times 0.10 = 0.0\overline{3}.
$$

$$
P(I \cap D) = 0.06.
$$

Since $0.06 \neq 0.0\overline{3}$, the events $I$ and $D$ are **not independent** — they are **dependent**.

An equivalent check: $P(D \mid I) = 0.18 \neq 0.10 = P(D)$. Knowing that a parcel is international changes the probability of delay.

---

### Part 4 — Does international shipping increase the probability of delay?

$$
P(D \mid I) = 0.18, \qquad P(D \mid I^c) = 0.06.
$$

The delay rate for international parcels (18%) is three times the delay rate for domestic parcels (6%). **Yes, international shipping substantially increases the probability of delay.**

---

### Part 5 — Compute $P(I \mid D)$

Among all delayed parcels ($n = 60$), 36 are international:

$$
P(I \mid D) = \frac{P(I \cap D)}{P(D)} = \frac{36/600}{60/600} = \frac{36}{60} = 0.60.
$$

---

### Part 6 — Difference between $P(D \mid I)$ and $P(I \mid D)$

The two expressions answer fundamentally different questions.

| Expression | Reference population | Question answered |
|---|---|---|
| $P(D \mid I) = 0.18$ | All international parcels | What fraction of international parcels are delayed? |
| $P(I \mid D) = 0.60$ | All delayed parcels | What fraction of delayed parcels are international? |

$P(D \mid I) = 0.18$ describes the **risk of delay for international parcels**: 18% of them are delayed.

$P(I \mid D) = 0.60$ describes the **composition of the delayed group**: 60% of delayed parcels happen to be international.

These two numbers are not interchangeable. Switching the condition changes the denominator entirely.

---

## Final Result

$$
P(I) = \frac{1}{3} \approx 0.333, \quad P(D) = 0.10, \quad P(I \cap D) = 0.06.
$$

$$
P(D \mid I) = 0.18, \quad P(D \mid I^c) = 0.06.
$$

$$
P(I \mid D) = 0.60.
$$

**$I$ and $D$ are dependent. International shipping increases the probability of delay by a factor of three.**

---

## Interpretation / Sanity Check

All values lie in $[0, 1]$. The four region probabilities sum to $1$:

$$
\frac{36 + 164 + 24 + 376}{600} = \frac{600}{600} = 1. \checkmark
$$

The large difference between $P(D \mid I) = 0.18$ and $P(D \mid I^c) = 0.06$ is a clear sign of dependence. The overall delay rate $P(D) = 0.10$ lies between the two conditional rates, as expected from the law of total probability:

$$
P(D) = P(D \mid I) \cdot P(I) + P(D \mid I^c) \cdot P(I^c) = 0.18 \cdot \frac{1}{3} + 0.06 \cdot \frac{2}{3} = 0.06 + 0.04 = 0.10. \checkmark
$$

---

## Common Mistakes

**Mistake 1: Confusing $P(D \mid I)$ and $P(I \mid D)$.**
$P(D \mid I) = 0.18$ is not the same as $P(I \mid D) = 0.60$. They share the same numerator but differ in the denominator. Always identify which group forms the denominator.

**Mistake 2: Concluding independence because both events are present in the table.**
The presence of both $I$ and $D$ in the data does not imply independence. Independence requires $P(I \cap D) = P(I) \cdot P(D)$, which must be verified numerically.

**Mistake 3: Using raw counts to compare rates.**
Domestic parcels have 24 delayed cases and international parcels have 36. One cannot directly compare 24 and 36 because the group sizes are different (400 vs. 200). The rates 6% and 18% are the correct basis for comparison.
