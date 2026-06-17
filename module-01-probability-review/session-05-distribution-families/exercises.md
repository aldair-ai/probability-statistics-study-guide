# Session 5 Exercises: Distribution Families and Continuous Random Variables

Solve these by hand, exam style, without code. Give answers as exact fractions (or exact expressions such as $5e^{-2}$), with decimals where they help. Unless a problem says otherwise, dice are fair six-sided dice, separate trials are independent, and a density is 0 outside the interval where it is given. Notation follows the notes: $B_p$ (Bernoulli), $B_{p,n}$ (binomial), $P_\lambda$ (Poisson), $G_p$ (geometric, counting trials up to and including the first success), and $q = 1 - p$.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 35 min |
| Exam-level | 5-9 | 71 min |
| Challenge | 10-12 | 56 min |

---

## Warm-up

### Problem 1. Name that distribution

**Tests:** recognizing the Bernoulli, binomial, Poisson, and geometric models and their assumptions. **Time:** 8 min.

For each random variable, name its distribution (Bernoulli, binomial, Poisson, or geometric), give the parameters, and give its mean. If none of the four fits, say which assumption fails.

(a) A factory makes chips, each defective with probability 0.04, independently of the others. An inspector tests 15 chips, and $X$ is the number of defective ones.

(b) A basketball player makes each free throw with probability 0.8, independently. She shoots until her first miss, and $X$ is the number of shots she takes, including the miss.

(c) A help line serves a very large number of customers, each of whom calls rarely and independently of the others. On average 3.5 calls arrive per minute, and $X$ is the number of calls in a given minute.

(d) A committee of 4 is chosen at random from a club of 6 women and 6 men, and $X$ is the number of women on it.

(e) A voter is chosen at random in a city where 55% of voters support a ballot measure. $X = 1$ if the voter supports it, and $X = 0$ otherwise.

(f) $X$ is the number of days next year on which it rains in San Diego.

### Problem 2. Guessing on a quiz

**Tests:** binomial PMF, complements, mean and variance, most likely value. **Time:** 7 min.

A quiz has 6 multiple-choice questions with 4 options each. A student guesses every answer at random, and $X$ is the number of correct answers.

(a) Find $P(X = 2)$.

(b) Find $P(X \ge 1)$.

(c) Find $E[X]$, $V(X)$, and $\sigma_X$.

(d) Find the most likely value of $X$. Which is more likely: no correct answers, or at least 3?

### Problem 3. True or false

**Tests:** PDFs, memorylessness, binomial symmetry, the Poisson PMF, change of variables. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences (a short proof or a counterexample).

(a) A probability density function satisfies $f(x) \le 1$ for every $x$.

(b) If $X \sim G_p$, then $P(X > 5 \mid X > 2) = P(X > 3)$.

(c) If $X \sim B_{p,n}$, then $n - X \sim B_{1-p,\,n}$.

(d) If $\lambda$ is a positive integer, then the PMF of $P_\lambda$ has a unique most likely value.

(e) If $X$ has PDF $f_X$ and $Y = 2X$, then $f_Y(y) = 2 f_X(y/2)$.

(f) If $X$ is continuous, then $P(a \le X \le b) = P(a < X < b)$ for all $a < b$.

### Problem 4. A hump-shaped density

**Tests:** normalizing a PDF, the CDF, interval probabilities, continuous expectation and variance. **Time:** 10 min.

A random variable $X$ has PDF $f(x) = c\, x(2 - x)$ for $0 \le x \le 2$.

(a) Find $c$.

(b) Find the CDF $F(x)$ for every real $x$.

(c) Find $P(1/2 < X \le 3/2)$.

(d) Find $E[X]$ and $V(X)$. Explain why $E[X]$ could have been predicted without integrating.

---

## Exam-level

### Problem 5. Spare hard drives

**Tests:** binomial model, Poisson approximation, ratio of consecutive Poisson probabilities, cumulative probabilities. **Time:** 14 min.

