# Task 5 — Combinations

## Problem Statement

1. A committee of 4 people is chosen from 12 students. How many committees are possible?
2. How many committees contain a particular student?
3. How many committees contain at least one of two particular students?
4. How many committees contain exactly two women if the group consists of 7 men and 5 women?

---

## Definitions / Theory

**Combination**: an unordered selection of $k$ elements from $n$ distinct elements, without repetition.

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

**Key properties:**

$$
\binom{n}{k} = \binom{n}{n-k}, \qquad \binom{n}{0} = \binom{n}{n} = 1
$$

**Complement method for "at least one":**

$$
|\text{at least one}| = |\text{total}| - |\text{none}|
$$

**Fixing a required element:** if a specific person must be on the committee, remove them from the pool and choose the remaining $k-1$ members from the remaining $n-1$ people.

**Product rule for grouped selection:** when choosing from separate groups (e.g. men and women), multiply the counts from each group.

---

## Step-by-Step Solution

### Problem 1 — Committee of 4 from 12 students

A committee is a set — order does not matter. No repetition.

$$
\binom{12}{4} = \frac{12!}{4! \cdot 8!} = \frac{12 \times 11 \times 10 \times 9}{4 \times 3 \times 2 \times 1} = \frac{11880}{24} = 495
$$

---

### Problem 2 — Committees containing a particular student

Call the required student $X$.

**Step 1 — Fix $X$ on the committee.**

$X$ is already placed. One of the 4 seats is taken.

**Step 2 — Choose the remaining 3 members.**

The remaining 3 members are chosen from the other $12 - 1 = 11$ students:

$$
\binom{11}{3} = \frac{11!}{3! \cdot 8!} = \frac{11 \times 10 \times 9}{3 \times 2 \times 1} = \frac{990}{6} = 165
$$

**Verification using proportional reasoning:**

Each of the 12 students appears in the same number of committees. The fraction containing $X$ is $\frac{4}{12} = \frac{1}{3}$.

$$
495 \times \frac{1}{3} = 165 \checkmark
$$

---

### Problem 3 — Committees containing at least one of two particular students

Call the two students $X$ and $Y$.

**Strategy: complement method.**

$$
|\text{at least one of } X, Y| = |\text{total}| - |\text{neither } X \text{ nor } Y|
$$

**Step 1 — Total committees.**

$$
\binom{12}{4} = 495
$$

**Step 2 — Committees containing neither $X$ nor $Y$.**

Exclude both $X$ and $Y$ from the pool. Choose all 4 members from the remaining $12 - 2 = 10$ students:

$$
\binom{10}{4} = \frac{10!}{4! \cdot 6!} = \frac{10 \times 9 \times 8 \times 7}{4 \times 3 \times 2 \times 1} = \frac{5040}{24} = 210
$$

**Step 3 — Subtract.**

$$
495 - 210 = 285
$$

**Verification by direct counting (inclusion-exclusion):**

$$
|\text{contains } X| + |\text{contains } Y| - |\text{contains both}|
$$

$$
= \binom{11}{3} + \binom{11}{3} - \binom{10}{2} = 165 + 165 - 45 = 285 \checkmark
$$

---

**Problem 4 — Exactly two women from 7 men and 5 women**

A committee of exactly 2 women and 2 men must be formed.
The two selections are independent, so the product rule applies.

**Step 1 — Choose 2 women from 5.**

Order does not matter — a committee is a set, not a ranked list.

$$
\binom{5}{2} = \frac{5!}{2! \cdot 3!} = \frac{5 \times 4}{2 \times 1} = 10
$$

All possible pairs of women: $\{W_1,W_2\},\ \{W_1,W_3\},\ \{W_1,W_4\},\ \{W_1,W_5\},\ \{W_2,W_3\}, \ldots$ — exactly 10 pairs.

**Step 2 — Choose 2 men from 7.**

$$
\binom{7}{2} = \frac{7!}{2! \cdot 5!} = \frac{7 \times 6}{2 \times 1} = 21
$$

**Step 3 — Multiply.**

For each of the 10 pairs of women, any of the 21 pairs of men can be independently selected:

$$
\binom{5}{2} \times \binom{7}{2} = 10 \times 21 = 210
$$

**Sanity check** — summing over all possible numbers of women must give $\binom{12}{4} = 495$:

$$
\binom{5}{0}\binom{7}{4} + \binom{5}{1}\binom{7}{3} + \binom{5}{2}\binom{7}{2} + \binom{5}{3}\binom{7}{1} + \binom{5}{4}\binom{7}{0}
= 35 + 175 + 210 + 70 + 5 = 495 \ \checkmark
$$

---

## Final Result

| Problem | Formula | Answer |
|---|---|---|
| 1. Committee of 4 from 12 | $\binom{12}{4}$ | $495$ |
| 2. Must include student $X$ | $\binom{11}{3}$ | $165$ |
| 3. At least one of $X, Y$ | $\binom{12}{4} - \binom{10}{4}$ | $285$ |
| 4. Exactly 2 women | $\binom{5}{2} \times \binom{7}{2}$ | $210$ |

---

## Common Mistakes

- In Problem 2, choosing 4 from 11 instead of 3 from 11. Since $X$ is already placed, only 3 more seats need to be filled.
- In Problem 3, computing $|\text{contains } X| + |\text{contains } Y|$ without subtracting $|\text{contains both}|$. This double-counts committees with both $X$ and $Y$.
- In Problem 4, adding instead of multiplying the two group counts. The product rule applies when the two choices are made independently.