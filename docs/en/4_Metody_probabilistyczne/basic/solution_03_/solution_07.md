# Task 7 - Hypergeometric Model

## Problem Statement

A box contains 12 working bulbs and 3 defective bulbs. Five bulbs are drawn without replacement. Compute the probability that exactly 2 defective bulbs are in the sample.

## Definitions / Theory

Sampling without replacement from a finite population with two classes is modeled by a hypergeometric distribution:

$$
P(X=k)=\frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}
$$

where:

- $N$ total items,
- $K$ defective items,
- $n$ draws,
- $X$ defective items in sample.

## Step-by-Step Solution

### Identify Parameters

Given:
- $N = 15$ total bulbs (12 working + 3 defective).
- $K = 3$ defective bulbs (the "success" items).
- $n = 5$ bulbs drawn without replacement.
- We want $P(X = 2)$ where $X$ = number of defective bulbs in the sample.

### Why Hypergeometric?

We **cannot use binomial** because:
- We draw **without replacement**.
- After drawing 1 defective bulb, there are only 2 defective left among 14 remaining.
- The probability changes: it was $3/15$, now it's $2/14$ — not constant.

Hypergeometric handles this changing probability automatically through the combinatorial structure.

### Apply the Hypergeometric Formula

$$
P(X=2)=\frac{\binom{3}{2}\binom{12}{3}}{\binom{15}{5}}
$$

**Component by component:**

- $\binom{3}{2} = 3$ = ways to choose 2 defective bulbs from 3 available.
- $\binom{12}{3} = 220$ = ways to choose 3 working bulbs from 12 available (to fill the remaining 3 of the 5 drawn).
- Numerator = $3 \times 220 = 660$ = total favorable outcomes (2 defective AND 3 working).
- $\binom{15}{5} = 3003$ = total ways to choose 5 bulbs from 15 (all possible samples).

### Calculate

$$
P(X=2)=\frac{660}{3003} \approx 0.21978 \approx 22.0\%
$$

**Interpretation:** About 1 in 5 samples of 5 bulbs will contain exactly 2 defective bulbs. This is reasonably likely because the defect rate is $3/15 = 20\%$, so in a sample of 5, we'd expect around 1 defect, making 2 defects plausible but not the most common outcome.

## Final Result

$$
P(\text{exactly 2 defective})=\frac{660}{3003} \approx 0.21978
$$

## Interpretation / Sanity Check

The probability is about 22.0%, which is reasonable because defects are relatively rare (3 out of 15), but sample size 5 is large enough to make two defects possible with moderate chance.

## Common Mistakes

- Using binomial distribution instead of hypergeometric.
- Ignoring that draws are without replacement.
- Arithmetic errors in combinations.
