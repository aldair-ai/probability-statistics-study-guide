# Session 3 Solutions: Bayes, Random Variables, Expectation

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given as an exact fraction and a decimal (rounded to 4 significant digits). Try each problem first.

---

## Warm-up

### Problem 1. Three coins in a box

The three coins partition the experiment: write $C_f$ (fair), $C_2$ (two-headed), $C_b$ (bent), each with prior $1/3$. The likelihoods of heads are $P(H \mid C_f) = 1/2$, $P(H \mid C_2) = 1$, $P(H \mid C_b) = 1/4$.

**(a)** By the law of total probability,

$$P(H) = \frac{1}{3} \cdot \frac{1}{2} + \frac{1}{3} \cdot 1 + \frac{1}{3} \cdot \frac{1}{4} = \frac{1}{3} \cdot \frac{7}{4} = \frac{7}{12} \approx 0.5833.$$

**(b)** By Bayes' rule, each posterior is (prior times likelihood) divided by $P(H) = 7/12$:

$$P(C_f \mid H) = \frac{1/6}{7/12} = \frac{2}{7} \approx 0.2857, \qquad P(C_2 \mid H) = \frac{1/3}{7/12} = \frac{4}{7} \approx 0.5714, \qquad P(C_b \mid H) = \frac{1/12}{7/12} = \frac{1}{7} \approx 0.1429.$$

Check: $2/7 + 4/7 + 1/7 = 1$, and the weights $1/6 : 1/3 : 1/12$ are in ratio $2 : 4 : 1$.

**(c)** Condition on the coin again. Given the coin, the two tosses are independent, so $P(H_1 \cap H_2 \mid C) = P(H \mid C)^2$:

$$P(H_1 \cap H_2) = \frac{1}{3}\left(\frac{1}{4} + 1 + \frac{1}{16}\right) = \frac{1}{3} \cdot \frac{21}{16} = \frac{7}{16}, \qquad P(H_2 \mid H_1) = \frac{7/16}{7/12} = \frac{3}{4} = 0.75.$$

Equivalently, average the heads probability over the *updated* beliefs from (b): $\frac{2}{7} \cdot \frac{1}{2} + \frac{4}{7} \cdot 1 + \frac{1}{7} \cdot \frac{1}{4} = \frac{21}{28} = \frac{3}{4}$.

This is larger than $P(H) = 7/12$: a first head shifts belief toward the two-headed coin, so the two tosses are *not* independent (they are independent only once you know which coin it is).

**Key idea:** total probability gives the denominator; Bayes reweights each hypothesis by how well it explains the evidence.

### Problem 2. Reading a CDF

**(a)** $F$ is a staircase that is flat between $-1, 0, 2, 5$ and jumps at those points. Each jump height is the probability at that point:

| $x$ | $-1$ | $0$ | $2$ | $5$ |
|---|---|---|---|---|
| $p(x)$ | $1/5$ | $1/2 - 1/5 = 3/10$ | $9/10 - 1/2 = 2/5$ | $1 - 9/10 = 1/10$ |

The probabilities add to 1, and $p(x) = 0$ everywhere else.

**(b)**

- $P(X = 1) = 0$: $F$ does not jump at 1.
- $P(X \le 1) = F(1) = 1/2 = 0.5$.
- $P(0 < X \le 4) = F(4) - F(0) = 9/10 - 1/2 = 2/5 = 0.4$ (only the value 2 lies in $(0, 4]$).
- $P(X \ge 2) = 1 - P(X < 2) = 1 - P(X \le 0) = 1 - 1/2 = 1/2 = 0.5$. Note $P(X < 2)$ is the value of $F$ just *before* the jump at 2, not $F(2)$.
- $P(X > 2) = 1 - F(2) = 1 - 9/10 = 1/10 = 0.1$.

**(c)**

$$E[X] = (-1) \cdot \frac{1}{5} + 0 \cdot \frac{3}{10} + 2 \cdot \frac{2}{5} + 5 \cdot \frac{1}{10} = -\frac{2}{10} + \frac{8}{10} + \frac{5}{10} = \frac{11}{10} = 1.1.$$

