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

Random experiment: count the number of error reports in one hour.

Sample space:

$$
\Omega = \{0,1,2,\ldots\}
$$

Given average is 3 reports per hour, parameter value is:

$$
\lambda = 3
$$

Distribution for one hour:

$$
P(X=k) = \frac{e^{-3}3^k}{k!}, \quad k=0,1,2,\ldots
$$

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
