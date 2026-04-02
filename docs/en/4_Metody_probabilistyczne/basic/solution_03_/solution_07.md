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

Given:

$$
N=15, \quad K=3, \quad n=5, \quad k=2
$$

Apply formula:

$$
P(X=2)=\frac{\binom{3}{2}\binom{12}{3}}{\binom{15}{5}}
$$

Compute combinations:

$$
\binom{3}{2}=3, \quad \binom{12}{3}=220, \quad \binom{15}{5}=3003
$$

Therefore:

$$
P(X=2)=\frac{3 \cdot 220}{3003}=\frac{660}{3003} \approx 0.21978
$$

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
