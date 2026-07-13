# Session 3 Solutions: Normal Approximation of the Binomial

Worked solutions to [exercises.md](exercises.md), in the same numbering. Approximate answers come from the table excerpt, so they carry its 4-digit rounding, and exact binomial values are quoted for comparison. Try each problem first.

---

## Warm-up

### Problem 1. Choosing the normal

**(a)** $\mu = 400(0.2) = 80$, $\sigma^2 = 80(0.8) = 64$, and $\sigma = 8$. So use $N_{80,64}$.

**(b)** $\frac{1}{8\sqrt{2\pi}} \approx 0.04987$.

**(c)** $k = 88$ is one $\sigma$ above the mean, so the value is $0.04987\, e^{-1/2} \approx 0.03025$.

**(d)** The first is better: its error is about $0.1\%$, against about $2.5\%$ for the second. The approximation is best at $k = np$, and it gets worse away from the center. It also suffers here because $p \ne \frac{1}{2}$ makes the binomial slightly skewed, while the normal is symmetric.

**Key idea:** use the normal with the same mean and variance, and expect the best accuracy near the mean.

### Problem 2. Translating events

List the integers first, and then extend half a unit beyond each end. With $\sigma = 4$, $z = (y - 32)/4$.

| Event | $Y$ event | $Z$ event |
|---|---|---|
| (a) $X = 30$ | $29.5 < Y < 30.5$ | $-0.625 < Z < -0.375$ |
| (b) $X \in \lbrace 31, 32, 33 \rbrace$ | $30.5 < Y < 33.5$ | $-0.375 < Z < 0.375$ |
| (c) $X \ge 36$ | $Y > 35.5$ | $Z > 0.875$ |
| (d) $X > 36$, that is, $X \ge 37$ | $Y > 36.5$ | $Z > 1.125$ |
| (e) $X < 28$, that is, $X \le 27$ | $Y < 27.5$ | $Z < -1.125$ |
| (f) $28 < X \le 35$, that is, $X \in \lbrace 29, \dots, 35 \rbrace$ | $28.5 < Y < 35.5$ | $-0.875 < Z < 0.875$ |
| (g) $30 < X < 31$ | no integers, so the event is empty | probability 0 |

**Key idea:** the correction applies to the set of integers in the event, not to the inequality as written.

### Problem 3. True or false

**(a) False.** $P(Y = k) = 0$ for a continuous $Y$. A binomial probability approximates the normal *density* at $k$.

**(b) True.** This is the theorem at $k = np$, and it is the normal's peak height.

**(c) False.** The theorem covers only $k$ within $c$ standard deviations of $np$, and $k = n$ moves away from $np$ by many standard deviations. For $p = \frac{1}{2}$, the ratio is about $5 \times 10^{-8}$ at $n = 100$, and it keeps falling.

**(d) False.** Here $npq \approx 0.1$, and the distribution is concentrated on 0 and 1, with a strong skew. The Poisson is the suitable tool.

**(e) True.** Both events use the single cut at $k + \frac{1}{2}$, so the two approximations sum to exactly 1.

**(f) False.** They give $P(Y > 59.5)$ and $P(Y > 60.5)$, which differ, as they should.

**Key idea:** $\simeq$ is a ratio statement, valid for $k$ near the mean and for large $npq$.

### Problem 4. Fair coin tosses

**(a)** $\mu = 200$ and $\sigma = \sqrt{400 \cdot \frac{1}{4}} = 10$.

**(b)** $P(189.5 \le Y \le 210.5) = P(-1.05 \le Z \le 1.05) = 2(0.8531) - 1 = 0.7062$. The exact value is $0.7063$.

**(c)** $P(Y \ge 219.5) = P(Z \ge 1.95) = 1 - 0.9744 = 0.0256$. The exact value is $0.0255$.

**Key idea:** a sum of 21 terms becomes one table lookup, thanks to symmetry.

---

## Exam-level

### Problem 5. An election poll

**(a)** $\mu = 1300$, and $\sigma = \sqrt{2500(0.52)(0.48)} = \sqrt{624} \approx 24.98$.

**(b)** $P(Y \le 1250.5)$, with $z = \frac{1250.5 - 1300}{24.98} \approx -1.98$. So the probability is $1 - 0.9761 = 0.0239$. The exact value is $0.0238$.

**(c)** We need $\frac{n/2 - 0.52n}{\sqrt{0.2496\, n}} = -1.96$, that is, $\frac{0.02\, n}{0.4996\, \sqrt{n}} = 1.96$. So $\sqrt{n} = \frac{1.96(0.4996)}{0.02} \approx 48.96$, and $n \approx 2397$.

**Key idea:** the mean's lead grows like $n$, while the spread grows like $\sqrt{n}$, so a small lead needs a large sample.

