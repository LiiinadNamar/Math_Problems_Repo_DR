# Problem 3 — Weather (7 days × 3 states)

## Problem Statement

Consider a week described day by day in terms of weather. Each day can be in
exactly one of three states: Sunny (S), Cloudy (C), or Rainy (R). The table
below is a graphical representation of a **single outcome** of a weekly weather
sequence — it is not a listing of all possible sequences. Marking a cell
$(w, d)$ means that on day $d$ the weather state is $w$.

The sample space $\Omega$ consists of all possible weekly weather sequences.
Since each of 7 days can independently take one of 3 states, the total number
of elementary outcomes is:

$$
|\Omega| = 3^7 = 2187
$$

Each elementary outcome is a function

$$
\omega : \{\text{Mon, Tue, Wed, Thu, Fri, Sat, Sun}\} \to \{S, C, R\}
$$

that assigns exactly one weather state to each day of the week.

---

## Definitions / Theory

**Elementary outcome**: A complete specification of the weather for every day
of the week. For example:

$$
\omega = (S, C, S, R, C, S, S)
$$

means: Monday sunny, Tuesday cloudy, Wednesday sunny, Thursday rainy, Friday
cloudy, Saturday sunny, Sunday sunny.

**Event**: Any subset $A \subseteq \Omega$. An event occurs when the realized
weekly sequence $\omega$ belongs to $A$.

**Graphical representation convention**: In the table below, rows correspond to
weather states $\{S, C, R\}$ and columns correspond to days of the week. A
cell $(w, d)$ is marked with `X` if the stated condition restricts day $d$ to
state $w$. A cell is left as `.` if the condition places no restriction on that
cell (any state is permitted there), or if that state is excluded for that day.

**Important**: The table does not represent one single outcome. It represents
a **constraint** — the set of all outcomes $\omega \in \Omega$ that satisfy the
described condition. An outcome belongs to the event if and only if for every
marked cell $(w, d)$, the outcome assigns state $w$ to day $d$.

---

## Part A — Marking Events

For each statement below, we identify which outcomes satisfy it and mark the
corresponding cells. A cell $(w, d)$ is marked `X` when the condition **forces**
day $d$ to be in state $w$. When the condition is silent about a day (any
state is allowed), all three cells in that column remain `.`.

---

### Statement 1 — Monday is sunny

The condition fixes exactly one day: Monday must be $S$. All other days are
unconstrained.

```
      Mon Tue Wed Thu Fri Sat Sun
S      X   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Interpretation**: Every weekly sequence in which Monday is sunny belongs to
this event, regardless of what happens on the remaining six days. The number
of such outcomes is $1 \cdot 3^6 = 729$.

---

### Statement 2 — The weekend (Saturday and Sunday) is rainy

Both Saturday and Sunday must be $R$. All weekdays are unconstrained.

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   X   X
```

**Interpretation**: The event consists of all sequences in which Saturday is
rainy **and** Sunday is rainy. The two conditions are joined by conjunction:

$$
A = \{\omega \in \Omega : \omega(\text{Sat}) = R \text{ and } \omega(\text{Sun}) = R\}
$$

The number of such outcomes is $3^5 \cdot 1 \cdot 1 = 243$.

---

### Statement 3 — It rains on Wednesday or Friday

This is a **disjunction**: at least one of Wednesday, Friday must be $R$.
The other days are unconstrained. We cannot mark both Wednesday and Friday
with a single pattern, because this event is not a simple rectangular
constraint — it is the union of two sub-events:

$$
A_1 = \{\omega : \omega(\text{Wed}) = R\}, \qquad A_2 = \{\omega : \omega(\text{Fri}) = R\}
$$

$$
A = A_1 \cup A_2
$$

It is cleaner to reason via the complement. The complement $A^c$ is:
**neither Wednesday nor Friday is rainy**, meaning both Wednesday and Friday
are in $\{S, C\}$. The table below marks the cells that are **forbidden**
(i.e., cells that must NOT be $R$ on those two days). Since marking
conventions show what is required — not what is forbidden — we state the
event verbally and note that no single ASCII marking can fully capture a
disjunction. However, we can represent the two generating sub-events:

Sub-event $A_1$: Wednesday is rainy (Friday unconstrained):

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   X   .   .   .   .
```

Sub-event $A_2$: Friday is rainy (Wednesday unconstrained):

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   X   .   .
```

The event $A = A_1 \cup A_2$ consists of all outcomes that appear in at
least one of the two tables above.

By inclusion-exclusion:

$$
|A| = |A_1| + |A_2| - |A_1 \cap A_2|
= 3^6 + 3^6 - 3^5
= 729 + 729 - 243 = 1215
$$

---

### Statement 4 — There is no rainy day during the week

Every day must be either $S$ or $C$. The row $R$ is entirely empty.

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Note on the representation**: The table above looks identical to the blank
sample space, yet its meaning is different. Here the empty $R$-row is not
"unconstrained" but "forbidden": no day may be rainy. The event is:

$$
A = \{\omega \in \Omega : \omega(d) \in \{S, C\} \text{ for all } d\}
$$

The number of such outcomes is $2^7 = 128$.

Since the convention of marking cells that are **required** cannot easily
express **prohibition**, we complement the description: this is the event
whose complement is "at least one rainy day." Equivalently, every column
is constrained to the two rows $S$ and $C$ only.

---

### Statement 5 — Thursday is not sunny

