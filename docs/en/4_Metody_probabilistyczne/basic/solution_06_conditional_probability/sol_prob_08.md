# Problem 08 — Bayes' Formula from a Table

## Problem Statement

Using the fraud detection table, compute base rates and conditional rates, apply the law of total probability to find $P(S)$, then compute $P(F \mid S)$ using Bayes' formula. Interpret why most suspicious transactions can still be legitimate.

| Transaction type | Marked suspicious | Not marked suspicious | Total |
| ---------------- | ----------------: | --------------------: | ----: |
| Fraudulent       |                98 |                     2 |   100 |
| Legitimate       |               297 |                  9603 |  9900 |
| Total            |               395 |                  9605 | 10000 |

$$
F = \text{transaction is fraudulent},\quad S = \text{transaction is marked suspicious}.
$$

---

## Definitions / Theory

**Law of total probability.**

$$
P(S) = P(S \mid F) P(F) + P(S \mid F^c) P(F^c).
$$

**Bayes' formula.**

$$
P(F \mid S) = \frac{P(S \mid F) P(F)}{P(S)}.
$$

---

## Step-by-Step Solution

### Part 1 — Compute $P(F)$, $P(S \mid F)$, $P(S \mid F^c)$

Total $n = 10000$.

$$
P(F) = \frac{100}{10000} = 0.01,
$$

$$
P(S \mid F) = \frac{98}{100} = 0.98,
$$

$$
P(S \mid F^c) = \frac{297}{9900} = 0.03.
$$

---

### Part 2 — Compute $P(S)$

$$
\begin{align}
P(S)
&= 0.98 \cdot 0.01 + 0.03 \cdot 0.99 \\
&= 0.0098 + 0.0297 \\
&= 0.0395.
\end{align}
$$

---

### Part 3 — Compute $P(F \mid S)$

$$
P(F \mid S) = \frac{0.98 \cdot 0.01}{0.0395} = \frac{0.0098}{0.0395} \approx 0.2481.
$$

---

### Part 4 — Are most suspicious transactions fraudulent?

No. Only about 24.8% of suspicious transactions are fraudulent. Therefore, most suspicious transactions are legitimate.

---

### Part 5 — Why can this happen with a good detector?

Even with a high detection rate ($P(S \mid F) = 0.98$), fraud is rare ($P(F) = 0.01$). The large number of legitimate transactions means that even a small false positive rate ($P(S \mid F^c) = 0.03$) generates many suspicious flags.

---

### Part 6 — Role of the base rate $P(F)$

The base rate $P(F)$ sets how common fraud is before any evidence. A very small base rate strongly limits $P(F \mid S)$, even when the detector is accurate.

---

## Final Result

$$
P(F) = 0.01,\quad P(S \mid F) = 0.98,\quad P(S \mid F^c) = 0.03.
$$

$$
P(S) = 0.0395,\quad P(F \mid S) \approx 0.2481.
$$

Most suspicious transactions are legitimate, due to the low base rate of fraud.

---

## Interpretation / Sanity Check

The suspicious rate $P(S) = 3.95\%$ lies between the two conditional rates, as expected for a weighted average. The posterior probability $P(F \mid S)$ is far below 1 because fraud is rare in the population.

---

## Common Mistakes

- Confusing $P(F \mid S)$ with $P(S \mid F)$.
- Ignoring the base rate $P(F)$ and focusing only on detector accuracy.
