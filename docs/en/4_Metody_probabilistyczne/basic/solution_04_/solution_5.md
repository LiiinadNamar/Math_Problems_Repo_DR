# Problem 5 — From Recorded Frequencies to Probability

## Problem Statement

A student rolled a six-sided die 1000 times. The recorded counts of each outcome are:

$$
n(\{1\}) = 168, \quad n(\{2\}) = 154, \quad n(\{3\}) = 181
$$

$$
n(\{4\}) = 167, \quad n(\{5\}) = 160, \quad n(\{6\}) = 170
$$

The sample space is $\Omega = \{1, 2, 3, 4, 5, 6\}$.

For any event $A \subseteq \Omega$, the **observed frequency** is defined as:

$$
f(A) = \frac{n(A)}{1000}
$$

where $n(A)$ is the number of throws in which the outcome belonged to $A$.

---

## Definitions / Theory

**Elementary outcome:** a single, indivisible result of the experiment — here, one of the six faces.

**Event:** any subset $A \subseteq \Omega$. An event "occurs" in a given throw if the result of that throw is an element of $A$.

**Observed frequency $f(A)$:** the proportion of throws in which event $A$ occurred. It is a number between 0 and 1. It measures how often $A$ was observed in this particular experiment of 1000 throws.

**Key principle for disjoint events:** if $A \cap B = \emptyset$ (no outcome belongs to both), then every throw that contributes to $n(A)$ does not contribute to $n(B)$, and vice versa. Therefore:

$$
n(A \cup B) = n(A) + n(B) \implies f(A \cup B) = f(A) + f(B)
$$

**Why additivity fails for non-disjoint events:** if $A \cap B \neq \emptyset$, then throws whose outcome lies in $A \cap B$ are counted once in $n(A)$ and once in $n(B)$, so in the sum $n(A) + n(B)$ they appear **twice**. The correct formula is:

$$
n(A \cup B) = n(A) + n(B) - n(A \cap B)
$$

$$
f(A \cup B) = f(A) + f(B) - f(A \cap B)
$$

This is the inclusion-exclusion principle for two sets.

---

## Part A — From Elementary Outcomes to Events

The count $n(A)$ for any event $A$ is the sum of counts of all elementary outcomes in $A$, because each throw produces exactly one outcome, and the outcome either belongs to $A$ or it does not.

$$
n(A) = \sum_{k \in A} n(\{k\})
$$

---

**Event $A = \{2, 4, 6\}$** — even results

$$
n(A) = n(\{2\}) + n(\{4\}) + n(\{6\}) = 154 + 167 + 170 = 491
$$

$$
f(A) = \frac{491}{1000} = 0.491
$$

---

**Event $B = \{1, 2, 3\}$** — results at most 3

$$
n(B) = n(\{1\}) + n(\{2\}) + n(\{3\}) = 168 + 154 + 181 = 503
$$

$$
f(B) = \frac{503}{1000} = 0.503
$$

---

**Event $C = \{5, 6\}$** — results at least 5

$$
n(C) = n(\{5\}) + n(\{6\}) = 160 + 170 = 330
$$

$$
f(C) = \frac{330}{1000} = 0.330
$$

---

**Event $D = \{1, 3, 5\}$** — odd results

$$
n(D) = n(\{1\}) + n(\{3\}) + n(\{5\}) = 168 + 181 + 160 = 509
$$

$$
f(D) = \frac{509}{1000} = 0.509
$$

---

**Event $E = \{1, 2, 3, 4\}$** — results at most 4

$$
n(E) = n(\{1\}) + n(\{2\}) + n(\{3\}) + n(\{4\}) = 168 + 154 + 181 + 167 = 670
$$

$$
f(E) = \frac{670}{1000} = 0.670
$$

---

## Part B — How Frequencies Combine

This part examines why certain equalities hold. Each equality is a consequence of the additivity of counts for disjoint sets.

---

**Equality 1:** $f(\{2,4,6\}) = f(\{2\}) + f(\{4\}) + f(\{6\})$

$$
f(\{2\}) + f(\{4\}) + f(\{6\}) = \frac{154}{1000} + \frac{167}{1000} + \frac{170}{1000} = \frac{491}{1000} = 0.491
$$

This equals $f(\{2,4,6\}) = 0.491$. $\checkmark$

**Why it holds:** the sets $\{2\}$, $\{4\}$, $\{6\}$ are pairwise disjoint — no element belongs to more than one of them. Therefore, no throw is counted twice. The count of the union is exactly the sum of counts.

---

**Equality 2:** $f(\{1,2,3,4\}) = f(\{1,2\}) + f(\{3,4\})$

$$
f(\{1,2\}) = \frac{168 + 154}{1000} = \frac{322}{1000}, \quad f(\{3,4\}) = \frac{181 + 167}{1000} = \frac{348}{1000}
$$

$$
f(\{1,2\}) + f(\{3,4\}) = \frac{322 + 348}{1000} = \frac{670}{1000} = 0.670 = f(\{1,2,3,4\}) \checkmark
$$

