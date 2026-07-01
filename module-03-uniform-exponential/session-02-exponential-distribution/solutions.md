# Session 2 Solutions: The Exponential Distribution and Service Times

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. A sensor's lifetime

**(a)** $\lambda = 1/\mu = \frac{1}{5}$ per year. For $t \ge 0$: $f(t) = \frac{1}{5} e^{-t/5}$ and $F(t) = 1 - e^{-t/5}$.

**(b)**

- $P(T > 5) = e^{-1} \approx 0.3679$.
- $P(T \le 2) = 1 - e^{-2/5} \approx 0.3297$.
- $P(2 < T \le 6) = e^{-2/5} - e^{-6/5} \approx 0.6703 - 0.3012 = 0.3691$.

**(c)** $\sigma_T = 1/\lambda = 5$ years, and the median is $5 \ln 2 \approx 3.466$ years.

**(d)** $P(T > \mu) = e^{-\lambda \cdot 1/\lambda} = e^{-1} \approx 0.3679$. This is the same for every exponential, so it would not change with a mean of 50 years.

**Key idea:** convert the mean to the rate first, and then read everything from the tail $e^{-\lambda t}$.

### Problem 2. Help desk calls

**(a)** $1 - e^{-\lambda t_q} = q$ gives $e^{-\lambda t_q} = 1 - q$, so $t_q = -\ln(1 - q)/\lambda$.

**(b)** With $\lambda = \frac{1}{4}$: the median is $4 \ln 2 \approx 2.773$ minutes, and the 90th percentile is $-4 \ln(0.1) = 4 \ln 10 \approx 9.210$ minutes.

**(c)** The factor $1/\lambda$ cancels in the ratio:

$$\frac{t_{0.9}}{t_{0.5}} = \frac{\ln 10}{\ln 2} = \log_2 10 \approx 3.322.$$

**Key idea:** every quantile is a fixed multiple of the mean, because $\lambda$ only sets the scale.

### Problem 3. True or false

**(a) True.** $P(X > 1/\lambda) = e^{-1}$ for all $\lambda$.

**(b) False.** $f(0) = \lambda$, which exceeds 1 whenever $\lambda > 1$. A density can exceed 1.

**(c) False.** Scaling by 3 divides the rate by 3, so $3X \sim E_{\lambda/3}$. Check: the mean of $3X$ is $3/\lambda$.

**(d) False.** $X + 1 \ge 1$ always, so $P(X + 1 > \frac{1}{2}) = 1$, which no exponential tail can match. An exponential puts positive probability on every interval starting at 0.

**(e) True.** Both equal $1/\lambda$.

**(f) True.** $e^{-2\lambda t} = (e^{-\lambda t})^2$. This is memorylessness with $a = b = t$.

**Key idea:** the family is closed under positive scaling but not under shifts, and the rate moves opposite to the scale.

### Problem 4. A polling server

**(a)** $n = 1000$ per second, $p = 0.002$, and $\lambda = np = 2$ per second.

**(b)** $T > 1.5$ means that the first 1500 checks all fail, so $P(T > 1.5) = 0.998^{1500}$. Using the expansion with $x = 0.002$: $\ln 0.998 \approx -0.002 - 0.000002 = -0.002002$, so $1500 \ln 0.998 \approx -3.003$, and

$$0.998^{1500} \approx e^{-3.003} \approx 0.04964.$$

The limit is $e^{-\lambda \cdot 1.5} = e^{-3} \approx 0.04979$, which differs by only about 0.3%.

**(c)** The geometric mean is $1/p = 500$ checks, that is, $0.5$ seconds. In the limit, $1/\lambda = 0.5$ seconds. They agree exactly.

**Key idea:** when $p$ is small, a geometric waiting time measured in time units is already nearly exponential, with rate $np$.

---

## Exam-level

### Problem 5. All the moments

**(a)** Take $u = x^n$ and $dv = \lambda e^{-\lambda x}\, dx$, so $du = n x^{n-1}\, dx$ and $v = -e^{-\lambda x}$:

$$E[X^n] = -x^n e^{-\lambda x} \Big|_0^\infty + \int_0^\infty n x^{n-1} e^{-\lambda x}\, dx = 0 + \frac{n}{\lambda} \int_0^\infty x^{n-1} \lambda e^{-\lambda x}\, dx = \frac{n}{\lambda} E[X^{n-1}].$$

