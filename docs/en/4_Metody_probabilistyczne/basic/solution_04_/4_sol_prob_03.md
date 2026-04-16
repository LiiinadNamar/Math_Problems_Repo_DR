# Problem 3 — Weather (7 days × 3 states)

---

## Problem Statement

We consider a random experiment that describes the weather over one full week,
day by day. Each day of the week is assigned exactly one weather state from
the set $\{S, C, R\}$, where:

- $S$ — sunny,
- $C$ — cloudy,
- $R$ — rainy.

The experiment produces one complete weekly weather sequence, specifying the
weather for each of the seven days: Monday through Sunday.

---

## Definitions and Theory

### The Sample Space

The **sample space** $\Omega$ is the set of all possible weekly weather
sequences. Since each of the 7 days can independently take one of 3 weather
states, the total number of elementary outcomes is:

$$
|\Omega| = 3^7 = 2187
$$

Each **elementary outcome** $\omega \in \Omega$ is a function

$$
\omega : \{\text{Mon, Tue, Wed, Thu, Fri, Sat, Sun}\} \to \{S, C, R\}
$$

that assigns exactly one weather state to each day. For example:

$$
\omega = (S,\, C,\, S,\, R,\, C,\, S,\, S)
$$

means: Monday is sunny, Tuesday is cloudy, Wednesday is sunny, Thursday is
rainy, Friday is cloudy, Saturday is sunny, Sunday is sunny.

**Key point**: An elementary outcome is a *complete* description of the whole
week. It does not say anything about probabilities — it is simply one of the
$2187$ possible weekly patterns.

---

### Events

An **event** is any subset $A \subseteq \Omega$. We say the event $A$ *occurs*
if the realized weekly sequence $\omega$ belongs to $A$, that is, if
$\omega \in A$.

Every statement about the weather during the week — such as "Monday is sunny"
or "there is no rainy day" — defines a subset of $\Omega$, namely the set of
all elementary outcomes for which the statement is true.

---

### The Graphical Representation

The table used in this problem has:

- **Rows** corresponding to weather states: $S$, $C$, $R$.
- **Columns** corresponding to days of the week: Mon, Tue, Wed, Thu, Fri,
  Sat, Sun.
- **Cells** that can be marked with `X` or left as `.`.

**How to read the table correctly:**

A cell $(w, d)$ is marked `X` if the event **requires** that on day $d$ the
weather state is $w$.

A cell is left as `.` either because:
1. the event places no restriction on that day (any of the 3 states is
   allowed), or
2. that particular state is excluded for that day by the condition.

**Critical observation**: The table does not represent a single elementary
outcome. It represents a *constraint* — the set of all elementary outcomes
$\omega \in \Omega$ that satisfy the described condition. Reading the table
means reading a description of an entire event, not of one weather sequence.

---

### Counting Outcomes Inside an Event

When a condition fixes $k$ specific days to specific states, and leaves the
remaining $7 - k$ days unconstrained, the number of elementary outcomes in the
event is:

$$
|A| = 1^k \cdot 3^{7-k} = 3^{7-k}
$$

Each fixed day contributes a factor of $1$ (only one state is allowed), and
each free day contributes a factor of $3$ (all three states remain possible).

For events involving disjunctions (the word "or"), we cannot simply mark a
single table. Instead, we decompose the event into sub-events and apply the
**inclusion-exclusion principle**:

$$
|A_1 \cup A_2| = |A_1| + |A_2| - |A_1 \cap A_2|
$$

---

## Part A — Marking Events

### Statement 1 — Monday is sunny

**Reading the condition**: The condition imposes exactly one restriction:
Monday must be $S$. No other day is mentioned, so all other days remain
completely free.

**How to mark**: In column Mon, row $S$, we place `X`. All other cells
remain `.`.

```
      Mon Tue Wed Thu Fri Sat Sun
S      X   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Why this is correct**: An outcome $\omega$ belongs to this event if and
only if $\omega(\text{Mon}) = S$. The remaining six days — Tuesday through
Sunday — can each be $S$, $C$, or $R$ independently. Therefore we are
counting sequences of length 7 where the first entry is fixed and the
remaining six are free.

**Counting outcomes**:

$$
|A| = 1 \cdot 3^6 = 729
$$

This means $729$ out of $2187$ possible weeks have Monday sunny — exactly
one third of all weeks, which makes intuitive sense since Monday is equally
likely to be in any of the three states.

---

### Statement 2 — The weekend (Saturday and Sunday) is rainy

**Reading the condition**: Two days are fixed — Saturday must be $R$ and
Sunday must be $R$. The five weekdays (Monday through Friday) are
unconstrained.

**How to mark**: In column Sat, row $R$, we place `X`. In column Sun, row
$R$, we place `X`. All other cells remain `.`.

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   X   X
```

