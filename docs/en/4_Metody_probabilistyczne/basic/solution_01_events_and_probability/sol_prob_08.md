# Task 8 — Events and Probabilities in Card Drawing

## Problem Statement

Using the sample spaces from Task 3, assign probabilities to elementary outcomes and compute the probabilities of the specified events for one card drawn, two cards drawn with replacement, and two cards drawn without replacement.

---

## Definitions / Theory

**Standard 52-card deck**: 4 suits, 13 ranks each. Face cards are J, Q, K (3 per suit, 12 total).

**Classical probability** (equally likely outcomes):

$$
P(A) = \frac{|A|}{|\Omega|}
$$

- $\Omega_1$: $|\Omega_1| = 52$, each card has probability $\frac{1}{52}$.
- $\Omega_2$ (with replacement): $|\Omega_2| = 2704$, each pair has probability $\frac{1}{2704}$.
- $\Omega_2'$ (without replacement): $|\Omega_2'| = 2652$, each pair has probability $\frac{1}{2652}$.

**Complement rule**: $P(A^c) = 1 - P(A)$.

---

## Step-by-Step Solution

### One Card Drawn

**Event $A_1$** — the card is a heart:

There are 13 hearts in the deck.

$$
P(A_1) = \frac{13}{52} = \frac{1}{4}
$$

**Event $B_1$** — the card is a king:

There are 4 kings (one per suit).

$$
P(B_1) = \frac{4}{52} = \frac{1}{13}
$$

**Event $C_1$** — the card is not a face card:

Face cards: J, Q, K — 3 per suit, 12 total. Non-face cards: $52 - 12 = 40$.

$$
P(C_1) = \frac{40}{52} = \frac{10}{13}
$$

---

### Two Cards Drawn With Replacement

$$
|\Omega_2| = 52^2 = 2704
$$

**Event $A_2$** — both cards are hearts:

$$
|A_2| = 13 \times 13 = 169
$$

$$
P(A_2) = \frac{169}{2704} = \frac{1}{16}
$$

**Event $B_2$** — both cards have the same rank:

Choose any rank for the first card: 52 ways. The second card must have the same rank: 4 ways (one per suit).

$$
|B_2| = 52 \times 4 = 208
$$

$$
P(B_2) = \frac{208}{2704} = \frac{1}{13}
$$

**Event $C_2$** — at least one card is an ace:

Use the complement. The number of pairs with no aces: $48 \times 48 = 2304$.

$$
P(C_2) = 1 - \frac{2304}{2704} = 1 - \frac{144}{169} = \frac{25}{169}
$$

---

### Two Cards Drawn Without Replacement

$$
|\Omega_2'| = 52 \times 51 = 2652
$$

**Event $A_3$** — both cards are hearts:

First card is any heart: 13 ways. Second card is any remaining heart: 12 ways.

$$
|A_3| = 13 \times 12 = 156
$$

$$
P(A_3) = \frac{156}{2652} = \frac{1}{17}
$$

**Event $B_3$** — both cards have the same rank:

Choose any card for the first draw: 52 ways. The second card must have the same rank but differ from the first: 3 ways.

$$
|B_3| = 52 \times 3 = 156
$$

$$
P(B_3) = \frac{156}{2652} = \frac{1}{17}
$$

**Event $C_3$** — one card is a king and the other is a queen (in any order):

- First card is a king, second is a queen: $4 \times 4 = 16$ outcomes.
- First card is a queen, second is a king: $4 \times 4 = 16$ outcomes.

$$
|C_3| = 32
$$

$$
P(C_3) = \frac{32}{2652} = \frac{8}{663}
$$

---

### Additional Event on $\Omega_2'$

**Event $D_3$** — both cards are aces:

$$
|D_3| = 4 \times 3 = 12
$$

$$
P(D_3) = \frac{12}{2652} = \frac{1}{221}
$$

---

## Final Result

| Event | Description | Probability |
|---|---|---|
| $A_1$ | Heart | $\frac{1}{4}$ |
| $B_1$ | King | $\frac{1}{13}$ |
| $C_1$ | Not a face card | $\frac{10}{13}$ |
| $A_2$ | Both hearts (with replacement) | $\frac{1}{16}$ |
| $B_2$ | Same rank (with replacement) | $\frac{1}{13}$ |
| $C_2$ | At least one ace (with replacement) | $\frac{25}{169}$ |
| $A_3$ | Both hearts (without replacement) | $\frac{1}{17}$ |
| $B_3$ | Same rank (without replacement) | $\frac{1}{17}$ |
| $C_3$ | One king and one queen | $\frac{8}{663}$ |
| $D_3$ | Both aces (without replacement) | $\frac{1}{221}$ |

---

## Interpretation / Sanity Check

Comparing $A_2$ and $A_3$: without replacement, the probability of both cards being hearts is $\frac{1}{17} \approx 0.059$, slightly higher than with replacement $\frac{1}{16} = 0.0625$. Wait — $\frac{1}{17} < \frac{1}{16}$, which is correct: without replacement, drawing a heart first makes it slightly less likely the second is also a heart (only 12 hearts remain out of 51 cards, compared to 13 out of 52).

$$
\frac{13}{52} \times \frac{12}{51} = \frac{156}{2652} = \frac{1}{17} < \frac{1}{16} = \frac{13}{52} \times \frac{13}{52} \checkmark
$$

---

## Common Mistakes

- Forgetting to reduce the deck size for the second draw in the without-replacement case.
- Forgetting to account for both orderings in event $C_3$ (king then queen, and queen then king).
- Using combinations instead of ordered pairs when the sample space is defined with order.
