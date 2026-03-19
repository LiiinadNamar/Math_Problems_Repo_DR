# Task 7 — k-Permutations (Ordered Selections Without Repetition)

## Problem Statement

1. In how many ways can the first three places be assigned among 12 runners?
2. How many 4-digit numbers with distinct digits can be formed from the digits 1–9?
3. How many of these numbers are divisible by 5?

---

## Definitions / Theory

A **k-permutation** is an ordered selection of $k$ elements from $n$ distinct elements, where no element may be used more than once.

$$
P(n, k) = \frac{n!}{(n-k)!} = n \times (n-1) \times \cdots \times (n-k+1)
$$

**Why ordered?** The first, second, and third places are distinct — finishing first is different from finishing second.

**Product rule with constraints:** when one position has a restricted choice, fix that position first, then count the remaining positions freely.

---

## Step-by-Step Solution

### Problem 1 — First three places among 12 runners

The three medals (1st, 2nd, 3rd) are distinct — order matters. No runner can receive two medals.

Reasoning position by position:

- 1st place: 12 choices (any runner)
- 2nd place: 11 choices (any runner except the one in 1st)
- 3rd place: 10 choices (any runner except those in 1st and 2nd)

$$
P(12, 3) = 12 \times 11 \times 10 = 1{,}320
$$

---

### Problem 2 — 4-digit numbers with distinct digits from $\{1, 2, \ldots, 9\}$

Available digits: $\{1, 2, 3, 4, 5, 6, 7, 8, 9\}$ — nine digits, no zero. Each digit used at most once. Order matters — different digit orders give different numbers.

Position by position:

- Thousands digit: 9 choices
- Hundreds digit: 8 choices (one digit already used)
- Tens digit: 7 choices
- Units digit: 6 choices

$$
P(9, 4) = 9 \times 8 \times 7 \times 6 = 3{,}024
$$

---

### Problem 3 — 4-digit numbers divisible by 5

A number is divisible by 5 if and only if its last digit is $0$ or $5$. Since the available digits are $\{1, \ldots, 9\}$, zero is not available. Therefore the units digit must be exactly $5$.

**Step 1 — Fix the units digit.**

The units digit is 5. Exactly 1 choice.

**Step 2 — Fill the remaining three positions.**

Choose from the remaining $9 - 1 = 8$ digits (all except 5), without repetition:

$$
P(8, 3) = 8 \times 7 \times 6 = 336
$$

**Step 3 — Multiply.**

$$
1 \times 336 = 336
$$

**Sanity check:** the fraction of all valid 4-digit numbers that are divisible by 5:

$$
\frac{336}{3{,}024} = \frac{1}{9}
$$

Exactly 1 out of the 9 available digits satisfies the condition, so $\frac{1}{9}$ is expected. $\checkmark$

---

## Final Result

| Problem | Formula | Answer |
|---|---|---|
| 1. First three places from 12 | $P(12,3) = 12 \times 11 \times 10$ | $1{,}320$ |
| 2. 4-digit numbers, distinct digits from 1–9 | $P(9,4) = 9 \times 8 \times 7 \times 6$ | $3{,}024$ |
| 3. Divisible by 5 | Fix units $= 5$, then $P(8,3)$ | $336$ |

---

## Common Mistakes

- Using $\binom{9}{4}$ instead of $P(9,4)$ in Problem 2. The digits form a number — their order matters.
- In Problem 3, allowing the units digit to be 0. Zero is not in the digit set $\{1, \ldots, 9\}$.
- Fixing the constrained position last instead of first, which complicates counting unnecessarily.