Starting from $E[X^0] = 1$, repeating this gives $E[X^n] = \frac{n}{\lambda} \cdot \frac{n - 1}{\lambda} \cdots \frac{1}{\lambda} = \frac{n!}{\lambda^n}$.

**(b)** Write $x = \int_0^x du$ and swap the order of integration over the region $0 \le u < x$:

$$E[X] = \int_0^\infty \left(\int_0^x du\right) f(x)\, dx = \int_0^\infty \left(\int_u^\infty f(x)\, dx\right) du = \int_0^\infty P(X > u)\, du.$$

For the exponential: $\int_0^\infty e^{-\lambda x}\, dx = 1/\lambda$.

**(c)** Expand with $\mu = 1/\lambda$, and use (a):

$$E[(X - \mu)^3] = E[X^3] - 3\mu E[X^2] + 3\mu^2 E[X] - \mu^3 = \frac{6}{\lambda^3} - \frac{6}{\lambda^3} + \frac{3}{\lambda^3} - \frac{1}{\lambda^3} = \frac{2}{\lambda^3}.$$

The positive sign reflects skew to the right: the long tail above the mean outweighs the short range below it.

**(d)** At $\lambda = 2$: $E[X^3] = \frac{6}{8} = \frac{3}{4} = 0.75$, and $E[(X - \mu)^3] = \frac{2}{8} = \frac{1}{4} = 0.25$.

**Key idea:** one integration by parts gives a recursion, so all the moments come at once.

### Problem 6. Waiting for a ride

Here $\lambda = \frac{1}{6}$.

**(a)** By memorylessness, $P(W > 7 \mid W > 4) = P(W > 3) = e^{-1/2} \approx 0.6065$.

**(b)** $E[W \mid W > 4] = 4 + 6 = 10$ minutes.

**(c)** $P(W \le 10 \mid W > 4) = P(W \le 6) = 1 - e^{-1} \approx 0.6321$.

**(d)** Given $W > 4$, a uniform on $[0, 12]$ is uniform on $(4, 12]$, so:

- $P(W > 7 \mid W > 4) = \frac{5}{8} = 0.625$.
- $E[W \mid W > 4] = 8$ minutes.
- $P(W \le 10 \mid W > 4) = \frac{6}{8} = \frac{3}{4} = 0.75$.

Under the uniform model, the ride must arrive by minute 12, so having waited brings it closer: the expected total is 8 and not 10. The exponential model has no such deadline, and past waiting buys nothing.

**Key idea:** memorylessness resets the clock, while a bounded lifetime ages.

### Problem 7. Units and other maps

**(a)** For $y \ge 0$, with $\lambda = \frac{1}{2}$:

$$F_Y(y) = P(12X \le y) = P\left(X \le \frac{y}{12}\right) = 1 - e^{-y/24},$$

which is the CDF of $E_{1/24}$.

**(b)** $P(Y > 30) = e^{-30/24} = e^{-5/4} \approx 0.2865$. The matching event is $X > 2.5$, and $P(X > 2.5) = e^{-2.5/2} = e^{-5/4}$.

**(c)** For $a > 0$: $P(aX > y) = P(X > y/a) = e^{-(\lambda/a) y}$, the tail of $E_{\lambda/a}$. For $a < 0$, the variable $aX$ is nonpositive, so it cannot be exponential.

**(d)** For $y \ge 0$: $P(X^2 > y) = P(X > \sqrt{y}) = e^{-\lambda\sqrt{y}}$. This is not of the form $e^{-cy}$ for any constant $c$, so $X^2$ is not exponential. With $\lambda = \frac{1}{2}$: $P(X^2 > 4) = P(X > 2) = e^{-1} \approx 0.3679$.

**(e)** $X + c$ has mean $\frac{1}{\lambda} + c$ and standard deviation $\frac{1}{\lambda}$. These differ when $c > 0$, but an exponential has equal mean and standard deviation.

**Key idea:** only positive scaling stays in the family. The fact that $\mu = \sigma$ gives a quick test for membership.

### Problem 8. Conditional means and a warranty

