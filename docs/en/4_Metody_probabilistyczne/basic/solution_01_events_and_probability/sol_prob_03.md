# Task 3 — Drawing Cards

## Problem Statement

Cards are drawn from a standard 52-card deck. The order of draws matters.
Construct the sample spaces for one card drawn, two cards drawn with replacement, and two cards drawn without replacement.

---

## Definitions / Theory

**Standard 52-card deck** consists of 4 suits (Hearts, Diamonds, Clubs, Spades) each containing 13 ranks (A, 2, 3, ..., 10, J, Q, K). Each card is uniquely identified by its rank and suit.

**With replacement**: after drawing a card, it is returned to the deck before the next draw. The deck is the same for every draw.

**Without replacement**: after drawing a card, it is not returned. The deck shrinks by one card with each draw.

**Ordered sequence**: the outcome $(c_1, c_2)$ is distinct from $(c_2, c_1)$ when $c_1 \neq c_2$.

The number of ordered sequences of length $r$ drawn from $n$ objects:

- With replacement: $n^r$
- Without replacement: $n \cdot (n-1) \cdots (n-r+1) = \frac{n!}{(n-r)!}$

---

## Step-by-Step Solution

### One Card Drawn

$$
\Omega_1 = \{\text{all 52 cards}\}
$$

Each elementary outcome is a single card, identified by its rank and suit. For example: Ace of Hearts, King of Spades, and so on.

$$
|\Omega_1| = 52
$$

---

### Two Cards Drawn With Replacement

After the first draw, the card is returned. The deck again contains 52 cards for the second draw. Each draw is independent.

$$
\Omega_2 = \{(c_1, c_2) : c_1 \in D,\ c_2 \in D\}
$$

where $D$ denotes the full 52-card deck.

$$
|\Omega_2| = 52 \times 52 = 52^2 = 2704
$$

Note that outcomes such as $(A\heartsuit,\ A\heartsuit)$ are possible — the same card can appear twice.

Each elementary outcome is an ordered pair of cards where repetition is allowed.

---

### Two Cards Drawn Without Replacement

After the first draw, the card is not returned. The second draw is from the remaining 51 cards.

$$
\Omega_2' = \{(c_1, c_2) : c_1 \in D,\ c_2 \in D \setminus \{c_1\}\}
$$

$$
|\Omega_2'| = 52 \times 51 = 2652
$$

The same card cannot appear twice. The outcome $(A\heartsuit,\ A\heartsuit)$ is impossible.

Each elementary outcome is an ordered pair of distinct cards.

---

## Final Result

| Experiment | Sample space | Number of outcomes |
|---|---|---|
| One card drawn | All 52 cards | $52$ |
| Two draws with replacement | Ordered pairs, repetition allowed | $52^2 = 2704$ |
| Two draws without replacement | Ordered pairs of distinct cards | $52 \times 51 = 2652$ |

---

## Interpretation / Sanity Check

The sample space without replacement is smaller than with replacement, since repeated cards are excluded. The difference is:

$$
2704 - 2652 = 52
$$

This equals exactly the 52 outcomes of the form $(c, c)$ that are possible with replacement but impossible without.

---

## Common Mistakes

- Treating $(c_1, c_2)$ and $(c_2, c_1)$ as the same outcome when order matters. They are distinct elementary outcomes.
- Using combinations $\binom{52}{2}$ instead of permutations $52 \times 51$ for the without-replacement case. Combinations are appropriate only when order does not matter.
- Forgetting that with replacement the two draws are independent, while without replacement they are not.
