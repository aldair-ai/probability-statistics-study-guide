# Session 2 Exercises: Geometric Examples, Odd Odds and a Rocket

Solve these by hand, exam style, without code. Give answers as exact fractions or exact expressions, with decimals where they help. Unless a problem says otherwise, separate trials are independent. Notation follows the notes: $G_p$ counts trials up to and including the first success, and $q = 1 - p$.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 32 min |
| Exam-level | 5-9 | 68 min |
| Challenge | 10-12 | 55 min |

---

## Warm-up

### Problem 1. First to roll a six

**Tests:** translating a game into a parity question, the formula $1/(2-p)$. **Time:** 6 min.

Dana and Eli take turns rolling a fair die, with Dana first, and whoever rolls the first six wins.

(a) Find the probability that Dana wins, and the probability that Eli wins.

(b) Find the expected number of rolls in the game.

(c) How much is going first worth here, compared with the fair coin game? Explain the difference in one sentence.

### Problem 2. More than parity

**Tests:** geometric series on subsets of the support. **Time:** 8 min.

Let $X \sim G_{1/3}$.

(a) Find $P(X \text{ odd})$ and $P(X \text{ even})$.

(b) Find $P(X \text{ is a multiple of } 3)$.

(c) For general $p$ and an integer $m \ge 1$, find $P(X \text{ is a multiple of } m)$. What is its limit as $p \to 0$? Interpret the limit.

### Problem 3. True or false

**Tests:** parity, limits, the worst-case bound. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) For $X \sim G_p$ with $0 < p \le 1$, $P(X \text{ odd}) > 1/2$.

(b) In the coin game with $p = 1$, the first player wins with probability $1/2$.

(c) $P(X = 11)$, as a function of $p$, is maximized at $p = 1/10$.

(d) The inequality $\max_p P(X = n) \le \frac{1}{e(n-1)}$ holds for every $n \ge 2$, not just in the limit.

(e) If a rocket passes 10 tests with no mishap, then $p_{\text{mh}} \le 0.1$.

(f) Doubling the number of test flights roughly halves the worst-case catastrophe bound.

### Problem 4. A drone program

**Tests:** the event $X = t + 1$, evaluating the bound, sizing a test program. **Time:** 8 min.

A delivery drone flies up to 10 test routes. If none has a failure, it starts service on a route over a crowded area. Flights fail independently with probability $p$.

(a) Find the probability that the first service flight fails after 10 clean tests, for $p = 0.02$ and $p = 0.1$.

(b) Find the $p$ that maximizes this probability and the maximum, and compare with the bound $1/(10e)$. You may use $(10/11)^{10} \approx 0.3855$.

(c) How many test flights does the bound $\frac{1}{e\,t}$ require for this risk to be at most 0.5%?

---

## Exam-level

### Problem 5. Three players

**Tests:** extending the parity argument to residues, conditioning, limits. **Time:** 12 min.

Three players A, B, C take turns in that order, each flipping a coin with $P(\text{heads}) = p$. The first to get heads wins.

(a) Find each player's winning probability, using the relation between the three series. Express the answers in terms of $q$.

(b) Evaluate for a fair coin and for a fair die (where "heads" is rolling a six).

(c) Find the limit of each probability as $p \to 0$ and as $p \to 1$, and explain the limits.

(d) State the result for $k$ players, and find the winning probability of the first of $k$ players.

### Problem 6. Unequal skills

**Tests:** first-step analysis, fairness condition, expected length. **Time:** 14 min.

Ana and Ben alternate free throws, with Ana first, and the first to score wins. Ana scores with probability $a$, and Ben scores with probability $b$, with $a, b$ in $(0, 1)$.

(a) Show that $P(\text{Ana wins}) = \dfrac{a}{1 - (1 - a)(1 - b)}$. Evaluate at $a = 2/5$ and $b = 1/2$.

(b) For which $a$ is the game fair when $b$ is given? Find this $a$ for $b = 1/2$, and interpret the answer.

(c) Let $T$ be the total number of throws. Use first-step analysis to show that $E[T] = \dfrac{2 - a}{1 - (1 - a)(1 - b)}$. Evaluate at $a = 2/5$, $b = 1/2$, and check the formula at $a = b = 1/2$.

### Problem 7. Conditioning on parity

**Tests:** memorylessness, conditional expectation, parity of sums. **Time:** 15 min.

Let $X \sim G_p$.

(a) Use memorylessness to show that $E[X \mid X \text{ even}] = 1 + E[X \mid X \text{ odd}]$.

(b) Use (a) and the law of total expectation to show that

$$E[X \mid X \text{ odd}] = \frac{1 + q^2}{p(1 + q)}.$$

(c) In the fair coin game, on average at which flip does Alice win, given that she wins? Check your answer against $E[X] = 2$.

(d) Let $X \sim G_{1/6}$ and $Y \sim G_{1/2}$ be independent. Find $P(X + Y \text{ is even})$.

### Problem 8. Exactly one success

**Tests:** maximizing a binomial term over $p$, a universal lower bound, the limit $1/e$. **Time:** 12 min.

Let $W \sim B_{p,\,m}$.

