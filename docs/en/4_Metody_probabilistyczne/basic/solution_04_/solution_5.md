# Problem 5 — From Recorded Frequencies to Probability

## What This Problem Is Really About

Before presenting any calculations, it is essential to understand the purpose of this problem. It is not an arithmetic exercise. Its goal is to trace the path from a concrete, real experiment — throwing a die 1000 times and recording results — to the abstract mathematical concept of probability.

The central question is: **where does probability come from?**

The answer this problem develops is the following. When we perform the same random experiment many times, the proportion of times each event occurs — its observed frequency — turns out to behave in a very structured, regular way. That structure does not depend on the specific numbers recorded in this particular experiment. It would hold in any repetition of this experiment, and it holds for any random experiment at all. Probability is the mathematical abstraction of that structure: it is a function that assigns numbers to events while preserving exactly the regularities we observe in frequencies.

This problem works through those regularities one by one, making each one explicit and explaining why it holds. The goal is not to compute — it is to understand.

---

## The Setup

A student rolled a fair six-sided die 1000 times. The results were recorded:

$$
n(\{1\}) = 168, \quad n(\{2\}) = 154, \quad n(\{3\}) = 181
$$

$$
n(\{4\}) = 167, \quad n(\{5\}) = 160, \quad n(\{6\}) = 170
$$

The sample space of a single throw is:

$$
\Omega = \{1, 2, 3, 4, 5, 6\}
$$

**What is $\Omega$?** It is the set of all possible outcomes of one throw. Before throwing the die, we do not know which outcome will occur — but we know it must be one of these six. The sample space is the complete list of possibilities.

**What is an event?** An event is any subset $A \subseteq \Omega$. An event "occurs" in a given throw if the result of that throw belongs to $A$. For example, the event $\{2, 4, 6\}$ occurs whenever the result is even.

For any event $A$, we define its **observed frequency**:

$$
f(A) = \frac{n(A)}{1000}
$$

where $n(A)$ is the number of throws in which event $A$ occurred. The frequency $f(A)$ measures how often $A$ was observed in this experiment. It is a number between 0 and 1.

---

## Part A — From Elementary Outcomes to Events

### The Core Idea

The six elementary outcomes partition every throw: each of the 1000 throws produced exactly one result, and that result belongs to exactly one of the singletons $\{1\}, \{2\}, \ldots, \{6\}$.

Now suppose we want $n(A)$ for some event $A$, say $A = \{2, 4, 6\}$. A throw contributes to $n(A)$ precisely when its result is 2, or 4, or 6. Since these are three distinct outcomes that cannot occur simultaneously in a single throw, the counts do not overlap:

$$
n(\{2, 4, 6\}) = n(\{2\}) + n(\{4\}) + n(\{6\})
$$

This is not a formula we impose — it follows from the meaning of "count." In each of the 1000 throws, the result was either 2 (counted in $n(\{2\})$), or 4 (counted in $n(\{4\})$), or 6 (counted in $n(\{6\})$), or something else (counted in none of them). No throw is counted twice.

The general rule: **for any event $A$, we compute $n(A)$ by summing the counts of the elementary outcomes it contains.**

$$
n(A) = \sum_{k \in A} n(\{k\})
$$

---

**Event $A = \{2, 4, 6\}$** — the result is even

A throw contributes to $n(A)$ when it shows 2, 4, or 6. These three outcomes are disjoint — no throw can show two values simultaneously.

$$
n(A) = 154 + 167 + 170 = 491
$$

$$
f(A) = \frac{491}{1000} = 0.491
$$

In roughly $49.1\%$ of throws, the result was even. For a fair die the theoretical value would be $0.5$ — our result is close, as expected.

---

**Event $B = \{1, 2, 3\}$** — the result is at most 3

$$
n(B) = 168 + 154 + 181 = 503, \qquad f(B) = 0.503
$$

---

**Event $C = \{5, 6\}$** — the result is 5 or 6

$$
n(C) = 160 + 170 = 330, \qquad f(C) = 0.330
$$

---

**Event $D = \{1, 3, 5\}$** — the result is odd

$$
n(D) = 168 + 181 + 160 = 509, \qquad f(D) = 0.509
$$

---

**Event $E = \{1, 2, 3, 4\}$** — the result is at most 4

$$
n(E) = 168 + 154 + 181 + 167 = 670, \qquad f(E) = 0.670
$$

---

## Part B — How Frequencies Combine

### What We Are Observing

This part does not simply verify arithmetic equalities. It reveals that the function $f$ has a structural property: it behaves predictably under set union, provided the sets are disjoint. This observation is the key step toward understanding probability.

---

