# Session 2 Solutions: Conditional Probability and Independence

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given as an exact fraction and a decimal (rounded to 4 significant digits). Try each problem first.

---

## Warm-up

### Problem 1. Languages at a company

Let $S$ = "speaks Spanish" and $F$ = "speaks French", with $P(S) = 0.45$, $P(F) = 0.30$, $P(S \cap F) = 0.12$.

**(a)** Inclusion-exclusion:

$$P(S \cup F) = 0.45 + 0.30 - 0.12 = 0.63 = \frac{63}{100}.$$

**(b)** Set difference: $P(S - F) = P(S) - P(S \cap F) = 0.45 - 0.12 = 0.33 = \frac{33}{100}$.

**(c)** Complement of (a): $P(\text{neither}) = 1 - 0.63 = 0.37 = \frac{37}{100}$.

As a check, the four regions are Spanish only 33%, French only $30 - 12 = 18\%$, both 12%, neither 37%, and they add to 100%.

**(d)**

$$P(F \mid S) = \frac{P(S \cap F)}{P(S)} = \frac{0.12}{0.45} = \frac{4}{15} \approx 0.2667 < 0.30 = P(F).$$

The languages are **negatively correlated**. Equivalently, $P(S \cap F) = 0.12 < 0.45 \cdot 0.30 = 0.135$.

**(e)** $S \subseteq S \cup F$, so $S \cap (S \cup F) = S$ and

$$P(S \mid S \cup F) = \frac{P(S)}{P(S \cup F)} = \frac{0.45}{0.63} = \frac{5}{7} \approx 0.7143.$$

**Key idea:** "at least one" is inclusion-exclusion, "neither" is its complement, and the sign of a correlation comes from comparing $P(F \mid S)$ with $P(F)$.

### Problem 2. A loaded die

**(a)** $\frac{1 + 2 + \cdots + 6}{21} = \frac{21}{21} = 1$, and

$$P(\text{even}) = \frac{2 + 4 + 6}{21} = \frac{12}{21} = \frac{4}{7} \approx 0.5714.$$

**(b)** Restrict to $\lbrace 2, 4, 6 \rbrace$, whose weights are in ratio $2 : 4 : 6$:

$$P(6 \mid \text{even}) = \frac{6/21}{12/21} = \frac{1}{2} = 0.5.$$

Counting faces would give $1/3$, which is wrong because the space is not equiprobable.

**(c)** $P(\text{at least } 4) = \frac{4 + 5 + 6}{21} = \frac{15}{21} = \frac{5}{7}$. Dividing the remaining weights by $15/21$ gives the conditional PMF

| $k$ | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| $P(k \mid \text{at least } 4)$ | 0 | 0 | 0 | $4/15$ | $1/3$ | $2/5$ |

so

$$P(\text{even} \mid \text{at least } 4) = \frac{4}{15} + \frac{6}{15} = \frac{2}{3} \approx 0.6667.$$

**(d)** $2/3 \approx 0.667 > 4/7 \approx 0.571 = P(\text{even})$, so the events are **positively correlated**. In product form: $P(\text{even} \cap \text{at least } 4) = 10/21 \approx 0.476$, which exceeds $P(\text{even})\,P(\text{at least } 4) = \frac{4}{7} \cdot \frac{5}{7} = \frac{20}{49} \approx 0.408$.

**(e)**

$$P(\text{at least } 4 \mid \text{even}) = \frac{10/21}{12/21} = \frac{5}{6} \approx 0.8333 > \frac{5}{7} \approx 0.7143 = P(\text{at least } 4).$$

Positive again, as it must be: correlation of events is symmetric.

**Key idea:** conditioning keeps the outcomes of $E$ with their relative weights and divides by $P(E)$. Count outcomes only in an equiprobable space.

### Problem 3. True or false

**(a) False.** If $A \cap B = \emptyset$, then $P(A \cap B) = 0 < P(A)P(B)$. For example, on a die $A = \lbrace 1 \rbrace$ and $B = \lbrace 2 \rbrace$ give $0 \ne 1/36$. Disjoint events with positive probability are negatively correlated: $P(B \mid A) = 0 < P(B)$.

**(b) True.** $A \cap B \subseteq A$, so $0 \le P(A \cap B) \le P(A) = 0$. Hence $P(A \cap B) = 0 = P(A)P(B)$.

**(c) True.**

