# Problem 09 — Law of Total Probability Without a Full Table

## Problem Statement

A company receives orders through three channels: website, mobile app, and phone. The proportions of orders and the per-channel cancellation rates are given directly (no full table is provided). The task is to compute the overall cancellation probability using the law of total probability, then apply Bayes' formula to find the conditional probability of each channel given that an order is cancelled.

**Given proportions (prior probabilities of channels):**

$$
P(W) = 0.50, \quad P(A) = 0.35, \quad P(H) = 0.15.
$$

**Given cancellation rates (conditional probabilities):**

$$
P(C \mid W) = 0.04, \quad P(C \mid A) = 0.06, \quad P(C \mid H) = 0.10.
$$

**Events defined:**

$$
W = \text{order came through the website},
$$

$$
A = \text{order came through the mobile app},
$$

$$
H = \text{order came by phone},
$$

$$
C = \text{the order is cancelled}.
$$

---

## Definitions / Theory

**Partition of the sample space.**
A collection of events $B_1, B_2, \ldots, B_k$ is a **partition** of $\Omega$ if:

1. the events are pairwise disjoint: $B_i \cap B_j = \emptyset$ for $i \neq j$,
2. they are exhaustive: $B_1 \cup B_2 \cup \cdots \cup B_k = \Omega$,
3. each event has positive probability.

**Law of total probability.**
If $B_1, B_2, \ldots, B_k$ form a partition of $\Omega$, then for any event $C$:

$$
P(C) = \sum_{i=1}^{k} P(C \mid B_i) \cdot P(B_i).
$$

This formula expresses $P(C)$ as a **weighted average** of the conditional cancellation rates, where the weights are the channel proportions.

**Bayes' formula.**
If $B_1, \ldots, B_k$ form a partition and $P(C) > 0$, then:

$$
P(B_j \mid C) = \frac{P(C \mid B_j) \cdot P(B_j)}{\sum_{i=1}^{k} P(C \mid B_i) \cdot P(B_i)} = \frac{P(C \mid B_j) \cdot P(B_j)}{P(C)}.
$$

Bayes' formula **reverses the direction of conditioning**: it converts $P(C \mid B_j)$ into $P(B_j \mid C)$.

---

## Step-by-Step Solution

### Part 1 — Verify that $W$, $A$, $H$ form a partition

**Mutual exclusivity:** An order arrives through exactly one channel. No order can belong to two channels simultaneously, so $W \cap A = W \cap H = A \cap H = \emptyset$.

**Exhaustiveness:** Every order must come through one of the three channels:

$$
P(W) + P(A) + P(H) = 0.50 + 0.35 + 0.15 = 1.00.
$$

The three events cover the entire sample space. Therefore $W$, $A$, $H$ form a partition of $\Omega$.

---

### Part 2 — Apply the law of total probability to compute $P(C)$

Decompose the event $C$ across the three channels:

$$
P(C) = P(C \mid W) \cdot P(W) + P(C \mid A) \cdot P(A) + P(C \mid H) \cdot P(H).
$$

Substitute the given values:

$$
P(C) = 0.04 \times 0.50 + 0.06 \times 0.35 + 0.10 \times 0.15.
$$

Compute each term separately:

$$
0.04 \times 0.50 = 0.0200,
$$

$$
0.06 \times 0.35 = 0.0210,
$$

$$
0.10 \times 0.15 = 0.0150.
$$

Sum the three terms:

$$
P(C) = 0.0200 + 0.0210 + 0.0150 = 0.0560.
$$

The overall cancellation probability is **5.6%**.

---

### Part 3 — Apply Bayes' formula to compute $P(W \mid C)$, $P(A \mid C)$, $P(H \mid C)$

Each posterior probability has the form:

$$
P(\text{channel} \mid C) = \frac{P(C \mid \text{channel}) \cdot P(\text{channel})}{P(C)}.
$$

The denominator $P(C) = 0.0560$ is the same in all three cases (already computed above).

**Posterior for website:**