A data center runs 500 hard drives. In a given month, each drive fails with probability 0.004, independently of the others. Let $X$ be the number of drives that fail this month. You may use $\ln(0.996) \approx -0.004008$ and $e^{-2} \approx 0.1353$.

(a) Name the exact distribution of $X$, and find $E[X]$ and $V(X)$.

(b) Write exact expressions for $P(X = 0)$ and $P(X \le 2)$, and evaluate $P(X = 0)$.

(c) Explain why a Poisson approximation is appropriate, and give its parameter. Use it to approximate $P(X = 0)$ and $P(X \le 2)$, and compare with (b).

(d) Let $Y \sim P_\lambda$. Show that $P(Y = k)/P(Y = k - 1) = \lambda/k$ for $k \ge 1$. Use this to find the most likely value or values of $Y$ when $\lambda = 2$ and when $\lambda = 2.5$.

(e) The data center keeps $s$ spare drives on site. Using the Poisson approximation, find the smallest $s$ with $P(X > s) \le 0.05$.

### Problem 6. Loot boxes

**Tests:** geometric PMF, tail and CDF, tail sums, memorylessness, median. **Time:** 15 min.

In a video game, each loot box contains a rare item with probability $1/20$, independently of the other boxes. A player opens boxes until the first rare item appears, and $X$ is the number of boxes opened, including the one with the item. You may use $(19/20)^5 \approx 0.7738$, $(19/20)^{20} \approx 0.3585$, $\ln 2 \approx 0.6931$, and $\ln(0.95) \approx -0.05129$.

(a) Name the distribution of $X$. Show that $P(X > n) = (19/20)^n$ for $n = 0, 1, 2, \dots$, and write the CDF.

(b) Find $P(X = 5)$, $P(X > 20)$, and $P(5 < X \le 20)$.

(c) Use tail sums to show that $E[X] = 20$. Given that $V(X) = q/p^2$, find $\sigma_X$ and compare it with the mean.

(d) The player has opened 30 boxes without finding the item. Find the expected total number of boxes they will open, and the probability that they need more than 50 in total.

(e) The median of $X$ is the smallest $n$ with $F(n) \ge 1/2$. Find it, and explain why it is smaller than the mean.

### Problem 7. Binomial moments the long way, and what independence buys

**Tests:** binomial PMF identities, factorial moments, indicators, covariance of indicators, the role of independence. **Time:** 15 min.

(a) Show that $k\binom{n}{k} = n\binom{n-1}{k-1}$ for $1 \le k \le n$. Use it to compute $E[X]$ for $X \sim B_{p,n}$ directly from the PMF.

(b) Show similarly that $E[X(X - 1)] = n(n - 1)p^2$, and deduce $V(X) = npq$.

(c) Five cards are dealt from a well-shuffled standard deck, and $X$ is the number of hearts. Explain why $X$ is not binomial. Then write $X$ as a sum of indicators and find $E[X]$.

(d) Find $V(X)$ from the covariances of the indicators, and compare it with the variance of $B_{1/4,\,5}$. Explain why the difference goes in the direction it does.

### Problem 8. A reciprocal

**Tests:** CDF method for a decreasing map, the change-of-variables formula, LOTUS, infinite moments. **Time:** 13 min.

$X$ has PDF $f_X(x) = 2x$ on $(0, 1]$, and $Y = 1/X$.

(a) Find the support of $Y$. Use the CDF method to find $F_Y$ and $f_Y$. (Careful: $g(x) = 1/x$ is decreasing.)

(b) Verify $f_Y$ with the formula $f_Y(y) = f_X(x)/\lvert g'(x) \rvert$ at $x = g^{-1}(y)$. What goes wrong without the absolute value?

(c) Find $E[Y]$ two ways: by LOTUS on $X$, and from $f_Y$.

(d) Show that $E[Y^2]$ is infinite, so $Y$ has a finite mean but an infinite variance.

(e) Find $P(Y > 2)$ and the median of $Y$.