$$P(A^c \cap B^c) = P\big((A \cup B)^c\big) = 1 - P(A) - P(B) + P(A)P(B) = \big(1 - P(A)\big)\big(1 - P(B)\big) = P(A^c)\,P(B^c).$$

**(d) True.** Multiply $P(A \cap B)/P(B) > P(A)$ by $P(B) > 0$ to get $P(A \cap B) > P(A)P(B)$, then divide by $P(A) > 0$ to get $P(B \mid A) > P(B)$.

**(e) False.** Toss two coins and let $A = C = H_1$ (first toss heads) and $B = H_2$. Separate tosses are independent, so $A \perp\!\!\!\perp B$ and $B \perp\!\!\!\perp C$. But $P(A \cap C) = P(H_1) = 1/2 \ne 1/4 = P(A)P(C)$. In general, an event is independent of itself only if $P(A) = P(A)^2$, that is, $P(A) \in \lbrace 0, 1 \rbrace$.

**Key idea:** independence is the product equation. Disjointness is the opposite extreme. Independence carries over to complements but is not transitive.

### Problem 4. Marbles drawn one at a time

At each draw, the numerator counts the marbles of the wanted color still in the bag, and the denominator counts all marbles still in the bag.

**(a)**

$$P(\text{all red}) = \frac{5}{10} \cdot \frac{4}{9} \cdot \frac{3}{8} = \frac{60}{720} = \frac{1}{12} \approx 0.08333.$$

Counting check: $\binom{5}{3} / \binom{10}{3} = 10/120 = 1/12$.

**(b)**

$$P(\text{red, white, green}) = \frac{5}{10} \cdot \frac{3}{9} \cdot \frac{2}{8} = \frac{30}{720} = \frac{1}{24} \approx 0.04167.$$

**(c)** Every one of the $3! = 6$ color orders has numerators 5, 3, 2 in some order over denominators $10, 9, 8$, so each has probability $1/24$:

$$P(\text{three colors}) = 6 \cdot \frac{1}{24} = \frac{1}{4} = 0.25.$$

Counting check: $\frac{5 \cdot 3 \cdot 2}{\binom{10}{3}} = \frac{30}{120} = \frac{1}{4}$.

**(d)** All red has probability $60/720$, all white $\frac{3}{10} \cdot \frac{2}{9} \cdot \frac{1}{8} = \frac{6}{720}$, and all green is impossible with only 2 green marbles:

$$P(\text{same color}) = \frac{60 + 6}{720} = \frac{11}{120} \approx 0.09167.$$

**(e)** With replacement every draw is red with probability $1/2$, independently: $(1/2)^3 = 1/8 = 0.125$. Without replacement, each red marble drawn makes red scarcer ($P(R_2 \mid R_1) = 4/9 < 1/2$), so the draws are negatively correlated and "all red" is less likely.

**Key idea:** chain rule for draws without replacement: multiply (wanted ones left) / (total left) at each step.

---

## Exam-level

### Problem 5. A die with painted faces

Call the faces $r, g, b, t$ ($t$ is the three-color face), each with probability $1/4$. Then $R = \lbrace r, t \rbrace$, $G = \lbrace g, t \rbrace$, $B = \lbrace b, t \rbrace$.

**(a)** $P(R) = P(G) = P(B) = 2/4 = 1/2$.

**(b)** Each pairwise intersection is $\lbrace t \rbrace$: $P(R \cap G) = P(R \cap B) = P(G \cap B) = \frac{1}{4} = \frac{1}{2} \cdot \frac{1}{2}$. All three pairs are independent.

**(c)** $R \cap G \cap B = \lbrace t \rbrace$, so $P(R \cap G \cap B) = \frac{1}{4} \ne \frac{1}{8} = P(R)P(G)P(B)$. The events are not mutually independent.

**(d)**

$$P(B \mid R \cap G) = \frac{P(\lbrace t \rbrace)}{P(\lbrace t \rbrace)} = 1 \ne \frac{1}{2} = P(B).$$

A face that shows both red and green must be the three-color face, so blue is certain. Either event alone says nothing about blue ($P(B \mid R) = 1/2$), but together they decide it.

**(e)** $G \cup B = \lbrace g, b, t \rbrace$ has probability $3/4$, and $R \cap (G \cup B) = \lbrace t \rbrace$ has probability $1/4 \ne \frac{1}{2} \cdot \frac{3}{4} = \frac{3}{8}$. So $R$ and $G \cup B$ are **dependent**, and

