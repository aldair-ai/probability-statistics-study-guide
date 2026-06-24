# Session 2 Solutions: Geometric Examples, Odd Odds and a Rocket

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. First to roll a six

**(a)** Dana wins exactly when the first six comes on an odd roll. With $p = 1/6$,

$$P(\text{Dana}) = \frac{1}{2 - 1/6} = \frac{6}{11} \approx 0.5455, \qquad P(\text{Eli}) = \frac{5}{11} \approx 0.4545.$$

**(b)** The number of rolls is $G_{1/6}$, so the mean is $6$.

**(c)** The edge over $1/2$ is $6/11 - 1/2 = 1/22 \approx 0.045$, compared with $2/3 - 1/2 = 1/6 \approx 0.167$ for a fair coin. Since each roll rarely ends the game, the first player's extra chance is a small part of a long game.

**Key idea:** the winner is determined by the parity of a geometric variable.

### Problem 2. More than parity

**(a)** With $p = 1/3$: $P(\text{odd}) = \frac{1}{2 - 1/3} = \frac{3}{5} = 0.6$, and $P(\text{even}) = \frac{2}{5} = 0.4$.

**(b)** Sum over multiples of 3, with $q = 2/3$:

$$P(3 \mid X) = \sum_{k \ge 1} q^{3k-1} p = \frac{p\,q^2}{1 - q^3} = \frac{(1/3)(4/9)}{1 - 8/27} = \frac{4/27}{19/27} = \frac{4}{19} \approx 0.2105.$$

**(c)** In general,

$$P(X \text{ is a multiple of } m) = \sum_{k \ge 1} q^{mk-1} p = \frac{p\,q^{m-1}}{1 - q^m}.$$

As $p \to 0$, write $1 - q^m = p(1 + q + \cdots + q^{m-1})$. Then the expression equals $\frac{q^{m-1}}{1 + q + \cdots + q^{m-1}} \to \frac{1}{m}$. When the wait is long, the value of $X$ modulo $m$ becomes nearly uniform, so each residue gets about $1/m$.

**Key idea:** the same series argument works for any arithmetic progression.

### Problem 3. True or false

**(a) True.** $P(\text{odd}) = \frac{1}{1 + q}$, and $1 + q < 2$ since $q < 1$.

**(b) False.** With $p = 1$, the first flip is always heads, so the first player wins with probability 1. The formula agrees: $\frac{1}{2 - 1} = 1$.

**(c) False.** The maximum is at $p = 1/n = 1/11$, from $1 - p = (n - 1)p$. The exponent is $n - 1 = 10$, but the answer involves $n = 11$.

**(d) True.** $\max_p P(X = n) = \frac{(1 - 1/n)^n}{n - 1}$, and $(1 - 1/n)^n$ increases to $1/e$ from below, so it is below $1/e$ for every $n$. For $n = 2$: $\frac{1}{4} \le \frac{1}{e}$.

**(e) False.** Clean tests make a large $p$ less plausible, but do not rule it out. Even at $p = 1/2$, there is a $1/1024$ chance of 10 clean tests.

**(f) True.** With $t = n - 1$ tests, the bound is $\frac{1}{e\,t}$, so doubling $t$ halves it. The exact maximum follows the bound closely: $0.0350$ at $t = 10$ and $0.0179$ at $t = 20$.

**Key idea:** read carefully which quantity is fixed, which is unknown, and whether a statement is about the limit or about every $n$.

### Problem 4. A drone program

**(a)** The event is $X = 11$, so $P = q^{10} p$.

- $p = 0.02$: $0.98^{10} \cdot 0.02 \approx 0.01634$.
- $p = 0.1$: $0.9^{10} \cdot 0.1 \approx 0.03487$.

**(b)** The maximum occurs at $p = 1/11 \approx 0.0909$, with value $(10/11)^{10}/11 \approx 0.3855/11 \approx 0.03505$. This is below the bound $1/(10e) \approx 0.03679$, as it should be.