$$
P(W \mid C) = \frac{0.04 \times 0.50}{0.0560} = \frac{0.0200}{0.0560} = \frac{200}{560} = \frac{5}{14} \approx 0.3571.
$$

**Posterior for mobile app:**

$$
P(A \mid C) = \frac{0.06 \times 0.35}{0.0560} = \frac{0.0210}{0.0560} = \frac{210}{560} = \frac{3}{8} = 0.375.
$$

**Posterior for phone:**

$$
P(H \mid C) = \frac{0.10 \times 0.15}{0.0560} = \frac{0.0150}{0.0560} = \frac{150}{560} = \frac{15}{56} \approx 0.2679.
$$

**Sanity check:** The three posteriors must sum to $1$:

$$
0.3571 + 0.3750 + 0.2679 = 1.0000. \checkmark
$$

---

### Part 4 — Which channel is most likely among cancelled orders?

$$
P(W \mid C) \approx 0.357, \quad P(A \mid C) = 0.375, \quad P(H \mid C) \approx 0.268.
$$

The **mobile app** is the most likely channel among cancelled orders, with a posterior probability of 37.5%.

---

### Part 5 — Is the most common channel among cancelled orders the same as the channel with the highest cancellation rate?

No. The channel with the **highest cancellation rate** is the phone channel:

$$
P(C \mid H) = 0.10 > P(C \mid A) = 0.06 > P(C \mid W) = 0.04.
$$

However, the channel **most likely among cancelled orders** is the mobile app:

$$
P(A \mid C) = 0.375 > P(W \mid C) \approx 0.357 > P(H \mid C) \approx 0.268.
$$

These two rankings differ because Bayes' formula combines two pieces of information: the cancellation rate **and** the volume (prior probability) of each channel. Phone has the highest rate, but it handles only 15% of all orders. Mobile app has a lower rate, but it handles 35% of all orders. The combined effect places mobile app first in the posterior ranking.

This is an instance of the **base-rate effect**: a rare channel with a high rate can still contribute fewer cancelled orders than a common channel with a moderate rate.

---

## Final Result

$$
P(C) = 0.0560.
$$

$$
P(W \mid C) \approx 0.357, \quad P(A \mid C) = 0.375, \quad P(H \mid C) \approx 0.268.
$$

**The most likely channel among cancelled orders is the mobile app, not the phone channel (which has the highest cancellation rate).**

---

## Interpretation / Sanity Check

$P(C) = 5.6\%$ lies strictly between the lowest rate $P(C \mid W) = 4\%$ and the highest rate $P(C \mid H) = 10\%$, as expected for a weighted average. This is a useful internal check.

The prior channel proportions $P(W) = 0.50$, $P(A) = 0.35$, $P(H) = 0.15$ change after conditioning on cancellation to $0.357$, $0.375$, $0.268$. The website shrinks (from 50% to 36%) because it has the lowest cancellation rate. The phone channel also shrinks (from 15% to 27% — wait, this actually *increases*). Let us verify:

- Website: prior $0.50 \to$ posterior $0.357$. Shrinks, because its cancellation rate 4% is below the average 5.6%.
- App: prior $0.35 \to$ posterior $0.375$. Grows slightly, because its rate 6% is above the average.
- Phone: prior $0.15 \to$ posterior $0.268$. Grows the most, because its rate 10% is the furthest above the average.

This pattern is consistent: channels with above-average cancellation rates gain weight after conditioning on a cancellation.

---

## Common Mistakes

**Mistake 1: Adding the conditional probabilities directly.**
$P(C \mid W) + P(C \mid A) + P(C \mid H) = 0.20 \neq P(C)$. The law of total probability requires weighting each conditional probability by the corresponding channel proportion.

**Mistake 2: Concluding that the most common channel among cancellations has the highest cancellation rate.**
These are different questions: $P(C \mid \text{channel})$ versus $P(\text{channel} \mid C)$. Always identify the direction of conditioning.

**Mistake 3: Forgetting to verify that the partition is exhaustive.**
Before applying the law of total probability, confirm that the prior probabilities sum to $1$.
