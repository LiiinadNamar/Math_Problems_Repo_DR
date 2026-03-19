# Task 12 — Mixed Counting Problem

## Problem Statement

### Part 1 — Student ID Codes
Two letters from $\{A,B,C,D,E\}$ followed by three digits from $0$–$9$.

1. Letters and digits may repeat.
2. Letters may not repeat, digits may repeat.
3. Neither letters nor digits may repeat.

### Part 2 — Medal Assignment
12 runners, medals for gold, silver, bronze.

1. In how many ways can medals be assigned?
2. Two particular runners must both receive medals. How many ways?

### Part 3 — Committee Selection
4 people from 10 students (6 men, 4 women).

1. How many committees are possible?
2. Exactly two women?
3. At least one woman?

### Part 4 — Circular Seating
7 people around a round table.

1. How many seating arrangements?
2. Two particular people sit next to each other?

### Part 5 — Passwords
5 characters from digits $0$–$9$ and letters $A$–$Z$ (36 characters total).

1. Repetition allowed.
2. No character may repeat.
3. Which counting model applies in each case?

---

## How to Approach a Mixed Problem

Before computing anything, always ask four questions:

1. Are we using **all** objects or only **some** of them?
2. Does **order** matter?
3. Is **repetition** allowed?
4. Are we choosing from **one group** or **multiple groups**?

The answers determine the model. In this task, each part uses a different model — identifying which one is the main skill being tested.

---

## Step-by-Step Solution

---

### Part 1 — Student ID Codes

The identifier looks like this:

$$
\underbrace{L_1\ L_2}_{\text{letters}} \underbrace{D_1\ D_2\ D_3}_{\text{digits}}
$$

The first important observation is that the letter section and the digit section are **completely independent** — whatever letters you choose does not affect the digit choices at all. This means we can count each section separately and then multiply the results at the end. This is the **product rule**.

$$
|\text{total IDs}| = |\text{letter section}| \times |\text{digit section}|
$$

---

#### Problem 1 — Letters and digits may repeat

Start with the letter section. There are 5 available letters: $\{A, B, C, D, E\}$.

For position $L_1$: any of the 5 letters is allowed. **5 choices.**

For position $L_2$: since repetition is allowed, the same letter can be used again. So again, any of the 5 letters. **5 choices.**

$$
\text{Letter section} = 5 \times 5 = 25
$$

Now the digit section. There are 10 available digits: $\{0, 1, \ldots, 9\}$.

Each of the three digit positions is filled independently, and repetition is allowed:

$$
\text{Digit section} = 10 \times 10 \times 10 = 10^3 = 1{,}000
$$

Multiply the two sections:

$$
25 \times 1{,}000 = 25{,}000
$$

---

#### Problem 2 — Letters may not repeat, digits may repeat

The digit section is unchanged — repetition is still allowed there:

$$
\text{Digit section} = 10^3 = 1{,}000
$$

The letter section now has a constraint. Think about filling the two letter positions one by one.

For position $L_1$: any of the 5 letters. **5 choices.**

For position $L_2$: the letter chosen for $L_1$ is now forbidden. So only 4 letters remain. **4 choices.**

$$
\text{Letter section} = 5 \times 4 = 20
$$

Multiply:

$$
20 \times 1{,}000 = 20{,}000
$$

Notice how removing the repetition constraint from the letter section reduced the count from 25 to 20.

---

#### Problem 3 — Neither letters nor digits may repeat

Now both sections have the no-repetition constraint.

**Letter section:** fill two positions from 5 letters without repetition and with order mattering (because $AB$ and $BA$ are different identifiers):

$$
\text{Letter section} = P(5,2) = 5 \times 4 = 20
$$

**Digit section:** fill three positions from 10 digits without repetition:

- $D_1$: 10 choices.
- $D_2$: one digit used, so 9 choices remain.
- $D_3$: two digits used, so 8 choices remain.

$$
\text{Digit section} = P(10,3) = 10 \times 9 \times 8 = 720
$$

