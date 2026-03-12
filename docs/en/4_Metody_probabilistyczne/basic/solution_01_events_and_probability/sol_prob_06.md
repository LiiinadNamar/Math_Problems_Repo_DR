# Task 6 — Events and Probabilities in Coin Tossing

## Problem Statement

Using the sample spaces from Task 1, assign probabilities to elementary outcomes and compute the probabilities of the specified events for one, two, and three coin tosses.

---

## Definitions / Theory

**Event** is a subset $A \subseteq \Omega$ of the sample space.

**Probability of an event** under the classical model (equally likely outcomes):

$$
P(A) = \frac{|A|}{|\Omega|}
$$

where $|A|$ is the number of elementary outcomes in $A$ and $|\Omega|$ is the total number of elementary outcomes.

**Fair coin**: all elementary outcomes are equally likely.

- In $\Omega_1$: each outcome has probability $\frac{1}{2}$.
- In $\Omega_2$: each outcome has probability $\frac{1}{4}$.
- In $\Omega_3$: each outcome has probability $\frac{1}{8}$.

**Complement rule**:

$$
P(A^c) = 1 - P(A)
$$

---

## Step-by-Step Solution

### One Coin Toss

$$
\Omega_1 = \{H, T\}, \quad |\Omega_1| = 2, \quad P(\{H\}) = P(\{T\}) = \frac{1}{2}
$$

**Event $A_1$** — the result is heads:

$$
A_1 = \{H\}, \quad P(A_1) = \frac{1}{2}
$$

**Event $B_1$** — the result is tails:

$$
B_1 = \{T\}, \quad P(B_1) = \frac{1}{2}
$$

**Event $C_1$** — the result is not tails:

$$
C_1 = \Omega_1 \setminus \{T\} = \{H\}, \quad P(C_1) = \frac{1}{2}
$$

Note that $C_1 = A_1$: "not tails" is the same event as "heads."

---

### Two Coin Tosses

$$
\Omega_2 = \{(H,H),\ (H,T),\ (T,H),\ (T,T)\}, \quad |\Omega_2| = 4
$$

Each elementary outcome has probability $\frac{1}{4}$.

**Event $A_2$** — exactly one head:

$$
A_2 = \{(H,T),\ (T,H)\}, \quad P(A_2) = \frac{2}{4} = \frac{1}{2}
$$

**Event $B_2$** — at least one head:

$$
B_2 = \{(H,H),\ (H,T),\ (T,H)\}, \quad P(B_2) = \frac{3}{4}
$$

Equivalently, using the complement (the only outcome with no heads is $(T,T)$):

$$
P(B_2) = 1 - P(\{(T,T)\}) = 1 - \frac{1}{4} = \frac{3}{4}
$$

**Event $C_2$** — both tosses give the same result:

$$
C_2 = \{(H,H),\ (T,T)\}, \quad P(C_2) = \frac{2}{4} = \frac{1}{2}
$$

---

### Three Coin Tosses

$$
\Omega_3 = \{(H,H,H),\ (H,H,T),\ (H,T,H),\ (H,T,T),\ (T,H,H),\ (T,H,T),\ (T,T,H),\ (T,T,T)\}
$$

$$
|\Omega_3| = 8, \quad \text{each outcome has probability } \frac{1}{8}
$$

**Event $A_3$** — exactly two heads:

$$
A_3 = \{(H,H,T),\ (H,T,H),\ (T,H,H)\}, \quad P(A_3) = \frac{3}{8}
$$

**Event $B_3$** — at least one tail:

The complement is "no tails at all," i.e. all heads:

$$
B_3^c = \{(H,H,H)\}, \quad P(B_3^c) = \frac{1}{8}
$$

$$
P(B_3) = 1 - \frac{1}{8} = \frac{7}{8}
$$

**Event $C_3$** — all three tosses give the same result:

$$
C_3 = \{(H,H,H),\ (T,T,T)\}, \quad P(C_3) = \frac{2}{8} = \frac{1}{4}
$$

---

### Additional Event on $\Omega_3$

**Event $D_3$** — the first toss is heads and the last toss is tails:

$$
D_3 = \{(H,H,T),\ (H,T,T)\}, \quad P(D_3) = \frac{2}{8} = \frac{1}{4}
$$

---

## Final Result

| Event | Description | Probability |
|---|---|---|
| $A_1$ | Heads in one toss | $\frac{1}{2}$ |
| $B_1$ | Tails in one toss | $\frac{1}{2}$ |
| $C_1$ | Not tails in one toss | $\frac{1}{2}$ |
| $A_2$ | Exactly one head in two tosses | $\frac{1}{2}$ |
| $B_2$ | At least one head in two tosses | $\frac{3}{4}$ |
| $C_2$ | Both tosses same result | $\frac{1}{2}$ |
| $A_3$ | Exactly two heads in three tosses | $\frac{3}{8}$ |
| $B_3$ | At least one tail in three tosses | $\frac{7}{8}$ |
| $C_3$ | All three tosses same result | $\frac{1}{4}$ |
| $D_3$ | First heads, last tails | $\frac{1}{4}$ |

---

## Interpretation / Sanity Check

All probabilities lie in $[0, 1]$. The probabilities of complementary events sum to $1$:

$$
P(B_3) + P(B_3^c) = \frac{7}{8} + \frac{1}{8} = 1 \checkmark
$$

The event $B_2$ (at least one head) has a higher probability than $A_2$ (exactly one head) because $B_2 \supset A_2$ — it includes more outcomes.

---

## Common Mistakes

- Listing outcomes for "exactly two heads" as only $(H,H,T)$, forgetting the other orderings $(H,T,H)$ and $(T,H,H)$.
- Computing "at least one" directly by listing outcomes instead of using the complement, which is faster and less error-prone.
- Assigning unequal probabilities to outcomes of a fair coin, for example assuming $(H,H)$ is less likely than $(H,T)$.