**Formal description of the event**:

$$
A = \{\omega \in \Omega : \omega(\text{Sat}) = R \;\text{and}\; \omega(\text{Sun}) = R\}
$$

The word "and" in the statement corresponds to the set-theoretic
**intersection**: both conditions must hold simultaneously.

**Counting outcomes**: Saturday is fixed (1 choice), Sunday is fixed (1
choice), and each of the five weekdays is free (3 choices each):

$$
|A| = 3^5 \cdot 1 \cdot 1 = 243
$$

---

### Statement 3 — It rains on Wednesday or Friday

**Reading the condition**: This is a **disjunction** — it is sufficient that
*at least one* of Wednesday or Friday is rainy. Both being rainy also
satisfies the condition.

**Why a single table is insufficient**: Our graphical convention marks cells
that are *required*. If we mark only Wednesday as $R$, we describe the
stricter event "Wednesday is rainy (and Friday is anything)." If we mark only
Friday as $R$, we describe "Friday is rainy (and Wednesday is anything)."
Neither single table captures the disjunction. We must work with two
sub-events and take their union.

**Decomposition into sub-events**:

$$
A_1 = \{\omega : \omega(\text{Wed}) = R\}
\qquad \text{(Wednesday is rainy)}
$$

$$
A_2 = \{\omega : \omega(\text{Fri}) = R\}
\qquad \text{(Friday is rainy)}
$$

$$
A = A_1 \cup A_2
\qquad \text{(at least one of them is rainy)}
$$

**Sub-event $A_1$** — Wednesday is rainy, all other days free:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   X   .   .   .   .
```

**Sub-event $A_2$** — Friday is rainy, all other days free:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   X   .   .
```

The event $A = A_1 \cup A_2$ is the set of all outcomes appearing in
**at least one** of the two tables above.

**Counting outcomes using inclusion-exclusion**:

$$
|A_1| = 3^6 = 729
\qquad \text{(Wednesday fixed, 6 days free)}
$$

$$
|A_2| = 3^6 = 729
\qquad \text{(Friday fixed, 6 days free)}
$$

The intersection $A_1 \cap A_2$ is the event "Wednesday is rainy **and**
Friday is rainy" — both days are fixed, 5 remaining days are free:

$$
|A_1 \cap A_2| = 3^5 = 243
$$

By inclusion-exclusion:

$$
|A| = |A_1| + |A_2| - |A_1 \cap A_2| = 729 + 729 - 243 = 1215
$$

**Why we subtract the intersection**: Without subtraction, outcomes in which
both Wednesday and Friday are rainy would be counted twice — once in $|A_1|$
and once in $|A_2|$. Subtracting $|A_1 \cap A_2|$ corrects for this
double-counting.

**Sanity check via complement**: The complement $A^c$ is the event "neither
Wednesday nor Friday is rainy." Each of these two days may be $S$ or $C$ (2
choices each), and the remaining 5 days are free (3 choices each):

$$
|A^c| = 2^2 \cdot 3^5 = 4 \cdot 243 = 972
$$

Indeed $|A| + |A^c| = 1215 + 972 = 2187 = |\Omega|$. $\checkmark$

---

### Statement 4 — There is no rainy day during the week

**Reading the condition**: Every single day must be either $S$ or $C$.
The state $R$ is forbidden for the entire week.

**How to mark**: No cell in row $R$ is marked — the condition prohibits $R$
on every day. But our convention marks states that are *required*, not states
that are *forbidden*. The table therefore looks like the empty starting table:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Important clarification**: Although this table looks identical to the blank
sample space, its meaning here is different. The blank sample space means
"no restriction whatsoever." Here, the row $R$ being empty means $R$ is
*excluded* for every day. The correct reading is:

$$
A = \{\omega \in \Omega : \omega(d) \in \{S, C\} \text{ for all } d\}
$$

This is an example of a **negative condition** — a condition expressed by
prohibiting a state rather than requiring one. To represent it graphically
in a more informative way, one would mark $S$ and $C$ for every column
(showing the two allowed states), as done in Part B, Case 2.

**Counting outcomes**: Each of the 7 days independently takes one of 2
values ($S$ or $C$):

$$
|A| = 2^7 = 128
$$