(a) Show that $P(W = 1)$ is maximized at $p = 1/m$, and find the maximum value.

(b) Show that the maximum in (a) decreases to $1/e$ as $m \to \infty$. (You may assume that $(1 - 1/m)^{m-1}$ is decreasing, with limit $1/e$.) Evaluate at $m = 10$, using $0.9^9 \approx 0.3874$.

(c) Generalize: show that $P(W = k)$ is maximized at $p = k/m$, for $1 \le k \le m - 1$. Evaluate the maximum at $m = 10$, $k = 3$.

(d) A lab tunes a reaction so that exactly one of its 10 samples activates. Which $p$ should it aim for, and what is the best achievable probability of success?

### Problem 9. Several crewed flights

**Tests:** optimizing a two-factor expression, scaling of the bound, the cost of more flights. **Time:** 15 min.

After $t$ clean test flights, a rocket flies a crew $k$ times, unless a mishap ends the program first. A catastrophe is a mishap on any crewed flight.

(a) Show that $P(\text{catastrophe}) = q^t (1 - q^k)$.

(b) Substitute $u = q^k$, and show that the maximum over $q$ is reached at $u = \frac{t}{t + k}$, with maximum value

$$B(t, k) = \left(\frac{t}{t + k}\right)^{t/k} \frac{k}{t + k}.$$

(c) Evaluate $B(10, 1)$, $B(10, 5)$, $B(10, 10)$, and $B(100, 10)$. You may use $(10/11)^{10} \approx 0.3855$. What do you notice about $B(10, 1)$ and $B(100, 10)$?

(d) Show that $B(t, k)$ depends only on the ratio $t/k$, and that $B(t, k) \le \frac{k}{e\,t}$. About how many tests keep the bound at 1% when the plan is $k = 5$ crewed flights?

---

## Challenge

### Problem 10. Joint versus conditional

**Tests:** averaging over an unknown $p$, joint versus conditional probabilities, a Beta integral. **Time:** 18 min.

The bound in the notes controls the joint event "clean tests and a mishap on the crewed flight". This problem shows why that differs from the risk the crew actually faces.

(a) Show that for each fixed $p$ with $0 < p < 1$, $P(\text{mishap on flight } t + 1 \mid t \text{ clean tests}) = p$. Conclude that this conditional probability cannot be bounded by anything below 1 over all $p$.

(b) Now suppose that $p$ is itself random and uniform on $[0, 1]$, reflecting complete ignorance, with flights independent given $p$. Show that

$$P(t \text{ clean tests}) = \frac{1}{t + 1}, \qquad P(t \text{ clean tests, then a mishap}) = \frac{1}{(t + 1)(t + 2)}.$$

(c) Conclude that $P(\text{mishap on flight } t + 1 \mid t \text{ clean tests}) = \frac{1}{t + 2}$. Evaluate the joint and conditional probabilities at $t = 10$, and compare both with $1/(10e)$.

(d) Explain why one of them must lie below the worst-case bound, while the other does not have to.

### Problem 11. First to two points

**Tests:** breaking a game into stages, reusing a result, the effect of longer matches. **Time:** 17 min.

Players A and B alternate flips, with A first. Each flip is heads with probability $p$, and heads gives the flipper a point. The turn alternates after every flip, whatever the result. The first to reach 2 points wins.

(a) Let $h = 1/(2 - p)$ be the probability that the player about to flip gets the next heads. Explain why this is valid at any point in the game.

(b) Show that $P(\text{A wins}) = 2h - 3h^2 + 2h^3$.

(c) Evaluate for a fair coin and a fair die. Is the advantage larger or smaller than in the one-point game?

(d) Show that $P(\text{A wins}) - \frac{1}{2} = (h - \frac{1}{2})(2h^2 - 2h + 1)$, and that the second factor lies in $(\frac{1}{2}, 1]$ for $\frac{1}{2} < h \le 1$. What does this say about first-mover advantage?

### Problem 12. Imperfect tests

**Tests:** modifying a model, optimizing with a constraint on $p$, interpreting the result. **Time:** 20 min.

Each flight has a mishap with probability $p$, but a test flight detects a mishap only with probability $d \in (0, 1]$. An undetected mishap has no effect on later flights. The crew flies once if all $t$ tests show no detected mishap.

(a) Show that $P(\text{catastrophe}) = (1 - pd)^t\, p$.

(b) Show that if $d \ge \frac{1}{t + 1}$, the maximum over $p$ occurs at $p = \frac{1}{d(t + 1)}$, with value

$$\frac{1}{d} \left(\frac{t}{t + 1}\right)^t \frac{1}{t + 1} \le \frac{1}{d\,e\,t}.$$

(c) Evaluate the maximum at $t = 10$ for $d = 1$, $d = 0.5$, and $d = 0.1$. You may use $(10/11)^{10} \approx 0.3855$. How many tests at $d = 0.5$ give the same bound $1/(e\,t)$ as 10 perfect tests?

(d) What is the maximum when $d < \frac{1}{t + 1}$? Evaluate it at $t = 10$, $d = 0.05$, using $0.95^{10} \approx 0.5987$.

(e) What practical lesson follows about test quality versus test quantity?
