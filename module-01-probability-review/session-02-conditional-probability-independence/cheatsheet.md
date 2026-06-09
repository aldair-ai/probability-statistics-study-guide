# Session 2 Cheatsheet: Conditional Probability and Independence

## Combining events

- **Complement:** $P(A^c) = 1 - P(A)$. **Difference:** $P(A - B) = P(A) - P(A \cap B)$.
- **Union (inclusion-exclusion):** $P(A \cup B) = P(A) + P(B) - P(A \cap B)$; just add if disjoint. **Union bound:** $P(\bigcup_i E_i) \le \sum_i P(E_i)$.

## Conditional probability

- $P(F \mid E) = \dfrac{P(E \cap F)}{P(E)}$ for $P(E) > 0$. **Restrict** to $E$, **rescale** by $1/P(E)$: $P(x \mid E) = P(x)/P(E)$ on $E$, 0 off $E$.
- Equiprobable only: $P(F \mid E) = \lvert E \cap F \rvert / \lvert E \rvert$. $P(\cdot \mid E)$ is a probability: $P(F^c \mid E) = 1 - P(F \mid E)$.
- **Correlation:** $P(F \mid E) >, =, < P(F)$ (positive, independent, negative), equivalently $P(E \cap F) >, =, < P(E)P(F)$. Symmetric in $E$ and $F$. Die, $F = \lbrace 5, 6 \rbrace$: given $\lbrace 6 \rbrace$ 1, given even $1/3$, given $\le 4$ 0.

## Independence

| | Informal $P(F \mid E) = P(F)$ | Formal $P(E \cap F) = P(E)\,P(F)$ |
|---|---|---|
| Symmetric | needs a proof | by inspection |
| $P(E) = 0$ | undefined | always independent |

- $E \perp\!\!\!\perp F \Rightarrow E \perp\!\!\!\perp F^c$ and $E^c \perp\!\!\!\perp F^c$. Separate experiments are independent; one experiment can also have independent events (die: square $\lbrace 1, 4 \rbrace$ and odd).
- **Three events.** Pairwise: 3 pair equations. Mutual: pairs **plus** $P(A \cap B \cap C) = P(A)P(B)P(C)$ (for $n$ events: every subcollection, $2^n - n - 1$ equations). Two dice, $A$ = 1st odd, $B$ = 2nd odd, $C$ = sum even: pairwise, but $P(C \mid A \cap B) = 1$.

## Product and chain rules

- $P(E \cap F) = P(E)\,P(F \mid E)$, and $P(E_1 \cap \cdots \cap E_n) = P(E_1)\,P(E_2 \mid E_1) \cdots P(E_n \mid E_1 \cap \cdots \cap E_{n-1})$.
- Draws without replacement: each factor = (wanted ones left)/(total left). Urn with 1 blue and 2 red: $\frac{2}{3} \cdot \frac{1}{2} = \frac{1}{3}$. Three hearts: $\frac{13}{52} \cdot \frac{12}{51} \cdot \frac{11}{50} = \frac{11}{850}$.

## Birthday problem ($n$ people, $N$ equally likely days)

- $P(\text{all different}) = \prod_{i=1}^{n-1}\left(1 - \frac{i}{N}\right) = \frac{N(N-1)\cdots(N-n+1)}{N^n} \le e^{-n(n-1)/(2N)} \approx e^{-n^2/(2N)}$, using $1 - x \le e^{-x}$.
- Even odds at $n \approx \sqrt{2N \ln 2} \approx 1.18\sqrt{N}$. Match with *one given* person: $1 - (1 - 1/N)^m$, needs $m \approx N \ln 2$ (253 for $N = 365$).
- Why $\sqrt{N}$: $\binom{n}{2} \approx n^2/2$ pairs, each matching with probability $1/N$. The pair events are pairwise but not mutually independent.

| $n$ | 10 | 20 | 22 | **23** | 30 | 40 | 57 |
|---|---|---|---|---|---|---|---|
| $P(\text{shared}),\ N = 365$ | 0.117 | 0.411 | 0.476 | **0.507** | 0.706 | 0.891 | 0.990 |

## Which tool when

| Situation | Tool |
|---|---|
| "at least one", "neither", "not all" | complement |
| "A or B" with overlap | inclusion-exclusion |
| extra information shrinks the outcomes | restrict and rescale, $P(E \cap F)/P(E)$ |
| a step-by-step experiment, draws without replacement | chain rule |
| physically separate trials | independence, multiply |
| "are they independent?" | test $P(E \cap F) = P(E)P(F)$; for 3 events test all 4 equations |
| "all different", "no collision" | complement + chain rule, then $1 - x \le e^{-x}$ |

## Traps

1. **Disjoint is not independent.** Disjoint events with positive probability are negatively correlated.
2. **Pairwise does not imply mutual.** Check the triple equation too (and the triple alone is not enough either).
3. **Counting in a non-equiprobable space.** Loaded 4-sided die: $P(\ge 2 \mid \le 3) = 0.5/0.6 = 5/6$, not $2/3$.
4. **$P(F \mid E)$, $P(E \mid F)$, $P(E \cap F)$ are different.** Die: $P(\text{square} \mid \text{odd}) = 1/3$, $P(\text{odd} \mid \text{square}) = 1/2$, $P(\text{both}) = 1/6$.
5. **Wrong birthday question.** "Any two share" (23 people) is not "someone shares mine" (253 others).
