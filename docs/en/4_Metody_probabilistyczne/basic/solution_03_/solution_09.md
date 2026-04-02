# Task 9 - Poisson Model

## Problem Statement

A service center receives on average 5 requests per hour. Compute probabilities that in one hour there are:

- exactly 3 requests,
- at least one request.

## Definitions / Theory

For $X \sim \mathrm{Poisson}(\lambda)$:

$$
P(X=k)=\frac{e^{-\lambda}\lambda^k}{k!}
$$

and:

$$
P(X \ge 1)=1-P(X=0)=1-e^{-\lambda}
$$

## Step-by-Step Solution

Given $\lambda=5$.

### 1. Exactly 3 Requests

**Reasoning:** We apply the Poisson probability mass function directly:

$$
P(X=k) = \frac{e^{-\lambda}\lambda^k}{k!}
$$

with $\lambda = 5$ (average requests per hour) and $k = 3$:

$$
P(X=3)=\frac{e^{-5} \cdot 5^3}{3!}
$$

**Calculate step-by-step:**
- $5^3 = 125$.
- $3! = 6$.
- $e^{-5} \approx 0.00674$.

$$
P(X=3) = \frac{0.00674 \times 125}{6} = \frac{0.8425}{6} \approx 0.14037 \approx 14.04\%
$$

**Interpretation:** With an average of 5 requests/hour, observing exactly 3 has probability about 14%. The mean is 5, so values near 5 (like 4, 5, 6) are more likely than 3. But 3 is still reasonably probable because the Poisson distribution spreads probability across all non-negative integers.

### 2. At Least One Request

**Reasoning:** "At least one" is the complement of "zero." Using the complement avoids calculating and summing contributions from $k=1, 2, 3, \ldots$ (infinitely many terms):

$$
P(X \ge 1) = 1 - P(X=0)
$$

**Calculate $P(X=0)$:**

$$
P(X=0) = \frac{e^{-5} \cdot 5^0}{0!} = \frac{e^{-5} \cdot 1}{1} = e^{-5} \approx 0.00674
$$

**Compute the complement:**

$$
P(X \ge 1) = 1 - 0.00674 \approx 0.99326 \approx 99.33\%
$$

**Interpretation:** It's virtually certain (≈99.3%) that at least one request arrives within an hour. This makes intuitive sense: with an average of 5 requests/hour, a completely silent hour is extremely unlikely.

## Final Result

$$
P(X=3) \approx 0.14037
$$

$$
P(X \ge 1) \approx 0.99326
$$

## Interpretation / Sanity Check

With mean 5 requests per hour, observing at least one request is very likely, close to 1. Exactly 3 requests has moderate probability.

## Common Mistakes

- Replacing $3!$ with $3$.
- Forgetting complement for $P(X \ge 1)$.
- Using normal approximation without being asked.
