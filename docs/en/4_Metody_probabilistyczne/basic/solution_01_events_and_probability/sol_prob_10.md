# Task 10 — Events and Probabilities in Buffon's Needle Experiment

## Problem Statement

Using the sample space from Task 5, compute the probabilities of the specified events.
Assume $L \leq d$. Let $X \in [0, \frac{d}{2}]$ be the distance from the needle's centre to the nearest line and $\theta \in [0, \frac{\pi}{2}]$ the angle between the needle and the lines. Assume $X$ and $\theta$ are independent and uniformly distributed.

---

## Definitions / Theory

**Geometric probability**: for a uniform distribution over a region $\Omega$, the probability of an event $A$ is:

$$
P(A) = \frac{\text{Area}(A)}{\text{Area}(\Omega)}
$$

**Sample space**:

$$
\Omega = \left[0,\ \frac{d}{2}\right] \times \left[0,\ \frac{\pi}{2}\right], \quad \text{Area}(\Omega) = \frac{d}{2} \cdot \frac{\pi}{2} = \frac{\pi d}{4}
$$

**Intersection condition**: the needle intersects a line if and only if:

$$
x \leq \frac{L}{2} \sin\theta
$$

---

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
