# Session 2 Exercises: Conditional Probability and Independence

Solve these by hand, exam style, without code. Give probabilities as exact fractions, with decimals where they help. Unless a problem says otherwise, dice are fair six-sided dice, separate dice and coins are independent, and "at random" means every possible choice is equally likely. A few problems supply logarithms or powers so that no calculator is needed.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 34 min |
| Exam-level | 5-9 | 63 min |
| Challenge | 10-12 | 60 min |

---

## Warm-up

### Problem 1. Languages at a company

**Tests:** set operations, inclusion-exclusion, conditional probability, sign of a correlation. **Time:** 8 min.

At a company, 45% of employees speak Spanish, 30% speak French, and 12% speak both. An employee is chosen at random.

(a) Find the probability that the employee speaks at least one of the two languages.

(b) Find the probability that the employee speaks Spanish but not French.

(c) Find the probability that the employee speaks neither language.

(d) Find $P(\text{French} \mid \text{Spanish})$. Are the two languages positively correlated, negatively correlated, or independent?

(e) Given that the employee speaks at least one of the two languages, find the probability that they speak Spanish.

### Problem 2. A loaded die

**Tests:** conditional probability as restricting the sample space, non-equiprobable spaces, symmetry of correlation. **Time:** 8 min.

A die is loaded so that face $k$ comes up with probability proportional to $k$: $P(k) = k/21$ for $k = 1, \dots, 6$.

(a) Check that these probabilities add to 1, and find $P(\text{even})$.

(b) Find $P(6 \mid \text{even})$.

(c) Write down the conditional PMF given that the roll is at least 4, and use it to find $P(\text{even} \mid \text{at least } 4)$.

(d) Are "even" and "at least 4" positively correlated, negatively correlated, or independent?

(e) Find $P(\text{at least } 4 \mid \text{even})$, and check that it agrees with your answer to (d).

### Problem 3. True or false

**Tests:** independence vs disjointness, the formal definition, complements, symmetry of correlation. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer with a short proof or a counterexample. All events live in the same sample space.

(a) If $A$ and $B$ are disjoint and both have positive probability, then $A$ and $B$ are independent.

(b) If $P(A) = 0$, then $A$ is independent of every event $B$.

(c) If $A$ and $B$ are independent, then $A^c$ and $B^c$ are independent.

(d) If $P(A) > 0$, $P(B) > 0$, and $P(A \mid B) > P(A)$, then $P(B \mid A) > P(B)$.

(e) If $A$ is independent of $B$ and $B$ is independent of $C$, then $A$ is independent of $C$.

### Problem 4. Marbles drawn one at a time

**Tests:** product rule, chain rule, sequential selection without replacement. **Time:** 8 min.

A bag holds 5 red, 3 white, and 2 green marbles. Three marbles are drawn one at a time without replacement.

(a) Use the chain rule to find the probability that all three are red. Confirm your answer by counting unordered selections.

(b) Find the probability that the marbles come out red, white, green, in that order.

(c) Find the probability that the three marbles have three different colors.

(d) Find the probability that all three have the same color.

(e) Repeat (a) when each marble is put back before the next draw. Explain in one sentence why the answer is larger.

---

## Exam-level

### Problem 5. A die with painted faces

**Tests:** pairwise vs mutual independence, conditional probability. **Time:** 12 min.

A fair four-sided die has one face painted red, one painted green, one painted blue, and the fourth face painted with all three colors. Roll it once and look at the face it lands on. Let $R$, $G$, $B$ be the events that this face shows red, green, and blue, respectively (the three-color face counts for all three).

(a) Find $P(R)$, $P(G)$, and $P(B)$.

(b) Show that $R$, $G$, $B$ are pairwise independent.

(c) Show that $R$, $G$, $B$ are not mutually independent.

(d) Find $P(B \mid R \cap G)$ and explain in words what it says.

(e) Is $R$ independent of $G \cup B$? If not, is the correlation positive or negative?

### Problem 6. The gambler's two bets

**Tests:** complement trick, independent repeated trials, the bound $1 - x \le e^{-x}$. **Time:** 12 min.

A gambler offers two bets. Bet 1 wins if at least one six appears in 4 rolls of a die. Bet 2 wins if at least one double six appears in 24 rolls of a pair of dice. He argues that the two bets must be equally good, since $4/6 = 24/36$.

(a) Find the probability of winning bet 1.

(b) Find the probability of winning bet 2. You may use $(35/36)^{24} \approx 0.5086$.

(c) Find the smallest number $n$ of rolls of a pair of dice for which the probability of at least one double six is at least $1/2$. You may use $\ln 2 \approx 0.6931$ and $\ln(36/35) \approx 0.02817$.

(d) Consider $n$ independent trials, each succeeding with probability $p$. Show that if $np \ge \ln 2$, then the probability of at least one success is at least $1/2$. (Hint: $1 - x \le e^{-x}$.) What does this guarantee for double sixes, and how does it compare with (c)?

### Problem 7. Birth months

**Tests:** the birthday problem, complement trick, chain rule. **Time:** 12 min.

Assume each person's birth month is equally likely to be any of the 12 months, independently of other people.

(a) Four people meet. Find the probability that at least two of them were born in the same month.

(b) Find the smallest group size $n$ for which a shared birth month has probability at least $1/2$.

(c) Compare (b) with the estimate $\sqrt{2 \cdot 12 \cdot \ln 2}$ from the birthday calculation.

