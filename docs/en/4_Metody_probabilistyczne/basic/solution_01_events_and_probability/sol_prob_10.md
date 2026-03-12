# Task 10 — Events and Probabilities in Buffon's Needle Experiment

## Problem Statement

Using the sample space from Task 5, compute the probabilities of the specified events.
Assume $L \leq d$. Let $X \in [0, \frac{d}{2}]$ be the distance from the needle's centre to the nearest line and $\theta \in [0, \frac{\pi}{2}]$ the angle between the needle and the lines. Assume $X$ and $\theta$ are independent and uniformly distributed.

---

## Definitions / Theory

## 1. The Setup: What Are We Measuring?

A needle of length $L$ is dropped randomly onto a floor ruled with parallel lines spaced $d$ apart, where $L \leq d$.

We need exactly **two numbers** to fully describe where the needle lands:

| Variable | Meaning | Range |
|---|---|---|
| $X$ | Distance from the needle's **centre** to the nearest line | $\left[0,\ \dfrac{d}{2}\right]$ |
| $\theta$ | **Angle** between the needle and the direction of the lines | $\left[0,\ \dfrac{\pi}{2}\right]$ |

> **Why $\frac{d}{2}$ and $\frac{\pi}{2}$?**
>
> - The nearest line is at most $\frac{d}{2}$ away (the midpoint between two adjacent lines), so $X$ never exceeds $\frac{d}{2}$.
> - By symmetry, angles in $\left[\frac{\pi}{2}, \pi\right]$ mirror those in $\left[0, \frac{\pi}{2}\right]$ (a needle pointing at $120°$ behaves identically to one at $60°$), so we only need $\theta \in \left[0, \frac{\pi}{2}\right]$.

---

## 2. The Sample Space $\Omega$

Since every pair $(x, \theta)$ uniquely describes one outcome of the experiment, the sample space is the **rectangle**:

$$\Omega = \left[0,\ \frac{d}{2}\right] \times \left[0,\ \frac{\pi}{2}\right]$$

Its area is:

$$\text{Area}(\Omega) = \frac{d}{2} \cdot \frac{\pi}{2} = \frac{\pi d}{4}$$

Each point $(x, \theta)$ in this rectangle is a possible outcome of the needle drop.

---

## 3. Uniform Distribution and Independence

Both variables are assumed to be **uniformly distributed** and **independent**. This means:

- Every value of $X$ in $\left[0, \frac{d}{2}\right]$ is equally likely — the needle is equally likely to land close to a line as far from one.
- Every value of $\theta$ in $\left[0, \frac{\pi}{2}\right]$ is equally likely — the needle has no preferred orientation.
- The two variables do **not** influence each other — knowing the angle tells you nothing about the distance, and vice versa.

The **joint density** of $(X, \theta)$ is therefore constant across $\Omega$:

$$f(x, \theta) = \frac{1}{\text{Area}(\Omega)} = \frac{4}{\pi d}$$

This is the formal meaning of "uniform distribution over $\Omega$."

---

## 4. Geometric Probability

Because the distribution is uniform, the probability of any event $A$ (a subset of $\Omega$) equals the **fraction of the rectangle's area** that $A$ occupies:

$$\boxed{P(A) = \frac{\text{Area}(A)}{\text{Area}(\Omega)}}$$

This is called **geometric probability**. The key insight is:

> Probability = Area, because every equally-sized region is equally likely.

**Example:** if event $A$ covers exactly half the rectangle, then $P(A) = \frac{1}{2}$, regardless of which half.

For one-dimensional events (constraints on $X$ alone or $\theta$ alone), "area" reduces to a **length ratio**:

$$P(\theta < \theta_0) = \frac{\theta_0}{\pi/2}, \qquad P(X < x_0) = \frac{x_0}{d/2}$$

---

## 5. The Intersection Condition

The geometric key to the whole problem: **when does the needle cross a line?**

The needle has half-length $\frac{L}{2}$. Its centre is at distance $X$ from the nearest line. The needle is tilted at angle $\theta$ relative to the lines.

The **perpendicular projection** of the half-needle onto the axis crossing the lines has length:

$$\frac{L}{2}\sin\theta$$

The needle **intersects** the nearest line if and only if this projection reaches the line, i.e.:

$$\boxed{X \leq \frac{L}{2}\sin\theta}$$

**Why $\sin\theta$ and not $\cos\theta$?**

- $\theta$ is the angle between the needle and the **lines themselves** (not the perpendicular to the lines).
- The component of the needle **perpendicular to the lines** is $\frac{L}{2}\sin\theta$.
- When $\theta = 0$ (needle parallel to lines): $\sin 0 = 0$, so the needle never crosses — correct.
- When $\theta = \frac{\pi}{2}$ (needle perpendicular to lines): $\sin\frac{\pi}{2} = 1$, maximising the chance of crossing — correct.

---

## 6. Computing Probabilities via Integration

For events defined by the intersection condition, the favourable region is **not** a simple rectangle, so we compute its area by integration.

**General formula** for an event of the form $\left\{X \leq \frac{L}{2}\sin\theta,\ \theta \in [\theta_1, \theta_2]\right\}$:

$$\text{Area}(R) = \int_{\theta_1}^{\theta_2} \frac{L}{2}\sin\theta \, d\theta$$

This integral sweeps over each angle $\theta$ and measures how wide the favourable $x$-strip is at that angle (from $0$ to $\frac{L}{2}\sin\theta$).

The antiderivative of $\sin\theta$ is $-\cos\theta$, so:

$$\int_{\theta_1}^{\theta_2} \sin\theta \, d\theta = \Big[-\cos\theta\Big]_{\theta_1}^{\theta_2} = \cos\theta_1 - \cos\theta_2$$

