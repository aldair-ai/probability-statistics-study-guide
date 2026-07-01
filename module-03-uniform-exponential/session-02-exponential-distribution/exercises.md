# Session 2 Exercises: The Exponential Distribution and Service Times

Solve these by hand, exam style, without code. Give answers as exact expressions, with decimals where they help. Notation follows the notes: $E_\lambda$ is the exponential distribution with rate $\lambda$, with density $\lambda e^{-\lambda x}$ for $x \ge 0$.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 31 min |
| Exam-level | 5-9 | 68 min |
| Challenge | 10-12 | 60 min |

---

## Warm-up

### Problem 1. A sensor's lifetime

**Tests:** rate versus mean, CDF, interval probabilities, median. **Time:** 7 min.

The lifetime $T$ of a sensor is exponential with mean 5 years.

(a) Find the rate $\lambda$, the PDF, and the CDF of $T$.

(b) Find $P(T > 5)$, $P(T \le 2)$, and $P(2 < T \le 6)$.

(c) Find $\sigma_T$ and the median of $T$.

(d) What fraction of sensors outlive the mean? Would this change if the mean were 50 years?

### Problem 2. Help desk calls

**Tests:** quantiles, a ratio free of the parameter. **Time:** 7 min.

Calls to a help desk last an exponential time with mean 4 minutes.

(a) For a general $E_\lambda$ and $0 < q < 1$, show that the value $t_q$ with $P(X \le t_q) = q$ is $t_q = -\ln(1 - q)/\lambda$.

(b) Find the median call length and the 90th percentile.

(c) Show that the ratio of the 90th percentile to the median does not depend on $\lambda$, and evaluate it.

### Problem 3. True or false

**Tests:** density versus probability, scaling, shifts, moments, tails. **Time:** 10 min.

Let $X \sim E_\lambda$. Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) $P(X > E[X])$ has the same value for all $\lambda$.

(b) The density of $X$ never exceeds 1.

(c) $3X \sim E_{3\lambda}$.

(d) $X + 1$ is exponentially distributed.

(e) The mean and the standard deviation of $X$ are equal.

(f) $P(X > 2t) = P(X > t)^2$ for all $t \ge 0$.

### Problem 4. A polling server

**Tests:** the geometric-to-exponential limit, the success rate. **Time:** 7 min.

A server checks for a request once per millisecond. Each check independently finds a request with probability 0.002. Let $T$ be the time in seconds until the first request.

(a) Identify the number of trials per second $n$, the success probability $p$, and the rate $\lambda$.

(b) Write the exact value of $P(T > 1.5)$, and find it using $\ln(1 - x) \approx -x - x^2/2$. Compare it with the exponential limit.

(c) Find the mean of $T$ in the discrete model and in the limit.

---

## Exam-level

### Problem 5. All the moments

**Tests:** integration by parts, an induction, tail integrals, the third central moment. **Time:** 13 min.

Let $X \sim E_\lambda$.

(a) Show by parts that $E[X^n] = \frac{n}{\lambda} E[X^{n-1}]$ for $n \ge 1$, and conclude that $E[X^n] = n!/\lambda^n$.

(b) Show that for any nonnegative $X$ with a density, $E[X] = \int_0^\infty P(X > x)\, dx$. Use this to find $E[X]$ for the exponential again.

(c) Show that $E[(X - \mu)^3] = 2/\lambda^3$. What does its positive sign say about the shape of the distribution?

(d) Evaluate $E[X^3]$ and the third central moment at $\lambda = 2$.

### Problem 6. Waiting for a ride

**Tests:** memorylessness, conditional means, comparison with an aging model. **Time:** 13 min.

The wait $W$ for a ride is exponential with mean 6 minutes. You have already waited 4 minutes.

(a) Find the probability that you wait at least 3 more minutes.

(b) Find your expected total wait, given what you know.

(c) Find $P(W \le 10 \mid W > 4)$.

(d) Answer (a), (b), and (c) again if $W$ is instead uniform on $[0, 12]$, which has the same mean. Explain the difference.

### Problem 7. Units and other maps

**Tests:** the CDF method, closure under scaling, recognizing non-exponential maps. **Time:** 14 min.

Let $X$ be exponential with mean 2 years, and let $Y = 12X$ be the same time in months.

(a) Use the CDF method to show that $Y \sim E_{1/24}$.

(b) Find $P(Y > 30)$, and check it by computing the matching probability for $X$.

(c) Show that $aX$ is exponential for every $a > 0$, with rate $\lambda/a$. Why does no negative $a$ work?