$$P(R \mid G \cup B) = \frac{1/4}{3/4} = \frac{1}{3} \approx 0.3333 < \frac{1}{2},$$

a **negative** correlation: knowing that green or blue shows rules out the red-only face. Under mutual independence this could not happen, since then $P(R \cap (G \cup B)) = P(R \cap G) + P(R \cap B) - P(R \cap G \cap B) = P(R)\big[P(G) + P(B) - P(G)P(B)\big] = P(R)\,P(G \cup B)$.

**Key idea:** pairwise independence controls what one event says about another. Combined information, such as $R \cap G$ or $G \cup B$, can still be informative unless the events are mutually independent.

### Problem 6. The gambler's two bets

**(a)** Complement: no six in 4 independent rolls has probability $(5/6)^4 = 625/1296$, so

$$P(\text{win bet 1}) = 1 - \frac{625}{1296} = \frac{671}{1296} \approx 0.5177.$$

**(b)** A roll of two dice is a double six with probability $1/36$. Complement again:

$$P(\text{win bet 2}) = 1 - \left(\frac{35}{36}\right)^{24} \approx 1 - 0.5086 = 0.4914.$$

(The exact fraction has a 38-digit denominator, so leave it as $1 - (35/36)^{24}$.) Bet 1 is favorable and bet 2 is slightly unfavorable, so the two bets are not equivalent.

**(c)** We need $(35/36)^n \le 1/2$, that is, $n \ln(36/35) \ge \ln 2$:

$$n \ge \frac{0.6931}{0.02817} \approx 24.6, \qquad \text{so } n = 25.$$

Check: $1 - (35/36)^{25} \approx 0.5055$, while $n = 24$ gives $0.4914$ from (b).

**(d)** By independence and $1 - p \le e^{-p}$,

$$P(\text{no success}) = (1 - p)^n \le e^{-np} \le e^{-\ln 2} = \frac{1}{2} \quad \text{whenever } np \ge \ln 2,$$

so $P(\text{at least one success}) \ge 1/2$. For double sixes, $n \ge 36 \ln 2 \approx 24.95$ guarantees it, so $n = 25$, exactly the answer to (c). The bound is tight here because $p = 1/36$ is small and $1 - p \approx e^{-p}$. The gambler's rule keeps $np = 2/3$, just short of $\ln 2 \approx 0.693$. That costs him on bet 2. Bet 1 survives only because $p = 1/6$ is not small, so $(5/6)^4 \approx 0.4823$ is well below $e^{-2/3} \approx 0.5134$.

**Key idea:** turn "at least one" into its complement "none", which is a product over independent trials. Then $(1 - p)^n \le e^{-np}$ gives the rule of thumb $n \approx \ln 2 / p$ for even odds.

### Problem 7. Birth months

**(a)** Complement plus chain rule: the second person avoids the first month with probability $11/12$, the third avoids both earlier months with probability $10/12$, and the fourth avoids three months with probability $9/12$:

$$P(\text{all different}) = \frac{11}{12} \cdot \frac{10}{12} \cdot \frac{9}{12} = \frac{990}{1728} = \frac{55}{96}, \qquad P(\text{shared month}) = 1 - \frac{55}{96} = \frac{41}{96} \approx 0.4271.$$

**(b)** Four people give $0.4271 < 1/2$. A fifth person must avoid 4 months, a factor of $8/12$:

$$P(\text{all different, } n = 5) = \frac{55}{96} \cdot \frac{8}{12} = \frac{55}{144}, \qquad P(\text{shared month}) = \frac{89}{144} \approx 0.6181.$$

So the smallest group size is $n = 5$.

**(c)** $\sqrt{2 \cdot 12 \cdot \ln 2} = \sqrt{16.64} \approx 4.08$, and the first integer above it is 5, in agreement with (b).

**(d)** Each of the other three misses your month with probability $11/12$, independently:

$$P = 1 - \left(\frac{11}{12}\right)^3 = 1 - \frac{1331}{1728} = \frac{397}{1728} \approx 0.2297.$$

In (a), a match can come from any of the $\binom{4}{2} = 6$ pairs. Here only the 3 pairs that include you count.

**(e)** We need $(11/12)^m \le 1/2$. Since $(11/12)^7 \approx 0.5439 > 1/2$ and $(11/12)^8 \approx 0.4985 \le 1/2$, the answer is **8 other people**, with