**(c)** We need $\frac{1}{e\,t} \le 0.005$, or $t \ge \frac{200}{e} \approx 73.6$, so **74 test flights**.

**Key idea:** the risk of the first service flight is maximized at $p = 1/n$, and the bound scales as one over the number of tests.

---

## Exam-level

### Problem 5. Three players

**(a)** Group the flips by whose turn it is. Each term of B's series is $q$ times a term of A's series, and each term of C's series is $q$ times a term of B's. So $P(B) = q\,P(A)$ and $P(C) = q^2 P(A)$. The three probabilities sum to 1, which gives

$$P(A) = \frac{1}{1 + q + q^2}, \qquad P(B) = \frac{q}{1 + q + q^2}, \qquad P(C) = \frac{q^2}{1 + q + q^2}.$$

**(b)**

- Fair coin, $q = 1/2$: $P(A) = \frac{4}{7} \approx 0.5714$, $P(B) = \frac{2}{7} \approx 0.2857$, $P(C) = \frac{1}{7} \approx 0.1429$.
- Fair die, $q = 5/6$: $P(A) = \frac{36}{91} \approx 0.3956$, $P(B) = \frac{30}{91} \approx 0.3297$, $P(C) = \frac{25}{91} \approx 0.2747$.

**(c)** As $p \to 0$ ($q \to 1$), each probability tends to $1/3$: the game lasts so long that order barely matters. As $p \to 1$ ($q \to 0$), $P(A) \to 1$ and the others tend to 0: the first flip decides.

**(d)** With $k$ players, the $i$th player (for $i = 1, \dots, k$) wins with probability $q^{i-1}/(1 + q + \cdots + q^{k-1})$. The first player wins with probability

$$\frac{1}{1 + q + \cdots + q^{k-1}} = \frac{1 - q}{1 - q^k} = \frac{p}{1 - q^k}.$$

**Key idea:** each later position shifts every term by a factor of $q$, so the probabilities form a geometric progression.

### Problem 6. Unequal skills

**(a)** Let $w = P(\text{Ana wins})$. Consider the first round. Ana scores with probability $a$. If both miss, with probability $(1 - a)(1 - b)$, the game restarts. Otherwise Ben has won. So

$$w = a + (1 - a)(1 - b)\,w \quad \Longrightarrow \quad w = \frac{a}{1 - (1 - a)(1 - b)}.$$

At $a = 2/5$, $b = 1/2$: $w = \frac{2/5}{1 - 3/10} = \frac{4}{7} \approx 0.5714$.

**(b)** Set $w = 1/2$. Since $1 - (1 - a)(1 - b) = a + b - ab$, we get $2a = a + b - ab$, so

$$a = \frac{b}{1 + b}.$$

For $b = 1/2$, this gives $a = \frac{1}{3} \approx 0.3333$. Going first is worth so much that a player scoring 1/3 of the time is an even match against one scoring 1/2 of the time.

**(c)** Let $\tau = E[T]$. Condition on the first round:

- Ana scores (probability $a$): the game took 1 throw.
- Ana misses and Ben scores (probability $(1 - a)b$): it took 2 throws.
- Both miss (probability $(1 - a)(1 - b)$): 2 throws so far, then the game restarts.

So $\tau = a + 2(1 - a)b + (1 - a)(1 - b)(2 + \tau)$. The terms without $\tau$ simplify to $a + 2(1 - a)(b + 1 - b) = 2 - a$, which gives

$$\tau = \frac{2 - a}{1 - (1 - a)(1 - b)}.$$

At $a = 2/5$, $b = 1/2$: $\tau = \frac{8/5}{7/10} = \frac{16}{7} \approx 2.286$. Check at $a = b = 1/2$: $\tau = \frac{3/2}{3/4} = 2$, which is the mean of $G_{1/2}$.

**Key idea:** when a game restarts after a round, first-step analysis replaces an infinite sum with one equation.