**Equality 1:** $f(\{2,4,6\}) = f(\{2\}) + f(\{4\}) + f(\{6\})$

$$
f(\{2\}) + f(\{4\}) + f(\{6\}) = \frac{154 + 167 + 170}{1000} = \frac{491}{1000} = f(\{2,4,6\}) \checkmark
$$

**Why does this hold?**

The three sets $\{2\}$, $\{4\}$, $\{6\}$ are pairwise disjoint — no element belongs to more than one of them. Therefore, no throw is counted in more than one of the three counts $n(\{2\})$, $n(\{4\})$, $n(\{6\})$. The total count of the union is exactly the sum of the individual counts. Dividing everything by 1000 gives the equality for frequencies.

The equality holds not because of the specific numbers, but because of the logical structure: **disjoint events do not overlap, so their counts do not overlap.**

---

**Equality 2:** $f(\{1,2,3,4\}) = f(\{1,2\}) + f(\{3,4\})$

$$
f(\{1,2\}) = \frac{168+154}{1000} = \frac{322}{1000}, \quad f(\{3,4\}) = \frac{181+167}{1000} = \frac{348}{1000}
$$

$$
f(\{1,2\}) + f(\{3,4\}) = \frac{670}{1000} = f(\{1,2,3,4\}) \checkmark
$$

**Why does this hold?**

We have partitioned $\{1,2,3,4\}$ into two disjoint parts: $\{1,2\}$ and $\{3,4\}$. No throw contributes to both counts. The same disjointness argument applies.

This illustrates an important point: the same set can be partitioned in many ways, and the frequency of the whole equals the sum of frequencies of the parts — as long as the parts do not overlap.

---

**Equality 3:** $f(\{1,3,5\}) + f(\{2,4,6\}) = 1$

$$
\frac{509}{1000} + \frac{491}{1000} = \frac{1000}{1000} = 1 \checkmark
$$

**Why does this hold?**

The events $\{1,3,5\}$ (odd outcomes) and $\{2,4,6\}$ (even outcomes) are complementary. They are disjoint, and together they cover all of $\Omega$. Every throw produces either an odd or an even result — never both, never neither.

This means every one of the 1000 throws is counted in exactly one of the two counts. The total is 1000, and dividing by 1000 gives 1. This is not a coincidence specific to this data — it would hold in any experiment with any counts.

---

**Equality 4:** $f(\{5,6\}) = 1 - f(\{1,2,3,4\})$

$$
1 - 0.670 = 0.330 = f(\{5,6\}) \checkmark
$$

**Why does this hold?**

$\{5,6\}$ is the complement of $\{1,2,3,4\}$ in $\Omega$. Every throw either shows a result in $\{1,2,3,4\}$ or a result in $\{5,6\}$ — exclusively and exhaustively. So:

$$
n(\{5,6\}) = 1000 - n(\{1,2,3,4\}) = 1000 - 670 = 330
$$

Dividing by 1000:

$$
f(\{5,6\}) = 1 - f(\{1,2,3,4\})
$$

This is the **complement rule**. It will become one of the standard consequences of the probability axioms.

---

## Part C — When Simple Addition Works and When It Fails

### The Most Important Conceptual Step

This part identifies the precise condition under which frequencies add simply. It is the most conceptually important part of Problem 5, because it reveals the exact reason why naive addition sometimes fails — and what the correct formula is.

---

**Sub-part 1:** $f(\{1,2\} \cup \{5,6\}) = f(\{1,2\}) + f(\{5,6\})$

$$
f(\{1,2\}) = \frac{322}{1000}, \quad f(\{5,6\}) = \frac{330}{1000}
$$

$$
\{1,2\} \cap \{5,6\} = \emptyset
$$

Since the two sets are disjoint, no throw is counted in both:

$$
f(\{1,2,5,6\}) = \frac{652}{1000} = f(\{1,2\}) + f(\{5,6\}) \checkmark
$$

---

**Sub-part 2:** The failing case — $M = \{1,2,3\}$, $N = \{3,4,5\}$

$$
n(M) = 168 + 154 + 181 = 503, \quad f(M) = 0.503
$$

$$
n(N) = 181 + 167 + 160 = 508, \quad f(N) = 0.508
$$

$$
M \cup N = \{1,2,3,4,5\}
$$

$$
n(M \cup N) = 168 + 154 + 181 + 167 + 160 = 830, \quad f(M \cup N) = 0.830
$$

$$
f(M) + f(N) = 0.503 + 0.508 = 1.011
$$

The sum exceeds 1. This is impossible for a frequency — no event can occur more than 100% of the time.

---

**Sub-part 3:** Why does the equality fail?

