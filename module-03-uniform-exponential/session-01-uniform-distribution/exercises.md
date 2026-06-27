# Session 1 Exercises: The Uniform Distribution

Solve these by hand, exam style, without code. Give answers as exact fractions or exact expressions, with decimals where they help. Notation follows the notes: $U_{[a,b]}$ is the uniform distribution on $[a, b]$, with density $1/(b - a)$ there.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 32 min |
| Exam-level | 5-9 | 68 min |
| Challenge | 10-12 | 55 min |

---

## Warm-up

### Problem 1. Waiting for a shuttle

**Tests:** density constant, CDF, interval probabilities, mean and variance. **Time:** 7 min.

A shuttle leaves every 12 minutes. You arrive with no knowledge of the schedule, so your wait $W$ (in minutes) is $U_{[0,12]}$.

(a) Find the density and the CDF of $W$.

(b) Find $P(W > 8)$ and $P(3 < W \le 5)$.

(c) Find $E[W]$, $V(W)$, and $\sigma_W$.

### Problem 2. An interval that crosses zero

**Tests:** clipping to the domain, absolute values, a quantile, conditional probability. **Time:** 8 min.

Let $X \sim U_{[-2,\,6]}$.

(a) Find $P(X > 0)$, $P(\lvert X \rvert < 1)$, $P(X = 1)$, and $P(X < 10)$.

(b) Find $E[X]$, $V(X)$, and $\sigma_X$.

(c) Find the value $t$ with $P(X \le t) = 1/4$.

(d) Find $P(X > 5 \mid X > 0)$.

### Problem 3. True or false

**Tests:** density versus probability, closure, moments, within-one-sigma. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) The density of $U_{[0,\,1/4]}$ is greater than 1 on its whole domain.

(b) For $X \sim U_{[a,b]}$, $P\big(X = \frac{a + b}{2}\big)$ is the largest single-point probability, and is positive.

(c) If $X \sim U_{[a,b]}$, then $-X \sim U_{[-b,\,-a]}$.

(d) If $X \sim U_{[0,1]}$, then $X^2 \sim U_{[0,1]}$.

(e) The standard deviation of $U_{[a,b]}$ is $(b - a)/12$.

(f) For every uniform distribution, $P(\mu - \sigma \le X \le \mu + \sigma)$ is the same number.

### Problem 4. A room's temperature

**Tests:** an affine map, tracking how the mean, the standard deviation, and the density change. **Time:** 7 min.

A room's temperature in Fahrenheit, $F$, is $U_{[68,\,77]}$. Let $C = \frac{5}{9}(F - 32)$ be the same temperature in Celsius.

(a) Find the distribution of $C$, including its interval and density.

(b) Find $E[C]$ and $\sigma_C$.

(c) Find $\sigma_F$, and verify that $\sigma_C/\sigma_F = 5/9$.

---

## Exam-level

### Problem 5. A decreasing map

**Tests:** the CDF method for a decreasing map, the change-of-variables formula, solving for the map. **Time:** 13 min.

Let $X \sim U_{[1,4]}$ and $Y = 10 - 2X$.

(a) Find the interval on which $Y$ lives.

(b) Find $F_Y$ with the CDF method, and differentiate to get $f_Y$. Check it against the formula $f_Y(y) = f_X(x)/\lvert g'(x) \rvert$.

(c) Find $E[Y]$ and $V(Y)$ in two ways: from the distribution of $Y$, and from the moments of $X$.

(d) Find $P(Y > 6)$ in two ways.

(e) Find all pairs of constants $(c, d)$ such that $cX + d \sim U_{[0,1]}$.

### Problem 6. The morning commute

**Tests:** an event as a union of intervals, total expectation with piecewise conditional means. **Time:** 15 min.

Trains leave a station at 15, 30, and 45 minutes past each hour. You arrive at a time uniform between 10 and 40 minutes past the hour, and you board the next train. Let $T$ be your wait.

(a) Find $P(T < 5)$ and $P(T > 10)$.

(b) By conditioning on which train you catch, find $E[T]$.

(c) Compare $E[T]$ with the mean wait for arrival times uniform on a whole number of 15-minute cycles. Explain why the two agree or differ.

### Problem 7. All the moments

**Tests:** moments of the uniform, deriving the variance directly, LOTUS, Jensen-type comparison. **Time:** 12 min.

(a) For $X \sim U_{[0,1]}$ and an integer $k \ge 0$, find $E[X^k]$.

(b) For $Y \sim U_{[a,b]}$, show that $E[Y^2] = \frac{a^2 + ab + b^2}{3}$, and derive $V(Y) = \frac{(b - a)^2}{12}$ directly from this. Check your work at $a = 1$, $b = 3$.

