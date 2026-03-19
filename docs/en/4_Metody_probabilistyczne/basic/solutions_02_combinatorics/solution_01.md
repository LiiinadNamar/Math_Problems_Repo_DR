# Task 1 — Recognizing Counting Models

## Problem Statement

For each situation determine which combinatorial model is most appropriate and justify the choice.

---

## Definitions / Theory

Before choosing a model, answer four questions:

1. Are we using **all objects** or only **some of them**?
2. Does **order** matter?
3. Is **repetition** allowed?
4. Are some objects **identical**?

| Model | All or some | Order | Repetition | Formula |
|---|---|---|---|---|
| Permutation | All | Yes | No | $n!$ |
| Circular permutation | All | Yes (relative) | No | $(n-1)!$ |
| Permutation with repeated elements | All | Yes | Some identical | $\frac{n!}{n_1! n_2! \cdots}$ |
| Combination | Some | No | No | $\binom{n}{k}$ |
| k-Permutation | Some | Yes | No | $\frac{n!}{(n-k)!}$ |
| Sequence with repetition | Some | Yes | Yes | $n^k$ |

---

## Step-by-Step Solution

### Problem 1 — Arranging 7 students in a line

**Questions:**
- Are we using all objects? Yes — all 7 students are placed.
- Does order matter? Yes — a line has a first position, a second position, etc.
- Repetition? No — each student occupies exactly one position.
- Identical objects? No — students are distinguishable.

**Model: Permutation**

$$
P_7 = 7! = 5040
$$

---

### Problem 2 — Choosing 4 members of a committee from 12 people

**Questions:**
- All or some? Some — only 4 out of 12 are chosen.
- Does order matter? No — a committee is a set of people, not a ranked list.
- Repetition? No — one person cannot hold two seats.

**Model: Combination**

$$
\binom{12}{4} = \frac{12!}{4! \cdot 8!} = 495
$$

---

### Problem 3 — Assigning gold, silver, and bronze medals among 15 athletes

**Questions:**
- All or some? Some — only 3 out of 15 receive medals.
- Does order matter? Yes — gold, silver, and bronze are distinct; receiving gold is different from receiving silver.
- Repetition? No — one athlete cannot receive two medals.

**Model: k-Permutation (ordered selection without repetition)**

$$
P(15, 3) = \frac{15!}{(15-3)!} = 15 \times 14 \times 13 = 2730
$$

---

### Problem 4 — Forming a 6-digit PIN code

**Questions:**
- All or some? Some — 6 digits chosen from $\{0, 1, \ldots, 9\}$.
- Does order matter? Yes — the code $1234$ is different from $4321$.
- Repetition? Yes — the same digit may appear more than once in a PIN.

**Model: Sequence with repetition**

$$
10^6 = 1{,}000{,}000
$$

---

### Problem 5 — Arranging the letters of the word BANANA

**Questions:**
- All or some? All — all 6 letters are arranged.
- Does order matter? Yes — different orderings give different words.
- Repetition / identical objects? Yes — the letters are not all distinct:
  - B appears 1 time
  - A appears 3 times
  - N appears 2 times

**Model: Permutation with repeated elements**

$$
\frac{6!}{1! \cdot 3! \cdot 2!} = \frac{720}{1 \cdot 6 \cdot 2} = 60
$$

---

### Problem 6 — Seating 6 people around a round table

**Questions:**
- All or some? All — all 6 people are seated.
- Does order matter? Yes — but rotations of the same arrangement are considered identical.
- Repetition? No.

**Model: Circular permutation**

In a circular arrangement, one position is fixed to eliminate equivalent rotations. The remaining $n - 1$ people are arranged in all possible ways.

$$
(6 - 1)! = 5! = 120
$$

---

## Final Result

| Problem | Model | Count |
|---|---|---|
| 1. Students in a line | Permutation | $7! = 5040$ |
| 2. Committee of 4 from 12 | Combination | $\binom{12}{4} = 495$ |
| 3. Gold/silver/bronze from 15 | k-Permutation | $P(15,3) = 2730$ |
| 4. 6-digit PIN code | Sequence with repetition | $10^6 = 1{,}000{,}000$ |
| 5. Letters of BANANA | Permutation with repeated elements | $\frac{6!}{1!\,3!\,2!} = 60$ |
| 6. 6 people at round table | Circular permutation | $5! = 120$ |

---

## Common Mistakes

- Confusing combinations and k-permutations. The key question is: does the order of selection matter? Medals are ordered (gold $\neq$ silver); committee seats are not.
- Applying $n!$ when objects are not all distinct. Identical objects reduce the count by dividing by the factorials of their multiplicities.
- Forgetting to divide by $n$ (or equivalently fixing one seat) in circular permutations.
- Using $n^k$ when repetition is not allowed. The sequence model requires that each position is chosen independently with the full set available.