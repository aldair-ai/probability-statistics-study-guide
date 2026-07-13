# Session 3 Exercises: Normal Approximation of the Binomial

Solve these by hand, exam style, without code. Use this excerpt from the Z table. Notation follows the notes: $B_{p,n}$ is the binomial with $n$ trials and success probability $p$, $q = 1 - p$, and $N_{\mu,\sigma^2}(x)$ is the normal density at $x$. Use the continuity correction unless a problem says otherwise.

| $z$ | 0.16 | 0.50 | 0.56 | 1.00 | 1.05 | 1.10 | 1.50 | 1.645 | 1.90 | 1.95 | 1.96 | 1.98 | 2.00 | 2.05 | 2.10 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| $\Phi(z)$ | .5636 | .6915 | .7123 | .8413 | .8531 | .8643 | .9332 | .9500 | .9713 | .9744 | .9750 | .9761 | .9772 | .9798 | .9821 |

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 30 min |
| Exam-level | 5-9 | 68 min |
| Challenge | 10-12 | 58 min |

---

## Warm-up

### Problem 1. Choosing the normal

**Tests:** matching mean and variance, the density approximation. **Time:** 7 min.

Let $X \sim B_{0.2,\,400}$.

(a) Find the normal distribution that approximates it.

(b) Use the normal density to approximate $P(X = 80)$.

(c) Use the normal density to approximate $P(X = 88)$.

(d) The exact values are $0.04981$ and $0.02952$. Which approximation is better, and why would you expect that?

### Problem 2. Translating events

**Tests:** the continuity correction with strict and non-strict inequalities. **Time:** 8 min.

Let $X \sim B_{1/2,\,64}$, approximated by $Y \sim N_{32,16}$. Translate each event into an event for $Y$, and give the matching limits for $Z$.

(a) $X = 30$.

(b) $X \in \lbrace 31, 32, 33 \rbrace$.

(c) $X \ge 36$.

(d) $X > 36$.

(e) $X < 28$.

(f) $28 < X \le 35$.

(g) $30 < X < 31$.

### Problem 3. True or false

**Tests:** the theorem's meaning and its limits. **Time:** 8 min.

For $X \sim B_{p,n}$ and $Y \sim N_{np,npq}$, decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) $P(X = k) \approx P(Y = k)$ for $k$ near $np$.

(b) For large $n$ with $np$ an integer, $P(X = np) \approx \frac{1}{\sqrt{2\pi npq}}$.

(c) For fixed $p$, the ratio $B_{p,n}(n)/N_{np,npq}(n)$ tends to 1 as $n \to \infty$.

(d) The normal approximation is accurate for $B_{0.001,\,100}$.

(e) The continuity correction keeps $P(X \le k) + P(X \ge k + 1) = 1$.

(f) With the continuity correction, $P(X \ge 60)$ and $P(X > 60)$ have the same approximation.

### Problem 4. Fair coin tosses

**Tests:** an interval probability, a tail probability. **Time:** 7 min.

A fair coin is tossed 400 times, and $X$ counts the heads.

(a) Find $\mu$ and $\sigma$.

(b) Approximate $P(190 \le X \le 210)$.

(c) Approximate $P(X \ge 220)$.

---

## Exam-level

### Problem 5. An election poll

**Tests:** approximating a small probability, planning a sample size. **Time:** 13 min.

In a large population, 52% support candidate $A$. A poll asks 2500 randomly chosen people, and $X$ counts the supporters of $A$.

(a) Find $\mu$ and $\sigma$ for $X$.

(b) The poll shows $A$ not winning if $X \le 1250$. Approximate this probability.

(c) Ignoring the continuity correction, approximately how many people must be polled, so that this error has probability at most $0.025$?

### Problem 6. Overbooking

**Tests:** a one-sided interval, solving for $n$, the size of the error. **Time:** 14 min.

A flight has 200 seats. Each ticket holder shows up independently with probability $0.9$.

(a) With 220 tickets sold, approximate the probability that more people show up than there are seats.

(b) Find the largest number of tickets for which the approximate overbooking probability is at most $0.05$.

(c) The exact probabilities are $0.2943$ for (a), and $0.0297$, $0.0496$, and $0.0782$ for 214, 215, and 216 tickets. Compare them with your answers. What feature of $B_{0.9,\,n}$ explains the error?

### Problem 7. Peak probabilities

**Tests:** the $k = np$ formula, its dependence on $n$ and $p$, the link to voting. **Time:** 13 min.

(a) Approximate $P(X = n/2)$ for a fair coin, with $n = 100$ and $n = 10{,}000$.