(c) For $X \sim U_{[0,1]}$, find $E[e^X]$ and $E\big[\frac{1}{1 + X}\big]$.

(d) Compare these with $e^{E[X]}$ and $\frac{1}{1 + E[X]}$. In which direction do they differ, and why?

### Problem 8. Breaking a stick

**Tests:** functions of a uniform, many-to-one maps, ratio distributions. **Time:** 15 min.

A stick of length 1 breaks at a point $X \sim U_{[0,1]}$. Let $L = \max(X, 1 - X)$ be the longer piece, and let $S = 1 - L$ be the shorter piece.

(a) Show that $L \sim U_{[1/2,\,1]}$ and $S \sim U_{[0,\,1/2]}$. Find $E[L]$, $E[S]$, and $V(L)$.

(b) Let $R = S/L$. Show that for $0 \le r \le 1$, $F_R(r) = \frac{2r}{1 + r}$, and find $f_R$.

(c) Find $P(R \le 1/2)$ and $E[R]$.

(d) Is $E[R]$ equal to $E[S]/E[L]$? Explain.

### Problem 9. Conditioning and memory

**Tests:** conditioning on an interval, total expectation, comparing conditional tails. **Time:** 13 min.

Let $X \sim U_{[0,10]}$ be the lifetime of a part, in years.

(a) Show that given $X > 4$, $X$ is uniform on $(4, 10]$. More generally, what is the distribution of a uniform variable conditioned on a subinterval?

(b) Find $E[X \mid X > 4]$ and $E[X \mid X \le 4]$, and verify the law of total expectation.

(c) Find $P(X > 6 \mid X > 4)$, and compare it with $P(X > 2)$.

(d) Find $P(X > s + 2 \mid X > s)$ as a function of $s$, for $0 \le s \le 8$. Does a part that has survived longer have a better or worse chance of lasting 2 more years? Evaluate at $s = 0, 4, 6$.

---

## Challenge

### Problem 10. From discrete to continuous

**Tests:** limits of discrete uniforms, moments, convergence of CDFs. **Time:** 15 min.

Let $D_n$ be uniform on $\lbrace 1/n, 2/n, \dots, n/n \rbrace$.

(a) Show that $E[D_n] = \frac{n + 1}{2n}$ and $V(D_n) = \frac{n^2 - 1}{12n^2}$. You may use $\sum_{k=1}^{n} k^2 = \frac{n(n+1)(2n+1)}{6}$.

(b) Find the limits as $n \to \infty$, and compare with $U_{[0,1]}$. Evaluate $V(D_n)$ at $n = 2, 5, 10$.

(c) Find the CDF of $D_n$, and show that it converges to the CDF of $U_{[0,1]}$ at every $x$.

(d) Explain in what sense $U_{[0,1]}$ is the "continuous version" of an equally likely discrete choice. Does $P(D_n = x)$ converge to $P(X = x)$ for $x$ in $(0, 1]$ that is a value of $D_n$?

### Problem 11. How spread out can a bounded variable be?

**Tests:** deviation probabilities, a proof of a variance bound, extremal distributions. **Time:** 20 min.

(a) Let $X \sim U_{[a,b]}$. For $t > 0$, find $P(\lvert X - \mu \rvert \ge t\sigma)$. Evaluate at $t = 1$ and $t = 1.5$. What happens for $t > \sqrt{3}$?

(b) Let $Z$ be any random variable with values in $[a, b]$. Show that $V(Z) \le E\big[(Z - c)^2\big]$ for any constant $c$, by expanding $E[(Z - c)^2]$.

(c) Take $c = \frac{a + b}{2}$ in (b) to show that $V(Z) \le \frac{(b - a)^2}{4}$. Find a distribution that attains the bound.

(d) For a given interval $[a, b]$, compute the ratio of the standard deviation of the uniform to this largest possible standard deviation. Interpret it.

### Problem 12. Maps that do and do not preserve uniformity

**Tests:** many-to-one maps, a non-affine map that preserves uniformity, a forward link to the exponential. **Time:** 20 min.

Let $X \sim U_{[0,1]}$.

(a) Let $T = 1 - \lvert 2X - 1 \rvert$ be the tent map. Show that $T \sim U_{[0,1]}$, even though the map is neither affine nor one-to-one.

(b) Find the density of $X^2$, and find its mean and variance in two ways, and $P(X^2 \le 1/4)$.

(c) Let $Y = -\ln(1 - X)$. Show that $P(Y > y) = e^{-y}$ for $y \ge 0$, and find its density. Find $E[Y]$ by LOTUS on $X$.

(d) Explain why (a) does not contradict the fact that, in general, non-affine maps destroy uniformity. What condition on the preimages of a point makes $f_Y$ flat?
