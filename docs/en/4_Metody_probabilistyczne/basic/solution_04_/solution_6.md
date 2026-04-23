# Problem 6 — Final Discussion: The Axiomatic Point of View

## What This Problem Is Really About

Problem 6 is the culmination of the entire problem set. Its purpose is not to state the Kolmogorov axioms and verify them — it is to explain **why** those axioms take precisely the form they do, where they come from, what they capture, and what goes beyond our earlier experience.

The central claim of this discussion is the following: two of the three Kolmogorov axioms — non-negativity and normalization — are immediately visible in observed frequencies and require almost no conceptual work beyond what we did in Problem 5. The finite part of the third axiom — additivity for disjoint events — is also suggested by frequencies, as we saw in detail. But the full third axiom — **countable additivity** — is a genuinely new postulate that goes beyond anything finite experiments can suggest, and understanding why it is needed, and what it does for the theory, is the deepest point in this discussion.

---

## The Setting: From Finite to General

In Problems 1–5, the sample space was always finite: a coin, a die, a week of weather. Every subset of $\Omega$ was automatically an event, and all our reasoning stayed within the finite.

When we move to general probability theory, the sample space may be infinite — even uncountably infinite, as in the Buffon needle experiment where outcomes are pairs of real numbers. In such settings, two complications arise.

**First complication — not all subsets can be events.** On uncountable sample spaces, it is mathematically impossible to assign probabilities consistently to every subset. The solution is to restrict attention to a specific collection $\mathcal{F}$ of "measurable" subsets, called a **$\sigma$-algebra**.

**Definition:** A **$\sigma$-algebra** on $\Omega$ is a collection $\mathcal{F}$ of subsets of $\Omega$ satisfying:
1. $\Omega \in \mathcal{F}$
2. If $A \in \mathcal{F}$, then $A^c \in \mathcal{F}$ (closed under complement)
3. If $A_1, A_2, A_3, \ldots \in \mathcal{F}$, then $\bigcup_{n=1}^{\infty} A_n \in \mathcal{F}$ (closed under countable union)

The triple $(\Omega, \mathcal{F}, P)$ is called a **probability space**.

**In the finite setting:** $\mathcal{F} = 2^{\Omega}$ (all subsets) is automatically a $\sigma$-algebra. This is why the $\sigma$-algebra never appeared in Problems 1–5 — it was always trivially the full power set.

**Second complication — finite additivity is not enough for infinite processes.** Even if we know how probabilities add for finite unions of disjoint events, this tells us nothing about infinite unions. A new axiom is needed.

---

## The Kolmogorov Axioms (1933)

Let $(\Omega, \mathcal{F})$ be a measurable space. A function $P : \mathcal{F} \to \mathbb{R}$ is a **probability measure** if it satisfies:

**Axiom 1 — Non-negativity:**

$$
P(A) \geq 0 \quad \text{for all } A \in \mathcal{F}
$$

**Axiom 2 — Normalization:**

$$
P(\Omega) = 1
$$

**Axiom 3 — Countable additivity ($\sigma$-additivity):**

For any sequence $A_1, A_2, A_3, \ldots$ of pairwise disjoint events in $\mathcal{F}$:

$$
P\!\left(\bigsqcup_{n=1}^{\infty} A_n\right) = \sum_{n=1}^{\infty} P(A_n)
$$

These three axioms are the complete foundation of probability theory. Every theorem — the law of large numbers, the central limit theorem, Bayes' theorem, the theory of stochastic processes — is derived from these three statements alone.

---

## Axiom 1 — Non-negativity: Transparent from Frequencies

In Problem 5, the observed frequency was:

$$
f(A) = \frac{n(A)}{1000}
$$

The count $n(A)$ is a non-negative integer (it counts throws), and 1000 is positive, so $f(A) \geq 0$ always. This is not a special property of our data — it holds for any experiment, with any number of repetitions, for any event.

**Why Axiom 1 takes this form:** A function modelling frequencies must be non-negative, because frequencies are non-negative. There is no mystery here. The axiom simply elevates an obvious empirical fact to a formal requirement.

