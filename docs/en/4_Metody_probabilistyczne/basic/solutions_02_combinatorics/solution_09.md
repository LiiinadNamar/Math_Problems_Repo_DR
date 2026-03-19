# Task 9 — Digit Restrictions

## Problem Statement

1. How many 5-digit numbers exist?
2. How many of them are even?
3. How many contain no repeated digits?
4. How many contain at least one repeated digit?

---

## Definitions / Theory

A **5-digit number** is an integer from $10{,}000$ to $99{,}999$.

**Available digits:** $\{0, 1, 2, \ldots, 9\}$ — ten digits in total.

**Leading digit constraint:** the ten-thousands digit cannot be zero. If it were zero, the number would have fewer than five digits. Therefore the ten-thousands digit is chosen from $\{1, 2, \ldots, 9\}$ — nine choices.

**Even number:** a number is even if and only if its units digit belongs to $\{0, 2, 4, 6, 8\}$ — five even digits.

**Product rule:** if a number is formed by filling $k$ independent positions with $n_1, n_2, \ldots, n_k$ choices respectively, the total count is $n_1 \times n_2 \times \cdots \times n_k$.

**Complement method:**

$$
|\text{at least one repeated digit}| = |\text{all 5-digit numbers}| - |\text{no repeated digits}|
$$

**Key subtlety for "no repeated digits":** after fixing the leading digit from $\{1,\ldots,9\}$, the second position may now include 0. The choices do not decrease uniformly from the start.

---

## Step-by-Step Solution

### Problem 1 — Total 5-digit numbers

A 5-digit number has five positions. The only constraint is that the leading digit is not zero.

Fill each position from left to right:

| Position | Available digits | Choices |
|---|---|---|
| Ten-thousands | $\{1,2,3,4,5,6,7,8,9\}$ | $9$ |
| Thousands | $\{0,1,2,\ldots,9\}$ | $10$ |
| Hundreds | $\{0,1,2,\ldots,9\}$ | $10$ |
| Tens | $\{0,1,2,\ldots,9\}$ | $10$ |
| Units | $\{0,1,2,\ldots,9\}$ | $10$ |

By the product rule:

$$
9 \times 10 \times 10 \times 10 \times 10 = 9 \times 10^4 = 90{,}000
$$

---

### Problem 2 — Even 5-digit numbers

A number is even when its units digit belongs to $\{0, 2, 4, 6, 8\}$.

Two positions are now constrained: the ten-thousands digit (cannot be 0) and the units digit (must be even). These constraints interact, so we split into two cases based on the units digit.

**Why split into cases?**

If the units digit is 0, the leading digit has 9 choices. If the units digit is one of $\{2,4,6,8\}$, the leading digit also has 9 choices — but it is important to verify this rather than assume. Splitting makes the reasoning explicit and avoids errors.

---

**Units digit $\in \{0, 2, 4, 6, 8\}$**

The units digit is a non-zero even digit. This does not affect the leading digit constraint — the leading digit is still chosen from $\{1,\ldots,9\}$.

| Position | Available digits | Choices |
|---|---|---|
| Ten-thousands | $\{1,\ldots,9\}$ | $9$ |
| Thousands | $\{0,\ldots,9\}$ | $10$ |
| Hundreds | $\{0,\ldots,9\}$ | $10$ |
| Tens | $\{0,\ldots,9\}$ | $10$ |
| Units | $\{0,2,4,6,8\}$ | $5$ |

$$
9 \times 10 \times 10 \times 10 \times 5 = 45{,}000
$$

---

**Sanity check:** among all integers, exactly half are even. Since the 5-digit numbers form a consecutive range, exactly half should be even:

$$
\frac{90{,}000}{2} = 45{,}000 \checkmark
$$

---

### Problem 3 — No repeated digits

Each of the 10 digits may appear at most once in the number.

**Step 1 — Fill the ten-thousands digit.**

Cannot be 0. Choose from $\{1,2,\ldots,9\}$:

$$
9 \text{ choices}
$$

**Step 2 — Fill the thousands digit.**

One digit has been used (the leading digit). The thousands digit can be any of the remaining $10 - 1 = 9$ digits.

Crucially, **0 is now available** — it was only forbidden for the leading position.

$$
9 \text{ choices}
$$

**Step 3 — Fill the hundreds digit.**

Two digits have been used. Choose from the remaining $10 - 2 = 8$ digits:

$$
8 \text{ choices}
$$

**Step 4 — Fill the tens digit.**

Three digits have been used:

$$
7 \text{ choices}
$$

**Step 5 — Fill the units digit.**

Four digits have been used:

$$
6 \text{ choices}
$$

**Multiply:**

$$
9 \times 9 \times 8 \times 7 \times 6 = 27{,}216
$$

**Why is the pattern $9, 9, 8, 7, 6$ and not $9, 8, 7, 6, 5$?**

If zero were forbidden in all positions, the sequence would be $9, 8, 7, 6, 5$. But zero is only forbidden in position 1. After position 1 is filled with some digit from $\{1,\ldots,9\}$, position 2 can take any of the 10 digits except that one — so 9 choices remain, including 0. From position 3 onwards, the count decreases by 1 at each step as usual.

---

### Problem 4 — At least one repeated digit

Counting directly requires handling many cases: exactly one pair of repeated digits, two pairs, one triple, etc. The complement method reduces this to a single subtraction.

**Step 1 — Total 5-digit numbers** (from Problem 1):

$$
90{,}000
$$

**Step 2 — 5-digit numbers with no repeated digits** (from Problem 3):

$$
27{,}216
$$

**Step 3 — Subtract:**

$$
90{,}000 - 27{,}216 = 62{,}784
$$

---

## Final Result

| Problem | Method | Answer |
|---|---|---|
| 1. All 5-digit numbers | Product rule, leading digit $\neq 0$ | $90{,}000$ |
| 2. Even 5-digit numbers | Split by units digit, sum cases | $45{,}000$ |
| 3. No repeated digits | Fill positions, decreasing choices | $27{,}216$ |
| 4. At least one repeated digit | Complement | $62{,}784$ |

---

## Interpretation / Sanity Check

About $70\%$ of 5-digit numbers contain at least one repeated digit:

$$
\frac{62{,}784}{90{,}000} \approx 0.698
$$

This is consistent with intuition from the birthday problem: with 5 positions and 10 available digits, repetition is more likely than not.

---

## Common Mistakes

- In Problem 2, treating the leading digit and units digit as fully independent and computing $9 \times 10 \times 10 \times 10 \times 5 = 45{,}000$. While the answer happens to be correct here, the reasoning is incomplete — the cases must be checked separately to verify there is no interaction.
- In Problem 3, computing $9 \times 8 \times 7 \times 6 \times 5 = 15{,}120$. This treats 0 as forbidden in all positions. Zero is only forbidden in position 1; after that it is available.
- In Problem 4, using $10^5 = 100{,}000$ as the total instead of $90{,}000$. The sequences $00000$ through $09999$ are not valid 5-digit numbers.