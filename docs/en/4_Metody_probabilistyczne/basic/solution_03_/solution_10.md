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

Apply multinomial formula:

$$
P = \frac{6!}{3!2!1!}(0.40)^3(0.35)^2(0.25)^1
$$

Compute coefficient:

$$
\frac{6!}{3!2!1!}=\frac{720}{6 \cdot 2}=60
$$

Compute product of probabilities:

$$
(0.40)^3(0.35)^2(0.25)=0.064 \cdot 0.1225 \cdot 0.25=0.00196
$$

Therefore:

$$
P=60 \cdot 0.00196=0.1176
$$

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
