# Problem 6 — Final Discussion: The Axiomatic Point of View

## Problem Statement

Using everything developed in the previous problems, write a short discussion of the axiomatic formulation of probability. State and comment on the Kolmogorov axioms. Explain which features were already suggested by earlier work with events and observed frequencies, and indicate clearly what goes beyond those finite considerations. In particular, discuss why non-negativity, normalization, and finite additivity appear naturally, and why countable additivity is a more subtle principle not directly obtained from finite experiments.

---

## Definitions / Theory

### The Setting: $\sigma$-algebra and Probability Space

In the finite setting of Problems 1–5, every subset of $\Omega$ was automatically an event. When $\Omega$ is infinite (or uncountable, as in the Buffon needle experiment), not every subset can be assigned a probability in a consistent way. This technical difficulty requires restricting attention to a collection $\mathcal{F}$ of "measurable" subsets.

A **$\sigma$-algebra** on $\Omega$ is a collection $\mathcal{F}$ of subsets of $\Omega$ satisfying:
1. $\Omega \in \mathcal{F}$
2. If $A \in \mathcal{F}$, then $A^c \in \mathcal{F}$
3. If $A_1, A_2, A_3, \ldots \in \mathcal{F}$, then $\bigcup_{n=1}^{\infty} A_n \in \mathcal{F}$

The triple $(\Omega, \mathcal{F}, P)$ is called a **probability space**.

In the finite setting, $\mathcal{F} = 2^{\Omega}$ (all subsets) is always a $\sigma$-algebra, so this distinction did not arise in Problems 1–5.

---

### The Kolmogorov Axioms (1933)

Let $(\Omega, \mathcal{F})$ be a measurable space. A **probability measure** is a function $P : \mathcal{F} \to \mathbb{R}$ satisfying the following three axioms.

**Axiom 1 — Non-negativity:**

$$
P(A) \geq 0 \quad \text{for all } A \in \mathcal{F}
$$

**Axiom 2 — Normalization:**

$$
P(\Omega) = 1
$$

**Axiom 3 — Countable additivity ($\sigma$-additivity):**

For any sequence of pairwise disjoint events $A_1, A_2, A_3, \ldots \in \mathcal{F}$:

$$
P\!\left(\bigcup_{n=1}^{\infty} A_n\right) = \sum_{n=1}^{\infty} P(A_n)
$$

These three axioms are the entire foundation of modern probability theory. Every theorem in the subject — the law of large numbers, the central limit theorem, Bayes' theorem — is derived from these axioms alone, without additional assumptions.

---

## Discussion

### Axiom 1 — Non-negativity: directly suggested by frequencies

In Problem 5, the observed frequency was defined as:

$$
f(A) = \frac{n(A)}{1000}
$$

where $n(A) \geq 0$ always, since it counts a number of throws. Division by 1000 preserves non-negativity. Therefore $f(A) \in [0, 1]$ for every event $A$.

Non-negativity is not a deep conceptual constraint — it simply reflects the fact that frequencies are ratios of non-negative integers. Any function meant to model frequencies must inherit this property. Axiom 1 formalizes it as an unconditional requirement on the abstract function $P$.

The upper bound $P(A) \leq 1$ is not a separate axiom — it follows from Axioms 1 and 2. Since $A \subseteq \Omega$, we have $A$ and $A^c$ disjoint with $A \cup A^c = \Omega$, so by Axioms 2 and 3: $P(A) + P(A^c) = 1$, and by Axiom 1: $P(A^c) \geq 0$, giving $P(A) \leq 1$.

---

### Axiom 2 — Normalization: directly suggested by frequencies

In Part D of Problem 5, it was observed that:

$$
\sum_{k=1}^{6} f(\{k\}) = 1
$$

and more generally:

$$
\sum_{i} f(A_i) = 1
$$

for any partition of $\Omega$ into disjoint events. In particular, $f(\Omega) = 1$ always, because every throw produces some outcome in $\Omega$.

Normalization is the mathematical expression of certainty: the experiment always produces some outcome, and the event "some outcome occurs" has probability 1. The choice of the value 1 (rather than 100, as in percentages) is a convention, but it is the natural one for a ratio.

This axiom, like Axiom 1, is immediately transparent from the frequency interpretation.

---

### Finite Additivity: directly suggested by frequencies

The crucial property discovered in Problem 5, Parts B and C, was:

$$
A \cap B = \emptyset \implies f(A \cup B) = f(A) + f(B)
$$

This held because of the simple counting argument: when $A$ and $B$ share no outcomes, no throw is counted in both $n(A)$ and $n(B)$, so $n(A \cup B) = n(A) + n(B)$.

This property extends by induction to any finite collection of pairwise disjoint events:

$$
A_1, \ldots, A_m \text{ pairwise disjoint} \implies f\!\left(\bigcup_{i=1}^{m} A_i\right) = \sum_{i=1}^{m} f(A_i)
$$

**Finite additivity** is therefore a direct, elementary consequence of the definition of frequency and the logic of counting. It requires no further justification once one understands what $f(A)$ means.

---

### Countable Additivity: the subtle step beyond finite experience

Axiom 3 extends finite additivity to **infinite sequences** of disjoint events. This is the step that genuinely goes beyond what finite experiments can suggest.

**Why finite experiments cannot establish countable additivity:**

