# Task 2 — Permutations

## Problem Statement

1. In how many ways can 8 different books be arranged on a shelf?
2. In how many ways can 8 people sit in a row if two particular people must sit next to each other?
3. In how many ways can they sit if those two people must not sit next to each other?
4. In how many ways can 10 questions in a test be ordered if the first question is fixed?

---

## Definitions / Theory

**Permutation** of $n$ distinct objects: an ordered arrangement of all $n$ objects.

$$
P_n = n!
$$

**Treating a constrained group as a block**: when two or more objects must stay together, merge them into a single "super-object." Count arrangements of the reduced set, then multiply by the internal arrangements of the block.

**Complement method**: instead of counting directly, compute:

$$
|\text{favourable}| = |\text{total}| - |\text{unfavourable}|
$$

This is useful for "must not" constraints.

---

## Step-by-Step Solution

### Problem 1 — 8 books on a shelf

All 8 books are distinct. Each arrangement is a permutation of all 8 objects. Order matters (a different left-to-right order is a different arrangement).

$$
P_8 = 8! = 40{,}320
$$

---

### Problem 2 — 8 people in a row, two particular people must sit next to each other

Call the two people who must be adjacent $A$ and $B$.

**Step 1 — Treat $A$ and $B$ as a single block.**

Merge $A$ and $B$ into one unit $[AB]$. The row now contains $7$ objects: $[AB]$ and the other $6$ people.

**Step 2 — Arrange the 7 objects.**

The number of arrangements of 7 distinct objects is:

$$
7! = 5040
$$

**Step 3 — Arrange $A$ and $B$ within the block.**

Inside the block, $A$ and $B$ can be ordered as $AB$ or $BA$:

$$
2! = 2
$$

**Step 4 — Multiply.**

$$
7! \times 2! = 5040 \times 2 = 10{,}080
$$

---

### Problem 3 — 8 people in a row, two particular people must not sit next to each other

**Strategy: complement method.**

$$
|\text{not adjacent}| = |\text{all arrangements}| - |\text{adjacent arrangements}|
$$

**Step 1 — Total arrangements.**

$$
8! = 40{,}320
$$

**Step 2 — Arrangements where $A$ and $B$ are adjacent** (from Problem 2).

$$
7! \times 2! = 10{,}080
$$

**Step 3 — Subtract.**

$$
40{,}320 - 10{,}080 = 30{,}240
$$

---

### Problem 4 — 10 questions, first question is fixed

**Step 1 — Fix the first question.**

One specific question is required to be first. It occupies position 1 with no choice.

**Step 2 — Arrange the remaining 9 questions.**

The remaining 9 questions can be placed in positions 2 through 10 in any order:

$$
9! = 362{,}880
$$

**Interpretation:** fixing one element reduces the problem from $10!$ to $9!$.

$$
\frac{10!}{10} = \frac{3{,}628{,}800}{10} = 362{,}880
$$

---

## Final Result

| Problem | Method | Answer |
|---|---|---|
| 1. 8 books on a shelf | Permutation | $8! = 40{,}320$ |
| 2. Two people adjacent | Block method | $7! \times 2 = 10{,}080$ |
| 3. Two people not adjacent | Complement | $8! - 7! \times 2 = 30{,}240$ |
| 4. First question fixed | Fix one, permute rest | $9! = 362{,}880$ |

---

## Interpretation / Sanity Check

For Problem 3: the fraction of arrangements where $A$ and $B$ are not adjacent is:

$$
\frac{30{,}240}{40{,}320} = \frac{3}{4}
$$

Intuitively, for any position of $A$, the probability that $B$ lands in a non-adjacent seat should be high when there are many seats. This value of $\frac{3}{4}$ is reasonable.

---

## Common Mistakes

- In Problem 2, forgetting to multiply by $2!$ for the internal order of $A$ and $B$ within the block.
- In Problem 3, computing $8! - 7!$ instead of $8! - 7! \times 2$. The factor of 2 accounts for both orderings $AB$ and $BA$ within the adjacent pair.
- In Problem 4, computing $10!$ without fixing the first question, or computing $\frac{10!}{10!}$ by over-fixing.