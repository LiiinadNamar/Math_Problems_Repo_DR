# Task 5 — Buffon's Needle Experiment

## Problem Statement

A needle of length $L$ is thrown randomly onto a floor with equally spaced parallel lines.
The distance between neighbouring lines is $d$.
Describe the sample space, identify the parameters that determine the outcome, and explain why the sample space is continuous.

---

## Definitions / Theory

**Buffon's Needle** is a classical problem in geometric probability, first posed by Georges-Louis Leclerc, Comte de Buffon, in 1777.

A **continuous sample space** is one in which the set of possible outcomes forms a continuum — an interval or region of real numbers — rather than a finite or countably infinite set.

**Uniform distribution** on an interval $[a, b]$ means every subinterval of the same length has the same probability. The probability of an outcome falling in $[c, d] \subseteq [a, b]$ is:

$$
P([c,d]) = \frac{d - c}{b - a}
$$

By symmetry of the problem, it suffices to consider:

- $x \in \left[0, \frac{d}{2}\right]$: distance from the needle's centre to the nearest line,
- $\theta \in \left[0, \frac{\pi}{2}\right]$: acute angle between the needle and the lines.

---

## Step-by-Step Solution

### Parameters Determining the Outcome

A single throw of the needle is completely determined by two quantities:

**1. Position** $x$ — the distance from the centre of the needle to the nearest parallel line.

By symmetry, it suffices to take $x \in \left[0, \frac{d}{2}\right]$.

**2. Orientation** $\theta$ — the angle between the needle and the direction of the parallel lines.

By symmetry, it suffices to take $\theta \in \left[0, \frac{\pi}{2}\right]$.

---

### Elementary Outcome

An elementary outcome is a pair:

$$
\omega = (x,\ \theta)
$$

where $x$ is the distance from the needle's centre to the nearest line and $\theta$ is the orientation angle.

---

### Sample Space

$$
\Omega = \left\{(x, \theta) : x \in \left[0,\ \frac{d}{2}\right],\ \theta \in \left[0,\ \frac{\pi}{2}\right]\right\}
$$

This is a rectangle in the $(x, \theta)$ plane with:

- width $\frac{d}{2}$ along the $x$-axis,
- height $\frac{\pi}{2}$ along the $\theta$-axis.

The area of this rectangle is:

$$
|\Omega| = \frac{d}{2} \cdot \frac{\pi}{2} = \frac{\pi d}{4}
$$

---

### Why the Sample Space Is Continuous

In the previous tasks (coin tossing, die rolling, card drawing, weather observation), the outcome of each step was chosen from a **finite set** of possibilities. The sample space was therefore finite and could be listed explicitly.

In Buffon's experiment, both $x$ and $\theta$ are **real-valued quantities** that can take any value in a continuous interval:

- $x$ can be any real number in $\left[0, \frac{d}{2}\right]$,
- $\theta$ can be any real number in $\left[0, \frac{\pi}{2}\right]$.

Between any two distinct values there are infinitely many other possible values. It is therefore impossible to list all elementary outcomes. The sample space is **uncountably infinite**.

In this setting, individual outcomes have probability zero:

$$
P(\{(x_0, \theta_0)\}) = 0
$$

for any specific pair $(x_0, \theta_0)$. Probability is assigned not to individual points but to **regions** (subsets) of $\Omega$.

---

## Final Result

The sample space of Buffon's needle experiment is:

$$
\Omega = \left[0,\ \frac{d}{2}\right] \times \left[0,\ \frac{\pi}{2}\right]
$$

An elementary outcome is a pair $(x, \theta)$ specifying the position and orientation of the needle after a single throw.

The sample space is continuous because both $x$ and $\theta$ are real-valued and vary over intervals, making the set of possible outcomes uncountably infinite.

---

## Interpretation / Sanity Check

The geometric representation of $\Omega$ as a rectangle is natural: the uniform distribution on $\Omega$ corresponds to a uniform distribution of area over this rectangle. Events correspond to subregions, and their probabilities are proportional to their area relative to the total area $\frac{\pi d}{4}$.

---

## Common Mistakes

- Confusing the angle $\theta \in \left[0, \frac{\pi}{2}\right]$ with a full rotation $\theta \in [0, 2\pi]$. The symmetry of the needle (it has no preferred direction) reduces the range to $\left[0, \frac{\pi}{2}\right]$.
- Treating the sample space as finite by discretising $x$ and $\theta$. This is an approximation, not the exact model.
- Forgetting that in a continuous sample space, probability is computed via integrals (areas), not by counting outcomes.
