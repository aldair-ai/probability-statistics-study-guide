# Session 5 Cheatsheet: Distribution Families and Continuous Random Variables

## Master table ($q = 1 - p$)

| Distribution | Support | PMF / PDF | Mean | Variance | Typical use |
|---|---|---|---|---|---|
| Bernoulli $B_p$ | $\lbrace 0, 1 \rbrace$ | $p(1) = p$, $p(0) = q$ | $p$ | $pq$ | one yes/no trial; any indicator $\mathbf{1}_A$ |
| Binomial $B_{p,n}$ | $\lbrace 0, 1, \dots, n \rbrace$ | $\binom{n}{k} p^k q^{n-k}$ | $np$ | $npq$ | successes in $n$ independent trials with a common $p$ |
| Poisson $P_\lambda$ | $\lbrace 0, 1, 2, \dots \rbrace$ | $e^{-\lambda} \lambda^k / k!$ | $\lambda$ | $\lambda$ | rare events among many chances: $B_{p,n}$ with $n$ large, $p$ small, $np = \lambda$ |
| Geometric $G_p$ | $\lbrace 1, 2, \dots \rbrace$ | $q^{n-1} p$ | $1/p$ | $q/p^2$ | trials up to and including the first success |
| Uniform on $[a, b]$ (slide 88) | $[a, b]$ | $1/(b - a)$ | $(a + b)/2$ | $(b - a)^2/12$ | a point equally likely anywhere in an interval |

Notation: $B_{p,n}$ here is $\mathrm{Bin}(n, p)$ in many books.

## Family facts

- **Binomial:** $X = \sum_i X_i$ with independent $X_i \sim B_p$, so the mean follows by linearity and the variance by independence. $n - X \sim B_{q,n}$. The peak sits near $np$; $\frac{b(k)}{b(k-1)} = \frac{(n - k + 1)p}{kq}$. Example: $b_{1/3,5}(2) = 80/243$.
- **Poisson:** $\frac{P_\lambda(k)}{P_\lambda(k-1)} = \frac{\lambda}{k}$, so the peak is at $\lfloor \lambda \rfloor$, with a tie at $\lambda - 1, \lambda$ when $\lambda$ is an integer. $E[X(X-1)] = \lambda^2$. $b_{\lambda/n,\,n}(k) \to P_\lambda(k)$, and the total variation error shrinks like $1/n$.
- **Geometric:** $P(X > n) = q^n$, $F(n) = 1 - q^n$, $\sigma = \sqrt{q}/p \approx 1/p$ for small $p$. **Memoryless:** $P(X = n + m \mid X > n) = P(X = m)$. $\min(G_p, G_r) \sim G_{1 - (1-p)(1-r)}$ for independent variables.

## Discrete vs continuous (sum becomes integral, difference becomes derivative)

| | Discrete | Continuous |
|---|---|---|
| Normalization, $P(A)$ | $\sum_x p(x) = 1$, $\sum_{x \in A} p(x)$ | $\int f = 1$, $\int_A f(x)\, dx$ |
| CDF, and back | $F(x) = \sum_{u \le x} p(u)$; $p$ = jump of $F$ | $F(x) = \int_{-\infty}^{x} f$; $f = F'$ |
| $E[X]$, $E[g(X)]$ | $\sum x\, p(x)$, $\sum g(x)\, p(x)$ | $\int x f(x)\, dx$, $\int g(x) f(x)\, dx$ |

Both cases: $P(a < X \le b) = F(b) - F(a)$, $E[aX + b] = aE[X] + b$, $V = E[X^2] - \mu^2$, $V(aX + b) = a^2 V$, and **total expectation** $E[X] = \sum_i P(A_i)\, E[X \mid A_i]$. Continuous only: $f$ is probability per unit length (it can exceed 1), and $P(X = x) = 0$, so $<$ and $\le$ give the same probabilities. Example: $f = 3x^2$ on $(0, 1]$ has $F = x^3$, $E = 3/4$, and $V = 3/80$.

## Functions $Y = g(X)$

> **CDF method:** (1) find the support of $Y$; (2) write $F_Y(y) = P(g(X) \le y)$ as an event for $X$: $F_X(g^{-1}(y))$ if $g$ is increasing, $1 - F_X(g^{-1}(y))$ if it is decreasing, a sum of intervals if it is many-to-one; (3) $f_Y = F_Y'$.
>
> **PDF formula:** $f_Y(y) = \sum_{x \in g^{-1}(y)} f_X(x)/\lvert g'(x) \rvert$. Check that $\int f_Y = 1$.

Slide 87: $f_X = 3x^2$ on $(0, 1]$ and $Y = X^{3/2}$ give $F_Y = y^2$ and $f_Y = 2y$. Slide 88: $X$ uniform on $[-2, 2]$ and $Y = X^2$ give $F_Y = \sqrt{y}/2$ and $f_Y = 1/(4\sqrt{y})$ on $(0, 4]$. Sampling: $F^{-1}(U)$ has CDF $F$, and $F(X)$ is uniform on $(0, 1)$.

## Which tool when

| Situation | Tool |
|---|---|
| Successes in a fixed number of independent trials, same $p$ | binomial |
| Many chances, each rare; only the average rate is known | Poisson with $\lambda = np$ |
| Attempts until the first occurrence (good or bad) | geometric; work with the tail $q^n$ |
| "Already waited $n$; how much longer?" | memorylessness |
| Mean of a count, with or without dependence | indicators and linearity |
| Variance of a count | $npq$ if independent; otherwise add the covariances |
| Second moment when the PMF has a $k!$ | $E[X(X-1)]$ first |
| Mean by cases, or a first-step argument | law of total expectation |
| Only $E[g(X)]$ is needed | LOTUS (no need for $f_Y$) |
| Distribution of $g(X)$ | CDF method, then differentiate |

## Traps

1. **Binomial needs independence and a common $p$:** a card hand, a committee, or rainy days in a year is not binomial.
2. **Geometric convention:** here the support is $\lbrace 1, 2, \dots \rbrace$ with mean $1/p$. Counting only the failures gives mean $q/p$.
3. **A density is not a probability:** $f$ can exceed 1, and $P(X = x) = 0$.
4. **Change of variables:** don't drop $1/\lvert g'(x) \rvert$, its absolute value, or a preimage, and flip the inequality for a decreasing $g$.
5. **Gambler's fallacy:** past failures never make a geometric success "due".
