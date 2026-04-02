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

### Define the Experiment and Variables

**Experiment:** Roll a die 5 times independently.  
**Classification:** Group each outcome into a category:
- Small: {1, 2} with probability $p_1 = 1/3$.
- Medium: {3, 4} with probability $p_2 = 1/3$.
- Large: {5, 6} with probability $p_3 = 1/3$.

Define counts:
- $X_1$ = number of rolls landing in the small category.
- $X_2$ = number of rolls landing in the medium category.
- $X_3$ = number of rolls landing in the large category.

### Identify Constraints

Since each roll contributes to exactly **one** category, the counts must sum to the total number of trials:

$$
X_1 + X_2 + X_3 = 5
$$

This is a **hard constraint** — not all triples $(x_1, x_2, x_3)$ are valid; only those summing to 5.

### Construct the Sample Space

The sample space consists of all valid count triples:

$$
\Omega = \{(x_1,x_2,x_3) \in \mathbb{Z}_{\ge 0}^3 : x_1+x_2+x_3=5\}
$$

For example: $(5,0,0)$ (all small), $(2,2,1)$ (2 small, 2 medium, 1 large), etc.

### Compute the Probability Distribution

For a given triple $(x_1, x_2, x_3)$:

$$
P(X_1=x_1,X_2=x_2,X_3=x_3)
=
\frac{5!}{x_1!x_2!x_3!}
\left(\frac{1}{3}\right)^{x_1}
\left(\frac{1}{3}\right)^{x_2}
\left(\frac{1}{3}\right)^{x_3}
=
\frac{5!}{x_1!x_2!x_3!}\left(\frac{1}{3}\right)^5
$$

**Why this formula?**
- $\frac{5!}{x_1!x_2!x_3!}$ = multinomial coefficient. It counts the **number of orderings** of 5 rolls that yield exactly $x_1$ small, $x_2$ medium, $x_3$ large outcomes. For instance, to get 2 small, 2 medium, 1 large, there are $\frac{5!}{2!\cdot 2!\cdot 1!} = 30$ different sequences.
- $\left(\frac{1}{3}\right)^{x_1} \left(\frac{1}{3}\right)^{x_2} \left(\frac{1}{3}\right)^{x_3}$ = probability of **any single ordered sequence** with that composition. Since each category has probability $1/3$ and rolls are independent.
- Together: (number of sequences) × (probability per sequence) = total probability.

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
