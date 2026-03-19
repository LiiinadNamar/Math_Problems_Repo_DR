# Task 3 — Permutations with Repeated Elements

## Problem Statement

1. How many distinct arrangements of the word MISSISSIPPI are possible?
2. How many distinct arrangements of STATISTICS are possible?
3. How many of the arrangements of STATISTICS start with the letter S?

---

## Definitions / Theory

When $n$ objects are arranged and some are identical, swapping identical objects does not produce a new arrangement. The number of distinct arrangements is:

$$
\frac{n!}{n_1!\, n_2!\, \cdots\, n_r!}
$$

where $n_1, n_2, \ldots, n_r$ are the multiplicities of the distinct types, and $n_1 + n_2 + \cdots + n_r = n$.

**Why divide by factorials?** Each group of $n_i$ identical objects can be permuted among themselves in $n_i!$ ways without changing the visible arrangement. Dividing removes these overcounted copies.

---

## Step-by-Step Solution

### Problem 1 — MISSISSIPPI

**Step 1 — Count total letters and identify repetitions.**

$$
\text{M I S S I S S I P P I}
$$

| Letter | Count |
|---|---|
| M | 1 |
| I | 4 |
| S | 4 |
| P | 2 |
| **Total** | **11** |

**Step 2 — Apply the formula.**

$$
\frac{11!}{1!\cdot 4!\cdot 4!\cdot 2!}
$$

**Step 3 — Compute.**

$$
11! = 39{,}916{,}800
$$

$$
1! = 1,\quad 4! = 24,\quad 4! = 24,\quad 2! = 2
$$

$$
1 \times 24 \times 24 \times 2 = 1152
$$

$$
\frac{39{,}916{,}800}{1152} = 34{,}650
$$

---

### Problem 2 — STATISTICS

**Step 1 — Count total letters and identify repetitions.**

$$
\text{S T A T I S T I C S}
$$

| Letter | Count |
|---|---|
| S | 3 |
| T | 3 |
| A | 1 |
| I | 2 |
| C | 1 |
| **Total** | **10** |

**Step 2 — Apply the formula.**

$$
\frac{10!}{3!\cdot 3!\cdot 1!\cdot 2!\cdot 1!}
$$

**Step 3 — Compute.**

$$
10! = 3{,}628{,}800
$$

$$
3! \times 3! \times 1! \times 2! \times 1! = 6 \times 6 \times 1 \times 2 \times 1 = 72
$$

$$
\frac{3{,}628{,}800}{72} = 50{,}400
$$

---

### Problem 3 — Arrangements of STATISTICS starting with S

**Strategy:** fix one S in position 1, then count arrangements of the remaining 9 letters.

**Step 1 — Fix S in the first position.**

One S is placed at the start. The remaining letters to arrange are:

$$
\text{S S T T T A I I C}
$$

(two S's remain, three T's, one A, two I's, one C — total 9 letters)

| Letter | Count in remaining 9 |
|---|---|
| S | 2 |
| T | 3 |
| A | 1 |
| I | 2 |
| C | 1 |
| **Total** | **9** |

**Step 2 — Count arrangements of the remaining 9 letters.**

$$
\frac{9!}{2!\cdot 3!\cdot 1!\cdot 2!\cdot 1!}
$$

**Step 3 — Compute.**

$$
9! = 362{,}880
$$

$$
2! \times 3! \times 1! \times 2! \times 1! = 2 \times 6 \times 1 \times 2 \times 1 = 24
$$

$$
\frac{362{,}880}{24} = 15{,}120
$$

**Verification using proportional reasoning.**

Out of the total $50{,}400$ arrangements, the fraction starting with S should be proportional to the number of S's relative to total letters:

$$
50{,}400 \times \frac{3}{10} = 15{,}120 \checkmark
$$

This works because all positions are equally likely in a uniform random arrangement.

---

## Final Result

| Problem | Formula | Answer |
|---|---|---|
| MISSISSIPPI | $\frac{11!}{1!\,4!\,4!\,2!}$ | $34{,}650$ |
| STATISTICS | $\frac{10!}{3!\,3!\,1!\,2!\,1!}$ | $50{,}400$ |
| STATISTICS starting with S | $\frac{9!}{2!\,3!\,1!\,2!\,1!}$ | $15{,}120$ |

---

## Interpretation / Sanity Check

The fraction of STATISTICS arrangements starting with S:

$$
\frac{15{,}120}{50{,}400} = \frac{3}{10}
$$

This equals exactly $\frac{\text{number of S's}}{\text{total letters}} = \frac{3}{10}$, which confirms the result.

---

## Common Mistakes

- Forgetting to count all occurrences of a repeated letter. In MISSISSIPPI, I appears 4 times, not 3.
- Dividing by $n_i$ instead of $n_i!$. The denominator must use factorials.
- In Problem 3, removing all three S's from the remaining pool instead of only one. Only the fixed S is removed; the other two S's remain available for the remaining 9 positions.