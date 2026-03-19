# Task 6 — Combinations in Card Problems

## Problem Statement

A standard deck contains 52 cards.

1. In how many ways can 5 cards be drawn so that the hand contains exactly 2 hearts?
2. In how many ways can a 5-card hand contain at least one heart?
3. In how many ways can a 5-card hand contain no face cards (J, Q, K)?

---

## Definitions / Theory

**Standard 52-card deck:** 4 suits (Hearts, Diamonds, Clubs, Spades), 13 ranks each (A, 2–10, J, Q, K).

- Hearts: 13 cards
- Non-hearts: 39 cards
- Face cards (J, Q, K): 3 per suit, $3 \times 4 = 12$ total
- Non-face cards: $52 - 12 = 40$

A **5-card hand** is an unordered selection — order of dealing does not matter.

$$
\text{Total 5-card hands} = \binom{52}{5} = \frac{52!}{5! \cdot 47!} = 2{,}598{,}960
$$

**Product rule for restricted selections:** choose from one group, then independently from another group, and multiply.

**Complement method:**

$$
P(\text{at least one}) = 1 - P(\text{none})
$$

---

## Step-by-Step Solution

### Problem 1 — Exactly 2 hearts in a 5-card hand

The hand must contain exactly 2 cards from the 13 hearts and exactly 3 cards from the 39 non-hearts.

**Step 1 — Choose 2 hearts from 13.**

$$
\binom{13}{2} = \frac{13 \times 12}{2} = 78
$$

**Step 2 — Choose 3 non-hearts from 39.**

$$
\binom{39}{3} = \frac{39 \times 38 \times 37}{3 \times 2 \times 1} = \frac{54{,}834}{6} = 9{,}139
$$

**Step 3 — Multiply.**

The two selections are independent:

$$
\binom{13}{2} \times \binom{39}{3} = 78 \times 9{,}139 = 712{,}842
$$

---

### Problem 2 — At least one heart in a 5-card hand

**Strategy: complement method.**

$$
|\text{at least one heart}| = |\text{all hands}| - |\text{no hearts}|
$$

**Step 1 — Total 5-card hands.**

$$
\binom{52}{5} = 2{,}598{,}960
$$

**Step 2 — Hands with no hearts.**

Choose all 5 cards from the 39 non-heart cards:

$$
\binom{39}{5} = \frac{39 \times 38 \times 37 \times 36 \times 35}{5!} = \frac{69{,}090{,}840}{120} = 575{,}757
$$

**Step 3 — Subtract.**

$$
2{,}598{,}960 - 575{,}757 = 2{,}023{,}203
$$

---

### Problem 3 — No face cards in a 5-card hand

Face cards are J, Q, K — 3 per suit, 12 total. Non-face cards: $52 - 12 = 40$.

**Step 1 — Choose all 5 cards from the 40 non-face cards.**

$$
\binom{40}{5} = \frac{40 \times 39 \times 38 \times 37 \times 36}{5!} = \frac{78{,}960{,}960}{120} = 658{,}008
$$

---

## Final Result

| Problem | Formula | Answer |
|---|---|---|
| 1. Exactly 2 hearts | $\binom{13}{2} \times \binom{39}{3}$ | $712{,}842$ |
| 2. At least one heart | $\binom{52}{5} - \binom{39}{5}$ | $2{,}023{,}203$ |
| 3. No face cards | $\binom{40}{5}$ | $658{,}008$ |

---

## Interpretation / Sanity Check

For Problem 2, the fraction of hands with at least one heart:

$$
\frac{2{,}023{,}203}{2{,}598{,}960} \approx 0.778
$$

Since $\frac{1}{4}$ of the deck is hearts, intuitively most hands will contain at least one — a probability near $0.78$ is plausible.

For Problem 1, the fraction of hands with exactly 2 hearts:

$$
\frac{712{,}842}{2{,}598{,}960} \approx 0.274
$$

This is the most likely number of hearts in a 5-card hand (by the hypergeometric distribution), which is consistent.

---

## Common Mistakes

- In Problem 1, choosing 2 from 52 and 3 from 52 independently. This ignores the suit constraint entirely. The correct approach separates hearts from non-hearts.
- In Problem 2, computing $1 - \binom{13}{5}/\binom{52}{5}$. The complement of "at least one heart" is "no hearts," not "all hearts."
- In Problem 3, subtracting face cards from the total before computing $\binom{}{5}$ rather than choosing directly from the 40 non-face cards.