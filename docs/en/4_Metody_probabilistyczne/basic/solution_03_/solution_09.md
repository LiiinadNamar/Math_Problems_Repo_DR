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

### 1. Exactly 3 requests

$$
P(X=3)=\frac{e^{-5}5^3}{3!}=\frac{125}{6}e^{-5}
$$

$$
P(X=3) \approx 0.14037
$$

### 2. At least one request

$$
P(X \ge 1)=1-e^{-5}
$$

$$
P(X \ge 1) \approx 0.99326
$$

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