Thursday must be in $\{C, R\}$. Both $C$ and $R$ are allowed for Thursday;
all other days are unconstrained. Since this is again a disjunction for
Thursday (either $C$ or $R$), we show the two sub-events:

Sub-event: Thursday is cloudy:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   X   .   .   .
R      .   .   .   .   .   .   .
```

Sub-event: Thursday is rainy:

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   .   .
C      .   .   .   .   .   .   .
R      .   .   .   X   .   .   .
```

The event is the union of these two. Equivalently, via the complement:
the complement is "Thursday is sunny," which has $1 \cdot 3^6 = 729$
outcomes. Therefore:

$$
|A| = 3^7 - 3^6 = 2187 - 729 = 1458
$$

---

## Part B — Interpretation of Given Tables

### Case 1

```
      Mon Tue Wed Thu Fri Sat Sun
S      .   .   .   .   .   X   X
C      .   .   .   .   .   .   .
R      .   .   .   .   .   .   .
```

**Reading the table**: The marks appear in row $S$, columns Saturday and
Sunday. No other cells are marked.

**Event described**: Both Saturday and Sunday are sunny. The five weekdays
are completely unconstrained.

**Formal description**:

$$
A = \{\omega \in \Omega : \omega(\text{Sat}) = S \text{ and } \omega(\text{Sun}) = S\}
$$

**Size of the event**: The two weekend days are fixed ($S$ each), and the
remaining five days each independently take one of three values:

$$
|A| = 3^5 = 243
$$

**Interpretation**: This event captures all weekly sequences in which the
weekend is entirely sunny, regardless of what happens from Monday to Friday.

---

### Case 2

```
      Mon Tue Wed Thu Fri Sat Sun
S      X   X   X   X   X   X   X
C      X   X   X   X   X   X   X
R      .   .   .   .   .   .   .
```

**Reading the table**: For every day (all seven columns), both rows $S$ and
$C$ are marked, while row $R$ is entirely empty.

**Event described**: There is no rainy day throughout the entire week. Each
day may be either sunny or cloudy, but not rainy.

**Formal description**:

$$
A = \{\omega \in \Omega : \omega(d) \neq R \text{ for all } d \in \{\text{Mon},\ldots,\text{Sun}\}\}
$$

equivalently:

$$
A = \{\omega \in \Omega : \omega(d) \in \{S, C\} \text{ for all } d\}
$$

**Size of the event**: Each of the seven days independently takes one of two
values ($S$ or $C$):

$$
|A| = 2^7 = 128
$$

**Interpretation**: This event captures all rain-free weeks. Compared to the
full sample space of $2187$ outcomes, only $128$ sequences avoid rain entirely —
roughly $5.85\%$ of all possible weeks.

**Remark on the representation**: This case illustrates an important feature
of the graphical convention. Marking both $S$ and $C$ in a column does not
mean "the day is both sunny and cloudy simultaneously" (which would be
impossible). It means "the day is allowed to be either sunny or cloudy." The
table represents a **constraint on the set of outcomes**, not a description of
a single outcome. Only one state is realized per day; the double mark expresses
that the event does not distinguish between these two states for that day.

---

## Final Result

| Part | Statement | Outcome count |
|------|-----------|---------------|
| A1 | Monday is sunny | $3^6 = 729$ |
| A2 | Weekend is rainy | $3^5 = 243$ |
| A3 | Rain on Wednesday or Friday | $1215$ |
| A4 | No rainy day | $2^7 = 128$ |
| A5 | Thursday is not sunny | $1458$ |
| B1 | Saturday and Sunday are sunny | $3^5 = 243$ |
| B2 | No rainy day during the week | $2^7 = 128$ |

---

## Interpretation / Sanity Check

All event sizes are positive integers and do not exceed $|\Omega| = 2187$,
which is consistent with the requirement that events are subsets of $\Omega$.

The complement relation can be verified for Statement A5:

$$
|\text{"Thursday is not sunny"}| + |\text{"Thursday is sunny"}| = 1458 + 729 = 2187 = |\Omega| \checkmark
$$

For Statement A3, the inclusion-exclusion count is consistent:

$$
|A_1 \cup A_2| = 1215, \qquad |A_1 \cup A_2|^c = 2187 - 1215 = 972 = 2^2 \cdot 3^5
$$

The complement counts sequences in which **neither** Wednesday nor Friday
is rainy: each of those two days takes 2 values, the remaining five days
take 3 values each: $2^2 \cdot 3^5 = 4 \cdot 243 = 972$. This confirms
the inclusion-exclusion calculation.

---

## Common Mistakes

1. **Confusing "or" with a single rectangular constraint.** Statements
   involving disjunctions (e.g., "Wednesday or Friday is rainy") cannot be
   captured by marking a single set of cells. They require union of events,
   and inclusion-exclusion must be used to count outcomes.

2. **Misreading double-marked columns.** Marking both $S$ and $C$ in a
   column does not describe an impossible outcome. It describes the fact
   that the event does not constrain that day to a single state.

3. **Forgetting that the table represents a set, not one outcome.** The
   graphical representation shows which outcomes belong to an event, not
   the state of a single elementary outcome.

4. **Confusing "no restriction" with "any restriction."** A column where
   all three cells are `.` means the event is completely silent about
   that day (all three states are allowed). A column where only certain
   rows are marked means only those states are permitted for that day.
