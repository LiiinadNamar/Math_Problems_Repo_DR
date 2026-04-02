# Task 4 - Poisson Model (Arrival of Events)

## Problem Statement

A web service receives on average 3 error reports per hour. The number of reports in a fixed one-hour interval is modeled by a Poisson distribution. Define the experiment, sample space, distribution formula, and interpret parameter $\lambda$.

## Definitions / Theory

For a Poisson random variable $X$ with parameter $\lambda > 0$:

$$
P(X=k) = \frac{e^{-\lambda}\lambda^k}{k!}, \quad k=0,1,2,\ldots
$$

The parameter $\lambda$ is both:

- expected number of events in the interval,
- variance of the number of events.

## Step-by-Step Solution

### Define the Experiment

We count the **number of error reports received in a one-hour interval**. The service center operates continuously, and reports arrive unpredictably throughout the hour.

### Construct the Sample Space

$$
\Omega = \{0,1,2,\ldots\}
$$

Why can the count be 0? Because it's possible (although perhaps unlikely) that no requests arrive in that hour.  
Why is there no upper bound? Because theoretically, any number of requests could arrive in one hour.

### Identify the Model Parameter

The problem states "on average 3 error reports per hour."

In a Poisson model, this **mean** is the parameter $\lambda$:

$$
\lambda = 3
$$

**Why?** The Poisson distribution naturally models the number of events in a fixed time interval when:
- Events occur randomly and independently.
- The average rate is constant (here, 3 per hour).
- We are interested in counting events, not time between events.

### Write the Probability Distribution

For one hour ($\lambda = 3$):

$$
P(X=k) = \frac{e^{-3} \cdot 3^k}{k!}, \quad k=0,1,2,\ldots
$$

**Why this formula?**
- The numerator $e^{-\lambda} \lambda^k$ encodes the rate and count.
- The denominator $k!$ accounts for the number of ways $k$ events can occur in a continuous interval.
- $e^{-3}$ is a normalizing constant ensuring the probabilities sum to 1.

## Final Result

The number of reports in one hour follows:

$$
X \sim \mathrm{Poisson}(3)
$$

with support $\{0,1,2,\ldots\}$.

## Interpretation / Sanity Check

The model predicts mean count 3 per hour. Values around 2-4 should be the most likely, while very large counts should be increasingly rare.

## Common Mistakes

- Treating $\lambda$ as probability.
- Using support starting at 1 instead of 0.
- Forgetting factorial in the denominator.