**Why it holds:** $\{1,2\}$ and $\{3,4\}$ are disjoint and their union is $\{1,2,3,4\}$. This is simply a different way of partitioning the same set.

---

**Equality 3:** $f(\{1,3,5\}) + f(\{2,4,6\}) = 1$

$$
\frac{509}{1000} + \frac{491}{1000} = \frac{1000}{1000} = 1 \checkmark
$$

**Why it holds:** $\{1,3,5\}$ and $\{2,4,6\}$ are complementary — they are disjoint and their union is all of $\Omega$. Every throw produces exactly one of the six outcomes, and each outcome belongs to exactly one of these two sets. Therefore every throw contributes to exactly one of the two counts, and the total is 1000 out of 1000.

---

**Equality 4:** $f(\{5,6\}) = 1 - f(\{1,2,3,4\})$

$$
1 - f(\{1,2,3,4\}) = 1 - 0.670 = 0.330 = f(\{5,6\}) \checkmark
$$

**Why it holds:** $\{5,6\}$ is the complement of $\{1,2,3,4\}$ in $\Omega$. Every throw either produces a result in $\{1,2,3,4\}$ or a result in $\{5,6\}$ — never both, never neither. Therefore $n(\{5,6\}) = 1000 - n(\{1,2,3,4\}) = 1000 - 670 = 330$.

---

## Part C — When Simple Addition Works and When It Fails

**Sub-part 1:** Check $f(\{1,2\} \cup \{5,6\}) = f(\{1,2\}) + f(\{5,6\})$

$$
n(\{1,2\}) = 168 + 154 = 322, \quad n(\{5,6\}) = 160 + 170 = 330
$$

$$
n(\{1,2\} \cup \{5,6\}) = n(\{1,2,5,6\}) = 322 + 330 = 652
$$

$$
f(\{1,2\}) + f(\{5,6\}) = \frac{322}{1000} + \frac{330}{1000} = \frac{652}{1000} \checkmark
$$

The equality holds because $\{1,2\} \cap \{5,6\} = \emptyset$ — the two events are disjoint.

---

**Sub-part 2:** Compute $f(M)$, $f(N)$, $f(M \cup N)$, and $f(M) + f(N)$ for $M = \{1,2,3\}$, $N = \{3,4,5\}$

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

---

**Sub-part 3:** Why $f(M \cup N) \neq f(M) + f(N)$

The sum $f(M) + f(N) = 1.011$ exceeds 1, which is already impossible for a frequency. The cause is clear: $M \cap N = \{3\}$.

In the sum $n(M) + n(N)$, the 181 throws that produced outcome 3 are counted **twice** — once because $3 \in M$, and once because $3 \in N$. But in $n(M \cup N)$, each throw is counted exactly once, regardless of how many of the events it satisfies.

The correct formula is:

$$
n(M \cup N) = n(M) + n(N) - n(M \cap N)
$$

$$
830 = 503 + 508 - 181 = 1011 - 181 = 830 \checkmark
$$

$$
f(M \cup N) = f(M) + f(N) - f(M \cap N) = 0.503 + 0.508 - 0.181 = 0.830 \checkmark
$$

---

**Sub-part 4:** Which outcomes are counted twice?

The element counted twice is $3 \in M \cap N$. Its count $n(\{3\}) = 181$ appears in $n(M)$ and again in $n(N)$. Simple addition therefore overcounts by exactly $n(\{3\}) = 181$.

**Summary:** simple addition $f(A) + f(B) = f(A \cup B)$ holds **if and only if** $A \cap B = \emptyset$. When events overlap, the overlapping outcomes are double-counted and the formula must be corrected by subtracting $f(A \cap B)$.

---

## Part D — Covering the Whole Sample Space

**Sub-part 1:** Sum of all elementary frequencies

$$
\sum_{k=1}^{6} f(\{k\}) = \frac{168 + 154 + 181 + 167 + 160 + 170}{1000} = \frac{1000}{1000} = 1
$$

**Sub-part 2:** Why the result must be exactly 1

Every throw produces exactly one outcome in $\Omega = \{1,2,3,4,5,6\}$. The six sets $\{1\}, \{2\}, \ldots, \{6\}$ are pairwise disjoint and their union is all of $\Omega$. Therefore every one of the 1000 throws is counted exactly once across the six counts. The total is 1000, and dividing by 1000 gives 1.

This is not a coincidence — it is a direct consequence of the definition of $f$ and the fact that outcomes partition every throw.

---

**Sub-part 3:** Partition into $\{1,2\}$, $\{3,4\}$, $\{5,6\}$

$$
f(\{1,2\}) = \frac{322}{1000}, \quad f(\{3,4\}) = \frac{348}{1000}, \quad f(\{5,6\}) = \frac{330}{1000}
$$

$$
f(\{1,2\}) + f(\{3,4\}) + f(\{5,6\}) = \frac{322 + 348 + 330}{1000} = \frac{1000}{1000} = 1
$$

