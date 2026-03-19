# Task 8 — Sequences with Repetition

## Problem Statement

1. How many 5-digit PIN codes are possible if digits may repeat?
2. How many such codes contain at least one repeated digit?
3. How many such codes have all digits different?

---

## Definitions / Theory

A **sequence with repetition** of length $k$ over an $n$-element set is an ordered selection where each position may independently contain any of the $n$ symbols.

$$
\text{Number of sequences} = n^k
$$

This model applies when:
- order matters,
- repetition is allowed,
- each position is chosen independently from the full set.

**Complement method:**

$$
|\text{at least one repeated digit}| = |\text{all codes}| - |\text{all digits different}|
$$

**Sequences without repetition** (all digits different): the first position has $n$ choices, the second has $n-1$, and so on:

$$
n \times (n-1) \times \cdots \times (n-k+1) = P(n,k)
$$

---

## Step-by-Step Solution

### Problem 1 — Total 5-digit PIN codes, digits may repeat

Available digits: $\{0, 1, 2, \ldots, 9\}$ — ten digits. Each of the 5 positions is chosen independently.

- Position 1: 10 choices
- Position 2: 10 choices
- Position 3: 10 choices
- Position 4: 10 choices
- Position 5: 10 choices

$$
10^5 = 100{,}000
$$

---

### Problem 2 — At least one repeated digit

**Strategy: complement method.**

Counting "at least one repeated digit" directly requires splitting into many cases
(exactly one pair, exactly two pairs, one triple, etc.) — this is tedious.
The complement has only one case: all digits different.

$$
|\text{at least one repeated digit}| = |\text{all PIN codes}| - |\text{all digits different}|
$$

**Step 1 — Total PIN codes.**

Each of the 5 positions is filled independently from $\{0,1,\ldots,9\}$:

$$
10^5 = 100{,}000
$$

**Step 2 — PIN codes with all digits different.**

Now each digit may be used at most once. Fill positions one by one:

- Position 1: 10 choices (any digit)
- Position 2: 9 choices (one digit already used)
- Position 3: 8 choices
- Position 4: 7 choices
- Position 5: 6 choices

$$
P(10,5) = 10 \times 9 \times 8 \times 7 \times 6 = 30{,}240
$$

**Step 3 — Subtract.**

$$
100{,}000 - 30{,}240 = 69{,}760
$$

---

### Problem 3 — All digits different

This was already computed in Step 2 above as part of the complement.
Here is the full reasoning independently.

**Step 1 — Fill position 1.**

Any of the 10 digits is available: **10 choices**.

**Step 2 — Fill position 2.**

One digit is already used and cannot repeat.
Remaining available digits: $10 - 1 = 9$: **9 choices**.

**Step 3 — Fill position 3.**

Two digits are already used.
Remaining: $10 - 2 = 8$: **8 choices**.

**Step 4 — Fill position 4.**

Three digits are already used.
Remaining: $10 - 3 = 7$: **7 choices**.

**Step 5 — Fill position 5.**

Four digits are already used.
Remaining: $10 - 4 = 6$: **6 choices**.

**Step 6 — Multiply by the product rule.**

$$
P(10,5) = 10 \times 9 \times 8 \times 7 \times 6 = 30{,}240
$$

**Sanity check** — this must be less than the total:

$$
30{,}240 < 100{,}000 \checkmark
$$

The fraction of PIN codes with all distinct digits:

$$
\frac{30{,}240}{100{,}000} = 0.3024
$$

So only about $30\%$ of all 5-digit PIN codes use entirely distinct digits.
The remaining $70\%$ contain at least one repeated digit, which matches Problem 2.

---

## Final Result

| Problem | Formula | Answer |
|---|---|---|
| 1. All 5-digit PIN codes | $10^5$ | $100{,}000$ |
| 2. At least one repeated digit | $10^5 - P(10,5)$ | $69{,}760$ |
| 3. All digits different | $P(10,5) = 10 \times 9 \times 8 \times 7 \times 6$ | $30{,}240$ |

---

## Interpretation / Sanity Check

The fraction of PIN codes with all digits different:

$$
\frac{30{,}240}{100{,}000} = 0.3024
$$

So about $30\%$ of 5-digit PIN codes use all distinct digits, and about $70\%$ contain at least one repeated digit. This is consistent with the birthday-problem intuition: with 10 digits and 5 positions, repetition is more likely than not.

---

## Common Mistakes

- Using $P(10,5)$ for Problem 1 instead of $10^5$. With repetition allowed, each position is independent — the full set of 10 digits is available at every position.
- Computing "at least one repeated digit" directly by trying to enumerate cases. The complement method is far simpler.
- Confusing a PIN code with a number. A PIN code $00000$ is valid — leading zeros are allowed. This is why the total is $10^5$ and not $9 \times 10^4$.