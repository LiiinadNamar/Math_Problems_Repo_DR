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

### Three Die Rolls
 
$$
\Omega_3 = \{(i,j,k) : i,j,k \in \{1,\ldots,6\}\}, \quad |\Omega_3| = 216
$$
 
Each elementary outcome is an ordered triple $(i,j,k)$ where $i,j,k \in \{1,2,3,4,5,6\}$. Each has probability $\frac{1}{216}$.
 
---
 
**Event $A_3$** — the sum of the results equals 10.
 
We need to count ordered triples $(i,j,k)$ with $i,j,k \in \{1,\ldots,6\}$ and $i+j+k = 10$.
 
**Step 1 — Substitution to simplify bounds.**
 
Let $i' = i - 1$, $j' = j - 1$, $k' = k - 1$. Then $i', j', k' \in \{0,1,2,3,4,5\}$ and:
 
$$
i' + j' + k' = 10 - 3 = 7
$$
 
We need to count non-negative integer solutions to $i' + j' + k' = 7$ with each variable at most $5$.
 
**Step 2 — Stars and bars without the upper bound.**
 
Without the constraint $i', j', k' \leq 5$, the number of non-negative integer solutions is:
 
$$
\binom{7 + 2}{2} = \binom{9}{2} = 36
$$
 
**Step 3 — Subtract solutions that violate the upper bound.**
 
A variable violates the bound if it equals $6$ or more. Suppose $i' \geq 6$. Set $i'' = i' - 6 \geq 0$. Then $i'' + j' + k' = 1$, which has $\binom{3}{2} = 3$ solutions.
 
By symmetry, the same count applies to $j' \geq 6$ and $k' \geq 6$. No two variables can simultaneously be $\geq 6$ (since $6 + 6 = 12 > 7$).
 
**Step 4 — Inclusion-exclusion.**
 
$$
|A_3| = \binom{9}{2} - 3 \cdot \binom{3}{2} = 36 - 9 = 27
$$
 
**Verification by listing** (grouped by the smallest value):
 
Triples with values from $\{1,\ldots,6\}$ summing to $10$, listed by unordered composition and then counting orderings:
 
| Unordered triple | Orderings |
|---|---|
| $\{1, 3, 6\}$ | $3! = 6$ |
| $\{1, 4, 5\}$ | $3! = 6$ |
| $\{2, 2, 6\}$ | $\frac{3!}{2!} = 3$ |
| $\{2, 3, 5\}$ | $3! = 6$ |
| $\{2, 4, 4\}$ | $\frac{3!}{2!} = 3$ |
| $\{3, 3, 4\}$ | $\frac{3!}{2!} = 3$ |
 
Total: $6 + 6 + 3 + 6 + 3 + 3 = 27$ $\checkmark$
 
$$
P(A_3) = \frac{27}{216} = \frac{1}{8}
$$
 
---
 
**Event $B_3$** — exactly two of the three rolls give the same number.
 
This means the outcome has the form $(a, a, b)$ in some order, where $a \neq b$.
 
**Step 1 — Choose the repeated value $a$.**
 
$a$ can be any face: $6$ choices.
 
**Step 2 — Choose the distinct value $b$.**
 
$b$ can be any face except $a$: $5$ choices.
 
**Step 3 — Choose which two of the three positions show $a$.**
 
The triple has three positions. We choose 2 of them for the repeated value:
 
$$
\binom{3}{2} = 3 \text{ ways}
$$
 
The remaining position automatically gets $b$.
 
**Step 4 — Multiply.**
 
$$
|B_3| = 6 \times 5 \times 3 = 90
$$
 
**Example outcomes** (for $a = 3$, $b = 5$):
 
$$
(3,3,5), \quad (3,5,3), \quad (5,3,3)
$$
 
$$
P(B_3) = \frac{90}{216} = \frac{5}{12}
$$
 
---
 
**Event $C_3$** — the outcome contains exactly two twos and one three, in any order.
 
We need triples using exactly the values $2, 2, 3$ (in any order).
 
**Step 1 — List all orderings.**
 
The three positions must contain two twos and one three. The position of the three can be:
 
- Position 1: $(3, 2, 2)$
- Position 2: $(2, 3, 2)$
- Position 3: $(2, 2, 3)$
 
**Step 2 — Count using the multinomial coefficient.**
 
The number of distinct orderings of the sequence $(2, 2, 3)$ is:
 
$$
\frac{3!}{2! \cdot 1!} = \frac{6}{2} = 3
$$
 
The denominator $2!$ accounts for the two identical twos.
 
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