### Problem 6. Overbooking

**(a)** $\mu = 198$, $\sigma^2 = 19.8$, and $\sigma \approx 4.450$. More than 200 means $X \ge 201$, so use $Y > 200.5$, with $z = \frac{2.5}{4.45} \approx 0.56$. The probability is $1 - 0.7123 = 0.2877$.

**(b)** We need $\frac{200.5 - 0.9n}{0.3\sqrt{n}} \ge 1.645$, that is, $0.9n + 0.4935\sqrt{n} - 200.5 \le 0$. Solving the quadratic in $\sqrt{n}$:

$$\sqrt{n} = \frac{-0.4935 + \sqrt{0.4935^2 + 4(0.9)(200.5)}}{2(0.9)} \approx 14.654, \qquad n \approx 214.7.$$

So the largest number of tickets is 214.

**(c)** In (a), the approximation is $0.2877$ against the exact $0.2943$. In (b), the exact probability at 215 tickets is $0.0496$, still below $0.05$, so the exact answer is 215, and not 214. The binomial with $p = 0.9$ is skewed to the left, so the symmetric normal is off by about 0.005 to 0.007 in the upper tail here. An answer that depends on one ticket should be checked exactly.

**Key idea:** the correction fixes the discreteness, but it cannot fix the skew when $p$ is far from $\frac{1}{2}$.

### Problem 7. Peak probabilities

**(a)** $\frac{1}{\sqrt{2\pi npq}} = \sqrt{\frac{2}{\pi n}}$ at $p = \frac{1}{2}$. So $n = 100$ gives $0.07979$ (exact $0.07959$), and $n = 10{,}000$ gives $0.007979$ (exact $0.007979$).

**(b)** $\sqrt{\frac{2}{\pi n}} < 0.01$ gives $n > \frac{20{,}000}{\pi} \approx 6366.2$, so the smallest even $n$ is 6368.

**(c)** $p = \frac{1}{2}$, because $pq \le \frac{1}{4}$ with equality there. The variance is largest at $p = \frac{1}{2}$, so the probability spreads over the most values, and the peak is lowest.

**(d)** With $n = 2m$ and $p = \frac{1}{2}$: $\frac{1}{\sqrt{2\pi \cdot 2m \cdot \frac{1}{4}}} = \frac{1}{\sqrt{\pi m}}$, which is exactly the rate from Module 02. At $m = 10^6$, it is about $5.642 \times 10^{-4}$.

**Key idea:** the peak is $\frac{1}{\sigma\sqrt{2\pi}} \approx \frac{0.4}{\sigma}$, for any binomial.

### Problem 8. Estimating a proportion

**(a)** $\lvert \hat{p} - p \rvert \le \varepsilon$ is equivalent to $\lvert X - np \rvert \le n\varepsilon$. Dividing by $\sqrt{npq}$, this becomes $\lvert Z \rvert \le \frac{n\varepsilon}{\sqrt{npq}} = \varepsilon\sqrt{\frac{n}{pq}}$, which has probability $2\Phi(\cdot) - 1$.

**(b)** Here $\sigma = 10$ and $n\varepsilon = 20$. Without the correction, $z = 2$, which gives $2(0.9772) - 1 = 0.9544$. With it, $180 \le X \le 220$ becomes $\lvert Y - 200 \rvert \le 20.5$, so $z = 2.05$, which gives $2(0.9798) - 1 = 0.9596$. The corrected value is much closer to the exact $0.9598$.

**(c)** We need $0.03\sqrt{n/(1/4)} \ge 1.96$, that is, $\sqrt{n} \ge \frac{1.96(0.5)}{0.03}$, so $n \ge 1067.1$. The smallest is $n = 1068$.

**(d)** Since $pq \le \frac{1}{4}$, the value $p = \frac{1}{2}$ gives the largest spread. A sample size that works at $p = \frac{1}{2}$ works for all $p$.

**Key idea:** the accuracy of an estimate depends on $n$ only through $\sqrt{n}$, so doubling the precision takes four times the data.

### Problem 9. Normal or Poisson?

**(a)** Poisson, with $\lambda = 10$: $0.1251$. Normal, with $\mu = 10$ and $\sigma^2 = 9.9$: $P(9.5 \le Y \le 10.5) = 2\Phi(0.16) - 1 = 2(0.5636) - 1 = 0.1272$. (Using $z = 0.1589$ without rounding gives $0.1263$.) Both are close to the exact $0.1257$.

**(b)** Poisson, with $\lambda = 1$: $e^{-1} \approx 0.3679$, which is excellent. Normal, with $\mu = 1$ and $\sigma \approx 1$: $P(-0.5 \le Y \le 0.5) = \Phi(-0.5) - \Phi(-1.5) = 0.9332 - 0.6915 = 0.2417$, which is far off the exact $0.3677$.

