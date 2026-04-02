# Task 10 - Multinomial Model

## Problem Statement

Candy flavors have probabilities:

- strawberry $0.40$,
- lemon $0.35$,
- mint $0.25$.

There are 6 independent selections with replacement. Compute probability of obtaining exactly:

- 3 strawberry,
- 2 lemon,
- 1 mint.

## Definitions / Theory

For counts $(X_1,X_2,X_3)$ in a multinomial model:

$$
P(X_1=x_1,X_2=x_2,X_3=x_3)
=
\frac{n!}{x_1!x_2!x_3!}p_1^{x_1}p_2^{x_2}p_3^{x_3}
$$

with $x_1+x_2+x_3=n$.

## Step-by-Step Solution

Given:

$$
n=6, \quad (x_1,x_2,x_3)=(3,2,1)
$$

$$
(p_1,p_2,p_3)=(0.40,0.35,0.25)
$$

### Apply the Multinomial Formula

For the desired outcome $(x_1, x_2, x_3) = (3, 2, 1)$ with $n=6$ selections:

$$
P(3\text{ strawberry}, 2\text{ lemon}, 1\text{ mint}) = \frac{6!}{3!\cdot 2!\cdot 1!} \cdot (0.40)^3 \cdot (0.35)^2 \cdot (0.25)^1
$$

### Compute the Multinomial Coefficient

$$
\frac{6!}{3!\cdot 2!\cdot 1!} = \frac{720}{6 \times 2 \times 1} = \frac{720}{12} = 60
$$

**Why this number?** It counts all the **orderings** of 6 selections that result in exactly 3 strawberry, 2 lemon, 1 mint. For example:
- (S, S, S, L, L, M)
- (S, S, L, S, L, M)
- (L, L, S, S, M, S)
- ... and 57 more distinct sequences.

Each ordering has the same probability (since selections are independent with the same probabilities), so we multiply the count by that probability.

### Compute the Probability of One Specific Sequence

$$
(0.40)^3 \times (0.35)^2 \times (0.25)^1
$$

**Why?** One particular sequence, say (S, S, S, L, L, M), has:
- 3 strawberry selections at probability 0.40 each: $(0.40)^3 = 0.064$.
- 2 lemon selections at probability 0.35 each: $(0.35)^2 = 0.1225$.
- 1 mint selection at probability 0.25 each: $(0.25)^1 = 0.25$.
- By independence: $0.064 \times 0.1225 \times 0.25 = 0.00196$.

### Combine

$$
P = 60 \times 0.00196 = 0.1176 \approx 11.76\%
$$

**Interpretation:** Among all ways to select 6 candies, about 11.8% will yield exactly 3 strawberry, 2 lemon, 1 mint. This is a moderate probability — not the most likely outcome, but plausible. The expected counts are $(6 \times 0.40, 6 \times 0.35, 6 \times 0.25) = (2.4, 2.1, 1.5)$, so our outcome (3, 2, 1) is close to the mode and has decent probability.

## Final Result

$$
P(3\text{ strawberry},2\text{ lemon},1\text{ mint})=0.1176
$$

## Interpretation / Sanity Check

The result is between 0 and 1 and reflects one specific composition among many possible flavor count combinations.

## Common Mistakes

- Using binomial coefficient instead of multinomial coefficient.
- Forgetting one factor in $p_1^{x_1}p_2^{x_2}p_3^{x_3}$.
- Using counts that do not sum to 6.