(d) You are one of the four people in (a). Find the probability that at least one of the other three was born in your month. Explain why this is much smaller than the answer to (a).

(e) How many other people are needed before the probability that someone shares your birth month reaches $1/2$? You may use $(11/12)^7 \approx 0.5439$ and $(11/12)^8 \approx 0.4985$.

### Problem 8. Divisible by 2 and by 3

**Tests:** the formal definition of independence, independence within one experiment, true/false with justification. **Time:** 12 min.

An integer $X$ is chosen at random from $\lbrace 1, 2, \dots, n \rbrace$. Let $A$ = "$X$ is even" and $B$ = "$X$ is divisible by 3".

(a) For $n = 12$, show that $A$ and $B$ are independent.

(b) For $n = 10$, show that $A$ and $B$ are dependent. Is the correlation positive or negative?

(c) Show that $A$ and $B$ are independent whenever $n$ is a multiple of 6.

(d) True or false: if $n$ is not a multiple of 6, then $A$ and $B$ are dependent. Justify.

### Problem 9. Socks without a match

**Tests:** chain rule, sequential selection without replacement, complement trick, counting check. **Time:** 15 min.

A drawer holds 10 pairs of socks, all pairs different (20 socks in all). Socks are pulled out one at a time, at random, without replacement.

(a) Use the chain rule to find the probability that the first 4 socks contain no matching pair.

(b) Show that for $1 \le k \le 10$, the probability that the first $k$ socks contain no matching pair is
$$\prod_{i=0}^{k-1} \frac{20 - 2i}{20 - i}.$$
Confirm your answer to (a) by counting unordered selections of 4 socks.

(c) Find the smallest $k$ for which the first $k$ socks contain a matching pair with probability at least $1/2$.

(d) What is the smallest $k$ for which a matching pair is certain? Show that the product in (b), extended to $k = 11$, agrees.

---

## Challenge

### Problem 10. Two children

**Tests:** conditional probability as restricting the sample space, how the conditioning event is defined. **Time:** 20 min.

A family has two children. Each child is a boy or a girl with probability $1/2$ each and is born on any of the 7 days of the week with probability $1/7$ each, all independently.

(a) Given that at least one child is a girl, find the probability that both are girls.

(b) Given that the older child is a girl, find the probability that both are girls.

(c) Given that at least one child is a girl born on a Tuesday, find the probability that both are girls.

(d) More generally, suppose each girl has some trait with probability $q$, independently of everything else ($q = 1$ means no extra information, and $q = 1/7$ is "born on a Tuesday"). Show that
$$P(\text{both girls} \mid \text{at least one girl with the trait}) = \frac{2 - q}{4 - q}.$$
Check the formula against (a) and (c), find its limit as $q \to 0$, and explain why a rare trait pushes the answer toward (b).

### Problem 11. Shared birthdays: pairwise but not mutual

**Tests:** pairwise vs mutual independence, the birthday problem, true/false with justification. **Time:** 20 min.

$n$ people have independent birthdays, each equally likely to be any of 365 days. For persons $i \ne j$, let $M_{ij}$ be the event that $i$ and $j$ share a birthday, and let $D_n$ be the event that all $n$ birthdays are different.

(a) Find $P(M_{ij})$. Show that $M_{12}$ and $M_{13}$ are independent, and that $M_{12}$ and $M_{34}$ are independent. Conclude that the events $M_{ij}$ are pairwise independent.

(b) Show that $M_{12}$, $M_{13}$, $M_{23}$ are not mutually independent. Find $P(M_{23} \mid M_{12} \cap M_{13})$ and $P(M_{23} \mid M_{12} \cap M_{13}^c)$.

(c) If the $\binom{n}{2}$ events $M_{ij}^c$ were mutually independent, the probability of no shared birthday would be $q_n = (364/365)^{\binom{n}{2}}$. For $n = 3$, find $P(D_3)$ and $q_3$ exactly, and show that $P(D_3) < q_3$.

(d) True or false: since the events $M_{ij}$ are pairwise independent, $P(D_n) = (364/365)^{\binom{n}{2}}$ for every $n$. Justify, and comment on $n = 23$, where $P(D_{23}) \approx 0.4927$ and $(364/365)^{253} \approx 0.4995$.

### Problem 12. Bounding the chance of a collision

**Tests:** complement trick, chain rule, $1 - x \le e^{-x}$, union bound from inclusion-exclusion, "show that". **Time:** 20 min.

A system gives each of $n$ users an ID chosen at random from $N$ possible IDs, independently. Let $C$ be the event that two or more users get the same ID.

(a) Show that $1 - x \le e^{-x}$ for every real $x$.

(b) Show that $P(C) \ge 1 - \exp\left(-\dfrac{n(n-1)}{2N}\right)$.

(c) Inclusion-exclusion gives $P(E \cup F) \le P(E) + P(F)$. Extend this to any finite number of events, and use it to show that $P(C) \le \dfrac{n(n-1)}{2N}$.

(d) With $N = 10^6$ (six-digit IDs) and $n = 1000$ users, use (b) and (c) to trap $P(C)$ between two numbers. You may use $e^{-0.4995} \approx 0.6068$.

(e) With $N = 10^6$, find the smallest $n$ for which the bound in (b) guarantees $P(C) \ge 1/2$. You may use $2 \cdot 10^6 \cdot \ln 2 \approx 1{,}386{,}294$.