This is only about $5.85\%$ of all $2187$ possible weeks — rain-free weeks
are relatively rare when each day has an equal chance of being rainy.

---

### Statement 5 — Thursday is not sunny

**Reading the condition**: Thursday must be in $\{C, R\}$ — any state except
$S$. All other days are unconstrained.

**Why a single mark is insufficient**: The condition allows Thursday to be
either $C$ or $R$. Since both states are permitted, we cannot mark a single
cell in the Thursday column. The event is again a union:

$$
A_1 = \{\omega : \omega(\text{Thu}) = C\}
\qquad \text{(Thursday is cloudy)}
$$

$$
A_2 = \{\omega : \omega(\text{Thu}) = R\}
\qquad \text{(Thursday is rainy)}
$$

$$
A = A_1 \cup A_2
$$

**Sub-event $A_1$** — Thursday is cloudy:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   X   .   .   .
R      .   .   .   .   .   .   .
```

**Sub-event $A_2$** — Thursday is rainy:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   X   .   .   .
```

Note that $A_1$ and $A_2$ are **disjoint** — a day cannot be both cloudy
and rainy — so $|A_1 \cap A_2| = 0$, and:

$$
|A| = |A_1| + |A_2| = 3^6 + 3^6 = 729 + 729 = 1458
$$

**Equivalent computation via complement**: The complement $A^c$ is the event
"Thursday is sunny." This fixes one day and leaves six free:

$$
|A^c| = 1 \cdot 3^6 = 729
$$

Therefore:

$$
|A| = |\Omega| - |A^c| = 2187 - 729 = 1458 \checkmark
$$

The complement method is often simpler for negation conditions: instead of
working with the excluded state directly, we compute the size of the
complement (which is a simple positive condition) and subtract.

---

## Part B — Interpretation of Given Tables

### Case 1

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   X   X
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Step-by-step reading of the table**:

We scan all cells. The only marks (`X`) appear at:
- Row $S$, column Sat — meaning Saturday is required to be sunny.
- Row $S$, column Sun — meaning Sunday is required to be sunny.

All other cells are `.`, so Monday through Friday carry no restriction
whatsoever.

**Event described**: Both Saturday and Sunday are sunny. The five weekdays
are completely unconstrained.

**Formal description**:

$$
A = \{\omega \in \Omega : \omega(\text{Sat}) = S \;\text{and}\; \omega(\text{Sun}) = S\}
$$

**Connection to set theory**: The conjunction "Saturday is sunny **and**
Sunday is sunny" corresponds to the **intersection** of two events:

$$
A = B_{\text{Sat}=S} \cap B_{\text{Sun}=S}
$$

where $B_{\text{Sat}=S} = \{\omega : \omega(\text{Sat}) = S\}$ and similarly
for Sunday.

**Counting outcomes**: Saturday and Sunday are each fixed to $S$ (1 choice
each). The remaining five days are each free (3 choices each):

$$
|A| = 1 \cdot 1 \cdot 3^5 = 243
$$

**Proportion of all weeks**: $243 / 2187 = 1/9 \approx 11.1\%$ of all possible
weeks have a fully sunny weekend. This makes sense: the probability that
both Saturday and Sunday are sunny (if states were equally likely) would be
$(1/3)^2 = 1/9$.

---

### Case 2

```
      Mon Tue Wed Thu Fri Sat Sun
S      X   X   X   X   X   X   X
C      X   X   X   X   X   X   X
R      .   .   .   .   .   .   .
```

**Step-by-step reading of the table**:

We scan all cells. For every column (every day of the week), both row $S$
and row $C$ are marked. Row $R$ is entirely empty — no day has $R$ marked.

This pattern is different from all previous ones. Instead of marking one
state per column (fixing a single state for that day), we mark *two* states
per column. The correct interpretation is:

- The event **allows** a day to be either $S$ or $C$.
- The event **forbids** $R$ on every day.

**Why double marks do not mean contradiction**: A double mark in a column
does not say "the day is simultaneously sunny and cloudy" — that would be
impossible. It says "the event does not distinguish between $S$ and $C$ for
this day; either state is compatible with the condition." Only one state is
actually realized; the double mark reflects the structure of the *event*,
not of a single *outcome*.

**Event described**: There is no rainy day throughout the entire week. Each
day may be sunny or cloudy, but not rainy.

**Formal description**:

$$
A = \{\omega \in \Omega : \omega(d) \neq R \;\text{for all}\; d \in \{\text{Mon},\ldots,\text{Sun}\}\}
$$

equivalently:

