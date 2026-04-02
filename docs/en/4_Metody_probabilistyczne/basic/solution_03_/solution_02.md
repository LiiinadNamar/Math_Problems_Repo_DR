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

### Identify the Model Parameters

Given:
- $N = 20$ total components
- $K = 5$ defective components  
- $n = 4$ components selected
- Success = selecting a defective component

Why **hypergeometric** and not binomial?
- Drawing **without replacement** means the probability of selecting a defective component changes after each draw.
- For example: if we draw 1 defective first, then $P(\text{2nd is defective}) = \frac{4}{19}$, not $\frac{5}{20}$ anymore.
- Binomial requires **independence** (constant probability); hypergeometric handles changing probabilities due to depletion.

### Determine Possible Values of $X$

Since we draw 4 components from only 5 defective ones, the number of defective items in the sample ranges from:

$$
k = \max(0, n - (N-K)) \text{ to } \min(n, K) = \max(0, 4-15) \text{ to } \min(4, 5) = 0 \text{ to } 4
$$

So $X \in \{0,1,2,3,4\}$.

### Apply the Hypergeometric Formula

For each value of $k$, the probability is:

$$
P(X = k) = \frac{\binom{5}{k}\binom{15}{4-k}}{\binom{20}{4}}, \quad k=0,1,2,3,4
$$

**Why this formula?**
- $\binom{5}{k}$ = ways to choose $k$ defective components from 5.
- $\binom{15}{4-k}$ = ways to choose $4-k$ good components from 15 (we need $4-k$ good to fill the remaining slots).
- The product gives all favorable outcomes.
- $\binom{20}{4}$ = total ways to choose 4 from 20 components.
- Division gives the probability.

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
