# Task 11 — Modeling Outcomes

## Problem Statement

A box contains 4 red, 4 blue, and 3 green balls (11 balls total).

**Part 1 — Distinguishable vs Indistinguishable Objects**

1. How many linear arrangements of all 11 balls are possible if balls of the same color are indistinguishable?
2. How many arrangements are possible if every ball is individually labeled?
3. Why are the answers different?

**Part 2 — Recording Order vs Ignoring Order**

Three balls are drawn without replacement.

1. How many outcomes if only the set of colors is recorded (order ignored)?
2. How many outcomes if the sequence of colors is recorded?
3. Why does recording order change the counting model?

**Part 3 — PIN Code vs Number**

1. How many 4-digit PIN codes (digits 0–9, repetition allowed)?
2. How many 4-digit numbers (first digit $\neq 0$)?
3. Why are these counted differently?
4. Why are $1234$ and $4321$ different outcomes?

---

## Definitions / Theory

The number of outcomes depends on **how outcomes are defined**, not only on the physical objects.

**Distinguishable objects:** each object is treated as a unique individual. Two arrangements that differ only by swapping objects of the same type are counted as different.

**Indistinguishable objects:** objects of the same type are treated as identical. Swapping two red balls produces no visible change — these arrangements are counted as one.

**Ordered outcome:** the sequence of selection is part of the result. $(R, B, G)$ and $(B, R, G)$ are different outcomes.

**Unordered outcome:** only the collection matters. $\{R, B, G\}$ and $\{B, R, G\}$ describe the same outcome.

**Permutation with repeated elements:** arranges $n$ objects where $n_i$ objects of type $i$ are identical:

$$
\frac{n!}{n_1!\, n_2!\, \cdots\, n_r!}
$$

---

## Step-by-Step Solution

### Part 1 — Distinguishable vs Indistinguishable

#### Problem 1 — Balls of the same color are indistinguishable

All 11 balls are arranged in a line. Balls of the same color look identical.

**Step 1 — Count the balls.**

| Color | Count |
|---|---|
| Red (R) | 4 |
| Blue (B) | 4 |
| Green (G) | 3 |
| **Total** | **11** |

**Step 2 — Apply the formula for permutations with repeated elements.**

If all 11 balls were distinct, there would be $11!$ arrangements. But swapping any two red balls among themselves produces no new arrangement — the $4!$ internal orderings of red balls all look the same. The same applies to blue ($4!$) and green ($3!$).

Dividing removes the overcounted copies:

$$
\frac{11!}{4!\cdot 4!\cdot 3!}
$$

**Step 3 — Compute.**

$$
11! = 39{,}916{,}800
$$

$$
4! \times 4! \times 3! = 24 \times 24 \times 6 = 3{,}456
$$

$$
\frac{39{,}916{,}800}{3{,}456} = 11{,}550
$$

---

#### Problem 2 — Every ball is individually labeled

The balls are $R_1, R_2, R_3, R_4, B_1, B_2, B_3, B_4, G_1, G_2, G_3$ — all 11 are distinct.

Swapping $R_1$ and $R_2$ now produces a genuinely different arrangement, because the labels differ.

Every ordering of 11 distinct objects is a valid distinct arrangement:

$$
11! = 39{,}916{,}800
$$

---

#### Problem 3 — Why the answers differ

When balls are indistinguishable by color, many physically different arrangements look identical. Specifically, for every visible arrangement there are:

$$
4! \times 4! \times 3! = 3{,}456
$$

physically distinct arrangements (from permuting identical balls internally) that all appear the same.

Dividing by this factor removes the duplicates:

$$
\frac{39{,}916{,}800}{3{,}456} = 11{,}550
$$

The recording rule determines what counts as "the same." If we cannot distinguish $R_1$ from $R_2$, then arrangements that differ only in how the red balls are ordered are identical outcomes.

---

### Part 2 — Recording Order vs Ignoring Order

Three balls are drawn without replacement from the 11-ball box.

#### Problem 1 — Only the set of colors is recorded, order ignored

The outcome is the color composition of the drawn sample: how many red, blue, and green balls were drawn. The order of drawing does not matter.

The possible compositions $(r, b, g)$ with $r + b + g = 3$, $r \leq 4$, $b \leq 4$, $g \leq 3$, counting the number of unordered samples for each:

| Red | Blue | Green | Count |
|---|---|---|---|
| 3 | 0 | 0 | $\binom{4}{3}\binom{4}{0}\binom{3}{0} = 4$ |
| 2 | 1 | 0 | $\binom{4}{2}\binom{4}{1}\binom{3}{0} = 24$ |
| 2 | 0 | 1 | $\binom{4}{2}\binom{4}{0}\binom{3}{1} = 18$ |
| 1 | 2 | 0 | $\binom{4}{1}\binom{4}{2}\binom{3}{0} = 24$ |
| 1 | 1 | 1 | $\binom{4}{1}\binom{4}{1}\binom{3}{1} = 48$ |
| 1 | 0 | 2 | $\binom{4}{1}\binom{4}{0}\binom{3}{2} = 12$ |
| 0 | 3 | 0 | $\binom{4}{0}\binom{4}{3}\binom{3}{0} = 4$ |
| 0 | 2 | 1 | $\binom{4}{0}\binom{4}{2}\binom{3}{1} = 18$ |
| 0 | 1 | 2 | $\binom{4}{0}\binom{4}{1}\binom{3}{2} = 12$ |
| 0 | 0 | 3 | $\binom{4}{0}\binom{4}{0}\binom{3}{3} = 1$ |

