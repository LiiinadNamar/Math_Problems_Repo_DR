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

### Define Success and the Experiment

**Success:** An error appears on a page.  
**Experiment:** Inspect pages one by one until we find the first page with an error.

### Construct the Sample Space

The sample space consists of the trial number on which the first success occurs:

$$
\Omega = \{1,2,3,\ldots\}
$$

Why only integers? Because we count **how many pages we inspect before finding an error**, not the pages themselves. If the first error appears on page 4, we record the outcome as $X = 4$.

Alternatively, as ordered sequences:

$$
E,\quad (NE, E),\quad (NE, NE, E),\quad \ldots
$$

where $NE$ = no error, $E$ = error.

### Derive the Probability Distribution

For the first success to occur on trial $k$:
- Trials $1$ through $k-1$ must be failures (no error): probability $(1-p)^{k-1}$.
- Trial $k$ must be a success (error appears): probability $p$.

Since trials are **independent**:

$$
P(X=k) = (1-p)^{k-1} \cdot p, \quad k = 1,2,3,\ldots
$$

**Why this form?**
- The factor $(1-p)^{k-1}$ penalizes larger $k$ exponentially: waiting longer is increasingly unlikely.
- Support starts at $k=1$, not $k=0$, because the first success cannot occur before trial 1.

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
