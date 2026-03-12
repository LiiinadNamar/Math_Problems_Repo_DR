# Task 2 — Rolling a Die

## Problem Statement

A fair six-sided die is rolled one, two, and three times in sequence. The order of outcomes matters.
For each case, construct the sample space and determine the number of elementary outcomes.

---

## Definitions / Theory

**Sample space** $\Omega$ is the set of all possible elementary outcomes of a random experiment.

**Elementary outcome** is a single indivisible result of the experiment.

**Fair die** means all six faces — $1, 2, 3, 4, 5, 6$ — are equally likely, each with probability $\frac{1}{6}$.

**Ordered sequence**: since the order of rolls matters, the outcome $(1, 2)$ is distinct from $(2, 1)$.

When the experiment consists of $n$ independent steps, each with $k$ possible outcomes, the total number of elementary outcomes is:

$$
|\Omega_n| = k^n
$$

For a six-sided die: $k = 6$, so $|\Omega_n| = 6^n$.

---

## Step-by-Step Solution

### One Roll

The experiment has a single step with six possible results.

$$
\Omega_1 = \{1, 2, 3, 4, 5, 6\}
$$

**Tree diagram:**

```
START
 ├── 1
 ├── 2
 ├── 3
 ├── 4
 ├── 5
 └── 6
```

Number of elementary outcomes:

$$
|\Omega_1| = 6^1 = 6
$$

Each elementary outcome is a single integer representing the face shown after one roll.

---

### Two Consecutive Rolls

Each roll is independent. The outcome is an ordered pair $(x_1, x_2)$ where $x_i \in \{1,2,3,4,5,6\}$.

$$
\Omega_2 = \{(i, j) : i, j \in \{1, 2, 3, 4, 5, 6\}\}
$$

The full set contains $36$ elements, for example:

$$
(1,1),\ (1,2),\ \ldots,\ (1,6),\ (2,1),\ \ldots,\ (6,6)
$$

**Tree diagram (first two branches shown):**

```
START
 ├── 1
 │     ├── 1  →  (1,1)
 │     ├── 2  →  (1,2)
 │     ├── 3  →  (1,3)
 │     ├── 4  →  (1,4)
 │     ├── 5  →  (1,5)
 │     └── 6  →  (1,6)
 ├── 2
 │     ├── 1  →  (2,1)
 │     └── ...
 └── ...
```

Number of elementary outcomes:

$$
|\Omega_2| = 6^2 = 36
$$

---

### Three Consecutive Rolls

The outcome is an ordered triple $(x_1, x_2, x_3)$ where $x_i \in \{1,2,3,4,5,6\}$.

$$
\Omega_3 = \{(i, j, k) : i, j, k \in \{1, 2, 3, 4, 5, 6\}\}
$$

Number of elementary outcomes:

$$
|\Omega_3| = 6^3 = 216
$$

Each elementary outcome is an ordered triple recording the result of each roll in sequence.

---

## Final Result

| Experiment | Sample space $\Omega$ | Number of outcomes $|\Omega|$ |
|---|---|---|
| One roll | $\{1, 2, 3, 4, 5, 6\}$ | $6$ |
| Two rolls | $\{(i,j) : i,j \in \{1,\ldots,6\}\}$ | $36$ |
| Three rolls | $\{(i,j,k) : i,j,k \in \{1,\ldots,6\}\}$ | $216$ |

In general, for $n$ rolls of a fair six-sided die:

$$
|\Omega_n| = 6^n
$$

---

## Interpretation / Sanity Check

Each additional roll multiplies the number of outcomes by $6$. This is consistent with the multiplication principle: at each stage, every existing outcome branches into $6$ new ones.

For $n = 2$: the $36$ outcomes can be visualised as a $6 \times 6$ grid where rows represent the first roll and columns represent the second.

---

## Common Mistakes

- Counting only outcomes where $x_1 \leq x_2$ (i.e. ignoring order). This gives $\binom{6}{2} + 6 = 21$ outcomes, which is incorrect when order matters.
- Confusing the sample space with the set of possible sums. The sum $x_1 + x_2$ is a random variable defined on $\Omega_2$, not the sample space itself.
- Forgetting that $(i,j)$ and $(j,i)$ are distinct outcomes when $i \neq j$.
