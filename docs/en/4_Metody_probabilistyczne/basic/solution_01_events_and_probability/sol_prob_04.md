# Task 4 — Weekly Weather Observation

## Problem Statement

The weather on a given day is classified as Sunny ($S$), Cloudy ($C$), or Rainy ($R$).
The weather is observed once per day for seven consecutive days.
Construct the sample spaces for one day, two days, and seven days.

---

## Definitions / Theory

**Sample space** $\Omega$ is the set of all possible elementary outcomes of the experiment.

Each day's weather is one of three states: $\{S, C, R\}$. The observations on different days are treated as independent.

When the experiment consists of $n$ independent steps each with $k$ possible outcomes:

$$
|\Omega_n| = k^n
$$

Here $k = 3$ (three weather states), so $|\Omega_n| = 3^n$.

---

## Step-by-Step Solution

### One Day

$$
\Omega_1 = \{S,\ C,\ R\}
$$

$$
|\Omega_1| = 3^1 = 3
$$

Each elementary outcome is a single weather state observed on one day.

---

### Two Consecutive Days

$$
\Omega_2 = \{(w_1, w_2) : w_1, w_2 \in \{S, C, R\}\}
$$

Listing all outcomes:

$$
(S,S),\ (S,C),\ (S,R),\ (C,S),\ (C,C),\ (C,R),\ (R,S),\ (R,C),\ (R,R)
$$

**Tree diagram:**

```
START
 ├── S
 │     ├── S  →  (S,S)
 │     ├── C  →  (S,C)
 │     └── R  →  (S,R)
 ├── C
 │     ├── S  →  (C,S)
 │     ├── C  →  (C,C)
 │     └── R  →  (C,R)
 └── R
       ├── S  →  (R,S)
       ├── C  →  (R,C)
       └── R  →  (R,R)
```

$$
|\Omega_2| = 3^2 = 9
$$

---

### Seven Consecutive Days

$$
\Omega_7 = \{(w_1, w_2, w_3, w_4, w_5, w_6, w_7) : w_i \in \{S, C, R\}\ \text{for all}\ i\}
$$

Each elementary outcome is an ordered sequence of seven weather states, one for each day of the week.

For example:

$$
(S, S, C, R, S, C, C)
$$

represents: sunny Monday, sunny Tuesday, cloudy Wednesday, rainy Thursday, sunny Friday, cloudy Saturday, cloudy Sunday.

$$
|\Omega_7| = 3^7 = 2187
$$

---

## Final Result

| Experiment | Number of outcomes $|\Omega|$ |
|---|---|
| One day | $3^1 = 3$ |
| Two days | $3^2 = 9$ |
| Seven days | $3^7 = 2187$ |

In general, for $n$ days:

$$
|\Omega_n| = 3^n
$$

---

## Interpretation / Sanity Check

The sample space for one week contains $2187$ elementary outcomes. Each outcome is a complete weather record for the entire week — a sequence of seven states chosen from $\{S, C, R\}$.

The number grows exponentially: each additional day triples the number of possible sequences.

---

## Common Mistakes

- Forgetting that the order of days matters. The sequence $(S, R, C, \ldots)$ is a different elementary outcome from $(R, S, C, \ldots)$.
- Confusing an elementary outcome with an event. For example, "at least one rainy day" is an event — a subset of $\Omega_7$ — not a single elementary outcome.
- Using $3 \times 7 = 21$ instead of $3^7 = 2187$. The multiplication principle requires exponentiation, not multiplication, when the same choices are available at each step.