The cause is the intersection: $M \cap N = \{3\}$.

In the sum $n(M) + n(N)$, the 181 throws that produced outcome 3 are counted **twice**: once because $3 \in M$, and once because $3 \in N$. But in $n(M \cup N)$, each throw is counted exactly once.

The error is precisely $n(\{3\}) = 181$:

$$
n(M) + n(N) - n(M \cap N) = 503 + 508 - 181 = 830 = n(M \cup N) \checkmark
$$

$$
f(M \cup N) = f(M) + f(N) - f(M \cap N) = 0.503 + 0.508 - 0.181 = 0.830 \checkmark
$$

This is the **inclusion-exclusion principle** for two events. It is not a correction imposed from outside — it is a direct consequence of the meaning of counting.

---

**Sub-part 4:** Identifying the double-counted outcomes

The outcomes counted twice in $n(M) + n(N)$ are exactly the elements of $M \cap N = \{3\}$.

More generally: the element $k$ is counted twice in $n(A) + n(B)$ if and only if $k \in A$ and $k \in B$, i.e., $k \in A \cap B$. The overcounting equals $n(A \cap B)$, and the correct formula subtracts it once.

**Summary of Part C:**

| Condition | Formula |
|---|---|
| $A \cap B = \emptyset$ | $f(A \cup B) = f(A) + f(B)$ |
| $A \cap B \neq \emptyset$ | $f(A \cup B) = f(A) + f(B) - f(A \cap B)$ |

Simple addition is a special case of inclusion-exclusion when the intersection is empty.

---

## Part D — Covering the Whole Sample Space

### The Idea of a Partition

A **partition** of $\Omega$ is a collection of pairwise disjoint events whose union is all of $\Omega$. Partitions matter because they decompose every experiment: each throw lands in exactly one piece.

---

**Sub-part 1:** Sum of all elementary frequencies

$$
\sum_{k=1}^{6} f(\{k\}) = \frac{168 + 154 + 181 + 167 + 160 + 170}{1000} = \frac{1000}{1000} = 1
$$

---

**Sub-part 2:** Why the result must equal 1 — necessarily, not by coincidence

Every throw produces exactly one outcome. The six singletons $\{1\}, \ldots, \{6\}$ are pairwise disjoint and their union is $\Omega$. Therefore every throw contributes to exactly one count $n(\{k\})$. Adding all six counts gives the total number of throws:

$$
n(\{1\}) + n(\{2\}) + \cdots + n(\{6\}) = 1000
$$

Dividing by 1000:

$$
\sum_{k=1}^{6} f(\{k\}) = 1
$$

This equality does not depend on the specific values $168, 154, \ldots$. It would hold for any counts, in any repetition of any experiment. It is a structural fact about how $f$ is defined, not a property of these particular data.

---

**Sub-part 3:** A different partition — $\{1,2\}$, $\{3,4\}$, $\{5,6\}$

$$
f(\{1,2\}) + f(\{3,4\}) + f(\{5,6\}) = \frac{322 + 348 + 330}{1000} = \frac{1000}{1000} = 1
$$

---

**Sub-part 4:** Why this sum is also 1

The three sets $\{1,2\}$, $\{3,4\}$, $\{5,6\}$ are pairwise disjoint and their union is $\Omega$. The same argument applies: each throw falls into exactly one piece, so the total count across the three events is 1000.

---

**Sub-part 5:** General statement — the partition rule

Let $A_1, A_2, \ldots, A_m$ be any pairwise disjoint events with $A_1 \cup A_2 \cup \cdots \cup A_m = \Omega$. Then:

$$
f(A_1) + f(A_2) + \cdots + f(A_m) = 1
$$

**Proof:** since the $A_i$ cover $\Omega$ without overlap, each throw lands in exactly one $A_i$:

$$
n(A_1) + \cdots + n(A_m) = 1000 \implies f(A_1) + \cdots + f(A_m) = 1
$$

This property — sometimes called **finite additivity on a partition of $\Omega$** — is the empirical basis for normalization in probability theory.

---

## Part E — From Observed Frequency to Probability

### The Decisive Conceptual Move

In Parts A–D, we worked with a specific experiment: 1000 throws with specific counts. The regularities we discovered — additivity for disjoint events, the complement rule, the partition rule — held for these data. But they would hold for any data from any similar experiment, because they follow from the logic of counting, not from the specific numbers.

This suggests the following question: **can we define a mathematical object that captures these regularities without referring to any specific experiment?**

The answer is yes. We define a **probability** $P$ as a function that assigns a number to every event $A \subseteq \Omega$, satisfying the properties that frequencies always have. Here is each property, with the justification that we have already built.