$$P = 1 - \left(\frac{11}{12}\right)^8 = \frac{215622815}{429981696} \approx 0.5015.$$

A shared month among *some* two people needs 5 people, but a match with *you* needs 9 people in total.

**Key idea:** complement plus chain rule gives $\prod (1 - i/12)$. The number of pairs grows like $n^2/2$, so a match between some two people arrives much sooner than a match with one particular person.

### Problem 8. Divisible by 2 and by 3

$X$ is even and divisible by 3 exactly when it is divisible by 6.

**(a)** For $n = 12$: $P(A) = 6/12 = 1/2$, $P(B) = |\lbrace 3, 6, 9, 12 \rbrace|/12 = 1/3$, and $P(A \cap B) = |\lbrace 6, 12 \rbrace|/12 = 1/6 = \frac{1}{2} \cdot \frac{1}{3}$. Independent.

**(b)** For $n = 10$: $P(A) = 5/10 = 1/2$, $P(B) = |\lbrace 3, 6, 9 \rbrace|/10 = 3/10$, and $P(A \cap B) = |\lbrace 6 \rbrace|/10 = 1/10$. Since $\frac{1}{10} \ne \frac{1}{2} \cdot \frac{3}{10} = \frac{3}{20}$, the events are dependent, and

$$P(B \mid A) = \frac{1/10}{1/2} = \frac{1}{5} = 0.2 < \frac{3}{10} = P(B),$$

a **negative** correlation. Among the even numbers up to 10, only 6 is a multiple of 3, while the multiple 9 is odd.

**(c)** If $n = 6m$, then $\lbrace 1, \dots, n \rbrace$ contains $3m$ even numbers, $2m$ multiples of 3, and $m$ multiples of 6. So $P(A) = 1/2$, $P(B) = 1/3$, and $P(A \cap B) = 1/6 = P(A)P(B)$.

**(d) False.** For $n = 8$: $P(A) = 4/8 = 1/2$, $P(B) = |\lbrace 3, 6 \rbrace|/8 = 1/4$, and $P(A \cap B) = |\lbrace 6 \rbrace|/8 = 1/8 = \frac{1}{2} \cdot \frac{1}{4}$. The events are independent although 8 is not a multiple of 6. (Checking every $n \le 20$, independence holds exactly for $n = 1, 2, 6, 8, 12, 14, 18, 20$. For $n = 1$ or $2$ one of the events has probability 0.)

**Key idea:** independence is an exact numerical equation about one probability model. Inside a single experiment it can hold or fail by arithmetic, not because the events are physically "unrelated".

### Problem 9. Socks without a match

**(a)** Let $N_i$ = "sock $i$ does not match any earlier sock". After 1 sock, 19 remain and 1 of them is its mate. After 2 unmatched socks, 18 remain and 2 are mates. After 3, 17 remain and 3 are mates. So

$$P(\text{no pair in 4}) = 1 \cdot \frac{18}{19} \cdot \frac{16}{18} \cdot \frac{14}{17} = \frac{16 \cdot 14}{19 \cdot 17} = \frac{224}{323} \approx 0.6935.$$

**(b)** Suppose the first $i$ socks come from $i$ different pairs. Then $20 - i$ socks remain, and $i$ of them are mates of socks already drawn. The next sock keeps the run going with probability $\frac{(20 - i) - i}{20 - i} = \frac{20 - 2i}{20 - i}$. The chain rule over $i = 0, 1, \dots, k-1$ gives the product.

Counting check for $k = 4$: an unordered selection of 4 socks without a pair picks 4 of the 10 pairs, then one sock from each, so there are $2^4 \binom{10}{4}$ of them:

$$\frac{2^4 \binom{10}{4}}{\binom{20}{4}} = \frac{16 \cdot 210}{4845} = \frac{3360}{4845} = \frac{224}{323}.$$

**(c)** Extend the product one factor at a time:

| $k$ | new factor | $P(\text{no pair})$ | $P(\text{pair})$ |
|---|---|---|---|
| 4 | | $224/323$ | $99/323 \approx 0.3065$ |
| 5 | $12/16$ | $168/323$ | $155/323 \approx 0.4799$ |
| 6 | $10/15$ | $112/323$ | $211/323 \approx 0.6533$ |

The smallest such $k$ is $k = 6$, with probability $211/323 \approx 0.6533$.

**(d)** $k = 11$: by the pigeonhole principle, 11 socks from 10 pairs must include two from the same pair. In the product, the factor for $i = 10$ is $\frac{20 - 20}{20 - 10} = 0$, so the probability of no pair is 0.

