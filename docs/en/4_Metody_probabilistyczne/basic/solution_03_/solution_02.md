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

Given:

$$
N = 20, \quad K = 5, \quad n = 4
$$

Success means selecting a defective component.

Possible values of $X$:

$$
k = 0,1,2,3,4
$$

Therefore:

$$
P(X = k) = \frac{\binom{5}{k}\binom{15}{4-k}}{\binom{20}{4}}, \quad k=0,1,2,3,4
$$

Numerical values:

$$
\begin{aligned}
P(X=0) &= \frac{\binom{5}{0}\binom{15}{4}}{\binom{20}{4}} = \frac{1365}{4845} \approx 0.2817 \\
P(X=1) &= \frac{\binom{5}{1}\binom{15}{3}}{\binom{20}{4}} = \frac{2275}{4845} \approx 0.4696 \\
P(X=2) &= \frac{\binom{5}{2}\binom{15}{2}}{\binom{20}{4}} = \frac{1050}{4845} \approx 0.2167 \\
P(X=3) &= \frac{\binom{5}{3}\binom{15}{1}}{\binom{20}{4}} = \frac{150}{4845} \approx 0.0310 \\
P(X=4) &= \frac{\binom{5}{4}\binom{15}{0}}{\binom{20}{4}} = \frac{5}{4845} \approx 0.0010
\end{aligned}
$$

## Final Result

The variable $X$ has a hypergeometric distribution:

$$
X \sim \mathrm{Hyp}(N=20, K=5, n=4)
$$

with support $\{0,1,2,3,4\}$ and probabilities given above.

## Interpretation / Sanity Check

The largest probability occurs at $X=1$, which is natural because the defect rate is $5/20 = 0.25$ and in 4 draws the expected number is near 1.

## Common Mistakes

- Using a binomial model despite sampling without replacement.
- Omitting feasible values of $X$.
- Forgetting that success means defective in this context.
