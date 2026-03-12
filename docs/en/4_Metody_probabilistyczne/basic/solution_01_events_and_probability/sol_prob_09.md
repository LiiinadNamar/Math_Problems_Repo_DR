# Task 9 — Events and Probabilities in Weekly Weather Observation

## Problem Statement

Using the sample space $\Omega_7$ from Task 4, compute the probabilities of specified events. Each day is independently Sunny ($S$), Cloudy ($C$), or Rainy ($R$) with probability $\frac{1}{3}$ each.

---

## Definitions / Theory

**Independent days**: the weather on each day does not affect the others. The probability of any specific sequence of seven states is:

$$
P((w_1, w_2, \ldots, w_7)) = \left(\frac{1}{3}\right)^7 = \frac{1}{2187}
$$

**Probability of an event** defined by conditions on specific days:

If an event constrains $k$ specific days to fixed states and leaves the remaining $7 - k$ days free, then:

$$
P(A) = \left(\frac{1}{3}\right)^k \times 1^{7-k} = \left(\frac{1}{3}\right)^k
$$

**Complement rule**: $P(A^c) = 1 - P(A)$.

**Binomial probability**: the probability that exactly $m$ out of $n$ independent days are in a given state with probability $p$:

$$
P = \binom{n}{m} p^m (1-p)^{n-m}
$$

---

## Step-by-Step Solution

Label the days: Monday = day 1, Tuesday = day 2, ..., Sunday = day 7. Saturday = day 6, Sunday = day 7.

**Event $A$** — the entire weekend is sunny (Saturday and Sunday are both $S$):

The two weekend days are fixed to $S$; the five weekdays are free.

$$
P(A) = \left(\frac{1}{3}\right)^2 = \frac{1}{9}
$$

**Event $B$** — Wednesday, Thursday, and Friday are all rainy (days 3, 4, 5 are $R$):

Three days are fixed to $R$; four days are free.

$$
P(B) = \left(\frac{1}{3}\right)^3 = \frac{1}{27}
$$

**Event $C$** — at least one day during the week is sunny:

Use the complement. The probability that no day is sunny equals the probability that every day is either $C$ or $R$:

$$
P(C^c) = \left(\frac{2}{3}\right)^7 = \frac{128}{2187}
$$

$$
P(C) = 1 - \frac{128}{2187} = \frac{2059}{2187}
$$

**Event $D$** — no rainy day occurs during the entire week:

Every day must be $S$ or $C$, probability $\frac{2}{3}$ each day:

$$
P(D) = \left(\frac{2}{3}\right)^7 = \frac{128}{2187}
$$

**Event $E$** — exactly two days during the week are sunny:

This is a binomial probability with $n = 7$, $m = 2$, $p = \frac{1}{3}$:

$$
P(E) = \binom{7}{2} \left(\frac{1}{3}\right)^2 \left(\frac{2}{3}\right)^5
= 21 \times \frac{1}{9} \times \frac{32}{243}
= \frac{672}{2187}
= \frac{224}{729}
$$

---

### Additional Event on $\Omega_7$

**Event $F$** — all seven days have the same weather state:

$$
F = \{(S,S,S,S,S,S,S),\ (C,C,C,C,C,C,C),\ (R,R,R,R,R,R,R)\}
$$

$$
P(F) = 3 \times \left(\frac{1}{3}\right)^7 = \frac{3}{2187} = \frac{1}{729}
$$

---

## Final Result

| Event | Description | Probability |
|---|---|---|
| $A$ | Entire weekend sunny | $\frac{1}{9}$ |
| $B$ | Wed, Thu, Fri all rainy | $\frac{1}{27}$ |
| $C$ | At least one sunny day | $\frac{2059}{2187}$ |
| $D$ | No rainy day | $\frac{128}{2187}$ |
| $E$ | Exactly two sunny days | $\frac{224}{729}$ |
| $F$ | All seven days identical | $\frac{1}{729}$ |

---

## Interpretation / Sanity Check

Event $C$ (at least one sunny day) has a very high probability $\approx 0.941$, which is expected: the chance of going an entire week with no sun is only $\left(\frac{2}{3}\right)^7 \approx 0.059$.

Events $C$ and $D$ have complementary structure but are not complementary to each other. $D$ is the event of no rain (not no sun), so $P(C) + P(D) \neq 1$.

For event $E$, a quick check: the expected number of sunny days is $7 \times \frac{1}{3} \approx 2.33$, so exactly 2 sunny days is close to the expected value and $\frac{224}{729} \approx 0.307$ is a reasonable probability.

---

## Common Mistakes

- Confusing "no rainy day" with "all days sunny." No rain means each day is $S$ or $C$, not necessarily $S$.
- Forgetting to use the complement for "at least one" events — direct counting is error-prone.
- In event $E$, using $\left(\frac{1}{3}\right)^2 \left(\frac{2}{3}\right)^5$ without the binomial coefficient $\binom{7}{2}$, which accounts for the different positions of the two sunny days.
