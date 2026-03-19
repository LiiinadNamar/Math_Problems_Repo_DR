# Task 4 — Circular Permutations

## Problem Statement

1. In how many ways can 7 people sit around a round table?
2. In how many ways can they sit if two particular people must sit next to each other?
3. In how many ways can they sit if those two people must sit opposite each other?

---

## Definitions / Theory

**Why circular permutations differ from linear permutations.**

In a linear arrangement, each position is distinct (position 1, position 2, etc.). In a circular arrangement, only the relative positions of people matter — rotating the entire group by one seat produces the same arrangement.

To eliminate equivalent rotations, one person is fixed in place. The remaining $n - 1$ people are arranged freely.

$$
\text{Circular permutations of } n \text{ distinct objects} = (n-1)!
$$

**Block method for adjacency constraints** works the same as in linear permutations: merge the constrained pair into a single block, reduce the count by one, then multiply by internal arrangements of the block.

**Opposite seats** exist only when $n$ is even. Two people sit opposite each other when there are exactly $\frac{n}{2} - 1$ people between them on each side.

---

## Step-by-Step Solution

### Problem 1 — 7 people around a round table

**Step 1 — Fix one person to eliminate rotational equivalence.**

Fix person $A$ in one seat. This seat is now a reference point.

**Step 2 — Arrange the remaining 6 people.**

The remaining 6 people can be placed in the other 6 seats in any order:

$$
6! = 720
$$

**Formula:**

$$
(7 - 1)! = 6! = 720
$$

---

### Problem 2 — Two particular people must sit next to each other

Call the two people who must be adjacent $A$ and $B$.

**Step 1 — Merge $A$ and $B$ into a block $[AB]$.**

The table now effectively has $6$ objects: the block $[AB]$ and the other $5$ people.

**Step 2 — Count circular arrangements of 6 objects.**

Fix the block in one position to remove rotational equivalence:

$$
(6 - 1)! = 5! = 120
$$

**Step 3 — Arrange $A$ and $B$ within the block.**

Inside the block, $A$ and $B$ can sit as $AB$ or $BA$:

$$
2! = 2
$$

**Step 4 — Multiply.**

$$
5! \times 2 = 120 \times 2 = 240
$$

---

### Problem 3 — Two particular people must sit opposite each other

**Note:** a round table with 7 seats has no pair of perfectly opposite seats (7 is odd). This problem is well-posed only for an even number of seats.

I solve it for a **round table with 6 seats** (6 people) as the natural even case. That this is impossible for odd $n$.

**For 6 people, two must sit directly opposite each other.**

**Step 1 — Fix person $A$ in one seat.**

This eliminates rotational equivalence.

**Step 2 — Place person $B$ opposite $A$.**

With $A$ fixed, exactly one seat is directly opposite. $B$ has no choice — there is only 1 valid seat.

**Step 3 — Arrange the remaining 4 people.**

The remaining 4 people sit in the remaining 4 seats in any order:

$$
4! = 24
$$

**Step 4 — Multiply.**

$$
1 \times 4! = 24
$$

---

## Final Result

| Problem | Method | Answer |
|---|---|---|
| 1. 7 people at round table | Circular permutation | $(7-1)! = 720$ |
| 2. Two adjacent | Block + circular | $5! \times 2 = 240$ |
| 3. Two opposite (6 people) | Fix one, constrain other | $4! = 24$ |

---

## Interpretation / Sanity Check

**Problem 2 check:** the fraction of circular arrangements where $A$ and $B$ are adjacent:

$$
\frac{240}{720} = \frac{1}{3}
$$

For 7 people at a round table, fix $A$. Then $B$ can sit in any of 6 remaining seats, of which 2 are adjacent to $A$. So the probability is $\frac{2}{6} = \frac{1}{3}$. $\checkmark$

---

## Common Mistakes

- Computing $7!$ instead of $6!$ for circular permutations of 7 people. Rotational equivalence must always be accounted for.
- In Problem 2, computing $(6-1)! \times 2 = 5! \times 2$ correctly, but forgetting the factor of $2$ for internal block order.
- Assuming "opposite" is always defined for any number of people. For odd $n$, no two seats are exactly opposite.---