**Sub-part 4:** Why this sum is also 1

The three sets $\{1,2\}$, $\{3,4\}$, $\{5,6\}$ are pairwise disjoint and their union is $\Omega$. By the same reasoning as above, every throw is counted in exactly one of the three counts.

---

**Sub-part 5:** General statement

Let $A_1, A_2, \ldots, A_m$ be any collection of pairwise disjoint events whose union is all of $\Omega$:

$$
A_i \cap A_j = \emptyset \text{ for } i \neq j, \qquad A_1 \cup A_2 \cup \cdots \cup A_m = \Omega
$$

Then:

$$
f(A_1) + f(A_2) + \cdots + f(A_m) = 1
$$

**Justification:** since the $A_i$ are disjoint and cover $\Omega$, every throw produces an outcome that belongs to exactly one $A_i$. Therefore:

$$
n(A_1) + n(A_2) + \cdots + n(A_m) = 1000
$$

Dividing both sides by 1000:

$$
f(A_1) + f(A_2) + \cdots + f(A_m) = 1
$$

This property is called **finite additivity on a partition of $\Omega$**.

---

## Part E — From Observed Frequency to Probability

The preceding parts revealed several structural properties of the function $f$. These properties did not arise from the specific numbers recorded — they followed from the **logic of counting** alone. Any repeated experiment of this type would produce a function $f$ with these same properties.

This observation motivates the following definition.

A **probability** on a finite sample space $\Omega$ is any function $P$ that assigns a real number $P(A)$ to every event $A \subseteq \Omega$, satisfying the following properties — each of which was already seen in the frequency data above.

---

**Property 1: $P(A) \in [0,1]$ for every event $A$**

An observed frequency is a count divided by the total number of throws. A count is non-negative and cannot exceed 1000, so $f(A) \in [0,1]$ always. Any function meant to model frequencies must respect this constraint.

---

**Property 2: $P(\emptyset) = 0$**

The empty set $\emptyset$ contains no outcomes. No throw can produce a result belonging to $\emptyset$. Therefore $n(\emptyset) = 0$ and $f(\emptyset) = 0$. The impossible event never occurs.

---

**Property 3: $P(\Omega) = 1$**

Every throw produces some outcome in $\Omega$. Therefore $n(\Omega) = 1000$ and $f(\Omega) = 1$. The certain event always occurs. This was verified explicitly in Part D.

---

**Property 4: For disjoint events, $P(A \cup B) = P(A) + P(B)$**

This was the central observation of Parts B and C. When $A \cap B = \emptyset$, no throw is counted in both $n(A)$ and $n(B)$, so $n(A \cup B) = n(A) + n(B)$ and dividing by 1000 gives $f(A \cup B) = f(A) + f(B)$. When $A \cap B \neq \emptyset$, simple addition overcounts.

---

**Property 5: $P(A^c) = 1 - P(A)$**

$A$ and its complement $A^c$ are disjoint and their union is $\Omega$. By Properties 3 and 4:

$$
P(A) + P(A^c) = P(A \cup A^c) = P(\Omega) = 1 \implies P(A^c) = 1 - P(A)
$$

This was verified in Part B (Equality 3 and 4): $f(D) + f(A) = 1$, and $f(C) = 1 - f(E)$.

---

## Part F — Conclusion: Three Connected Levels

The progression through this problem illustrates how mathematical abstraction is built from concrete experience.

---

**Level 1 — Elementary outcomes and events**

The starting point is the sample space $\Omega = \{1,2,3,4,5,6\}$ and the collection of all its subsets. Events are sets of outcomes. Set operations — union, intersection, complement — correspond to logical operations on statements: "or," "and," "not." This is a purely combinatorial, logical structure with no numbers attached yet.

---

**Level 2 — Observed frequencies from a real experiment**

When the experiment is actually performed, each event acquires a number: the proportion of trials in which it occurred. These numbers are empirical — they depend on the specific sequence of 1000 throws. A different experiment would give slightly different numbers. Nevertheless, the numbers always satisfy certain structural properties: they lie in $[0,1]$, they add up correctly for disjoint events, they sum to 1 over any partition of $\Omega$. These properties are not statistical coincidences — they follow from the logic of counting and the definition of $f$.

---

**Level 3 — Probability as mathematical abstraction**

Probability is a function $P$ defined on all events, satisfying the properties discovered at Level 2. It is an idealization: instead of recording what happened in a finite experiment, it describes what we expect to happen in the long run, or what we believe before any experiment is performed.

The connection between the three levels is this: observed frequencies motivate the definition of probability, and in a well-designed model the probabilities predict what frequencies will typically be observed in large experiments. The structural properties of $f$ — non-negativity, normalization, additivity for disjoint events — are elevated from observed regularities to axioms that any function called a probability must satisfy.

The movement from Level 1 to Level 3 is the movement from concrete counting to abstract formalism. The definitions, axioms, and theorems of probability theory are not arbitrary rules; they are a precise mathematical rendering of the structure already present in the act of counting outcomes in repeated trials.