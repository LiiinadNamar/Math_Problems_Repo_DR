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

### Step 1: Define the Random Experiment

We inspect 3 consecutive screws. Each inspection is **independent** (outcome of one screw does not affect another) and each screw has the same probability $p$ of being defective. This is the foundation of the binomial model: identical, independent trials with two outcomes.

### Step 2: Construct the Sample Space

Since order matters and each screw can be either $G$ (good) or $D$ (defective), we list all ordered sequences of length 3:

$$
\Omega = \{GGG, GGD, GDG, DGG, GDD, DGD, DDG, DDD\}
$$

There are $2^3 = 8$ outcomes. We use ordered sequences (not just counts) because **elementary outcomes must be atomic and indivisible**. For instance, $(G,G,D)$ and $(G,D,G)$ are different because the position of the defect matters in a real inspection process.

### Step 3: Assign Probabilities to Elementary Outcomes

Since trials are **independent**, the probability of a sequence is the product of individual probabilities:

$$
P(\text{sequence}) = P(\text{1st screw}) \times P(\text{2nd screw}) \times P(\text{3rd screw})
$$

For example:
- $P(GGG) = (1-p) \times (1-p) \times (1-p) = (1-p)^3$ (all three good).
- $P(GGD) = (1-p) \times (1-p) \times p = (1-p)^2 p$ (good, good, defective).
- $P(DDD) = p \times p \times p = p^3$ (all three defective).

Grouping by the number of defects:

$$
\begin{aligned}
P(GGG) &= (1-p)^3 & \text{(0 defects)} \\
P(GGD) = P(GDG) = P(DGG) &= p(1-p)^2 & \text{(1 defect, 3 positions)} \\
P(GDD) = P(DGD) = P(DDG) &= p^2(1-p) & \text{(2 defects, 3 positions)} \\
P(DDD) &= p^3 & \text{(3 defects)}
\end{aligned}
$$

Note: sequences with the same number of defects have **equal probability** because they involve the same product of $p$ and $(1-p)$ factors, just in different orders.

### Step 4: Define Success

In this context, a **success** is observing a defective screw. Why? Because:
- The problem states "probability $p$ that a screw is defective."
- We count defects, not good screws.
- In quality control, "success" of the inspection means identifying a problem (defect).

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