Note: the upper bound $P(A) \leq 1$ is not a separate axiom. It follows from Axioms 1 and 2: since $A$ and $A^c$ are disjoint with $A \cup A^c = \Omega$, Axiom 3 (applied finitely) gives $P(A) + P(A^c) = 1$, and Axiom 1 gives $P(A^c) \geq 0$, so $P(A) \leq 1$.

---

## Axiom 2 — Normalization: Transparent from Frequencies

In Part D of Problem 5, we showed that for any partition of $\Omega$ into disjoint events — in particular the partition $\Omega$ itself — the frequencies sum to 1. The key argument:

Every throw produces some outcome in $\Omega$. Therefore $n(\Omega) = 1000$ (the total number of throws), and:

$$
f(\Omega) = \frac{1000}{1000} = 1
$$

This would hold with any total number of throws, not just 1000. **The certain event always occurs.** Normalization to 1 (rather than some other constant) is the natural choice because frequencies are naturally ratios between 0 and 1.

**Why Axiom 2 takes this form:** It formalizes the certainty of the whole sample space. In every throw, something happens — and the event "something happens" is $\Omega$. Its probability must be 1.

---

## Finite Additivity: Fully Explained by Counting

### The Key Observation from Problem 5

The most important discovery in Part C of Problem 5 was this: **simple addition of frequencies works if and only if the events are disjoint.**

When $A \cap B = \emptyset$: no throw produces a result in both $A$ and $B$ simultaneously. Therefore $n(A \cup B) = n(A) + n(B)$, and dividing by 1000:

$$
f(A \cup B) = f(A) + f(B)
$$

When $A \cap B \neq \emptyset$: throws whose result lies in $A \cap B$ are counted once in $n(A)$ and once in $n(B)$. In $n(A) + n(B)$ they appear twice, but in $n(A \cup B)$ they appear only once. The overcounting is $n(A \cap B)$, giving:

$$
f(A \cup B) = f(A) + f(B) - f(A \cap B)
$$

### Why This Works for Any Finite Collection

By induction, the same argument extends to any finite collection of pairwise disjoint events $A_1, \ldots, A_m$:

$$
n(A_1 \cup \cdots \cup A_m) = n(A_1) + \cdots + n(A_m) \quad \text{(disjointness prevents double-counting)}
$$

$$
\implies f(A_1 \cup \cdots \cup A_m) = f(A_1) + \cdots + f(A_m)
$$

**Finite additivity is not an assumption — it is a consequence of what counting means.** It holds because the definition of $n(A)$ is: count the throws whose result belongs to $A$. When events are disjoint, each throw is counted at most once.

This is the origin of the additivity clause in Axiom 3 — for finite collections. But Axiom 3 says something more.

---

## Countable Additivity: The Genuinely New Postulate

### What Finite Experiments Cannot Tell Us

Axiom 3 applies to **infinite** sequences of disjoint events. Consider:

$$
P\!\left(\bigsqcup_{n=1}^{\infty} A_n\right) = \sum_{n=1}^{\infty} P(A_n)
$$

No finite experiment can verify this. In 1000 throws of a die, there are at most $2^6 = 64$ events. There is no way to exhibit an infinite collection of disjoint events in a finite experiment. The right-hand side is an infinite series — a limit — and limits simply do not appear in finite counting.

A student who has only Problem 5 to go on cannot "see" countable additivity. They can see that addition works for two disjoint events, and for three, and for six. But the step to infinitely many disjoint events requires a new idea.

### Why Countable Additivity Is Needed

**Example 1 — Countably infinite sample spaces.** Consider the geometric distribution from Problem Set 3: $\Omega = \{1, 2, 3, \ldots\}$ with $P(\{k\}) = (1-p)^{k-1}p$.

The event $\Omega$ itself is:

$$
\Omega = \{1\} \sqcup \{2\} \sqcup \{3\} \sqcup \cdots
$$

