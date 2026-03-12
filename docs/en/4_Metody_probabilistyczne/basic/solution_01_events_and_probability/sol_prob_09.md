# Task 9 — Events and Probabilities in Weekly Weather Observation

## Problem Statement

Using the sample space $\Omega_7$ from Task 4, compute the probabilities of specified events. Each day is independently Sunny ($S$), Cloudy ($C$), or Rainy ($R$) with probability $\frac{1}{3}$ each.

---

## Definitions / Theory

## 1. Sample Space $\Omega_7$

We observe the weather over **7 consecutive days** (Monday through Sunday). Each day takes exactly one of three possible states:

$$S \text{ (Sunny)}, \quad C \text{ (Cloudy)}, \quad R \text{ (Rainy)}$$

A single **elementary outcome** is a specific sequence of weather states for the entire week, for example:

$$\omega = (S,\ C,\ S,\ R,\ R,\ C,\ S)$$

The full collection of all such sequences is called the **sample space**:

$$\Omega_7 = \{\,(w_1, w_2, \ldots, w_7) \mid w_i \in \{S, C, R\}\,\}$$

The total number of elementary outcomes is $|\Omega_7| = 3^7 = 2187$.

---

## 2. Independence of Days

The days are assumed to be **mutually independent** — this is the central modelling assumption. It means that the weather on any one day **has no influence** on the weather on any other day.

Formally, for independent events $A_1, A_2, \ldots, A_n$ the following holds:

$$P(A_1 \cap A_2 \cap \cdots \cap A_n) = P(A_1) \cdot P(A_2) \cdots P(A_n)$$

This is exactly why the probability of any **specific sequence** is computed as the product of the individual daily probabilities:

$$P\bigl((w_1, w_2, \ldots, w_7)\bigr)
= P(w_1) \cdot P(w_2) \cdots P(w_7)
= \underbrace{\frac{1}{3} \cdot \frac{1}{3} \cdots \frac{1}{3}}_{7 \text{ times}}
= \left(\frac{1}{3}\right)^7
= \frac{1}{2187}$$

Because every one of the $2187$ outcomes is equally likely, the model is called a **uniform probability model**.

---

## 3. Probability of an Event with Fixed Days

Suppose an event $A$ imposes conditions on exactly $k$ specific days, while the remaining $7 - k$ days are left completely free (any state is allowed).

**Counting logic:**

- Each of the $k$ fixed days contributes a factor of $\left(\dfrac{1}{3}\right)$
- Each of the $7 - k$ free days may be in any of the 3 states, contributing a factor of $1$ (i.e. certainty)

$$\boxed{P(A) = \left(\frac{1}{3}\right)^k \times 1^{7-k} = \left(\frac{1}{3}\right)^k}$$

**Example:** the event "Saturday and Sunday are both Sunny" fixes $k = 2$ days:

$$P = \left(\frac{1}{3}\right)^2 = \frac{1}{9}$$

Alternatively: out of $2187$ total outcomes, exactly $3^5 = 243$ have $S$ in positions 6 and 7, so:

$$P = \frac{243}{2187} = \frac{1}{9} \checkmark$$

---

## 4. The Complement Rule

For any event $A$ and its **complement** $A^c$ (the event "$A$ did not occur"):

$$P(A) + P(A^c) = 1 \implies \boxed{P(A) = 1 - P(A^c)}$$

This rule is especially powerful for events of the form **"at least one …"**, because:

> Counting "at least one Sunny day" directly is cumbersome — there are many favourable sequences.  
> Its complement — "no Sunny day at all" — is straightforward to compute.

$$P(\text{at least one } S) = 1 - P(\text{no } S) = 1 - \left(\frac{2}{3}\right)^7$$

Here $\dfrac{2}{3}$ is the probability that a single day is **not** Sunny (i.e. it is $C$ or $R$). Since the days are independent, the probability of avoiding $S$ every day is $\left(\dfrac{2}{3}\right)^7$.

---

## 5. Binomial Probability (Bernoulli Formula)

Used when we want the probability that **exactly $m$ out of $n$ days** are in a given state (e.g. exactly 2 of 7 days are Sunny).

$$\boxed{P = \binom{n}{m} \cdot p^m \cdot (1-p)^{n-m}}$$

Each factor has a clear meaning:

| Factor | Meaning |
|---|---|
| $\binom{n}{m} = \dfrac{n!}{m!\,(n-m)!}$ | Number of ways to **choose** which $m$ days will be in the given state |
| $p^m$ | Probability that those $m$ chosen days **are** in the given state |
| $(1-p)^{n-m}$ | Probability that the remaining $n-m$ days are **not** in the given state |

**Example** — exactly 2 Sunny days out of 7, with $p = \dfrac{1}{3}$:

$$P = \underbrace{\binom{7}{2}}_{21 \text{ combinations}}
\cdot \underbrace{\left(\frac{1}{3}\right)^2}_{2 \text{ sunny days}}
\cdot \underbrace{\left(\frac{2}{3}\right)^5}_{5 \text{ non-sunny days}}
= 21 \cdot \frac{1}{9} \cdot \frac{32}{243}
= \frac{672}{2187}
= \frac{224}{729}$$

---

## Summary of Tools

| Situation | Formula to use |
|---|---|
| Probability of one specific sequence | $\left(\frac{1}{3}\right)^7$ |
| Event fixes $k$ days, rest are free | $\left(\frac{1}{3}\right)^k$ |
| "At least one" or "none" | Complement rule: $1 - P(A^c)$ |
| Exactly $m$ out of $n$ days in a state | Binomial: $\binom{n}{m}p^m(1-p)^{n-m}$ |

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

