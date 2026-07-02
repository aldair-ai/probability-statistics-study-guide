# Session 2 Cheatsheet: The Exponential Distribution and Service Times

## $X \sim E_\lambda$, rate $\lambda > 0$

| Quantity | Formula | Example $\lambda = \frac{1}{2}$ (mean 2) |
|---|---|---|
| PDF, $x \ge 0$ | $\lambda e^{-\lambda x}$ | $\frac{1}{2} e^{-x/2}$ |
| Right CDF | $P(X > x) = e^{-\lambda x}$ | $P(X > 4) = e^{-2} \approx 0.135$ |
| CDF | $1 - e^{-\lambda x}$ | $F(4) \approx 0.865$ |
| Interval | $P(a \le X \le b) = e^{-\lambda a} - e^{-\lambda b}$ | $P(3 < X \le 4) \approx 0.088$ |
| Mean, std | $\mu = \sigma = 1/\lambda$ | 2 |
| Variance | $1/\lambda^2$ | 4 |
| Median | $\ln 2/\lambda = \ln 2 \cdot \mu \approx 0.7\mu$ | $\approx 1.386$ |
| Moments | $E[X^n] = n!/\lambda^n$ | $E[X^2] = 8$ |
| Quantile | $t_q = -\ln(1 - q)/\lambda$ | $t_{0.9} \approx 4.605$ |

Origin: $n$ trials per second with $p = \lambda/n$ give $P(X > x) = (1 - \lambda/n)^{nx} \to e^{-\lambda x}$. Only $\lambda$ remains.

## Properties

- **Scaling, $a > 0$:** $aX \sim E_{\lambda/a}$. Slower events have a smaller rate and a larger mean. No shifts, and no negative $a$.
- **Memoryless:** $P(X \ge a + b \mid X \ge a) = P(X \ge b)$, $\;P(X < a + b \mid X \ge a) = P(X < b)$, $\;f(X = a + b \mid X \ge a) = f(X = b)$.
- **Conditional means:** $E[X \mid X > a] = a + \frac{1}{\lambda}$ and $E[X \mid X \le a] = \frac{1}{\lambda} - \frac{a e^{-\lambda a}}{1 - e^{-\lambda a}}$.
- **Unique:** the only memoryless distribution on $\mathbb{R}^+$ (the geometric is its discrete analog).
- **Fixed facts:** $P(X > \mu) = e^{-1} \approx 0.368$ for every $\lambda$, and $P(X > 2t) = P(X > t)^2$.
- **Races, independent:** $\min(X, Y) \sim E_{\lambda + \mu}$ and $P(X < Y) = \frac{\lambda}{\lambda + \mu}$.
- **Python:** `scipy.stats.expon(scale=1/lam)`.

## Service times: $P(\text{you finish last})$

| Situation | Answer |
|---|---|
| 3 people, 2 servers, fair random order | $1/3$ |
| You are placed last, constant service | $1$ |
| You are placed last, exponential service | $1/2$, only $1/6$ more than fair |
| You are placed last, uniform service | $2/3$ |
| $s$ servers, you are last, exponential service | $1/s$ |
| 2 clerks with rates $\lambda_1, \lambda_2$, exponential service | $\frac{2\lambda_1\lambda_2}{(\lambda_1 + \lambda_2)^2} \le \frac{1}{2}$ |

Why: when you start, everyone in service has a fresh exponential remaining time, so all are symmetric.

## Which tool when

| Situation | Tool |
|---|---|
| Given the mean | $\lambda = 1/\text{mean}$ first |
| "Has already lasted $a$" | memorylessness: restart the clock |
| Changed units | scaling: multiply the mean, divide the rate |
| $X^2$, $X + c$, other maps | CDF method, from the tail |
| Several exponentials in service | stages: the first finish is $E_{\text{sum of rates}}$, then restart |
| Who finishes first | $P = \text{rate} / \text{sum of rates}$ |

## Traps

1. **Rate versus mean:** mean 2 means $\lambda = \frac{1}{2}$, not 2.
2. **Scaling direction:** $aX$ has rate $\lambda/a$. Slide 19's $E_{\alpha\lambda}$ is a typo.
3. **Total versus remaining:** $E[X \mid X > a] = a + \frac{1}{\lambda}$, and only the remaining part is $\frac{1}{\lambda}$.
4. **The mean is not typical:** about 63% of values fall below it.
5. **All models are wrong:** real cars age, so the exponential is an approximation. Some models are useful.
