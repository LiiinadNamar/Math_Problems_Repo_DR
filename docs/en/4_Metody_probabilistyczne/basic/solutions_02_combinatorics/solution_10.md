# Task 10 — Urn Models

## Problem Statement

An urn contains 5 red balls, 4 blue balls, and 3 green balls (12 balls total).

1. Three balls are drawn without replacement. How many samples are possible if order is ignored?
2. How many samples contain exactly two red balls?
3. Three balls are drawn and the order of colors is recorded. How many outcomes are possible?
4. How many outcomes contain exactly two red balls?

---

## Definitions / Theory

The counting model depends entirely on **how the outcome is recorded**.

**Order ignored, no replacement → Combination:**

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

Use this when the result is a set — the identity of the drawn balls matters, but not the order in which they were drawn.

**Order recorded, no replacement → k-Permutation:**

$$
P(n,k) = \frac{n!}{(n-k)!} = n \times (n-1) \times \cdots \times (n-k+1)
$$

Use this when the sequence of draws matters — drawing red then blue is different from blue then red.

**Product rule for restricted samples:** to count samples with specific compositions, count each color group separately and multiply.

**Relationship between ordered and unordered counts:**

Every unordered sample of $k$ distinct objects corresponds to exactly $k!$ ordered sequences (all possible orderings of the same objects). Therefore:

$$
P(n,k) = \binom{n}{k} \times k!
$$

---

## Step-by-Step Solution

### Problem 1 — Three balls drawn, order ignored

We select 3 balls from 12. Only which balls are chosen matters, not the order of drawing.

$$
\binom{12}{3} = \frac{12!}{3! \cdot 9!} = \frac{12 \times 11 \times 10}{3 \times 2 \times 1} = \frac{1{,}320}{6} = 220
$$

Each elementary outcome is an unordered set of 3 balls, for example $\{R_1, B_3, G_2\}$.

---

### Problem 2 — Exactly two red balls, order ignored

The sample of 3 must contain **exactly 2 red balls** and **exactly 1 non-red ball**.

The two selections (red balls and non-red ball) are made from separate, disjoint groups, so the product rule applies.

**Step 1 — Choose 2 red balls from the 5 red balls.**

Order does not matter within the sample:

$$
\binom{5}{2} = \frac{5 \times 4}{2 \times 1} = 10
$$

**Step 2 — Choose 1 non-red ball from the remaining $4 + 3 = 7$ balls.**

$$
\binom{7}{1} = 7
$$

**Step 3 — Multiply.**

For each of the 10 ways to choose 2 red balls, there are 7 independent choices for the non-red ball:

$$
\binom{5}{2} \times \binom{7}{1} = 10 \times 7 = 70
$$

**Verification:** the fraction of samples containing exactly 2 red balls:

$$
\frac{70}{220} = \frac{7}{22} \approx 0.318
$$

This is the hypergeometric probability of drawing exactly 2 red balls from an urn with 5 red and 7 non-red balls when drawing 3 without replacement. The value is reasonable.

---

### Problem 3 — Three balls drawn, order recorded

Now the sequence of draws matters. Drawing $R_1$ first, then $B_2$, then $G_1$ is a different outcome from drawing $B_2$ first, then $R_1$, then $G_1$.

**Step 1 — First draw.**

Any of the 12 balls can be drawn: **12 choices**.

**Step 2 — Second draw.**

One ball has been removed. Any of the remaining 11 balls: **11 choices**.

**Step 3 — Third draw.**

Two balls have been removed. Any of the remaining 10 balls: **10 choices**.

**Step 4 — Multiply:**

$$
P(12,3) = 12 \times 11 \times 10 = 1{,}320
$$

**Verification using the relationship between ordered and unordered counts:**

Each unordered sample of 3 balls can be arranged in $3! = 6$ different sequences:

$$
\binom{12}{3} \times 3! = 220 \times 6 = 1{,}320 \checkmark
$$

---

### Problem 4 — Exactly two red balls, order recorded

The outcome is an ordered sequence of 3 balls containing exactly 2 red balls and 1 non-red ball.

Both the positions of the red balls and the identities of the balls now matter.

**Step 1 — Choose which 2 of the 3 positions contain red balls.**

The 3 positions are ordered (1st draw, 2nd draw, 3rd draw). We choose 2 of them to hold red balls:

$$
\binom{3}{2} = 3
$$

The three possible position patterns are:

$$
(R, R, N), \quad (R, N, R), \quad (N, R, R)
$$

**Step 2 — Fill the 2 red positions with distinct red balls.**

There are 5 red balls. The two red positions are ordered (1st red position and 2nd red position), so we count ordered selections:

$$
P(5, 2) = 5 \times 4 = 20
$$

For example, if the pattern is $(R, R, N)$: the first position could be $R_1$ and the second $R_3$, or $R_2$ and $R_5$, etc. — 20 ordered pairs.

**Step 3 — Fill the 1 non-red position.**

There are 7 non-red balls ($4$ blue $+$ $3$ green). One position to fill:

$$
P(7, 1) = 7
$$

**Step 4 — Multiply.**

$$
\binom{3}{2} \times P(5,2) \times P(7,1) = 3 \times 20 \times 7 = 420
$$

**Verification using the relationship between ordered and unordered counts:**

Each unordered sample of exactly 2 red and 1 non-red ball can be arranged in $3! = 6$ sequences:

$$
70 \times 6 = 420 \checkmark
$$

---

## Final Result

| Problem | Model | Formula | Answer |
|---|---|---|---|
| 1. Three balls, order ignored | Combination | $\binom{12}{3}$ | $220$ |
| 2. Exactly 2 red, order ignored | Product of combinations | $\binom{5}{2} \times \binom{7}{1}$ | $70$ |
| 3. Three balls, order recorded | k-Permutation | $P(12,3)$ | $1{,}320$ |
| 4. Exactly 2 red, order recorded | Position choice $\times$ k-permutations | $\binom{3}{2} \times P(5,2) \times P(7,1)$ | $420$ |

---

## Interpretation / Sanity Check

The ratio between ordered and unordered counts is always $3! = 6$ in both the unrestricted and restricted cases:

$$
\frac{P(12,3)}{\binom{12}{3}} = \frac{1{,}320}{220} = 6 = 3! \checkmark
$$

$$
\frac{420}{70} = 6 = 3! \checkmark
$$

This confirms that every unordered sample of 3 balls corresponds to exactly 6 ordered sequences, regardless of the composition of the sample.

---

## Common Mistakes

- In Problem 2, choosing 2 balls from all 12 and then 1 from all 12 without enforcing the color constraint. The groups (red and non-red) must be treated separately.
- In Problem 4, using $\binom{5}{2} \times \binom{7}{1} = 70$ (the unordered count) without accounting for the ordering of positions. When order is recorded, the two red positions are distinct and the assignment of specific balls to specific positions matters.
- Forgetting that the 5 red balls are individually distinguishable. The urn contains $R_1, R_2, R_3, R_4, R_5$ — distinct objects. Choosing $\{R_1, R_2\}$ and $\{R_1, R_3\}$ are different outcomes even though both contain 2 red balls.