### Problem 9. Squaring a lopsided uniform

**Tests:** CDF method for a many-to-one map, piecewise densities, the change-of-variables formula with a varying number of preimages. **Time:** 14 min.

$X$ is uniform on $[-1, 2]$, so $f_X(x) = 1/3$ there. Let $Y = X^2$.

(a) Find the support of $Y$. For which $y$ does $x^2 = y$ have two solutions in $[-1, 2]$, and for which only one?

(b) Use the CDF method to find $F_Y(y)$ for every real $y$.

(c) Differentiate to find $f_Y$, and verify it with $f_Y(y) = \sum_{x \in g^{-1}(y)} f_X(x)/\lvert g'(x) \rvert$. Check that $f_Y$ integrates to 1.

(d) Find $E[Y]$ two ways, and find $P(Y \le 1/4)$.

---

## Challenge

### Problem 10. Where the Poisson comes from

**Tests:** the binomial-to-Poisson limit, Poisson variance, the approximation in practice. **Time:** 18 min.

(a) Fix $\lambda > 0$ and an integer $k \ge 0$. Show that $b_{\lambda/n,\,n}(k) \to e^{-\lambda}\lambda^k/k!$ as $n \to \infty$. You may use $(1 - \lambda/n)^n \to e^{-\lambda}$.

(b) For $Y \sim P_\lambda$, show that $E[Y(Y - 1)] = \lambda^2$, and deduce that $V(Y) = \lambda$.

(c) $B_{\lambda/n,\,n}$ has mean $\lambda$ and variance $\lambda(1 - \lambda/n)$. Explain why this is consistent with (a) and (b), and why the binomial variance is always a little smaller.

(d) A 3000-character message crosses a noisy channel that corrupts each character independently with probability $1/2000$. Approximate the probability that at most one character is corrupted, and write the exact binomial expression that it approximates. You may use $e^{-1.5} \approx 0.2231$.

### Problem 11. Memorylessness characterizes the geometric

**Tests:** proof of a characterization, minimum of independent geometrics, sums over joint events. **Time:** 18 min.

(a) A random variable $X$ takes values in $\lbrace 1, 2, \dots \rbrace$, has $P(X > n) > 0$ for every $n$, and satisfies $P(X > n + m \mid X > n) = P(X > m)$ for all integers $n, m \ge 0$. Show that $X \sim G_p$ with $p = P(X = 1)$. (Hint: let $t_n = P(X > n)$.)

(b) Let $X \sim G_p$ and $Y \sim G_r$ be independent. Show that $\min(X, Y) \sim G_s$ with $s = 1 - (1 - p)(1 - r)$, and explain the result in words.

(c) Ana and Ben each roll their own die once per round, at the same time. Let $A$ and $B$ be the rounds in which Ana and Ben roll their first six. Find the expected number of rounds until at least one of them has rolled a six. Then find $P(A < B)$ and $P(A = B)$.

### Problem 12. The CDF method in reverse

**Tests:** the probability integral transform, inverse-CDF sampling, a many-to-one map with a non-uniform density. **Time:** 20 min.

(a) Let $X$ be continuous with a CDF $F$ that is strictly increasing on an interval $(a, b)$ holding all of $X$'s probability. Show that $U = F(X)$ is uniform on $(0, 1)$, that is, $P(U \le u) = u$ for $0 < u < 1$.

(b) Conversely, let $U$ be uniform on $(0, 1)$, with $F$ as in (a). Show that $X = F^{-1}(U)$ has CDF $F$. Use this to find a function $h$ for which $h(U)$ has PDF $3x^2$ on $(0, 1]$, and a function $k$ for which $k(U)$ has PDF $2y$ on $(0, 1]$.

(c) Let $X$ have PDF $f_X(x) = 3x^2$ on $(0, 1]$, and let $Z = (2X - 1)^2$. Find $F_Z$ and $f_Z$, and check that $f_Z$ integrates to 1.

(d) Find $E[Z]$ two ways.
