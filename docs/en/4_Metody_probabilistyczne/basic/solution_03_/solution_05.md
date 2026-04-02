# Task 5 - Multinomial Model (Categories of Outcomes)

## Problem Statement

A die is rolled 5 times. Outcomes are grouped into categories: small (1-2), medium (3-4), large (5-6), each with probability $1/3$. Define the experiment, sample space, multinomial distribution, and parameter interpretation.

## Definitions / Theory

For $n$ independent trials and $m$ categories with probabilities $p_1,\ldots,p_m$, counts $(X_1,\ldots,X_m)$ follow a multinomial distribution:

$$
P(X_1=x_1,\ldots,X_m=x_m)
=
\frac{n!}{x_1!\cdots x_m!}p_1^{x_1}\cdots p_m^{x_m}
$$

with constraints:

$$
x_i \in \{0,1,2,\ldots\}, \quad \sum_{i=1}^m x_i = n
$$

## Step-by-Step Solution

Random experiment: perform 5 independent die rolls and classify each roll into one of three categories.

Let:

- $X_1$ = number of small outcomes,
- $X_2$ = number of medium outcomes,
- $X_3$ = number of large outcomes.

Then:

$$
X_1 + X_2 + X_3 = 5
$$

Sample space can be represented by all count triples:

$$
\Omega = \{(x_1,x_2,x_3) \in \mathbb{Z}_{\ge 0}^3 : x_1+x_2+x_3=5\}
$$

Model parameters:

$$
n=5, \quad (p_1,p_2,p_3)=\left(\frac{1}{3},\frac{1}{3},\frac{1}{3}\right)
$$

Hence:

$$
P(X_1=x_1,X_2=x_2,X_3=x_3)
=
\frac{5!}{x_1!x_2!x_3!}
\left(\frac{1}{3}\right)^{x_1}
\left(\frac{1}{3}\right)^{x_2}
\left(\frac{1}{3}\right)^{x_3}
$$

which simplifies to:

$$
P(X_1=x_1,X_2=x_2,X_3=x_3)
=
\frac{5!}{x_1!x_2!x_3!}\left(\frac{1}{3}\right)^5
$$

## Final Result

The vector of counts follows:

$$
(X_1,X_2,X_3) \sim \mathrm{Multinomial}\left(5;\frac{1}{3},\frac{1}{3},\frac{1}{3}\right)
$$

## Interpretation / Sanity Check

Each trial contributes exactly to one category, so counts must sum to 5. Symmetry of equal probabilities implies no category is preferred.

## Common Mistakes

- Forgetting constraint $x_1+x_2+x_3=5$.
- Treating category counts as independent random variables.
- Using binomial coefficient instead of multinomial coefficient.
