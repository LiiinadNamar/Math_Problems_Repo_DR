# Task 1 - Binomial Model (Quality Control)

## Problem Statement

In a sequence of three independent inspections, each screw is either good or defective. The probability of a defective screw is $p$ in every trial. The model must be formalized by defining the experiment, sample space, probabilities of elementary outcomes, and the notion of success.

## Definitions / Theory

The binomial setting uses independent Bernoulli trials with two outcomes.

- Defective with probability $p$.
- Good with probability $1-p$.

For $n$ trials, an elementary sequence with $k$ defects has probability:

$$
p^k (1-p)^{n-k}
$$

In this task, $n = 3$.

## Step-by-Step Solution

1. Random experiment: inspect 3 consecutive screws.

2. Sample space (ordered outcomes):

$$
\Omega = \{GGG, GGD, GDG, DGG, GDD, DGD, DDG, DDD\}
$$

Here, $D$ means defective and $G$ means good.

3. Probabilities of elementary outcomes:

$$
\begin{aligned}
P(GGG) &= (1-p)^3 \\
P(GGD) = P(GDG) = P(DGG) &= p(1-p)^2 \\
P(GDD) = P(DGD) = P(DDG) &= p^2(1-p) \\
P(DDD) &= p^3
\end{aligned}
$$

4. Success definition: a success is observing a defective screw (event $D$ in a single trial).

## Final Result

The experiment is a 3-trial Bernoulli scheme with success probability $p$, sample space of 8 ordered sequences, and outcome probabilities determined by the number of defective screws in each sequence.

## Interpretation / Sanity Check

All probabilities are nonnegative. Their sum equals:

$$
(1-p)^3 + 3p(1-p)^2 + 3p^2(1-p) + p^3 = (p + 1 - p)^3 = 1
$$

So the model is consistent.

## Common Mistakes

- Treating order as irrelevant when listing elementary outcomes.
- Defining success as a good screw instead of a defective one after introducing $p$ as defect probability.
- Assigning the same probability to all 8 sequences when $p \neq \frac{1}{2}$.