**Key idea:** the PMF is the list of jump heights of the CDF; $P(X \le x) = F(x)$ includes the jump at $x$, while $P(X < x)$ does not.

### Problem 3. True or false

**(a) False.** Let 1% of people have a condition $B$, and let a test be positive ($A$) for 90% of people with $B$ and 10% of people without it. Then $P(A \mid B) = 0.9$, but

$$P(B \mid A) = \frac{0.01 \cdot 0.9}{0.01 \cdot 0.9 + 0.99 \cdot 0.1} = \frac{0.009}{0.108} = \frac{1}{12} \approx 0.08333.$$

Reversing a conditional requires the prior $P(B)$.

**(b) False.** A fair die has $E[X] = (1 + 2 + \cdots + 6)/6 = 7/2$, which is not a face of the die.

**(c) False.** Let $X$ be 1 or 3 with probability $1/2$ each. Then $E[X] = 2$, so $1/E[X] = 1/2$, but $E[1/X] = \frac{1}{2}(1 + \frac{1}{3}) = 2/3 \approx 0.6667$.

**(d) True.** By the tail-sum formula, $E[X] = \sum_{i \ge 1} P(X \ge i) \le \sum_{i \ge 1} 2^{-i} = 1$.

**Key idea:** $P(A \mid B) \ne P(B \mid A)$ and $E[g(X)] \ne g(E[X])$ in general; tail sums turn bounds on tails into bounds on the mean.

### Problem 4. A partly guessed quiz

**(a)** Write $C = 6 + G_1 + G_2 + G_3 + G_4$, where $G_j = 1$ if guess $j$ is correct. Each $G_j$ is Bernoulli with $p = 1/4$, so $E[G_j] = 1/4$ and, by linearity,

$$E[C] = 6 + 4 \cdot \frac{1}{4} = 7.$$

**(b)** There are $10 - C$ wrong answers, so

$$S = C - \frac{1}{3}(10 - C) = \frac{4C - 10}{3}, \qquad E[S] = \frac{4 \cdot 7 - 10}{3} = 6.$$

**(c)** A blind guess is right with probability $1/4$ (+1 point) and wrong with probability $3/4$ ($-1/3$ point):

$$1 \cdot \frac{1}{4} - \frac{1}{3} \cdot \frac{3}{4} = \frac{1}{4} - \frac{1}{4} = 0.$$

**(d)** Now each guess is right with probability $1/3$, so its expected score is $\frac{1}{3} - \frac{1}{3} \cdot \frac{2}{3} = \frac{1}{9}$. The 6 known answers contribute 6 points, so

$$E[S] = 6 + 4 \cdot \frac{1}{9} = \frac{58}{9} \approx 6.444.$$

(Equivalently, $E[C] = 6 + 4/3 = 22/3$ and $E[S] = (4 \cdot 22/3 - 10)/3 = 58/9$.)

**Key idea:** a count of successes is a sum of Bernoulli variables, and an affine score has $E[aC + b] = aE[C] + b$.

---

## Exam-level

### Problem 5. A rare disease

Let $D$ = "has the disease" and $+$ = "test positive". The data: $P(D) = 1/200$, $P(+ \mid D) = 0.98$, $P(+ \mid D^c) = 0.03$.

**(a)** Total probability:

$$P(+) = \frac{1}{200} \cdot 0.98 + \frac{199}{200} \cdot 0.03 = 0.0049 + 0.02985 = 0.03475 = \frac{139}{4000}.$$

**(b)** Bayes' rule:

$$P(D \mid +) = \frac{0.0049}{0.03475} = \frac{98}{695} \approx 0.1410.$$

**Natural frequencies.** Out of 100,000 people, 500 are sick and 490 of them test positive. Of the 99,500 healthy people, 2,985 test positive. So only $490 / (490 + 2985) = 490/3475 \approx 14\%$ of positives are sick. The disease is so rare that false positives from the huge healthy group outnumber true positives about 6 to 1. The 98% is $P(+ \mid D)$; the question asks for $P(D \mid +)$.

