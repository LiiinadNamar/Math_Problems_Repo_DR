# Task 8 - Geometric Model

## Problem Statement

Compilation error probability is $p=0.1$ in each independent compilation. A programmer repeats compilations until the first error. Compute:

- probability that first error appears on 4th compilation,
- probability that first error appears no later than 3rd compilation.

## Definitions / Theory

If $X$ is trial index of the first success in geometric model:

$$
P(X=k)=(1-p)^{k-1}p
$$

Also:

$$
P(X \le m)=1-(1-p)^m
$$

## Step-by-Step Solution

Given $p=0.1$, so $1-p=0.9$.

### 1. First Error on 4th Compilation

**Reasoning:** For the first error to occur on the 4th compilation:
- Compilations 1, 2, 3 must be **successful** (no error): probability $1-p = 0.9$ each.
- Compilation 4 must **fail** (error occurs): probability $p = 0.1$.
- By independence, multiply:

$$
P(X=4) = (0.9)^3 \times 0.1
$$

Compute:

$$
P(X=4) = 0.729 \times 0.1 = 0.0729 \approx 7.29\%
$$

**Interpretation:** It's fairly unlikely (≈7%) that we need exactly 4 compilations. The exponential decay makes waiting longer increasingly rare.

### 2. First Error No Later Than 3rd Compilation

**Reasoning:** "No later than 3rd" means the first error occurs at compilation 1, 2, **or** 3. In other words:

$$
P(X \le 3) = P(X=1) + P(X=2) + P(X=3)
$$

Computing all three terms is tedious, so use the **complement:**

$$
P(X \le 3) = 1 - P(X > 3) = 1 - P(X \ge 4)
$$

$P(X \ge 4)$ means the first 3 compilations are all successful (no error) **and** we haven't counted later compilations:

$$
P(X \ge 4) = (0.9)^3 = 0.729
$$

Therefore:

$$
P(X \le 3) = 1 - 0.729 = 0.271 \approx 27.1\%
$$

**Interpretation:** There's roughly a 27% chance that we'll see the first error within the first 3 compilations. This is higher than the single event $P(X=4)$ because it includes multiple ways for an error to occur (on attempts 1, 2, or 3).

## Final Result

$$
P(X=4)=0.0729
$$

$$
P(X \le 3)=0.271
$$

## Interpretation / Sanity Check

A first error at exactly attempt 4 is less likely than an error by attempt 3, which is consistent with event inclusion:

$$
\{X=4\} \subsetneq \{X \le 4\}, \quad \{X=4\} \not\subseteq \{X \le 3\}
$$

Both values are in $[0,1]$.

## Common Mistakes

- Using exponent 4 instead of 3 for $P(X=4)$.
- Computing $P(X \le 3)$ by summing with arithmetic mistakes instead of complement.
