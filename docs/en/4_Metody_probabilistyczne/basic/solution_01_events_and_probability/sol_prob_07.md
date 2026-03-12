# Task 7 — Events and Probabilities in Die Rolling

## Problem Statement

Using the sample spaces from Task 2, assign probabilities to elementary outcomes and compute the probabilities of the specified events for one, two, and three rolls of a fair six-sided die.

---

## Definitions / Theory

**Fair die**: all six faces are equally likely.

- In $\Omega_1$: each outcome has probability $\frac{1}{6}$.
- In $\Omega_2$: each outcome has probability $\frac{1}{36}$.
- In $\Omega_3$: each outcome has probability $\frac{1}{216}$.

**Classical probability**:

$$
P(A) = \frac{|A|}{|\Omega|}
$$

**Complement rule**:

$$
P(A^c) = 1 - P(A)
$$

---

## Step-by-Step Solution

### One Die Roll

$$
\Omega_1 = \{1, 2, 3, 4, 5, 6\}, \quad |\Omega_1| = 6, \quad P(\{i\}) = \frac{1}{6}
$$

**Event $A_1$** — the result is even:

$$
A_1 = \{2, 4, 6\}, \quad P(A_1) = \frac{3}{6} = \frac{1}{2}
$$

**Event $B_1$** — the result is greater than 4:

$$
B_1 = \{5, 6\}, \quad P(B_1) = \frac{2}{6} = \frac{1}{3}
$$

**Event $C_1$** — the result is at most 3:

$$
C_1 = \{1, 2, 3\}, \quad P(C_1) = \frac{3}{6} = \frac{1}{2}
$$

---

### Two Die Rolls

$$
\Omega_2 = \{(i,j) : i,j \in \{1,\ldots,6\}\}, \quad |\Omega_2| = 36
$$

**Event $A_2$** — the sum equals 7:

The pairs $(i,j)$ with $i + j = 7$:

$$
A_2 = \{(1,6),\ (2,5),\ (3,4),\ (4,3),\ (5,2),\ (6,1)\}
$$

$$
P(A_2) = \frac{6}{36} = \frac{1}{6}
$$

**Event $B_2$** — both results are the same:

$$
B_2 = \{(1,1),\ (2,2),\ (3,3),\ (4,4),\ (5,5),\ (6,6)\}
$$

$$
P(B_2) = \frac{6}{36} = \frac{1}{6}
$$

**Event $C_2$** — the sum is at least 10:

Pairs with $i + j \geq 10$:

$$
\{(4,6),\ (5,5),\ (5,6),\ (6,4),\ (6,5),\ (6,6)\}
$$

$$
P(C_2) = \frac{6}{36} = \frac{1}{6}
$$

---

### Three Die Rolls

$$
\Omega_3 = \{(i,j,k) : i,j,k \in \{1,\ldots,6\}\}, \quad |\Omega_3| = 216
$$

**Event $A_3$** — the sum equals 10:

Count the number of ordered triples $(i,j,k)$ with $i+j+k = 10$ and $i,j,k \in \{1,\ldots,6\}$.

Using stars and bars adjusted for the constraint $1 \leq i,j,k \leq 6$, substitute $i' = i-1$ etc. to get $i'+j'+k' = 7$ with $0 \leq i',j',k' \leq 5$.

By inclusion-exclusion:

$$
\binom{9}{2} - 3\binom{3}{2} = 36 - 9 = 27
$$

$$
P(A_3) = \frac{27}{216} = \frac{1}{8}
$$

**Event $B_3$** — exactly two rolls give the same number:

Choose the repeated value: 6 ways. Choose which two of the three rolls show it: $\binom{3}{2} = 3$ ways. The third roll must differ from the repeated value: 5 ways.

$$
|B_3| = 6 \times 3 \times 5 = 90
$$

$$
P(B_3) = \frac{90}{216} = \frac{5}{12}
$$

**Event $C_3$** — exactly two twos and one three (in any order):

The sequences $(2,2,3)$, $(2,3,2)$, $(3,2,2)$ are the only outcomes.

$$
|C_3| = 3
$$

$$
P(C_3) = \frac{3}{216} = \frac{1}{72}
$$

---

### Additional Event on $\Omega_3$

**Event $D_3$** — all three rolls give distinct values:

$$
|D_3| = 6 \times 5 \times 4 = 120
$$

$$
P(D_3) = \frac{120}{216} = \frac{5}{9}
$$

---

## Final Result

| Event | Description | Probability |
|---|---|---|
| $A_1$ | Even result | $\frac{1}{2}$ |
| $B_1$ | Result greater than 4 | $\frac{1}{3}$ |
| $C_1$ | Result at most 3 | $\frac{1}{2}$ |
| $A_2$ | Sum equals 7 | $\frac{1}{6}$ |
| $B_2$ | Both results equal | $\frac{1}{6}$ |
| $C_2$ | Sum at least 10 | $\frac{1}{6}$ |
| $A_3$ | Sum equals 10 | $\frac{1}{8}$ |
| $B_3$ | Exactly two rolls equal | $\frac{5}{12}$ |
| $C_3$ | Two twos and one three | $\frac{1}{72}$ |
| $D_3$ | All three rolls distinct | $\frac{5}{9}$ |

---

## Interpretation / Sanity Check

The sum of 7 in two dice rolls has the highest probability among all possible sums ($\frac{1}{6}$), which is consistent with the well-known result that 7 is the most likely sum.

For event $B_3$, a sanity check: the complementary events are "all three equal" and "all three distinct."

$$
P(\text{all equal}) = \frac{6}{216} = \frac{1}{36}, \quad P(\text{all distinct}) = \frac{120}{216} = \frac{5}{9}
$$

$$
P(B_3) + \frac{1}{36} + \frac{5}{9} = \frac{90}{216} + \frac{6}{216} + \frac{120}{216} = \frac{216}{216} = 1 \checkmark
$$

---

## Common Mistakes

- Forgetting to account for all orderings when counting triples. For example, for $C_3$ one might write only $(2,2,3)$ and miss the other two orderings.
- Using combinations instead of permutations when order matters.
- In event $A_3$, attempting to list all triples manually instead of using combinatorial counting.