**(c)** In (b), $npq \approx 1$: the distribution is strongly skewed, and it is bounded on the left at 0, so it does not look like a bell. In (a), $npq \approx 10$, and the bell shape has begun to emerge. A common rule of thumb is to use the normal when $npq \ge 10$, and the Poisson when $n$ is large and $p$ is small with $np$ of moderate size.

**Key idea:** the Poisson handles rare events, and the normal needs a large variance.

---

## Challenge

### Problem 10. Beyond $k = np$

**(a)** The ratio of binomial terms is $\frac{n - k}{k + 1} \cdot \frac{p}{q}$. With $k = np + j$, we have $n - k = nq - j$ and $k + 1 = np + j + 1$. Dividing the top by $nq$ and the bottom by $np$:

$$\frac{(nq - j)p}{(np + j + 1)q} = \frac{1 - \frac{j}{nq}}{1 + \frac{j + 1}{np}}.$$

**(b)** The logarithm is approximately $-\frac{j}{nq} - \frac{j + 1}{np}$. Ignoring the $\frac{1}{np}$ term,

$$-j\left(\frac{1}{nq} + \frac{1}{np}\right) = -j \cdot \frac{p + q}{npq} = -\frac{j}{npq}.$$

**(c)** The logarithm of a product of ratios is a sum:

$$\ln\frac{B_{p,n}(np + J)}{B_{p,n}(np)} \approx -\sum_{j = 0}^{J - 1} \frac{j}{npq} = -\frac{J(J - 1)}{2npq} \approx -\frac{J^2}{2npq}.$$

So $B_{p,n}(np + J) \approx B_{p,n}(np)\, e^{-J^2/(2npq)}$. The proof in the notes gives the factor $\frac{1}{\sqrt{2\pi npq}}$ at the center, and this supplies the exponent. Together they form the normal density $N_{np,npq}(np + J)$, which is the theorem for $k$ near $np$.

**(d)** $e^{-100/(2 \cdot 25)} = e^{-2} \approx 0.1353$, against the exact $0.1362$.

**Key idea:** ratios of consecutive terms are simple, and summing their logarithms produces the Gaussian exponent.

### Problem 11. What the correction buys

**(a)** Both become $P(Y \ge 60) = P(Z \ge 2) = 1 - 0.9772 = 0.0228$. They cannot be equal, since the two events differ by $P(X = 60) \approx 0.0108$, which is about half of this value.

**(b)** With the correction, $P(X \ge 60) \approx P(Z \ge 1.9) = 1 - 0.9713 = 0.0287$, against the exact $0.0284$. And $P(X > 60) \approx P(Z \ge 2.1) = 1 - 0.9821 = 0.0179$, against the exact $0.0176$. Their difference, $0.0108$, matches $P(X = 60)$.

**(c)** With $(k - \mu)^2 = 100$ and $\sigma^2 = 25$:

$$\frac{f''(60)}{f(60)} = \frac{100}{625} - \frac{1}{25} = 0.16 - 0.04 = 0.12.$$

So the relative difference is $\frac{0.12}{24} = 0.005$, or $0.5\%$. This gives $0.010798(1.005) \approx 0.010852$, which matches the interval probability to all the digits shown. At $k = 60$ the density is convex, so the interval probability lies slightly above the density.

**Key idea:** the correction makes the approximation correct to first order, and the size of the remaining error is set by the curvature.

### Problem 12. A random walk

**(a)** With $X$ steps of $+1$ and $n - X$ steps of $-1$: $S_n = X - (n - X) = 2X - n$. So $E[S_n] = 2 \cdot \frac{n}{2} - n = 0$, and $V(S_n) = 4 \cdot \frac{n}{4} = n$.

**(b)** $S_n = 0$ exactly when $X = n/2$, so $P(S_n = 0) \approx \sqrt{\frac{2}{\pi n}}$. At $n = 100$: $0.07979$ (exact $0.07959$).

**(c)** $\lvert S_n \rvert \le 10$ means $45 \le X \le 55$, so use $P(44.5 \le Y \le 55.5) = P(\lvert Z \rvert \le 1.1) = 2(0.8643) - 1 = 0.7286$. It is above the $0.6827$ for one standard deviation, because the 11 integer values of $X$ cover a width of 11, and not 10. So the correction here is a tenth of a standard deviation on each side.

**(d)** $\frac{100}{\sqrt{n}} = 1.96$ gives $\sqrt{n} \approx 51.02$, so $n \approx 2603$.

**Key idea:** a walk is a rescaled binomial, so it inherits both the normal shape and the need for a continuity correction.