### Problem 7. Conditioning on parity

**(a)** $X$ is even only if the first trial fails. Given a failure on trial 1, memorylessness says that $X = 1 + X'$, where $X' \sim G_p$ is independent of trial 1. Also, $X$ is even exactly when $X'$ is odd. Hence

$$E[X \mid X \text{ even}] = 1 + E[X' \mid X' \text{ odd}] = 1 + E[X \mid X \text{ odd}].$$

**(b)** Let $m = E[X \mid X \text{ odd}]$. With $P(\text{odd}) = \frac{1}{1 + q}$ and $P(\text{even}) = \frac{q}{1 + q}$, total expectation gives

$$\frac{1}{p} = \frac{1}{1 + q} m + \frac{q}{1 + q} (1 + m) = m + \frac{q}{1 + q}.$$

So

$$m = \frac{1}{p} - \frac{q}{1 + q} = \frac{1 + q - pq}{p(1 + q)} = \frac{1 + q(1 - p)}{p(1 + q)} = \frac{1 + q^2}{p(1 + q)}.$$

**(c)** At $p = q = 1/2$: $m = \frac{5/4}{3/4} = \frac{5}{3} \approx 1.667$. So when Alice wins, she does so on flip $5/3$ on average. Bob wins on flip $8/3$ on average. Check: $\frac{2}{3} \cdot \frac{5}{3} + \frac{1}{3} \cdot \frac{8}{3} = \frac{18}{9} = 2 = E[X]$.

**(d)** With $P(X \text{ odd}) = \frac{6}{11}$ and $P(Y \text{ odd}) = \frac{2}{3}$, the sum is even exactly when both are odd or both are even:

$$P(X + Y \text{ even}) = \frac{6}{11} \cdot \frac{2}{3} + \frac{5}{11} \cdot \frac{1}{3} = \frac{17}{33} \approx 0.5152.$$

**Key idea:** memorylessness shifts an even outcome to an odd one, which gives the conditional means without any sum.

### Problem 8. Exactly one success

**(a)** $P(W = 1) = m p q^{m-1}$. Its derivative in $p$ is $m q^{m-2}(q - (m - 1)p)$, which vanishes at $1 - p = (m - 1)p$, that is, at $p = 1/m$. The function is 0 at $p = 0$ and at $p = 1$ (for $m \ge 2$), so this is the maximum, with value

$$m \cdot \frac{1}{m} \cdot \left(1 - \frac{1}{m}\right)^{m-1} = \left(1 - \frac{1}{m}\right)^{m-1}.$$

**(b)** It decreases to $1/e \approx 0.3679$, so the best achievable probability of exactly one success always stays above $1/e$. At $m = 10$: $0.9^9 \approx 0.3874$.

**(c)** $P(W = k) = \binom{m}{k} p^k q^{m-k}$. Differentiate its logarithm in $p$: $\frac{k}{p} - \frac{m - k}{q} = 0$ gives $kq = (m - k)p$, so $p = k/m$. It is the maximum since the log-derivative is positive before and negative after. At $m = 10$, $k = 3$:

$$\binom{10}{3} (0.3)^3 (0.7)^7 = \frac{66{,}706{,}983}{250{,}000{,}000} \approx 0.2668.$$

**(d)** Aim for $p = 1/10$. The probability of exactly one activation is then $0.9^9 \approx 0.3874$, and no choice of $p$ does better.

**Key idea:** a binomial term is largest when the mean $mp$ equals the target count $k$.

### Problem 9. Several crewed flights

**(a)** A catastrophe needs $t$ clean tests, with probability $q^t$, and then at least one mishap among the $k$ crewed flights, with probability $1 - q^k$. Flights are independent, so the product rule gives $q^t(1 - q^k)$.

**(b)** Let $u = q^k \in (0, 1)$ and $r = t/k$. Then the expression is $g(u) = u^r (1 - u)$, and