**(c)** Given the true status, the two results are independent, so $P(++ \mid D) = 0.98^2$ and $P(++ \mid D^c) = 0.03^2$:

$$P(D \mid ++) = \frac{\frac{1}{200} \cdot 0.98^2}{\frac{1}{200} \cdot 0.98^2 + \frac{199}{200} \cdot 0.03^2} = \frac{0.004802}{0.004802 + 0.0008955} = \frac{9604}{11395} \approx 0.8428.$$

Same answer, sequentially: use $98/695$ from (b) as the new prior and update on one more positive test.

**(d)** With prevalence $\pi$, $P(D \mid +) = 1/2$ exactly when the two joint weights are equal: $0.98\,\pi = 0.03\,(1 - \pi)$, so

$$\pi = \frac{0.03}{1.01} = \frac{3}{101} \approx 0.02970,$$

about 3 in 100 people.

**Key idea:** a positive result multiplies the odds of disease by $0.98/0.03 \approx 33$, but with a prior of 1 in 200 the posterior is still small; base rates matter.

### Problem 6. Adding a ball of the same color

Write $R_1, R_2$ for "first ball red" and "second ball red".

**(a)** After a red draw the urn has 4 red and 2 blue; after a blue draw it has 3 red and 3 blue. Total probability with the chain rule:

$$P(R_2) = P(R_1)P(R_2 \mid R_1) + P(R_1^c)P(R_2 \mid R_1^c) = \frac{3}{5} \cdot \frac{4}{6} + \frac{2}{5} \cdot \frac{3}{6} = \frac{12}{30} + \frac{6}{30} = \frac{3}{5} = 0.6.$$

**(b)**

$$P(R_1 \mid R_2) = \frac{P(R_1 \cap R_2)}{P(R_2)} = \frac{12/30}{18/30} = \frac{2}{3} \approx 0.6667.$$

Seeing red on the second draw makes a red first draw more likely than its prior $3/5$, because a red first draw adds a red ball.

**(c)** Same two branches:

$$P(R_2) = \frac{r}{r+b} \cdot \frac{r+1}{r+b+1} + \frac{b}{r+b} \cdot \frac{r}{r+b+1} = \frac{r\,(r + 1 + b)}{(r+b)(r+b+1)} = \frac{r}{r+b}. \qquad \blacksquare$$

**Key idea:** split on the first draw (total probability), use the chain rule on each branch, and divide one branch by the total to reverse the conditioning.

### Problem 7. Expectations of functions

**(a)**

$$E[X] = -\frac{1}{10} + 0 + \frac{3}{10} + \frac{6}{10} + \frac{6}{10} = \frac{14}{10} = \frac{7}{5} = 1.4.$$

**(b)** $Y = (X - 1)^2$ maps $-1 \mapsto 4$, $0 \mapsto 1$, $1 \mapsto 0$, $2 \mapsto 1$, $3 \mapsto 4$. Collect the $x$ values that share a $y$:

| $y$ | $0$ | $1$ | $4$ |
|---|---|---|---|
| $x$ values | $1$ | $0, 2$ | $-1, 3$ |
| $p(y)$ | $3/10$ | $1/10 + 3/10 = 2/5$ | $1/10 + 1/5 = 3/10$ |

$$E[Y] = 0 \cdot \frac{3}{10} + 1 \cdot \frac{2}{5} + 4 \cdot \frac{3}{10} = \frac{4}{10} + \frac{12}{10} = \frac{8}{5} = 1.6.$$

**(c)** LOTUS, $E[g(X)] = \sum_x g(x)\,p(x)$:

$$E[Y] = 4 \cdot \frac{1}{10} + 1 \cdot \frac{1}{10} + 0 \cdot \frac{3}{10} + 1 \cdot \frac{3}{10} + 4 \cdot \frac{1}{5} = \frac{4 + 1 + 0 + 3 + 8}{10} = \frac{8}{5}.$$