Multiply:

$$
20 \times 720 = 14{,}400
$$

**Summary for Part 1:**

| Case | Letter section | Digit section | Total |
|---|---|---|---|
| Both repeat | $5 \times 5 = 25$ | $10^3 = 1{,}000$ | $25{,}000$ |
| Letters no repeat, digits repeat | $5 \times 4 = 20$ | $10^3 = 1{,}000$ | $20{,}000$ |
| Neither repeats | $5 \times 4 = 20$ | $10 \times 9 \times 8 = 720$ | $14{,}400$ |

---

### Part 2 — Medal Assignment

#### Problem 1 — Total ways to assign medals

The first thing to notice is that gold, silver, and bronze are **different** awards. Winning gold is not the same as winning silver. This means **order matters** — we are not just choosing a set of 3 winners, we are assigning specific medals to specific runners.

Think of it as filling three distinct positions: the gold position, the silver position, and the bronze position.

**Gold:** any of the 12 runners can win it. **12 choices.**

**Silver:** the gold medalist cannot win silver — one runner is eliminated. **11 choices.**

**Bronze:** both the gold and silver medalists are out. **10 choices.**

By the product rule:

$$
P(12, 3) = 12 \times 11 \times 10 = 1{,}320
$$

---

#### Problem 2 — Runners $A$ and $B$ must both receive medals

This constraint means that both $A$ and $B$ appear among the three medal winners. The third medal goes to someone else from the remaining 10 runners.

The key insight is to handle the constrained part first.

**Step 1 — Decide which medals $A$ and $B$ get.**

$A$ and $B$ must each receive one of the three medals (gold, silver, or bronze), and they must receive different medals. So we are distributing 2 distinct medals to 2 specific people — this is an ordered assignment.

The number of ways to pick and assign 2 medals out of 3 to $A$ and $B$:

$$
P(3,2) = 3 \times 2 = 6
$$

It helps to list all six options explicitly:

| $A$ receives | $B$ receives | Remaining medal |
|---|---|---|
| Gold | Silver | Bronze |
| Gold | Bronze | Silver |
| Silver | Gold | Bronze |
| Silver | Bronze | Gold |
| Bronze | Gold | Silver |
| Bronze | Silver | Gold |

**Step 2 — Assign the remaining medal.**

Whichever medal is left over goes to one of the $12 - 2 = 10$ runners who are neither $A$ nor $B$. **10 choices.**

**Step 3 — Multiply.**

$$
6 \times 10 = 60
$$

**Sanity check:** only about $4.5\%$ of all assignments satisfy this constraint:

$$
\frac{60}{1{,}320} = \frac{1}{22} \approx 0.045
$$

This makes intuitive sense — requiring two specific runners to both be among only three medal winners is quite restrictive.

---

### Part 3 — Committee Selection

#### Problem 1 — Total committees

A committee is a **set** of people. The person chosen first or last does not matter — there is no ranking within the committee. This means **order does not matter**, so we use combinations.

$$
\binom{10}{4} = \frac{10 \times 9 \times 8 \times 7}{4 \times 3 \times 2 \times 1} = \frac{5{,}040}{24} = 210
$$

---

#### Problem 2 — Exactly two women

The group consists of 6 men and 4 women. The committee must have exactly 2 women, which automatically means exactly 2 men (since the committee has 4 seats total).

The key idea here is that choosing the women and choosing the men are **independent decisions** — whoever you pick from the women does not restrict who you can pick from the men. So we count each group separately and multiply.

**Choose 2 women from the 4 available women:**

$$
\binom{4}{2} = \frac{4 \times 3}{2 \times 1} = 6
$$

To see why this is 6 and not more, label the women $W_1, W_2, W_3, W_4$. The possible pairs are:

$$
\{W_1,W_2\},\ \{W_1,W_3\},\ \{W_1,W_4\},\ \{W_2,W_3\},\ \{W_2,W_4\},\ \{W_3,W_4\}
$$