(b) How large must an even $n$ be, for $P(X = n/2)$ to be below $0.01$, according to the approximation?

(c) For a fixed $n$, which $p$ gives the smallest peak probability? Why does this make sense?

(d) Use the formula to approximate the probability of an exact tie among $2m$ fair voters, and evaluate it at $m = 10^6$. Compare with the Module 02 rate.

### Problem 8. Estimating a proportion

**Tests:** the sample proportion, the effect of the correction, sample-size planning. **Time:** 14 min.

Let $X \sim B_{p,n}$, and let $\hat{p} = X/n$ be the sample proportion.

(a) Ignoring the continuity correction, show that $P(\lvert \hat{p} - p \rvert \le \varepsilon) \approx 2\Phi\big(\varepsilon\sqrt{n/(pq)}\big) - 1$.

(b) For $p = \frac{1}{2}$, $n = 400$, and $\varepsilon = 0.05$, approximate this with and without the correction. The exact value is $0.9598$.

(c) Using (a), find the smallest $n$ that gives $\pm 3\%$ accuracy with probability $0.95$, at $p = \frac{1}{2}$.

(d) Why is $p = \frac{1}{2}$ the safe choice when $p$ is unknown?

### Problem 9. Normal or Poisson?

**Tests:** choosing the right approximation. **Time:** 14 min.

(a) For $B_{0.01,\,1000}$, approximate $P(X = 10)$ with the Poisson and with the normal. You may use $e^{-10} 10^{10}/10! = 0.1251$, and $0.5/\sqrt{9.9} \approx 0.16$. The exact value is $0.1257$.

(b) For $B_{0.001,\,1000}$, approximate $P(X = 0)$ with the Poisson and with the normal. The exact value is $0.3677$.

(c) Explain the difference, and state a rule of thumb for using the normal.

---

## Challenge

### Problem 10. Beyond $k = np$

**Tests:** deriving the exponent from a ratio of consecutive terms. **Time:** 20 min.

Assume that $np$ is an integer, and consider $k = np + j$ with $j$ small compared to $n$.

(a) Show that

$$\frac{B_{p,n}(k + 1)}{B_{p,n}(k)} = \frac{(n - k)p}{(k + 1)q} = \frac{1 - \frac{j}{nq}}{1 + \frac{j + 1}{np}}.$$

(b) Using $\ln(1 + x) \approx x$ for small $x$, and ignoring terms of order $1/n$, show that the logarithm of this ratio is about $-\frac{j}{npq}$.

(c) Sum over $j = 0, \dots, J - 1$ to show that $B_{p,n}(np + J) \approx B_{p,n}(np)\, e^{-J^2/(2npq)}$. How does this complete the picture of the theorem?

(d) Test this at $n = 100$, $p = \frac{1}{2}$, $J = 10$. The exact ratio $\binom{100}{60}/\binom{100}{50}$ is $0.1362$.

### Problem 11. What the correction buys

**Tests:** quantifying the correction, a midpoint expansion. **Time:** 18 min.

Let $X \sim B_{1/2,\,100}$.

(a) Approximate $P(X \ge 60)$ and $P(X > 60)$ without the correction. Why is this clearly wrong, given $P(X = 60) \approx 0.0108$?

(b) Approximate both with the correction. The exact values are $0.0284$ and $0.0176$.

(c) For a smooth $f$, a Taylor expansion gives $\int_{k - 1/2}^{k + 1/2} f(x)\, dx \approx f(k) + \frac{1}{24} f''(k)$. For $f = N_{50,25}$ and $k = 60$, use $f''(k) = f(k)\left(\frac{(k - \mu)^2}{\sigma^4} - \frac{1}{\sigma^2}\right)$ to find the relative difference between the interval probability and the density at $k$. Compare it with $f(60) = 0.010798$ and $P(59.5 \le Y \le 60.5) = 0.010852$.

### Problem 12. A random walk

**Tests:** a transformation of the binomial, lattice spacing. **Time:** 20 min.

A walk takes $n$ independent steps of $\pm 1$, each with probability $\frac{1}{2}$. Let $S_n$ be its final position, and let $X$ count the $+1$ steps.

(a) Show that $S_n = 2X - n$. Find $E[S_n]$ and $V(S_n)$.

(b) For even $n$, approximate $P(S_n = 0)$, and evaluate it at $n = 100$.

(c) For $n = 100$, approximate $P(\lvert S_n \rvert \le 10)$ by converting to $X$ and using the correction. The exact value is $0.7287$. Why does the answer differ from the "68%" of one standard deviation?

(d) Ignoring the correction, find the $n$ for which $P(\lvert S_n \rvert \ge 100) \approx 0.05$.