---

**Property 1: $P(A) \in [0,1]$ for every event $A$**

A frequency is a count divided by 1000. Counts are non-negative and cannot exceed 1000, so $f(A) \in [0,1]$ always. Any abstract function modelling frequencies must inherit this constraint.

This rules out negative probabilities and probabilities greater than 1 — not as arbitrary conventions, but as reflections of what frequencies actually do.

---

**Property 2: $P(\emptyset) = 0$**

The empty set contains no outcomes. No throw can produce a result that belongs to $\emptyset$, so $n(\emptyset) = 0$ and $f(\emptyset) = 0$. The impossible event never occurs — in any experiment, with any counts.

---

**Property 3: $P(\Omega) = 1$**

Every throw produces some outcome in $\Omega$. Therefore $n(\Omega) = 1000$ and $f(\Omega) = 1$. This was the conclusion of Part D.

---

**Property 4: For disjoint events, $P(A \cup B) = P(A) + P(B)$**

This is the central regularity of Parts B and C. When $A \cap B = \emptyset$, no throw contributes to both $n(A)$ and $n(B)$, so:

$$
n(A \cup B) = n(A) + n(B) \implies f(A \cup B) = f(A) + f(B)
$$

When $A \cap B \neq \emptyset$, the formula fails and must be corrected. The additivity property holds precisely because disjointness prevents double-counting.

---

**Property 5: $P(A^c) = 1 - P(A)$**

This follows from Properties 3 and 4: $A$ and $A^c$ are disjoint with $A \cup A^c = \Omega$, so $P(A) + P(A^c) = P(\Omega) = 1$. It was verified empirically in Equalities 3 and 4 of Part B.

---

## Part F — Conclusion: Three Connected Levels

The work of this problem traces a path through three distinct levels of description. Understanding how they connect is the central conceptual goal of the entire problem set.

---

**Level 1 — Elementary outcomes and events**

The sample space $\Omega = \{1,2,3,4,5,6\}$ and the collection of all its subsets. Events are sets. Logical statements about the die result — "even," "at most 3," "odd" — are translated into subsets. Logical operations on statements correspond to set operations:

- "or" $\longleftrightarrow$ union $\cup$
- "and" $\longleftrightarrow$ intersection $\cap$
- "not" $\longleftrightarrow$ complement $^c$

At this level, there are no numbers. The structure is purely combinatorial and logical.

By my own words: 
At this level, there’s no magic and no math yet. This is just taking inventory.
For example lets imagine you’re looking at a restaurant menu. The menu is your sample space (Ω). You haven’t ordered anything yet, but you know for a fact that this place only serves six dishes (labeled 1 through 6).

Events are just "combo meals." For example, "anything vegetarian" or "even-numbered dishes."

Logic works just like it does in real life: "I want 1 OR 2" is a Union (∪). "I want something that is BOTH spicy AND meat-based" is an Intersection (∩).

---

**Level 2 — Observed frequencies from a real experiment**

Now we start actually doing things. We roll the die 1000 times and write down what happens. This is like the stats after a football match.
We see that the number 3 came up 181 times. These are "messy," real-world numbers. If you rolled the die another 1000 times, the numbers would change slightly.

But here’s the trick: no matter how much the numbers change, the rules of the game stay the same:

You can’t score "negative" goals (frequency is never below 0).

The total of all results always adds up to 100% (you definitely rolled something).

If you want to know how many times you got "a 1 or a 2," you just add their individual scores. You can't count the same physical roll twice.

---

**Level 3 — Probability as mathematical abstraction**

Probability is a function $P$ defined on all events, satisfying the same properties that $f$ always has. It is not tied to any particular experiment. It describes what we expect in the long run — or what we believe before any experiment is performed.

The movement from Level 2 to Level 3 is the movement from empirical regularity to mathematical axiom. The properties of $f$ that we verified in specific data become the axioms that $P$ must satisfy by definition. Probability theory then develops as the body of theorems that can be proved from those axioms alone.

In my own words: 
We take the rules from Level 2 (which always work) and "detach" them from any specific experiment.

Probability is the "perfect version" of frequency. We say: "It doesn't matter exactly how many times we rolled a 3 today. We are going to create a mathematical model (P) that acts exactly how a frequency would act if we rolled the die forever."

**The path of this problem:**

$$
\text{concrete outcomes} \xrightarrow{\text{events are sets}} \text{logical structure} \xrightarrow{\text{1000 throws}} \text{observed frequencies} \xrightarrow{\text{abstraction}} \text{probability}
$$

This path — from the concrete to the abstract, from the empirical to the formal — is the birth of probability theory.