**Key idea:** complement ("no pair") plus chain rule. Each factor is (socks that keep the run going) / (socks left), the same structure as the birthday problem but without replacement.

---

## Challenge

### Problem 10. Two children

Order the children as (older, younger).

**(a)** The four sex patterns BB, BG, GB, GG are equally likely. "At least one girl" restricts the space to $\lbrace \text{BG}, \text{GB}, \text{GG} \rbrace$, and only one of these is GG:

$$P(\text{GG} \mid \text{at least one girl}) = \frac{1}{3} \approx 0.3333.$$

**(b)** "Older is a girl" restricts to $\lbrace \text{GB}, \text{GG} \rbrace$:

$$P(\text{GG} \mid \text{older is a girl}) = \frac{1}{2} = 0.5.$$

**(c)** Each child has 14 equally likely (sex, day) types, so the $14^2 = 196$ families are equally likely. Let a "T-girl" be a girl born on a Tuesday. By inclusion-exclusion, the number of families with at least one T-girl is $14 + 14 - 1 = 27$ (older is a T-girl, younger is a T-girl, both). Among them, the two-girl families number $7 + 7 - 1 = 13$ (older is a T-girl and younger is any of 7 girl types, the same with roles swapped, minus the double count). So

$$P(\text{GG} \mid \text{at least one T-girl}) = \frac{13}{27} \approx 0.4815.$$

**(d)** A given child is a girl with the trait with probability $q/2$, so by the complement,

$$P(\text{at least one girl with the trait}) = 1 - \left(1 - \frac{q}{2}\right)^2 = q - \frac{q^2}{4} = \frac{q(4 - q)}{4}.$$

Both girls and at least one with the trait: $P(\text{GG}) \cdot P(\text{at least one of two girls has it}) = \frac{1}{4}\big(1 - (1 - q)^2\big) = \frac{q(2 - q)}{4}$. Dividing,

$$P(\text{GG} \mid \text{at least one girl with the trait}) = \frac{q(2 - q)/4}{q(4 - q)/4} = \frac{2 - q}{4 - q}.$$

Checks: $q = 1$ gives $1/3$, as in (a); $q = 1/7$ gives $\frac{13/7}{27/7} = \frac{13}{27}$, as in (c). As $q \to 0$ the formula tends to $2/4 = 1/2$, the answer to (b).

**Why.** When the trait is rare, it is very unlikely that both children have it. The condition then effectively points at one particular child, the one with the trait, and says that she is a girl. The other child's sex is independent of that, so it is a girl with probability $1/2$, as in (b), where the condition also names a specific child. With $q = 1$, "at least one girl" names no child, and the restricted space keeps two mixed families (BG, GB) for every GG.

**Key idea:** $P(F \mid E)$ depends on exactly which event $E$ you condition on. Restrict to $E$ and count; "at least one is a girl" is a different event from "this one is a girl".

### Problem 11. Shared birthdays: pairwise but not mutual

**(a)** Whatever $i$'s birthday is, $j$ matches it with probability $1/365$, so $P(M_{ij}) = 1/365$.

- $M_{12} \cap M_{13}$ means persons 2 and 3 both match person 1, which has probability $\frac{1}{365} \cdot \frac{1}{365} = P(M_{12})P(M_{13})$.
- $M_{12}$ and $M_{34}$ depend on disjoint groups of people with independent birthdays, so $P(M_{12} \cap M_{34}) = \frac{1}{365^2} = P(M_{12})P(M_{34})$.

Two different pair events share either exactly one person (like $M_{12}, M_{13}$) or none (like $M_{12}, M_{34}$). By symmetry every such pair is covered by one of these two cases, so the events $M_{ij}$ are pairwise independent.

**(b)** If $b_1 = b_2$ and $b_1 = b_3$, then $b_2 = b_3$. So $M_{12} \cap M_{13} \subseteq M_{23}$ and

$$P(M_{12} \cap M_{13} \cap M_{23}) = P(M_{12} \cap M_{13}) = \frac{1}{365^2} \ne \frac{1}{365^3}.$$

Not mutually independent. Moreover, $P(M_{23} \mid M_{12} \cap M_{13}) = 1$. And if $b_2 = b_1 \ne b_3$, then $b_2 \ne b_3$, so $P(M_{23} \mid M_{12} \cap M_{13}^c) = 0$. Both differ sharply from $P(M_{23}) = 1/365 \approx 0.002740$.