In a finite experiment with 1000 throws, there are at most $2^6 = 64$ events. The statement "$f(A \cup B) = f(A) + f(B)$ for disjoint $A, B$" is verified in finitely many cases. But the statement:

$$
P\!\left(\bigcup_{n=1}^{\infty} A_n\right) = \sum_{n=1}^{\infty} P(A_n)
$$

involves an **infinite** union and an **infinite** series. No finite experiment can exhibit infinitely many disjoint events or verify an identity involving an infinite sum.

**Why countable additivity is needed:**

Consider the geometric distribution from Problem Set 3: the sample space is $\Omega = \{1, 2, 3, \ldots\}$, with $P(\{k\}) = (1-p)^{k-1}p$. The event $\Omega$ itself is an infinite disjoint union:

$$
\Omega = \{1\} \cup \{2\} \cup \{3\} \cup \cdots
$$

For $P(\Omega) = 1$ to hold, we need:

$$
\sum_{k=1}^{\infty} P(\{k\}) = \sum_{k=1}^{\infty} (1-p)^{k-1}p = 1
$$

This is precisely Axiom 3 applied to the partition $\{\{k\}\}_{k=1}^{\infty}$. Without Axiom 3, we cannot even verify that a probability distribution on an infinite sample space is well-defined.

**Why finite additivity alone is insufficient:**

There exist functions satisfying Axioms 1, 2, and finite additivity, but **not** countable additivity. Such functions are called finitely additive measures. They are mathematically consistent but they fail to produce a coherent theory of infinite processes. For instance, with only finite additivity one cannot prove:

$$
P\!\left(\bigcup_{n=1}^{\infty} A_n\right) = \lim_{m \to \infty} P\!\left(\bigcup_{n=1}^{m} A_n\right)
$$

This property — **continuity of probability** — is essential for the analysis of sequences of events, limits of random variables, and the law of large numbers. It follows directly from countable additivity but not from finite additivity alone.

**The conceptual leap:**

Finite additivity says: the probability of a finite union of disjoint events equals the finite sum of their probabilities. This is observed in every experiment.

Countable additivity says: the probability of a countably infinite union of disjoint events equals the limit of the partial sums. This is a **topological** property — it says that $P$ is continuous with respect to monotone limits of events. It is an assumption about the behavior of $P$ at infinity, and it cannot be verified empirically.

Kolmogorov's insight was to recognize that this assumption — while not derivable from finite experiments — is the precisely correct one for developing a rich and consistent mathematical theory. It is both the minimal assumption needed to make the theory work and the natural one from the perspective of measure theory.

---

### Summary: What Each Axiom Expresses

| Axiom | Mathematical content | Origin |
|---|---|---|
| Non-negativity | $P(A) \geq 0$ | Frequencies are non-negative ratios |
| Normalization | $P(\Omega) = 1$ | Every experiment produces some outcome |
| Finite additivity | $P(A \cup B) = P(A) + P(B)$ for $A \cap B = \emptyset$ | Counting argument for disjoint events |
| Countable additivity | Extension to infinite disjoint unions | Not derivable from finite experiments; required for continuity and infinite sample spaces |

---

## Final Result

The axiomatic formulation of probability, as given by Kolmogorov in 1933, is organized as follows. A probability space consists of a sample space $\Omega$, a $\sigma$-algebra $\mathcal{F}$ of events, and a function $P : \mathcal{F} \to [0,1]$ satisfying:

$$
P(A) \geq 0, \qquad P(\Omega) = 1, \qquad P\!\left(\bigsqcup_{n=1}^{\infty} A_n\right) = \sum_{n=1}^{\infty} P(A_n)
$$

Non-negativity and normalization are direct abstractions of properties already present in observed frequencies. Finite additivity is a consequence of the elementary counting argument: disjoint events contribute non-overlapping sets of throws. Countable additivity is the genuinely new postulate — it extends the framework to infinite processes and is required to make the theory mathematically complete.

---

## Interpretation / Sanity Check

The following consequences of the axioms — all derived from the three axioms alone — match perfectly with what was observed empirically in Problem 5:

$$
P(\emptyset) = 0 \quad \text{(impossible event)}
$$

$$
P(A^c) = 1 - P(A) \quad \text{(complement rule)}
$$

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B) \quad \text{(inclusion-exclusion)}
$$

$$
A \subseteq B \implies P(A) \leq P(B) \quad \text{(monotonicity)}
$$

Each of these was already visible in the frequency data. The axiomatic system is therefore not an arbitrary set of rules — it is a precise and minimal codification of the structure already present in the act of counting outcomes.

---

## Common Mistakes

- Treating the three Kolmogorov axioms as independent definitions of probability, rather than recognizing them as abstractions of concrete counting properties. The axioms should be understood as capturing, in minimal form, what frequencies already do.
- Confusing finite additivity with countable additivity. These are genuinely different properties. Every countably additive measure is finitely additive (by taking $A_n = \emptyset$ for $n > m$), but the converse fails.
- Believing that countable additivity "follows from" finite additivity by "taking limits." This is false. Finite additivity says nothing about limits. Countable additivity is a separate postulate that gives $P$ its topological (continuity) properties.
- Thinking that the $\sigma$-algebra $\mathcal{F}$ is merely a technical nuisance. In fact, the need for $\mathcal{F}$ reflects a genuine mathematical fact: on uncountable sample spaces, not every subset can be assigned a probability in a way consistent with the axioms. The $\sigma$-algebra specifies exactly which events are "measurable."