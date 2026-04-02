# Task 6 - Binomial Model

## Problem Statement

The defect probability is $p=0.04$. An inspector checks $n=10$ independent parts. Compute:

- probability of exactly 2 defective parts,
- probability of at least one defective part.

## Definitions / Theory

If $X$ is the number of defective parts among $n$ independent checks with defect probability $p$, then:

$$
X \sim \mathrm{Bin}(n,p)
$$

and:

$$
P(X=k)=\binom{n}{k}p^k(1-p)^{n-k}
$$

## Step-by-Step Solution

Given:

$$
n=10, \quad p=0.04, \quad 1-p=0.96
$$

### 1. Exactly 2 defective parts

$$
P(X=2)=\binom{10}{2}(0.04)^2(0.96)^8
$$

$$
P(X=2)=45 \cdot 0.0016 \cdot 0.7213895789838336 \approx 0.05194
$$

### 2. At least one defective part

Use complement:

$$
P(X \ge 1)=1-P(X=0)=1-(0.96)^{10}
$$

$$
P(X \ge 1)=1-0.664832635991501 \approx 0.33517
$$

## Final Result

$$
P(X=2) \approx 0.05194
$$

$$
P(X \ge 1) \approx 0.33517
$$

## Interpretation / Sanity Check

With small defect probability and only 10 parts, exactly 2 defects is relatively unlikely (about 5.2%). The chance of observing at least one defect is about 33.5%, which is plausible for $p=0.04$ repeated 10 times.

## Common Mistakes

- Confusing $P(X \ge 1)$ with $P(X=1)$.
- Forgetting complement rule for faster computation.
- Using $\binom{10}{2}$ incorrectly.