**(c)**

$$P(D_3) = \frac{364}{365} \cdot \frac{363}{365} = \frac{132132}{133225} \approx 0.9918, \qquad q_3 = \left(\frac{364}{365}\right)^3 = \frac{48228544}{48627125} \approx 0.9918.$$

They agree to 4 digits, but

$$\frac{P(D_3)}{q_3} = \frac{363 \cdot 365}{364^2} = \frac{(364 - 1)(364 + 1)}{364^2} = \frac{364^2 - 1}{364^2} < 1,$$

so $P(D_3) < q_3$. The exact gap is $q_3 - P(D_3) = \frac{364}{365^3} = \frac{364}{48627125} \approx 7.486 \times 10^{-6}$.

**(d) False.** Already for $n = 3$, part (c) shows $P(D_3) \ne q_3$. Pairwise independence justifies multiplying probabilities for two events at a time. "No pair matches" is an intersection of $\binom{n}{2}$ events, and multiplying their probabilities requires mutual independence, which fails by (b). Still, the dependence only appears through triangles of people, so it is weak: at $n = 23$ the pair formula gives $0.4995$ against the true $0.4927$. That is close enough to explain why the heuristic "$\binom{n}{2}$ pairs, each matching with probability $1/365$" works so well.

**Key idea:** the matching events are pairwise independent but not mutually independent. That is why $(364/365)^{\binom{n}{2}}$ is an excellent but not exact stand-in for $P(D_n)$.

### Problem 12. Bounding the chance of a collision

**(a)** Let $f(x) = e^{-x} - (1 - x)$. Then $f(0) = 0$ and $f'(x) = 1 - e^{-x}$, which is negative for $x < 0$ and positive for $x > 0$. So $f$ decreases to its minimum $f(0) = 0$ and then increases, giving $f(x) \ge 0$ for all $x$.

**(b)** If $n > N$, then $P(C) = 1$ and there is nothing to prove. Otherwise use the complement and the chain rule, exactly as for birthdays. User $i + 1$ avoids the $i$ IDs already taken with probability $1 - i/N$, so

$$P(C^c) = \prod_{i=1}^{n-1} \left(1 - \frac{i}{N}\right) \le \prod_{i=1}^{n-1} e^{-i/N} = \exp\left(-\frac{1}{N} \sum_{i=1}^{n-1} i\right) = \exp\left(-\frac{n(n-1)}{2N}\right).$$

Multiplying the inequalities factor by factor is valid because all factors are nonnegative. Hence $P(C) = 1 - P(C^c) \ge 1 - \exp\left(-\frac{n(n-1)}{2N}\right)$.

**(c)** By induction, $P(E_1 \cup \cdots \cup E_m) \le P(E_1 \cup \cdots \cup E_{m-1}) + P(E_m) \le \cdots \le \sum_{i=1}^{m} P(E_i)$. Now $C = \bigcup_{i < j} M_{ij}$, where $M_{ij}$ = "users $i$ and $j$ get the same ID" has probability $1/N$. There are $\binom{n}{2}$ pairs, so

$$P(C) \le \binom{n}{2} \frac{1}{N} = \frac{n(n-1)}{2N}.$$

**(d)** Here $\frac{n(n-1)}{2N} = \frac{1000 \cdot 999}{2 \cdot 10^6} = \frac{999}{2000} = 0.4995$. So

$$0.3932 \approx 1 - e^{-0.4995} \le P(C) \le \frac{999}{2000} = 0.4995.$$

The exact value is about $0.3933$, so the lower bound is nearly exact. The union bound counts a configuration with several matching pairs more than once, which is why it overshoots.

**(e)** We need $n(n-1) \ge 2 \cdot 10^6 \ln 2 \approx 1{,}386{,}294$. Since $\sqrt{1{,}386{,}294} \approx 1177.4$, try nearby values: $1177 \cdot 1176 = 1{,}384{,}152$ is too small, and $1178 \cdot 1177 = 1{,}386{,}506$ is enough. So $n = 1178$, about $\sqrt{N}$ times $1.18$, compared with the million available IDs.

**Key idea:** the birthday calculation works for any number $N$ of equally likely values. Collisions become likely around $n \approx \sqrt{2N \ln 2}$, and the union bound shows they stay unlikely while $n \ll \sqrt{2N}$.