**(a)** Using the density given $X > a$, which is $\lambda e^{-\lambda x}/e^{-\lambda a}$ on $x > a$, and substituting $x = a + t$:

$$E[X \mid X > a] = \frac{1}{e^{-\lambda a}} \int_a^\infty x \lambda e^{-\lambda x}\, dx = \int_0^\infty (a + t) \lambda e^{-\lambda t}\, dt = a + \frac{1}{\lambda}.$$

**(b)** Total expectation gives

$$\frac{1}{\lambda} = (1 - e^{-\lambda a})\, E[X \mid X \le a] + e^{-\lambda a}\left(a + \frac{1}{\lambda}\right).$$

Moving the last term across, $(1 - e^{-\lambda a})\, E[X \mid X \le a] = \frac{1 - e^{-\lambda a}}{\lambda} - a e^{-\lambda a}$. Divide by $1 - e^{-\lambda a}$.

**(c)** At $\lambda = a = 1$:

$$E[X \mid X \le 1] = 1 - \frac{e^{-1}}{1 - e^{-1}} = 1 - \frac{1}{e - 1} = \frac{e - 2}{e - 1} \approx 0.4180.$$

This is below $a/2 = 0.5$, as it should be: on $[0, 1]$ the density is decreasing, so the probability leans toward 0.

**(d)** The expected payout is $100\, P(X \le 1) = 100(1 - e^{-1/2}) \approx \$39.35$. By memorylessness, a device that survives the warranty has an expected further life of 2 years.

**Key idea:** one of the two conditional means is easy, and total expectation then gives the other one.

### Problem 9. Two clerks and you

Here $\lambda = \frac{1}{10}$.

**(a)** $\frac{1}{2}$. When the first of $A, B$ finishes, you start, and two people are in service. By memorylessness, the other person's remaining time is $E_\lambda$, independent of everything before, just like yours. By symmetry, each of you is equally likely to finish last.

**(b)** By independence, $P(M > t) = P(A > t) P(B > t) = e^{-2\lambda t}$, so $M \sim E_{2\lambda}$, with mean $\frac{1}{2\lambda} = 5$ minutes.

**(c)** You start at $M$, and then take an independent $E_\lambda$ service: $5 + 10 = 15$ minutes.

**(d)** Split the time into stages. For the first 5 minutes on average, $A$ and $B$ are in service. Then two people are in service, and the first of them finishes after another 5 minutes on average. Then the last person needs a fresh 10 minutes on average. The total is $5 + 5 + 10 = 20$ minutes.

**(e)** With constant service, you start at 10 and finish at 20, and all three are done at 20. So your finish time gets worse (15 to 20), while the time for all three stays 20. You are now certainly the last one, as opposed to last with probability $\frac{1}{2}$.

**Key idea:** memorylessness restarts every remaining service at each event, so the time splits into independent stages.

---

## Challenge

### Problem 10. The only memoryless distribution

**(a)** Since $X > a + b$ implies $X > a$, the conditional probability is $G(a + b)/G(a)$. Setting it equal to $G(b)$ gives $G(a + b) = G(a) G(b)$, and dividing by $G(a)$ reverses this. Division is safe, since $G(n) = G(1)^n > 0$ by (b) and $G$ is nonincreasing, so $G(a) > 0$ for all $a$.

**(b)** By induction, $G(n) = G(n - 1) G(1) = G(1)^n$.

**(c)** Applying the product rule $m$ times to $1/m$: $G(1) = G(1/m)^m$, so $G(1/m) = G(1)^{1/m}$. For $r = k/m$: $G(r) = G(1/m)^k = G(1)^{k/m}$.

**(d)** Let $\lambda = -\ln G(1)$, which is positive since $0 < G(1) < 1$. By (c), $G(r) = e^{-\lambda r}$ for every rational $r > 0$. For real $x > 0$, take rationals $r < x < s$. Since $G$ is nonincreasing,

$$e^{-\lambda s} = G(s) \le G(x) \le G(r) = e^{-\lambda r}.$$

Letting $r$ and $s$ approach $x$ gives $G(x) = e^{-\lambda x}$.