$$
A = \{\omega \in \Omega : \omega(d) \in \{S, C\} \;\text{for all}\; d\}
$$

**Connection to Part A, Statement 4**: This is precisely the same event
described in Statement 4. There we approached it as a negative condition
(prohibiting $R$); here the table makes it explicit by showing $S$ and $C$
as the two permitted states in every column. Both descriptions define the
same subset of $\Omega$.

**Counting outcomes**: Each of the 7 days independently takes one of 2
values ($S$ or $C$):

$$
|A| = 2^7 = 128
$$

**Proportion of all weeks**: $128 / 2187 \approx 5.85\%$. Only about 1 in 17
possible weeks is entirely rain-free.

**Complement interpretation**: The complement $A^c$ consists of all weeks
with **at least one rainy day**:

$$
|A^c| = 2187 - 128 = 2059
$$

So more than $94\%$ of all possible weekly weather sequences include at least
one rainy day.

---

## Final Result

| Part | Statement | Formal description | Outcome count |
|------|-----------|-------------------|---------------|
| A1 | Monday is sunny | $\omega(\text{Mon}) = S$ | $3^6 = 729$ |
| A2 | Weekend is rainy | $\omega(\text{Sat}) = R$ and $\omega(\text{Sun}) = R$ | $3^5 = 243$ |
| A3 | Rain on Wed or Fri | $\omega(\text{Wed}) = R$ or $\omega(\text{Fri}) = R$ | $1215$ |
| A4 | No rainy day | $\omega(d) \in \{S,C\}$ for all $d$ | $2^7 = 128$ |
| A5 | Thursday not sunny | $\omega(\text{Thu}) \neq S$ | $1458$ |
| B1 | Sat and Sun are sunny | $\omega(\text{Sat}) = S$ and $\omega(\text{Sun}) = S$ | $3^5 = 243$ |
| B2 | No rainy day | $\omega(d) \in \{S,C\}$ for all $d$ | $2^7 = 128$ |

---

## Interpretation / Sanity Check

**Check 1 — Complement of A5**:

$$
|\text{Thu not sunny}| + |\text{Thu sunny}| = 1458 + 729 = 2187 = |\Omega| \checkmark
$$

**Check 2 — Inclusion-exclusion for A3**:

$$
|A^c_{3}| = |\text{Wed not rainy and Fri not rainy}| = 2^2 \cdot 3^5 = 4 \cdot 243 = 972
$$

$$
|A_3| + |A^c_3| = 1215 + 972 = 2187 = |\Omega| \checkmark
$$

**Check 3 — Proportion checks**:

- A1: $729/2187 = 1/3$ — exactly one third of weeks have a sunny Monday. $\checkmark$
- A2: $243/2187 = 1/9$ — exactly one ninth of weeks have a rainy weekend. $\checkmark$
- B1: $243/2187 = 1/9$ — exactly one ninth of weeks have a sunny weekend. $\checkmark$

The symmetry between A2 and B1 is expected: both fix 2 specific days to
specific states, so both have size $3^5 = 243$.

---

## Common Mistakes

1. **Treating the table as a single outcome.** The table represents an
   *event* — a set of outcomes — not one particular weather sequence. Every
   unmarked column represents a day that can take any of the three states.

2. **Applying simple addition to overlapping events.** For Statement A3,
   one might incorrectly compute $|A| = 729 + 729 = 1458$ by simply adding
   $|A_1|$ and $|A_2|$. This double-counts the outcomes where both Wednesday
   and Friday are rainy. The correct formula always requires subtracting the
   intersection: $|A_1 \cup A_2| = |A_1| + |A_2| - |A_1 \cap A_2|$.

3. **Misreading double-marked columns.** When both $S$ and $C$ are marked
   in a column (as in Part B, Case 2), students sometimes think the table
   is describing two different things at once or that it is contradictory.
   The correct reading is: the event allows either state for that day; the
   specific state realized depends on the particular elementary outcome
   $\omega$.

4. **Confusing a negative condition with an empty table.** Statement A4
   ("no rainy day") produces a table where row $R$ is entirely empty. This
   looks like the blank starting table, but the meaning is entirely
   different: here $R$ is prohibited, whereas in the blank starting table
   every state is permitted. Always read the table together with its
   verbal description.

5. **Forgetting to use the complement for negation.** For Statement A5
   ("Thursday is not sunny"), the complement method is much cleaner than
   listing all allowed cases. Computing $|\Omega| - |\text{Thu is sunny}|$
   avoids the need to handle the two sub-events separately.