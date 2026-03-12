# Task 1 — Coin Tossing

## Problem Statement

A fair coin is tossed one, two, and three times in sequence. The order of outcomes matters.
For each case, construct the sample space and determine the number of elementary outcomes.

---

## Definitions / Theory

**Sample space** $\Omega$ is the set of all possible elementary outcomes of a random experiment.

**Elementary outcome** (also called a sample point) is a single, indivisible result of the experiment. It cannot be decomposed into simpler outcomes within the given model.

**Fair coin** means both outcomes — Heads ($H$) and Tails ($T$) — are equally likely, each with probability $\frac{1}{2}$.

**Ordered sequence**: since the order of tosses matters, the outcome $(H, T)$ is distinct from $(T, H)$.

When the experiment consists of $n$ independent steps, each with $k$ possible outcomes, the total number of elementary outcomes is:

$$
|\Omega_n| = k^n
$$

For a coin: $k = 2$, so $|\Omega_n| = 2^n$.

---

## Step-by-Step Solution

### One Coin Toss

The experiment has a single step with two possible results.

$$
\Omega_1 = \{H, T\}
$$

**Tree diagram:**

```
START
 ├── H
 └── T
```

Number of elementary outcomes:

$$
|\Omega_1| = 2^1 = 2
$$

Each elementary outcome is a single symbol representing the result of one toss.

---

### Two Coin Tosses

The experiment consists of two consecutive steps. Each toss can yield $H$ or $T$, independently of the other.

$$
\Omega_2 = \{(H,H),\ (H,T),\ (T,H),\ (T,T)\}
$$

**Tree diagram:**

```
START
 ├── H
 │     ├── H  →  (H,H)
 │     └── T  →  (H,T)
 └── T
       ├── H  →  (T,H)
       └── T  →  (T,T)
```

Number of elementary outcomes:

$$
|\Omega_2| = 2^2 = 4
$$

Each elementary outcome is an ordered pair $(x_1, x_2)$ where $x_i \in \{H, T\}$ records the result of the $i$-th toss.

---

### Three Coin Tosses

The experiment consists of three consecutive steps.

$$
\Omega_3 = \{
(H,H,H),\ (H,H,T),\ (H,T,H),\ (H,T,T),\
(T,H,H),\ (T,H,T),\ (T,T,H),\ (T,T,T)
\}
$$

**Tree diagram:**

```
START
 ├── H
 │     ├── H
 │     │     ├── H  →  (H,H,H)
 │     │     └── T  →  (H,H,T)
 │     └── T
 │           ├── H  →  (H,T,H)
 │           └── T  →  (H,T,T)
 └── T
       ├── H
       │     ├── H  →  (T,H,H)
       │     └── T  →  (T,H,T)
       └── T
             ├── H  →  (T,T,H)
             └── T  →  (T,T,T)
```

Number of elementary outcomes:

$$
|\Omega_3| = 2^3 = 8
$$

Each elementary outcome is an ordered triple $(x_1, x_2, x_3)$ where $x_i \in \{H, T\}$ records the result of the $i$-th toss.

---

## Final Result

| Experiment | Sample space $\Omega$ | Number of outcomes $|\Omega|$ |
|---|---|---|
| One toss | $\{H,\ T\}$ | $2$ |
| Two tosses | $\{(H,H),\ (H,T),\ (T,H),\ (T,T)\}$ | $4$ |
| Three tosses | $\{(H,H,H), \ldots, (T,T,T)\}$ | $8$ |

In general, for $n$ tosses of a fair coin:

$$
|\Omega_n| = 2^n
$$

---

## Interpretation / Sanity Check

The sample space grows exponentially with each additional toss. This is expected: each new toss doubles the number of possible sequences, since it adds either $H$ or $T$ to every existing outcome.

For $n = 3$: $2^3 = 8$ outcomes are listed explicitly above, and all 8 are distinct ordered triples. The count is consistent.

Note that although the outcomes $(H,T,T)$, $(T,H,T)$, and $(T,T,H)$ all contain one head and two tails, they are **distinct elementary outcomes** because the order matters.

---

## Common Mistakes

- Treating $(H,T)$ and $(T,H)$ as the same outcome. They are distinct because order matters.
- Confusing elementary outcomes with events. For example, "exactly one head in two tosses" is an **event** $\{(H,T), (T,H)\}$, not an elementary outcome.
- Forgetting that the sample space must list **all** possible outcomes, not only the "interesting" ones.
- Applying the formula $|\Omega_n| = 2^n$ without verifying it by listing outcomes, at least for small $n$.
