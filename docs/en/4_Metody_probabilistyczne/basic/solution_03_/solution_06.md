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

### 1. Exactly 2 Defective Parts

**Reasoning:** We use the binomial formula because:
- We have a fixed number of trials ($n=10$).
- Each trial is independent.
- Each trial has two outcomes (defective or good) with constant probability.

Apply the formula:

$$
P(X=2)=\binom{10}{2}(0.04)^2(0.96)^8
$$

**Break down each component:**
- $\binom{10}{2} = \frac{10!}{2! \cdot 8!} = 45$ = number of ways to choose which 2 of the 10 parts are defective.
- $(0.04)^2 = 0.0016$ = probability that those 2 specific parts are defective.
- $(0.96)^8 \approx 0.7214$ = probability that the remaining 8 parts are good.

Multiply:

$$
P(X=2) = 45 \times 0.0016 \times 0.7214 \approx 0.05194 \approx 5.19\%
$$

**Interpretation:** It's relatively unlikely (≈5%) to see exactly 2 defective parts because the defect rate is low (4%) and 10 parts is a small sample. Most of the time, we expect 0 or 1 defect.

### 2. At Least One Defective Part

**Reasoning:** "At least one" ($X \ge 1$) is the complement of "zero" ($X = 0$). Using the complement is numerically faster and avoids summing many terms.

$$
P(X \ge 1) = 1 - P(X=0)
$$

**Calculate $P(X=0)$:**

$$
P(X=0) = \binom{10}{0}(0.04)^0(0.96)^{10} = 1 \times 1 \times (0.96)^{10} \approx 0.6648
$$

Why this form? All 10 parts must be good, each with probability $0.96$. By independence, multiply the probabilities.

**Compute the complement:**

$$
P(X \ge 1) = 1 - 0.6648 \approx 0.3352 \approx 33.52\%
$$

**Interpretation:** There's roughly a 1 in 3 chance of finding at least one defective part in a batch of 10 when the defect rate is 4%. This makes sense: we're sampling, and defects, though rare, do exist.

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