Total:

$$
4+24+18+24+48+12+4+18+12+1 = 165
$$

**Verification:**

$$
\binom{11}{3} = \frac{11 \times 10 \times 9}{6} = 165 \checkmark
$$

---

#### Problem 2 — Sequence of colors recorded, order matters

Now the first, second, and third draws are distinct positions. Drawing $R_1, B_2, G_1$ in that order is different from drawing $B_2, R_1, G_1$.

Fill positions one by one:

- 1st draw: 11 choices (any ball)
- 2nd draw: 10 choices (one ball removed)
- 3rd draw: 9 choices

$$
P(11, 3) = 11 \times 10 \times 9 = 990
$$

---

#### Problem 3 — Why recording order changes the model

When order is ignored, the outcomes $\{R_1, B_2, G_1\}$ and all other orderings of the same three balls — $(R_1, B_2, G_1)$, $(R_1, G_1, B_2)$, $(B_2, R_1, G_1)$, $(B_2, G_1, R_1)$, $(G_1, R_1, B_2)$, $(G_1, B_2, R_1)$ — are counted as a single outcome.

When order is recorded, each of those $3! = 6$ sequences is a separate outcome.

Therefore:

$$
P(11,3) = \binom{11}{3} \times 3! = 165 \times 6 = 990 \checkmark
$$

The recording rule determines the granularity of the sample space: recording order multiplies the count by $k!$ for samples of size $k$.

---

### Part 3 — PIN Code vs Number

#### Problem 1 — 4-digit PIN codes

A PIN code is a sequence of 4 symbols from $\{0,1,\ldots,9\}$. Repetition is allowed. Leading zeros are permitted — $0042$ is a valid PIN.

Each of the 4 positions is filled independently from all 10 digits:

$$
10 \times 10 \times 10 \times 10 = 10^4 = 10{,}000
$$

---

#### Problem 2 — 4-digit numbers

A 4-digit number ranges from $1{,}000$ to $9{,}999$. The thousands digit cannot be zero.

| Position | Available digits | Choices |
|---|---|---|
| Thousands | $\{1,\ldots,9\}$ | $9$ |
| Hundreds | $\{0,\ldots,9\}$ | $10$ |
| Tens | $\{0,\ldots,9\}$ | $10$ |
| Units | $\{0,\ldots,9\}$ | $10$ |

$$
9 \times 10 \times 10 \times 10 = 9{,}000
$$

---

#### Problem 3 — Why the rules differ

A **PIN code** is a sequence of symbols used for identification. It has no numeric value. The code $0042$ is distinct from $0420$ and both are valid — the leading zero is meaningful as part of the sequence.

A **number** is a mathematical quantity. The string $0042$ represents the integer $42$, which is a 2-digit number, not a 4-digit one. Leading zeros are not part of the standard decimal representation of integers.

The difference in count:

$$
10{,}000 - 9{,}000 = 1{,}000
$$

These 1000 "missing" entries are exactly the codes $0000$ through $0999$ — valid PINs that are not valid 4-digit numbers.

---

#### Problem 4 — Why $1234$ and $4321$ are different outcomes

A PIN code is an **ordered sequence** — the positions are distinct (1st digit, 2nd digit, 3rd digit, 4th digit). Entering $1234$ and $4321$ into a keypad produces two different sequences of key presses.

Formally, two sequences $(a_1, a_2, a_3, a_4)$ and $(b_1, b_2, b_3, b_4)$ are the same outcome if and only if $a_i = b_i$ for every position $i$. Since $1 \neq 4$ in position 1, the codes $1234$ and $4321$ are distinct outcomes.

This is why the sequence model ($n^k$) is appropriate for PIN codes, not combinations ($\binom{n}{k}$).

---

## Final Result

| Problem | Model | Answer |
|---|---|---|
| 1.1 Arrangements, indistinguishable balls | Permutation with repeats | $11{,}550$ |
| 1.2 Arrangements, labeled balls | Permutation | $11! = 39{,}916{,}800$ |
| 2.1 Draw 3, order ignored | Combination | $\binom{11}{3} = 165$ |
| 2.2 Draw 3, order recorded | k-Permutation | $P(11,3) = 990$ |
| 3.1 4-digit PIN codes | Sequence with repetition | $10^4 = 10{,}000$ |
| 3.2 4-digit numbers | Leading digit restricted | $9 \times 10^3 = 9{,}000$ |

---

## Common Mistakes

- In Part 1, applying $n!$ when objects are not all distinct. Identical objects require dividing by the product of their factorials.
- In Part 2, using $\binom{11}{3}$ when order is recorded. Combinations ignore order; when the sequence matters, use k-permutations.
- In Part 3, treating PIN codes and numbers as interchangeable. The leading-zero rule is the key distinction.
- Treating $1234$ and $4321$ as the same because they contain the same digits. Order is part of the definition of a sequence — the same digits in a different order form a different outcome.