Then:

$$P = \frac{\text{Area}(R)}{\text{Area}(\Omega)} = \frac{\displaystyle\frac{L}{2}(\cos\theta_1 - \cos\theta_2)}{\dfrac{\pi d}{4}} = \frac{2L(\cos\theta_1 - \cos\theta_2)}{\pi d}$$

For the full range $\theta_1 = 0$, $\theta_2 = \frac{\pi}{2}$:

$$P(A) = \frac{2L(\cos 0 - \cos\frac{\pi}{2})}{\pi d} = \frac{2L(1 - 0)}{\pi d} = \frac{2L}{\pi d}$$

---

## 7. The Complement Rule

As in any probability model:

$$P(A^c) = 1 - P(A)$$

For example, the probability of **not** crossing a line is simply:

$$P(B) = 1 - \frac{2L}{\pi d}$$

---

## Summary of Tools

| Situation | Formula |
|---|---|
| Probability of any event in $\Omega$ | $P(A) = \dfrac{\text{Area}(A)}{\text{Area}(\Omega)}$ |
| Constraint on $\theta$ only | $P(\theta \in [\theta_1, \theta_2]) = \dfrac{\theta_2 - \theta_1}{\pi/2}$ |
| Constraint on $X$ only | $P(X \leq x_0) = \dfrac{x_0}{d/2}$ |
| Intersection over angle range $[\theta_1, \theta_2]$ | $\dfrac{L}{2}\displaystyle\int_{\theta_1}^{\theta_2}\sin\theta\,d\theta \div \dfrac{\pi d}{4}$ |
| Complement | $P(A^c) = 1 - P(A)$ |

## Step-by-Step Solution

### Event $A$ — the needle intersects one of the lines

The favourable region is:

$$
R_A = \left\{(x, \theta) : 0 \leq x \leq \frac{L}{2}\sin\theta,\ \theta \in \left[0, \frac{\pi}{2}\right]\right\}
$$

$$
\text{Area}(R_A) = \int_0^{\pi/2} \frac{L}{2} \sin\theta \, d\theta = \frac{L}{2} \Big[-\cos\theta\Big]_0^{\pi/2} = \frac{L}{2}(0+1) = \frac{L}{2}
$$

$$
P(A) = \frac{L/2}{\pi d/4} = \frac{2L}{\pi d}
$$

This is the classical Buffon formula.

---

### Event $B$ — the needle does not intersect any line

$$
P(B) = 1 - P(A) = 1 - \frac{2L}{\pi d}
$$

---

### Event $C$ — the angle is smaller than $\frac{\pi}{6}$

Since $\theta$ is uniform on $\left[0, \frac{\pi}{2}\right]$:

$$
P(C) = \frac{\pi/6}{\pi/2} = \frac{1}{3}
$$

---

### Event $D$ — the centre falls at distance less than $\frac{d}{4}$ from the nearest line

Since $x$ is uniform on $\left[0, \frac{d}{2}\right]$:

$$
P(D) = \frac{d/4}{d/2} = \frac{1}{2}
$$

---

### Event $E$ — the needle intersects a line and the angle is greater than $\frac{\pi}{4}$

The conditions are $x \leq \frac{L}{2}\sin\theta$ and $\theta > \frac{\pi}{4}$:

$$
\text{Area}(R_E) = \int_{\pi/4}^{\pi/2} \frac{L}{2} \sin\theta \, d\theta = \frac{L}{2}\Big[-\cos\theta\Big]_{\pi/4}^{\pi/2} = \frac{L}{2}\left(0 + \frac{\sqrt{2}}{2}\right) = \frac{L\sqrt{2}}{4}
$$

$$
P(E) = \frac{L\sqrt{2}/4}{\pi d/4} = \frac{L\sqrt{2}}{\pi d}
$$

---

### Additional Event

**Event $F$** — the angle is greater than $\frac{\pi}{3}$:

$$
P(F) = \frac{\pi/2 - \pi/3}{\pi/2} = \frac{\pi/6}{\pi/2} = \frac{1}{3}
$$

---

## Final Result

| Event | Description | Probability |
|---|---|---|
| $A$ | Needle intersects a line | $\dfrac{2L}{\pi d}$ |
| $B$ | Needle does not intersect | $1 - \dfrac{2L}{\pi d}$ |
| $C$ | Angle less than $\frac{\pi}{6}$ | $\dfrac{1}{3}$ |
| $D$ | Centre within $\frac{d}{4}$ of nearest line | $\dfrac{1}{2}$ |
| $E$ | Intersects and angle greater than $\frac{\pi}{4}$ | $\dfrac{L\sqrt{2}}{\pi d}$ |
| $F$ | Angle greater than $\frac{\pi}{3}$ | $\dfrac{1}{3}$ |

---

## Interpretation / Sanity Check

The result $P(A) = \frac{2L}{\pi d}$ allows estimation of $\pi$:

$$
\pi \approx \frac{2L}{d \cdot P(A)}
$$

For $L = d$: $P(A) = \frac{2}{\pi} \approx 0.637$. Since $L \leq d$, we have $P(A) \leq \frac{2}{\pi} < 1$.

Events $C$ and $F$ both have probability $\frac{1}{3}$ by symmetry of the uniform distribution on $[0, \frac{\pi}{2}]$.

---

## Common Mistakes

- Using $\cos\theta$ instead of $\sin\theta$ in the intersection condition. The angle $\theta$ is measured from the direction of the lines, so the perpendicular projection of the half-needle is $\frac{L}{2}\sin\theta$.
- Forgetting to divide by $\text{Area}(\Omega)$ when computing geometric probability.
- Treating $x$ and $\theta$ as dependent. They are independent by assumption.