**(d)**

$$E[X^2] = 1 \cdot \frac{1}{10} + 0 + 1 \cdot \frac{3}{10} + 4 \cdot \frac{3}{10} + 9 \cdot \frac{1}{5} = \frac{1 + 3 + 12 + 18}{10} = \frac{17}{5} = 3.4.$$

By linearity, $E[(X-1)^2] = E[X^2] - 2E[X] + 1 = \frac{17}{5} - \frac{14}{5} + 1 = \frac{8}{5}$. Note that $(E[X] - 1)^2 = 4/25$ is very different.

**(e)**

$$E[2^X] = \frac{1}{2} \cdot \frac{1}{10} + 1 \cdot \frac{1}{10} + 2 \cdot \frac{3}{10} + 4 \cdot \frac{3}{10} + 8 \cdot \frac{1}{5} = \frac{0.5 + 1 + 6 + 12 + 16}{10} = \frac{71}{20} = 3.55,$$

while $2^{E[X]} = 2^{1.4} \approx 2.639$. So $E[2^X]$ is larger. (For convex functions such as $2^x$ this always happens; the general statement is Jensen's inequality.)

**Key idea:** LOTUS weights $g(x)$ by $p(x)$ with no need for the PMF of $g(X)$; only affine $g$ satisfies $E[g(X)] = g(E[X])$.

### Problem 8. The smallest of three dice

**(a)** Write $p_k = P(X = k)$. Each term $P(X \ge i) = \sum_{k \ge i} p_k$, so

$$\sum_{i=1}^{\infty} P(X \ge i) = \sum_{i=1}^{\infty} \sum_{k=i}^{\infty} p_k = \sum_{k=1}^{\infty} \sum_{i=1}^{k} p_k = \sum_{k=1}^{\infty} k\,p_k = E[X].$$

Swapping the order of summation is allowed because every term is nonnegative: $p_k$ is counted once for each $i = 1, \dots, k$, that is, $k$ times. $\blacksquare$

(Alternative: $X = \sum_{i \ge 1} \mathbf{1}\lbrace X \ge i \rbrace$, since exactly $X$ of these indicators equal 1; take expectations.)

**(b)** $M \ge i$ exactly when all three dice show $i$ or more, which has $7 - i$ options per die:

$$P(M \ge i) = \left(\frac{7-i}{6}\right)^3: \qquad 1, \ \frac{125}{216}, \ \frac{64}{216}, \ \frac{27}{216}, \ \frac{8}{216}, \ \frac{1}{216} \quad (i = 1, \dots, 6).$$

$$E[M] = \frac{216 + 125 + 64 + 27 + 8 + 1}{216} = \frac{441}{216} = \frac{49}{24} \approx 2.042.$$

**(c)**

$$P(M = 2) = P(M \ge 2) - P(M \ge 3) = \frac{125 - 64}{216} = \frac{61}{216} \approx 0.2824.$$

**(d)** If $D_1, D_2, D_3$ are independent fair dice, so are $7 - D_1, 7 - D_2, 7 - D_3$. The largest of the $D_j$ is $L = 7 - \min(7 - D_1, 7 - D_2, 7 - D_3)$, and the minimum on the right has the same distribution as $M$. By linearity,

$$E[L] = 7 - E[M] = 7 - \frac{49}{24} = \frac{119}{24} \approx 4.958.$$

**Key idea:** for a minimum, $P(\min \ge i)$ is a simple product, so the tail-sum formula is the natural route to the mean.

### Problem 9. Couples side by side

**(a)** $N = k$ requires *exactly* $k$ couples together, which depends on the whole seating. The events "couple $i$ is together" overlap in complicated ways (two couples can both be together, some seatings make three or more couples adjacent), so each $P(N = k)$ needs an inclusion-exclusion count over sets of couples.

**(b)** Let $I_i = 1$ if couple $i$ sits together, so $N = I_1 + \cdots + I_{10}$. The two chairs taken by couple $i$ are equally likely to be any of the $\binom{20}{2} = 190$ pairs of chairs, and 19 of those pairs are adjacent:

$$E[I_i] = P(\text{couple } i \text{ together}) = \frac{19}{190} = \frac{1}{10}, \qquad E[N] = 10 \cdot \frac{1}{10} = 1.$$

**(c)** A round table with 20 seats has 20 adjacent pairs, so $P(\text{couple } i \text{ together}) = 20/190 = 2/19$ and

$$E[N] = 10 \cdot \frac{2}{19} = \frac{20}{19} \approx 1.053.$$

**(d) False.** Linearity of expectation holds for any random variables, independent or not. The events are in fact dependent: gluing two couples into blocks gives $P(\text{couples 1 and 2 both together}) = \frac{2 \cdot 2 \cdot 18!}{20!} = \frac{1}{95}$, which differs from $\frac{1}{10} \cdot \frac{1}{10} = \frac{1}{100}$.

**Key idea:** to find the mean of a count, sum the probabilities of the individual events; dependence does not matter.

---

## Challenge

### Problem 10. Waiting for the first ace

**(a)** $X \ge i$ means the first $i - 1$ cards contain no ace, that is, all four aces lie in positions $i, \dots, 52$, a block of $53 - i$ positions. In a shuffled deck the set of four ace positions is equally likely to be any of the $\binom{52}{4}$ four-element subsets of positions, and $\binom{53-i}{4}$ of those subsets lie inside the block. $\blacksquare$

**(b)** Substitute $j = 53 - i$ (as $i$ runs from 1 to 49, $j$ runs from 52 down to 4):

$$E[X] = \sum_{i=1}^{49} P(X \ge i) = \frac{1}{\binom{52}{4}} \sum_{j=4}^{52} \binom{j}{4} = \frac{\binom{53}{5}}{\binom{52}{4}} = \frac{53! / (5! \, 48!)}{52! / (4! \, 48!)} = \frac{53}{5} = 10.6. \qquad \blacksquare$$

**(c)** The cards before the first ace are exactly the non-aces that precede all four aces, so $X - 1 = \sum_c J_c$ over the 48 non-aces $c$, where $J_c = 1$ if $c$ comes before every ace. Look only at the relative order of the 5 cards $c$ and the four aces: by symmetry each of the 5 is equally likely to come first, so $E[J_c] = 1/5$. Therefore

$$E[X] = 1 + 48 \cdot \frac{1}{5} = \frac{53}{5}.$$

**(d)** The same argument with $n - k$ ordinary cards, each ahead of all $k$ special cards with probability $1/(k+1)$:

$$E[X] = 1 + \frac{n-k}{k+1} = \frac{n+1}{k+1}.$$

(The tail-sum route gives the same: $\sum_{j=k}^{n} \binom{j}{k} / \binom{n}{k} = \binom{n+1}{k+1} / \binom{n}{k} = (n+1)/(k+1)$.) With $n = 52$ this gives $53/2 = 26.5$ for the queen of hearts ($k = 1$) and $53/3$ for the first red queen ($k = 2$), matching the session's examples. For the first heart ($k = 13$):

$$E[X] = \frac{53}{14} \approx 3.786.$$

**Key idea:** "position of the first special card" = 1 + (number of ordinary cards ahead of all special ones), and each ordinary card wins that race with probability $1/(k+1)$.

### Problem 11. Records

**(a)** Write each order as the scores' ranks, 3 = best. Records are marked by the running maximum:

| Order | 123 | 132 | 213 | 231 | 312 | 321 |
|---|---|---|---|---|---|---|
| Records | 3 | 2 | 2 | 2 | 1 | 1 |

$$E[R] = \frac{3 + 2 + 2 + 2 + 1 + 1}{6} = \frac{11}{6} \approx 1.833.$$

**(b)** The $i$-th candidate is a record exactly when they are the best among the first $i$ candidates. In a uniformly random order, the first $i$ candidates are a random set in a random order, so each of them is equally likely to be the best of the group. Hence the probability is $1/i$. $\blacksquare$

**(c)** Let $I_i$ indicate that candidate $i$ is a record. Then $R = \sum_{i=1}^{n} I_i$ and, by linearity and (b),

$$E[R] = \sum_{i=1}^{n} \frac{1}{i} = 1 + \frac{1}{2} + \cdots + \frac{1}{n}. \qquad \blacksquare$$

For $n = 3$ this gives $1 + 1/2 + 1/3 = 11/6$, matching (a). For $n = 10$:

$$E[R] = \frac{7381}{2520} \approx 2.929.$$

**(d) False.** For $i \ge 2$, $1/i \le \int_{i-1}^{i} dx/x$ because $1/x \ge 1/i$ on $[i-1, i]$. Summing over $i = 2, \dots, n$:

$$E[R] \le 1 + \int_1^n \frac{dx}{x} = 1 + \ln n, \qquad n = 1000: \quad E[R] \le 1 + 6.908 = 7.908 < 10.$$

(The exact value is about 7.485.) Records thin out: the $i$-th candidate has only a $1/i$ chance.

**Key idea:** a record at position $i$ is "the best of the first $i$", which has probability $1/i$ by symmetry; summing indicators gives the harmonic number.

### Problem 12. Three versions of the game-show host

Let $C_1, C_2, C_3$ be "the car is behind door 1, 2, 3", each with prior $1/3$. In every version, Bayes' rule is: weight = prior times likelihood of what you observed, then normalize.

**(a)** Observation: the host opens door 3. Likelihoods: under $C_1$ he chooses door 2 or 3 at random, so $1/2$; under $C_2$ he must open door 3, so $1$; under $C_3$ he never opens door 3, so $0$.

| | $C_1$ | $C_2$ | $C_3$ |
|---|---|---|---|
| prior times likelihood | $\frac{1}{3} \cdot \frac{1}{2} = \frac{1}{6}$ | $\frac{1}{3} \cdot 1 = \frac{1}{3}$ | $0$ |

The total is $1/2$, so

$$P(C_1 \mid \text{opens } 3) = \frac{1}{3} \approx 0.3333, \qquad P(C_2 \mid \text{opens } 3) = \frac{2}{3} \approx 0.6667.$$

Switching doubles the chance of winning.

**(b)** Now the likelihood under $C_1$ is $q$; the others are unchanged. The weights are $q/3$, $1/3$, $0$, so

$$P(C_1 \mid \text{opens } 3) = \frac{q/3}{q/3 + 1/3} = \frac{q}{1+q}, \qquad P(C_2 \mid \text{opens } 3) = \frac{1}{1+q}. \qquad \blacksquare$$

Since $0 \le q \le 1$, $\frac{q}{1+q} \le \frac{1}{2} \le \frac{1}{1+q}$, so switching is never worse. For example, $q = 1/4$ gives $1/5 = 0.2$ for staying.

**(c)** Observation: the host opens door 3 *and* it shows a goat. Under $C_1$: he opens door 3 with probability $1/2$ and it is a goat, so $1/2$. Under $C_2$: likewise $1/2$. Under $C_3$: opening door 3 would reveal the car, so $0$. The weights are $1/6$, $1/6$, $0$, so

$$P(C_1 \mid \text{opens 3, goat}) = \frac{1/6}{1/3} = \frac{1}{2} = 0.5. \qquad \blacksquare$$

Staying and switching are now equally good.

**(d) False.** The posterior of $C_1$ equals its prior $1/3$ only when the observation is exactly as likely under $C_1$ as it is overall: $P(\text{obs} \mid C_1) = P(\text{obs})$. That holds in (a) ($1/2 = 1/2$) but not in (b) unless $q = 1/2$ (the posterior is $q/(1+q)$, anywhere from 0 to $1/2$), and not in (c) (the posterior is $1/2$). What the host does, and why he does it, is evidence about door 1 as well.

**Key idea:** in Bayes problems, model *how the evidence is generated* under each hypothesis; the same visible event can carry different likelihoods.