(d) Find $P(X^2 > y)$ for $y \ge 0$. Why is $X^2$ not exponential? Evaluate $P(X^2 > 4)$.

(e) For $c > 0$, use the mean and the standard deviation to show that $X + c$ is not exponential.

### Problem 8. Conditional means and a warranty

**Tests:** direct integration, total expectation, an application. **Time:** 14 min.

Let $X \sim E_\lambda$ and $a > 0$.

(a) Find $E[X \mid X > a]$ by integrating, without using memorylessness.

(b) Use the law of total expectation to show that

$$E[X \mid X \le a] = \frac{1}{\lambda} - \frac{a e^{-\lambda a}}{1 - e^{-\lambda a}}.$$

(c) Evaluate this at $\lambda = 1$, $a = 1$. Should the answer be above or below $a/2$? Explain.

(d) A device with mean life 2 years has a one-year warranty that pays \$100 if it fails during that year. Find the expected payout, and the expected further life of a device that survives the warranty period.

### Problem 9. Two clerks and you

**Tests:** memorylessness at a counter, the minimum of two exponentials, expected finish times. **Time:** 14 min.

Two clerks have just started serving customers $A$ and $B$, and you are next in line. All service times are independent and exponential with mean 10 minutes.

(a) Find the probability that you are the last of the three to finish. Justify your answer.

(b) Let $M = \min(A, B)$. Show that $P(M > t) = e^{-2\lambda t}$, and find the expected time until you start.

(c) Find the expected time until you finish.

(d) Find the expected time until all three are done.

(e) Answer (c) and (d) again if every service takes exactly 10 minutes. What changed, and what did not?

---

## Challenge

### Problem 10. The only memoryless distribution

**Tests:** a uniqueness proof, functional equations. **Time:** 20 min.

Let $X > 0$ be a continuous random variable with tail $G(x) = P(X > x)$, and assume that $0 < G(1) < 1$.

(a) Show that $P(X > a + b \mid X > a) = P(X > b)$ for all $a, b \ge 0$ is equivalent to $G(a + b) = G(a) G(b)$ for all $a, b \ge 0$.

(b) Assuming this, show that $G(n) = G(1)^n$ for positive integers $n$.

(c) Show that $G(1/m) = G(1)^{1/m}$ for positive integers $m$, and hence that $G(r) = G(1)^r$ for every rational $r > 0$.

(d) Use the fact that $G$ is monotone to show that $G(x) = e^{-\lambda x}$ for all $x > 0$, with $\lambda = -\ln G(1) > 0$.

(e) What does the same argument give for a random variable on the positive integers?

### Problem 11. Races between exponentials

**Tests:** minimum of exponentials, competing rates, a counter with unequal clerks. **Time:** 20 min.

Let $X \sim E_\lambda$ and $Y \sim E_\mu$ be independent.

(a) Show that $\min(X, Y) \sim E_{\lambda + \mu}$.

(b) Use $P(X < Y) = \int_0^\infty f_X(x) P(Y > x)\, dx$ to show that $P(X < Y) = \frac{\lambda}{\lambda + \mu}$.

(c) Clerks with rates $\lambda_1$ and $\lambda_2$ are serving customers $A$ and $B$, and you take the first clerk who becomes free. Show that

$$P(\text{you finish last}) = \frac{2\lambda_1\lambda_2}{(\lambda_1 + \lambda_2)^2}.$$

(d) Evaluate this for $\lambda_1 = 2$ and $\lambda_2 = 1$. Show that the probability never exceeds $\frac{1}{2}$, and find when it equals $\frac{1}{2}$.

### Problem 12. More servers, and service that ages

**Tests:** the general $s$-server result, its cost, a counterexample without memorylessness. **Time:** 20 min.

(a) A counter has $s$ servers and exponential service times with a common rate. You stand behind at least $s$ other customers, with nobody behind you. Show that $P(\text{you finish last}) = 1/s$.

(b) If the $s + 1$ customers at an $s$-server counter were placed in a random order, each one would finish last with probability $\frac{1}{s + 1}$. Find the increase in your probability when you are placed last, and evaluate it at $s = 2, 3, 10$.

(c) Take $s = 3$, $\lambda = 1$, and exactly 3 customers ahead of you. Find the expected time until everyone is done.

(d) Now take two clerks, one customer ahead of you at each, and independent service times uniform on $[0, 1]$. Show that $P(\text{you finish last}) = \frac{2}{3}$. You may use $E\lvert A - B \rvert = \frac{1}{3}$ for independent uniforms $A$ and $B$. Compare this with the exponential and constant cases, and explain the order of the three answers.
