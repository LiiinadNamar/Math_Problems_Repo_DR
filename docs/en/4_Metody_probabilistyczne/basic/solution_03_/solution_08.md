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

### 1. First error on 4th compilation

Need three no-error attempts and then one error:

$$
P(X=4)=(0.9)^3 \cdot 0.1 = 0.0729
$$

### 2. First error no later than 3rd compilation

Use cumulative formula:

$$
P(X \le 3)=1-(0.9)^3=1-0.729=0.271
$$

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