$$g'(u) = r u^{r-1}(1 - u) - u^r = u^{r-1}\big(r - (r + 1)u\big),$$

which vanishes at $u = \frac{r}{r + 1} = \frac{t}{t + k}$. Since $g$ is 0 at both ends, this is the maximum, with value

$$B(t, k) = \left(\frac{t}{t + k}\right)^{t/k} \frac{k}{t + k}.$$

**(c)**

| $(t, k)$ | $u$ | $B(t, k)$ |
|---|---|---|
| $(10, 1)$ | $10/11$ | $0.3855/11 \approx 0.03505$ |
| $(10, 5)$ | $2/3$ | $(2/3)^2 (1/3) = 4/27 \approx 0.1481$ |
| $(10, 10)$ | $1/2$ | $1/4 = 0.25$ |
| $(100, 10)$ | $10/11$ | $(10/11)^{10}(1/11) \approx 0.03505$ |

$B(10, 1)$ and $B(100, 10)$ are equal.

**(d)** With $r = t/k$, $B = \left(\frac{r}{r+1}\right)^r \frac{1}{r+1}$, which depends only on $r$. Since $r + 1 = r\left(1 + \frac{1}{r}\right)$ and $\left(1 + \frac{1}{r}\right)^{r+1} \ge e$ for every $r > 0$,

$$B = \frac{1}{(r+1)\left(1 + \frac{1}{r}\right)^{r}} = \frac{1}{r\left(1 + \frac{1}{r}\right)^{r+1}} \le \frac{1}{e\,r} = \frac{k}{e\,t}.$$

For $k = 5$ and a 1% target, $\frac{5}{e\,t} \le 0.01$ needs $t \ge \frac{500}{e} \approx 184$ test flights. (The exact $B$ reaches 1% at $t = 182$.)

**Key idea:** tests must scale in proportion to the planned crewed flights, since only the ratio $t/k$ matters.

---

## Challenge

### Problem 10. Joint versus conditional

**(a)** For fixed $p$, flights are independent, so the outcome of flight $t + 1$ ignores the tests, and the conditional probability is $p$. As $p$ ranges over $(0, 1)$, this can be arbitrarily close to 1, so no bound below 1 can hold for every $p$.

**(b)** Averaging over $p$:

$$P(t \text{ clean tests}) = \int_0^1 (1 - p)^t \, dp = \frac{1}{t + 1},$$

$$P(t \text{ clean, then mishap}) = \int_0^1 (1 - p)^t p \, dp = \int_0^1 u^t (1 - u) \, du = \frac{1}{t + 1} - \frac{1}{t + 2} = \frac{1}{(t + 1)(t + 2)}.$$

**(c)** Divide: $P(\text{mishap} \mid t \text{ clean}) = \frac{1}{t + 2}$. At $t = 10$:

- joint: $\frac{1}{132} \approx 0.007576$, which is below $\frac{1}{10e} \approx 0.03679$;
- conditional: $\frac{1}{12} \approx 0.08333$, which is above it.

**(d)** The joint probability is an average of $q^t p$ over $p$, and an average cannot exceed the maximum, so it must lie below the bound. The conditional probability is a different quantity that has no such constraint. The worst-case bound covers the whole program's risk before testing starts. It does not tell a crew member who already knows the tests were clean how risky the next flight is.

**Key idea:** "the tests are clean and then a disaster occurs" and "a disaster occurs, given clean tests" are different events with different probabilities.

### Problem 11. First to two points

**(a)** Flips are independent and memoryless, so at any moment the sequence of future flips looks like a new game with the current flipper going first. The next heads comes on an odd future flip, which belongs to the current flipper, with probability $h = 1/(2 - p)$.

**(b)** Condition on who gets the first point, and track who flips next. Since turns alternate after every flip, the opponent of the player who just scored flips next.

