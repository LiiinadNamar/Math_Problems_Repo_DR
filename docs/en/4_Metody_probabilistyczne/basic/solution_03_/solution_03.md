# Task 3 - Geometric Model (Waiting for the First Event)

## Problem Statement

Each printed page contains an error with probability $p$, independently of other pages. Pages are observed until the first error appears. Define the experiment, sample space, distribution, and success meaning.

## Definitions / Theory

If $X$ is the trial number of the first success in independent Bernoulli trials with success probability $p$, then:

$$
P(X=k) = (1-p)^{k-1}p, \quad k=1,2,3,\ldots
$$

This is the geometric distribution.

## Step-by-Step Solution

Success is: an error appears on a page.

Random experiment: inspect pages sequentially until the first page with an error.

Sample space as trial indices:

$$
\Omega = \{1,2,3,\ldots\}
$$

Equivalent sequence representation:

$$
E,\; NE, E,\; NE, NE, E,\; \ldots
$$

where $E$ denotes error and $NE$ denotes no error.

Distribution:

$$
P(X=k) = (1-p)^{k-1}p, \quad k \in \mathbb{N}
$$

## Final Result

The model is geometric with support $\{1,2,3,\ldots\}$ and parameter $p$.

## Interpretation / Sanity Check

The probability decreases geometrically with $k$, which is expected: waiting longer for the first error is less likely. Also:

$$
\sum_{k=1}^{\infty} (1-p)^{k-1}p = 1
$$

so this is a valid probability model.

## Common Mistakes

- Starting support at $k=0$.
- Using $k$ instead of $k-1$ in the exponent.
- Mixing geometric and binomial interpretation.