For $P(\Omega) = 1$ (Axiom 2) to be consistent with the individual probabilities, we need:

$$
\sum_{k=1}^{\infty} P(\{k\}) = \sum_{k=1}^{\infty} (1-p)^{k-1}p = 1
$$

This is precisely Axiom 3 applied to the countably infinite partition $\{\{k\}\}_{k=1}^{\infty}$. Without it, we could not even define a probability distribution on $\Omega = \{1, 2, 3, \ldots\}$ in a consistent way.

**Example 2 — Continuity of probability.** One of the most powerful consequences of countable additivity is the **continuity property**: if $A_1 \subseteq A_2 \subseteq A_3 \subseteq \cdots$ is an increasing sequence of events with union $A$, then:

$$
P(A) = \lim_{n \to \infty} P(A_n)
$$

This says that probability is continuous with respect to monotone limits of events. It is essential for the analysis of random variables, the law of large numbers, and the central limit theorem.

**This property does not follow from finite additivity alone.** There exist finitely additive functions satisfying Axioms 1 and 2 and finite additivity, but failing this continuity property. Such functions produce incoherent answers when infinite processes are involved.

### What Finite Additivity Fails to Capture

Finite additivity says: the probability of a finite disjoint union equals the finite sum. Countable additivity says: probability is **continuous** — it respects the operation of taking limits of increasing or decreasing sequences of events.

Continuity is a topological property. It describes behavior at infinity. It cannot be observed in any finite experiment, no matter how many throws are made. This is why countable additivity is not derivable from empirical observations — it is a mathematical assumption about how probability behaves in the limit.

Kolmogorov's insight was to recognize this property as the precisely correct one. It is:
- **minimal**: weaker assumptions produce a theory too limited for real analysis
- **not arbitrary**: it is the natural condition for probability to be a measure in the sense of Lebesgue integration theory
- **powerful**: from it, essentially all of modern probability follows

---

## Summary: The Origin of Each Axiom

| Axiom | Mathematical content | Origin | What it captures |
|---|---|---|---|
| Non-negativity | $P(A) \geq 0$ | Frequencies are non-negative | Counts cannot be negative |
| Normalization | $P(\Omega) = 1$ | Every throw lands in $\Omega$ | Certainty of the certain event |
| Finite additivity | $P(A \cup B) = P(A) + P(B)$ for $A \cap B = \emptyset$ | Disjoint events do not overlap in counting | No double-counting |
| Countable additivity | Extension to $\bigcup_{n=1}^{\infty} A_n$ | **Not derivable from finite experiments** | Continuity with respect to monotone limits |

---

## The Kolmogorov Axioms as the Formalization of Discovered Structure

The deepest message of this problem set is this:

The Kolmogorov axioms are not arbitrary rules invented from nothing. They are the precise mathematical formulation of regularities that we discovered concretely — in coins, dice, weather experiments, and 1000 die throws. Non-negativity, normalization, and additivity for disjoint events were all visible in the data of Problem 5. They were not assumed — they were observed, then understood, then abstracted.

The one genuine conceptual addition — countable additivity — extends the framework to infinite processes and gives probability its full mathematical power. It is the step from finite empirical experience to infinite mathematical theory.

This is what formalism means: it is not the replacement of understanding by symbol manipulation. It is the precise organization of understanding — the crystallization of observed regularities into a small number of axioms from which everything else can be derived.

---

## Consequences of the Axioms

All of the following follow from Axioms 1, 2, 3 alone — no additional assumptions:

$$
P(\emptyset) = 0
$$

$$
P(A^c) = 1 - P(A)
$$

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

$$
A \subseteq B \implies P(A) \leq P(B)
$$

$$
A_n \nearrow A \implies P(A_n) \to P(A) \quad \text{(continuity from below)}
$$

$$
A_n \searrow A \implies P(A_n) \to P(A) \quad \text{(continuity from above)}
$$

Each of these was suggested — at least in the finite case — by the empirical work of Problem 5. The axiomatic system captures them all in three lines.