**(e)** On the positive integers, only (b) is needed: $G(n) = q^n$ with $q = G(1)$, and $P(X = n) = G(n - 1) - G(n) = q^{n-1}(1 - q)$. This is the geometric distribution, the discrete memoryless distribution.

**Key idea:** the product rule pins $G$ down on integers, then rationals, and monotonicity fills in the rest.

### Problem 11. Races between exponentials

**(a)** By independence, $P(\min(X, Y) > t) = P(X > t) P(Y > t) = e^{-\lambda t} e^{-\mu t} = e^{-(\lambda + \mu) t}$.

**(b)**

$$P(X < Y) = \int_0^\infty \lambda e^{-\lambda x} e^{-\mu x}\, dx = \lambda \int_0^\infty e^{-(\lambda + \mu) x}\, dx = \frac{\lambda}{\lambda + \mu}.$$

**(c)** Condition on who frees up first.

- $A$ finishes first, with probability $\frac{\lambda_1}{\lambda_1 + \lambda_2}$. You now have clerk 1 (rate $\lambda_1$), and $B$'s remaining time is $E_{\lambda_2}$ by memorylessness. You finish last if $B$ finishes before you, with probability $\frac{\lambda_2}{\lambda_1 + \lambda_2}$.
- $B$ finishes first, with probability $\frac{\lambda_2}{\lambda_1 + \lambda_2}$. You now have clerk 2, and $A$'s remaining time is $E_{\lambda_1}$. You finish last with probability $\frac{\lambda_1}{\lambda_1 + \lambda_2}$.

Each case contributes $\frac{\lambda_1\lambda_2}{(\lambda_1 + \lambda_2)^2}$, which gives the total.

**(d)** For $\lambda_1 = 2$ and $\lambda_2 = 1$: $\frac{2 \cdot 2 \cdot 1}{9} = \frac{4}{9} \approx 0.4444$. Also,

$$\frac{1}{2} - \frac{2\lambda_1\lambda_2}{(\lambda_1 + \lambda_2)^2} = \frac{(\lambda_1 - \lambda_2)^2}{2(\lambda_1 + \lambda_2)^2} \ge 0,$$

with equality exactly when $\lambda_1 = \lambda_2$. So equal clerks are the worst case for the person who starts last.

**Key idea:** a race between exponentials is won with probability proportional to rate, and memorylessness makes each stage a fresh race.

### Problem 12. More servers, and service that ages

**(a)** At the moment you start, exactly $s - 1$ others are in service, and everyone else ahead of you has finished. By memorylessness, the $s - 1$ remaining times are fresh and identically distributed, just like yours, and they are independent. By symmetry, you are last among these $s$ with probability $1/s$.

**(b)** The increase is $\frac{1}{s} - \frac{1}{s + 1} = \frac{1}{s(s + 1)}$. That is $\frac{1}{6} \approx 0.1667$ at $s = 2$, $\frac{1}{12} \approx 0.08333$ at $s = 3$, and $\frac{1}{110} \approx 0.009091$ at $s = 10$.

**(c)** With 3 servers busy, the first finishes after a mean of $\frac{1}{3}$, and you start. Then 3 are in service, with stage means $\frac{1}{3}$, $\frac{1}{2}$, and $1$. The total is

$$\frac{1}{3} + \frac{1}{3} + \frac{1}{2} + 1 = \frac{13}{6} \approx 2.167.$$

**(d)** You start at $\min(A, B)$, and the other customer finishes $\lvert A - B \rvert$ later. So you finish last exactly when your service $Y$ exceeds $\lvert A - B \rvert$. Given $\lvert A - B \rvert = t$, this has probability $1 - t$, since $Y$ is uniform on $[0, 1]$. Therefore

$$P(\text{you finish last}) = E\big[1 - \lvert A - B \rvert\big] = 1 - \frac{1}{3} = \frac{2}{3} \approx 0.6667.$$

The three answers are ordered $1 > \frac{2}{3} > \frac{1}{2}$ for constant, uniform, and exponential service. Uniform service ages, so the person already in service tends to have less time left than your fresh service, which puts you at a disadvantage. Constant service is the extreme case, and the exponential has no aging at all.

**Key idea:** the fair-looking $\frac{1}{s}$ comes from memorylessness. Service that ages makes starting late worse.