That is exactly 6 pairs. $\checkmark$

**Choose 2 men from the 6 available men:**

$$
\binom{6}{2} = \frac{6 \times 5}{2 \times 1} = 15
$$

**Multiply** (because for each of the 6 pairs of women, we can independently choose any of the 15 pairs of men):

$$
6 \times 15 = 90
$$

---

#### Problem 3 — At least one woman

"At least one woman" means the committee contains 1, 2, 3, or 4 women. Counting all four cases separately and adding them up works, but it takes a lot of steps.

The **complement method** is much faster. Ask: what is the opposite of "at least one woman"? It is "zero women" — a committee consisting entirely of men.

$$
|\text{at least one woman}| = |\text{all committees}| - |\text{no women}|
$$

**Total committees:**

$$
\binom{10}{4} = 210
$$

**Committees with no women** — choose all 4 members from the 6 men:

$$
\binom{6}{4} = \frac{6 \times 5}{2 \times 1} = 15
$$

**Subtract:**

$$
210 - 15 = 195
$$

**Verification by listing all cases directly:**

| Number of women | Number of men | Count |
|---|---|---|
| 1 | 3 | $\binom{4}{1} \times \binom{6}{3} = 4 \times 20 = 80$ |
| 2 | 2 | $\binom{4}{2} \times \binom{6}{2} = 6 \times 15 = 90$ |
| 3 | 1 | $\binom{4}{3} \times \binom{6}{1} = 4 \times 6 = 24$ |
| 4 | 0 | $\binom{4}{4} \times \binom{6}{0} = 1 \times 1 = 1$ |
| **Total** | | $80 + 90 + 24 + 1 = \mathbf{195}$ $\checkmark$ |

The complement method gave the same answer with far less work.

---

### Part 4 — Circular Seating

#### Problem 1 — 7 people around a round table

This is where students often make a mistake by simply writing $7!$. Let us understand why that is wrong.

In a **linear** arrangement (a row), every seat has a fixed label: seat 1, seat 2, and so on. Moving everyone one seat to the right produces a genuinely different arrangement.

In a **circular** arrangement, the seats have no fixed labels — only relative positions matter. If everyone shifts one seat clockwise, the arrangement looks exactly the same (each person still has the same neighbours). This means many linear arrangements correspond to the same circular arrangement.

Specifically, for $n$ people seated in a circle, every circular arrangement corresponds to exactly $n$ linear arrangements (all rotations of each other). So:

$$
\text{circular arrangements} = \frac{n!}{n} = (n-1)!
$$

The standard way to apply this is to **fix one person** in a seat, removing the rotational freedom. Then arrange the remaining $n-1$ people freely.

Fix person $A$ in one seat. This seat is now a reference point — all rotations are equivalent to this fixed arrangement.

Arrange the remaining 6 people in the other 6 seats:

$$
6! = 720
$$

$$
(7-1)! = 6! = 720
$$

---

#### Problem 2 — Two particular people must sit next to each other

Call the two people $A$ and $B$. The constraint is that they must occupy adjacent seats.

**The block method:** when two objects must always be together, treat them as a single combined object. Instead of 7 individual people, we now have 6 objects: the block $[AB]$ and the other 5 people.

**Step 1 — Count circular arrangements of the 6 objects.**

Apply the circular permutation formula to 6 objects:

$$
(6-1)! = 5! = 120
$$

**Step 2 — Count the internal arrangements within the block.**

The block $[AB]$ can be arranged in two ways internally:
- $A$ sits to the left of $B$: arrangement $AB$
- $A$ sits to the right of $B$: arrangement $BA$

These are genuinely different seatings because the neighbours of $A$ and $B$ differ. So:

$$
2! = 2
$$

**Step 3 — Multiply.**

$$
5! \times 2 = 120 \times 2 = 240
$$