- A gets the first point (probability $h$). Now B flips next. A wins if the next point is A's (probability $1 - h$). If it is B's (probability $h$), the score is 1-1, A flips next, and A wins with probability $h$. So A wins with probability $(1 - h) + h \cdot h$.
- B gets the first point (probability $1 - h$). Now A flips next. A must get the next point (probability $h$), which leaves 1-1 with B flipping next, and then A wins with probability $1 - h$. So A wins with probability $h(1 - h)$.

Total:

$$P(\text{A wins}) = h\big[(1 - h) + h^2\big] + (1 - h) \cdot h(1 - h) = 2h - 3h^2 + 2h^3.$$

**(c)**

- Fair coin, $h = 2/3$: $\frac{4}{3} - \frac{4}{3} + \frac{16}{27} = \frac{16}{27} \approx 0.5926$.
- Fair die, $h = 6/11$: $\frac{696}{1331} \approx 0.5229$.

Both are smaller than the one-point values $2/3$ and $6/11$.

**(d)** Expanding: $(h - \frac{1}{2})(2h^2 - 2h + 1) = 2h^3 - 2h^2 + h - h^2 + h - \frac{1}{2} = 2h^3 - 3h^2 + 2h - \frac{1}{2}$, as claimed. Also, $2h^2 - 2h + 1 = 2(h - \frac{1}{2})^2 + \frac{1}{2}$, which lies in $(\frac{1}{2}, 1]$ for $\frac{1}{2} < h \le 1$, and equals 1 only at $h = 1$. So the first player's edge over $\frac{1}{2}$ shrinks by the factor $2h^2 - 2h + 1$. It is still positive, but longer matches reduce the first-mover advantage.

**Key idea:** memorylessness lets a longer game be broken into independent one-point games.

### Problem 12. Imperfect tests

**(a)** A test flight shows a detected mishap with probability $pd$, independently across flights, so all $t$ tests look clean with probability $(1 - pd)^t$. The crewed flight is then a mishap with probability $p$.

**(b)** Differentiate $g(p) = (1 - pd)^t p$:

$$g'(p) = (1 - pd)^{t-1}\big(1 - pd - t d p\big) = (1 - pd)^{t-1}\big(1 - (t + 1)dp\big).$$

This vanishes at $p^* = \frac{1}{d(t + 1)}$, which lies in $(0, 1]$ exactly when $d \ge \frac{1}{t + 1}$. Since $g'$ changes sign from positive to negative there, it is the maximum. At $p^*$, $1 - p^* d = \frac{t}{t + 1}$, so

$$g(p^*) = \frac{1}{d}\left(\frac{t}{t + 1}\right)^t \frac{1}{t + 1}.$$

Using $\left(\frac{t}{t+1}\right)^t \frac{1}{t+1} \le \frac{1}{e\,t}$ from the notes (with $n - 1 = t$) gives the bound $\frac{1}{d\,e\,t}$.

**(c)** At $t = 10$, the base value is $0.3855/11 \approx 0.03505$.

- $d = 1$: $0.03505$.
- $d = 0.5$: $0.07010$.
- $d = 0.1$: $0.3505$.

The bound $\frac{1}{d\,e\,t}$ depends only on the product $d\,t$. So $d = 0.5$ needs $t = 20$ tests to match 10 perfect tests. The exact maxima agree closely: $0.03589$ at $d = 0.5$, $t = 20$, against $0.03505$.

**(d)** If $d < \frac{1}{t + 1}$, then $p^* > 1$, so $g'(p) > 0$ on $(0, 1)$, and the maximum is at $p = 1$, with value $(1 - d)^t$. At $t = 10$, $d = 0.05$: $0.95^{10} \approx 0.5987$. Tests this weak barely protect the crew against a rocket that always fails.

**(e)** Halving test sensitivity doubles the worst-case risk, and the only way to recover it is to double the number of tests. Better detection can therefore be worth as much as many extra flights. This is the "no substitute for good engineering" point in quantitative form.

**Key idea:** the effective number of tests is $d \cdot t$, so test quality and test quantity trade off one for one.
