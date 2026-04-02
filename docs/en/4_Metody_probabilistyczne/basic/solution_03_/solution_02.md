# Task 2 - Hypergeometric Model (Sampling from a Batch)

## Problem Statement

From a batch of 20 components (5 defective, 15 functional), 4 components are selected without replacement. Define the random variable $X$ as the number of defective components in the sample and determine its distribution.

## Definitions / Theory

The hypergeometric model applies when sampling without replacement from a finite population.

- Population size: $N$.
- Number of success states in population: $K$.
- Sample size: $n$.
- Random variable $X$: number of successes in the sample.

Probability mass function:

$$
P(X = k) = \frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}
$$

## Step-by-Step Solution

### Part 1 — Description of the Experiment

We have a batch of 20 components: 5 defective and 15 functional. We draw a random sample of 4 components without returning any drawn component to the batch. We record how many of the 4 drawn components are defective.

The draw is unordered — we do not care about the sequence in which the components are drawn, only about the composition of the sample.

**Parameters:**
- $N = 20$ (population size)
- $K = 5$ (defectives in population)
- $n = 4$ (sample size)

### Part 2 — Random Variable

$$
X = \text{number of defective components in the sample of 4}
$$

### Part 3 — Possible Values of $X$

$X$ can range from 0 (no defectives in the sample) to the smaller of $n$ and $K$:

$$
X \in \{0, 1, 2, 3, 4\}
$$

However, we must also check that $n - k \leq N - K$, i.e. that enough functional items exist to fill the non-defective positions.

- $k = 4$: need $n - k = 0$ functional items. $0 \leq 15$. ✓
- $k = 3$: need 1 functional item. $1 \leq 15$. ✓
- $k = 2$: need 2. ✓
- $k = 1$: need 3. ✓
- $k = 0$: need 4. ✓

All values $k \in \{0, 1, 2, 3, 4\}$ are valid.

### Part 4 — Probability Distribution

The total number of ways to draw 4 items from 20 is:

$$
\binom{20}{4} = \frac{20!}{4!\cdot 16!} = \frac{20 \times 19 \times 18 \times 17}{4 \times 3 \times 2 \times 1} = 4{,}845
$$

**$P(X = 0)$** — no defectives, all 4 from the 15 functional:

$$
P(X=0) = \frac{\binom{5}{0}\binom{15}{4}}{\binom{20}{4}} = \frac{1 \times 1{,}365}{4{,}845} = \frac{1{,}365}{4{,}845} \approx 0.2817
$$

where $\binom{15}{4} = \frac{15 \times 14 \times 13 \times 12}{24} = 1{,}365$.

**$P(X = 1)$** — exactly 1 defective, 3 functional:

$$
P(X=1) = \frac{\binom{5}{1}\binom{15}{3}}{\binom{20}{4}} = \frac{5 \times 455}{4{,}845} = \frac{2{,}275}{4{,}845} \approx 0.4696
$$

where $\binom{15}{3} = \frac{15 \times 14 \times 13}{6} = 455$.

**$P(X = 2)$** — exactly 2 defectives, 2 functional:

$$
P(X=2) = \frac{\binom{5}{2}\binom{15}{2}}{\binom{20}{4}} = \frac{10 \times 105}{4{,}845} = \frac{1{,}050}{4{,}845} \approx 0.2167
$$

where $\binom{15}{2} = 105$.

**$P(X = 3)$** — exactly 3 defectives, 1 functional:

$$
P(X=3) = \frac{\binom{5}{3}\binom{15}{1}}{\binom{20}{4}} = \frac{10 \times 15}{4{,}845} = \frac{150}{4{,}845} \approx 0.0310
$$

**$P(X = 4)$** — all 4 defectives:

$$
P(X=4) = \frac{\binom{5}{4}\binom{15}{0}}{\binom{20}{4}} = \frac{5 \times 1}{4{,}845} = \frac{5}{4{,}845} \approx 0.0010
$$

**Verification:**

$$
\frac{1{,}365 + 2{,}275 + 1{,}050 + 150 + 5}{4{,}845} = \frac{4{,}845}{4{,}845} = 1 \checkmark
$$

**Distribution table:**

| $k$ | $P(X = k)$ | Approximate value |
|---|---|---|
| 0 | $\frac{1{,}365}{4{,}845}$ | $0.2817$ |
| 1 | $\frac{2{,}275}{4{,}845}$ | $0.4696$ |
| 2 | $\frac{1{,}050}{4{,}845}$ | $0.2167$ |
| 3 | $\frac{150}{4{,}845}$ | $0.0310$ |
| 4 | $\frac{5}{4{,}845}$ | $0.0010$ |

### Part 5 — Definition of Success

In this model, **success** is drawing a **defective component**. The random variable $X$ counts the number of successes in the sample of 4.

---

## Final Result

$$
X \sim \text{Hypergeometric}(N=20,\ K=5,\ n=4)
$$

The most likely outcome is $X = 1$ (one defective in the sample), with probability approximately $46.96\%$.

---

## Interpretation / Sanity Check

The expected number of defectives in the sample is:

$$
E[X] = n \cdot \frac{K}{N} = 4 \cdot \frac{5}{20} = 4 \cdot 0.25 = 1
$$

The distribution is centred near $k = 1$, which is consistent with $E[X] = 1$.

---

## Simulation Note

This distribution can be simulated by:

- Representing the 20 components as a list (5 defective, 15 functional).
- Randomly drawing 4 without replacement and counting defectives.
- Repeating $N$ times and plotting the empirical distribution.

A simulation slider for $N$ (number of trials) would clearly show convergence to the theoretical distribution as $N$ increases.

---

## Common Mistakes

- Using the binomial formula instead of hypergeometric. The binomial model assumes independence and constant $p$ at each draw — neither holds here because we draw without replacement.
- Forgetting to check that $k \leq K$ and $n - k \leq N - K$. Drawing 4 defectives from 5 is possible; drawing 5 defectives when $K = 5$ and $n = 4$ is not.
- Computing $\binom{N}{n}$ incorrectly by treating the draws as ordered. The hypergeometric formula uses combinations (unordered draws).