**Intuitive check:** fix $A$ at the table. $B$ can sit in any of the 6 remaining seats. Exactly 2 of those seats are adjacent to $A$ (one on each side). So the fraction of arrangements where $A$ and $B$ are adjacent is $\frac{2}{6} = \frac{1}{3}$.

$$
720 \times \frac{1}{3} = 240 \checkmark
$$

---

### Part 5 — Passwords

The character set consists of all digits $\{0,\ldots,9\}$ and all uppercase letters $\{A,\ldots,Z\}$:

$$
n = 10 + 26 = 36 \text{ characters}
$$

The password has $k = 5$ positions. Order always matters for passwords — the password $AB123$ is different from $BA123$ even though they contain the same characters.

---

#### Problem 1 — Repetition allowed

Since repetition is allowed, each of the 5 positions is filled **independently** and freely from all 36 characters. Using the same character twice (or more) is permitted.

Fill each position:

- Position 1: 36 choices
- Position 2: 36 choices (the same character can be reused)
- Position 3: 36 choices
- Position 4: 36 choices
- Position 5: 36 choices

$$
36^5 = 60{,}466{,}176
$$

**Model: sequence with repetition** — $n^k$.

---

#### Problem 2 — No character may repeat

Now each character can appear at most once. Each time a position is filled, that character is removed from the available pool.

- Position 1: 36 choices (full set)
- Position 2: one character used, 35 remain
- Position 3: two characters used, 34 remain
- Position 4: 33 remain
- Position 5: 32 remain

$$
P(36,5) = 36 \times 35 \times 34 \times 33 \times 32 = 45{,}239{,}040
$$

**Model: k-permutation** — $P(n,k)$.

---

#### Problem 3 — Model identification

Before computing, identify the model by answering the standard questions:

| Question | Repetition allowed | No repetition |
|---|---|---|
| All or some characters? | Some (5 of 36) | Some (5 of 36) |
| Does order matter? | Yes | Yes |
| Repetition allowed? | Yes | No |
| **Model** | Sequence with repetition | k-Permutation |
| **Formula** | $n^k = 36^5$ | $P(n,k) = P(36,5)$ |

In both cases order matters because $AB123 \neq BA123$ — passwords are sequences, not sets.

---

## Final Result

| Part | Problem | Answer |
|---|---|---|
| 1 | Letters repeat, digits repeat | $25{,}000$ |
| 1 | Letters no repeat, digits repeat | $20{,}000$ |
| 1 | Neither repeats | $14{,}400$ |
| 2 | Total medal assignments | $1{,}320$ |
| 2 | Both $A$ and $B$ get medals | $60$ |
| 3 | Committee of 4 from 10 | $210$ |
| 3 | Exactly 2 women | $90$ |
| 3 | At least 1 woman | $195$ |
| 4 | 7 people at round table | $720$ |
| 4 | Two particular people adjacent | $240$ |
| 5 | Password, repetition allowed | $60{,}466{,}176$ |
| 5 | Password, no repetition | $45{,}239{,}040$ |

---

## Common Mistakes

- **Part 1:** computing $5^2 \times 10^3 = 25{,}000$ even when letters cannot repeat. Once repetition is forbidden, the second letter position has only 4 choices, not 5.

- **Part 2 Problem 2:** assigning only 1 way for $A$ and $B$ to receive medals (forgetting that $A$ gold + $B$ silver is different from $A$ silver + $B$ gold). There are $P(3,2) = 6$ distinct ordered assignments.

- **Part 3 Problem 3:** computing $\binom{10}{4} - \binom{4}{4} = 209$. The complement of "at least one woman" is "no women at all" — committees from only the 6 men, which number $\binom{6}{4} = 15$, not 1.

- **Part 4:** writing $7!$ for circular arrangements. Rotations of the same arrangement are identical in a circle. Fix one person and arrange the remaining $6$, giving $6! = 720$.

- **Part 5:** using $P(36,5)$ when repetition is allowed, or $36^5$ when repetition is forbidden. Repetition allowed $\to$ $n^k$; repetition forbidden $\to$ $P(n,k)$.