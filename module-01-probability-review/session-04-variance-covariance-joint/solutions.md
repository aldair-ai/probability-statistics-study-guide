# Session 4 Solutions: Variance, Covariance, Joint Distributions

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given as an exact fraction and a decimal (rounded to 4 significant digits). Try each problem first.

---

## Warm-up

### Problem 1. A carnival wheel

**(a)** The mean is

$$\mu = 0 \cdot \frac{1}{2} + 2 \cdot \frac{1}{3} + 6 \cdot \frac{1}{6} = \frac{2}{3} + 1 = \frac{5}{3} \approx 1.667.$$

The deviations from the mean are $-5/3$, $1/3$, and $13/3$, with squares $25/9$, $1/9$, and $169/9$. Weighting by the probabilities,

$$V(X) = \frac{1}{2} \cdot \frac{25}{9} + \frac{1}{3} \cdot \frac{1}{9} + \frac{1}{6} \cdot \frac{169}{9} = \frac{75}{54} + \frac{2}{54} + \frac{169}{54} = \frac{246}{54} = \frac{41}{9} \approx 4.556.$$

**(b)** $E[X^2] = 0 \cdot \frac{1}{2} + 4 \cdot \frac{1}{3} + 36 \cdot \frac{1}{6} = \frac{4}{3} + 6 = \frac{22}{3}$, so

$$V(X) = \frac{22}{3} - \frac{25}{9} = \frac{66 - 25}{9} = \frac{41}{9}, \qquad \sigma_X = \frac{\sqrt{41}}{3} \approx 2.134.$$

**(c)** Both are affine functions of $X$, so no new distribution is needed.

| | Mean | Variance | Std |
|---|---|---|---|
| $G = X - 3$ | $5/3 - 3 = -4/3 \approx -1.333$ | $V(X) = 41/9 \approx 4.556$ | $\sqrt{41}/3 \approx 2.134$ |
| $H = 3 - X$ | $4/3 \approx 1.333$ | $(-1)^2\, V(X) = 41/9 \approx 4.556$ | $\lvert -1 \rvert\, \sigma_X \approx 2.134$ |

You and the operator face the same uncertainty, with opposite means.

**(d)** The new net gain is $Y = 2X - 4$:

$$E[Y] = 2 \cdot \frac{5}{3} - 4 = -\frac{2}{3} \approx -0.6667, \qquad V(Y) = 4 \cdot \frac{41}{9} = \frac{164}{9} \approx 18.22, \qquad \sigma_Y = \frac{2\sqrt{41}}{3} \approx 4.269.$$

On average the promotion is better for you ($-2/3 > -4/3$), but it is riskier: the standard deviation doubles.

**Key idea:** adding a constant moves only the mean; multiplying by $a$ multiplies the std by $\lvert a \rvert$ and the variance by $a^2$.

### Problem 2. The variance of an indicator

**(a)** $I$ only takes the values 0 and 1, and $0^2 = 0$, $1^2 = 1$, so $I^2 = I$. Hence $E[I^2] = E[I] = p$ and

$$V(I) = E[I^2] - (E[I])^2 = p - p^2 = p(1 - p).$$

**(b)** Completing the square, $p(1 - p) = \frac{1}{4} - \left(p - \frac{1}{2}\right)^2 \le \frac{1}{4}$, with equality exactly when $p = 1/2$.

**(c)** $p - p^2 = \frac{3}{16}$ means $16p^2 - 16p + 3 = 0$, that is $(4p - 1)(4p - 3) = 0$. So $p = 1/4 = 0.25$ or $p = 3/4 = 0.75$. The variance does not determine $p$, because swapping $p$ and $1 - p$ leaves it unchanged.

**(d)** $1 - I$ is the affine map $-I + 1$, so by the affine rule for covariance

$$\mathrm{Cov}(I, 1 - I) = (-1)\,\mathrm{Cov}(I, I) = -V(I) = -p(1 - p).$$

Also $V(1 - I) = V(I) = p(1 - p)$, so for $0 < p < 1$

$$\rho_{I,\,1 - I} = \frac{-p(1 - p)}{\sqrt{p(1 - p)}\,\sqrt{p(1 - p)}} = -1.$$

This is expected: $1 - I$ is an exact linear function of $I$ with negative slope, and $\rho = -1$ for exactly such pairs.

**Key idea:** a 0/1 variable satisfies $I^2 = I$, so its second moment equals its mean.

### Problem 3. True or false

**(a) True.** $V(X) = \sum_x (x - \mu)^2\, p(x)$ is a sum of nonnegative terms. If it is 0, then every term is 0, so $p(x) = 0$ for every $x \ne \mu$, that is, $P(X = \mu) = 1$.

**(b) False.** Variances of independent variables add even for a difference: $V(X - Y) = V(X) + V(-Y) + 2\,\mathrm{Cov}(X, -Y) = V(X) + V(Y) - 2\,\mathrm{Cov}(X, Y) = V(X) + V(Y)$. For two dice, $V(D_1 - D_2) = 35/6$, while $V(D_1) - V(D_2) = 0$. (The claimed formula would even give a negative variance whenever $V(Y) > V(X)$.)

**(c) False.** Let $X$ be uniform on $\lbrace -2, -1, 1, 2 \rbrace$ and $Y = \lvert X \rvert$. Then $E[X] = 0$ and $E[XY] = E[X \lvert X \rvert] = \frac{1}{4}(-4 - 1 + 1 + 4) = 0$, so $\mathrm{Cov}(X, Y) = 0$. But $P(X = 1, Y = 2) = 0$, while $P(X = 1)\,P(Y = 2) = \frac{1}{4} \cdot \frac{1}{2} = \frac{1}{8}$.

**(d) True.** $\mathrm{Cov}(X, Y) \le \sigma_X \sigma_Y$: when both stds are positive this is $\rho \le 1$, and when one is 0 that variable is constant and the covariance is 0. Hence

$$\sigma_{X+Y}^2 = \sigma_X^2 + \sigma_Y^2 + 2\,\mathrm{Cov}(X, Y) \le \sigma_X^2 + \sigma_Y^2 + 2\sigma_X \sigma_Y = (\sigma_X + \sigma_Y)^2,$$

and taking square roots gives the claim. Equality needs $\rho = 1$ (or a constant variable).

**(e) False.** Let $I, J$ be independent indicators with probability $1/2$ each, so $V(I) = V(J) = 1/4$ and $\mathrm{Cov}(I, J) = 0$.

- $U = W = I$: $\mathrm{Cov}(U, W) = V(I) = 1/4$ and $\rho_{U,W} = 1$.
- $X = 10I$, $Y = 10(I + J)$: $\mathrm{Cov}(X, Y) = 100\big(V(I) + \mathrm{Cov}(I, J)\big) = 25 > 1/4$. But $V(X) = 25$ and $V(Y) = 100 \cdot \frac{1}{2} = 50$, so $\rho_{X,Y} = \dfrac{25}{5 \cdot 5\sqrt{2}} = \dfrac{1}{\sqrt{2}} \approx 0.7071 < 1$.

A covariance grows with the scale of the variables; only $\rho$ is comparable across pairs.

**Key idea:** one counterexample settles a "false"; variances of independent pieces add, even in a difference.

### Problem 4. Uniform over a triangle

**(a)** $S = \lbrace (1,1), (1,2), (1,3), (2,1), (2,2), (3,1) \rbrace$, so $\lvert S \rvert = 6$ and each point has probability $1/6 \approx 0.1667$.

**(b)** Count points per row: $x = 1$ has 3, $x = 2$ has 2, $x = 3$ has 1. So

$$P(X = 1) = \frac{1}{2}, \qquad P(X = 2) = \frac{1}{3}, \qquad P(X = 3) = \frac{1}{6}.$$

$S$ is symmetric under swapping $x$ and $y$, so $Y$ has the same PMF.

**(c)** $\mu_X = \mu_Y = 1 \cdot \frac{1}{2} + 2 \cdot \frac{1}{3} + 3 \cdot \frac{1}{6} = \frac{5}{3}$. The triangle slopes downward: points with large $x$ have small $y$. Relative to $(5/3, 5/3)$, the points $(1,1)$ and $(2,2)$ give positive products of deviations, and the other four give negative ones, so predict a negative covariance.

$$E[XY] = \frac{1 + 2 + 3 + 2 + 4 + 3}{6} = \frac{15}{6} = \frac{5}{2}, \qquad \mathrm{Cov}(X, Y) = \frac{5}{2} - \frac{25}{9} = \frac{45 - 50}{18} = -\frac{5}{18} \approx -0.2778.$$

$E[X^2] = 1 \cdot \frac{1}{2} + 4 \cdot \frac{1}{3} + 9 \cdot \frac{1}{6} = \frac{10}{3}$, so $V(X) = V(Y) = \frac{10}{3} - \frac{25}{9} = \frac{5}{9}$ and

$$\rho_{X,Y} = \frac{-5/18}{5/9} = -\frac{1}{2} = -0.5.$$

**(d)** No. $p(3, 3) = 0$, but $P(X = 3)\,P(Y = 3) = \frac{1}{36} > 0$. (The nonzero covariance already proves dependence.)

**Key idea:** for a uniform distribution over a support, count points; the tilt of the support predicts the sign of the covariance.

---

## Exam-level

### Problem 5. Running partners

**(a)** Row sums give $p_X$ and column sums give $p_Y$:

| value | 0 | 1 | 2 |
|---|---|---|---|
| $p_X$ | $0.1 + 0.1 + 0 = 0.2$ | $0.1 + 0.2 + 0.1 = 0.4$ | $0 + 0.1 + 0.3 = 0.4$ |
| $p_Y$ | $0.1 + 0.1 + 0 = 0.2$ | $0.1 + 0.2 + 0.1 = 0.4$ | $0 + 0.1 + 0.3 = 0.4$ |

So $X$ and $Y$ have the same marginal PMF: $1/5, 2/5, 2/5$.

**(b)** $E[X] = 0.4 + 2(0.4) = 1.2 = 6/5$ and $E[X^2] = 0.4 + 4(0.4) = 2$, so

$$V(X) = 2 - 1.2^2 = 0.56 = \frac{14}{25}.$$

By (a), $E[Y] = 6/5 = 1.2$ and $V(Y) = 14/25 = 0.56$ as well.

**(c)** Only the cells with $x, y \ge 1$ contribute to $E[XY]$:

$$E[XY] = 1 \cdot 1 \cdot 0.2 + 1 \cdot 2 \cdot 0.1 + 2 \cdot 1 \cdot 0.1 + 2 \cdot 2 \cdot 0.3 = 0.2 + 0.2 + 0.2 + 1.2 = 1.8 = \frac{9}{5},$$

$$\mathrm{Cov}(X, Y) = 1.8 - 1.2 \cdot 1.2 = 0.36 = \frac{9}{25}.$$

**(d)**

$$\rho_{X,Y} = \frac{0.36}{\sqrt{0.56}\,\sqrt{0.56}} = \frac{0.36}{0.56} = \frac{9}{14} \approx 0.6429.$$

**(e)** From the variance-of-sums formula,

$$V(T) = 0.56 + 0.56 + 2(0.36) = 1.84 = \frac{46}{25}, \qquad V(D) = 0.56 + 0.56 - 2(0.36) = 0.40 = \frac{2}{5}.$$

Direct check: $D = 0$ on the diagonal ($0.1 + 0.2 + 0.3 = 0.6$), $D = 1$ at $(1,0)$ and $(2,1)$ ($0.2$), $D = -1$ at $(0,1)$ and $(1,2)$ ($0.2$), and $D = \pm 2$ has probability 0. So $E[D] = 0$, $E[D^2] = 0.2 + 0.2 = 0.4$, and $V(D) = 0.4$. The positive covariance makes the difference less variable than it would be for independent runners ($1.12$).

**(f)** No. $p(0, 2) = 0$, but $p_X(0)\,p_Y(2) = 0.2 \cdot 0.4 = 0.08$. (Again, $\mathrm{Cov} \ne 0$ already proves dependence.)

**Key idea:** marginals are row and column sums, and the shortcut $E[XY] - \mu_X \mu_Y$ only needs the cells where $xy \ne 0$.

### Problem 6. Sum and difference of two dice

**(a)** Expand with bilinearity:

$$\mathrm{Cov}(X + Y,\, X - Y) = \mathrm{Cov}(X, X) - \mathrm{Cov}(X, Y) + \mathrm{Cov}(Y, X) - \mathrm{Cov}(Y, Y) = V(X) - V(Y),$$

since the two middle terms cancel by symmetry.

**(b)** The dice are independent, each with variance $35/12$, so

$$V(S) = V(T) = \frac{35}{12} + \frac{35}{12} = \frac{35}{6} \approx 5.833, \qquad \mathrm{Cov}(S, T) = V(D_1) - V(D_2) = 0.$$

(For $T$, the covariance term is $-2\,\mathrm{Cov}(D_1, D_2) = 0$.)

**(c)** $S = 2$ happens only for $(1, 1)$, which forces $T = 0$. So $P(S = 2, T = 1) = 0$, while $P(S = 2)\,P(T = 1) = \frac{1}{36} \cdot \frac{5}{36} = \frac{5}{1296} \approx 0.003858 > 0$. ($T = 1$ for $(2,1), (3,2), (4,3), (5,4), (6,5)$.) Equivalently, $P(T = 0 \mid S = 2) = 1 \ne P(T = 0) = 1/6$.

**(d) False.** (b) and (c) give a counterexample: $V(D_1) = V(D_2)$, and $S, T$ are uncorrelated but dependent.

**Key idea:** $\mathrm{Cov}(X + Y, X - Y) = V(X) - V(Y)$; zero covariance never certifies independence.

### Problem 7. Weather and drink sales

**(a)** $Z_X = \frac{1}{\sigma_X} X - \frac{\mu_X}{\sigma_X}$ is affine with $a = 1/\sigma_X$, so

$$E[Z_X] = \frac{\mu_X - \mu_X}{\sigma_X} = 0, \qquad V(Z_X) = \frac{V(X)}{\sigma_X^2} = 1.$$

**(b)** Since both means are 0, $E[Z_X Z_Y] = \mathrm{Cov}(Z_X, Z_Y) + E[Z_X]\,E[Z_Y] = \mathrm{Cov}(Z_X, Z_Y)$. By the affine rule (the shifts drop out),

$$\mathrm{Cov}(Z_X, Z_Y) = \frac{1}{\sigma_X} \cdot \frac{1}{\sigma_Y}\,\mathrm{Cov}(X, Y) = \rho_{X,Y}.$$

**(c)**

$$\rho_{C,S} = \frac{150}{4 \cdot 50} = \frac{3}{4} = 0.75.$$

**(d)**

- $E[F] = 1.8 \cdot 22 + 32 = 71.6 = 358/5$ and $\sigma_F = 1.8 \cdot 4 = 7.2 = 36/5$.
- $\sigma_D = 50/12 = 25/6 \approx 4.167$.
- $\mathrm{Cov}(F, D) = 1.8 \cdot \frac{1}{12} \cdot 150 = 22.5 = 45/2$.
- $\rho_{F,D} = \dfrac{22.5}{7.2 \cdot 25/6} = \dfrac{22.5}{30} = \dfrac{3}{4} = 0.75$, unchanged, since both scale factors are positive.

**(e)**

- $E[H] = 400 - 0.4 \cdot 300 = 280$ and $\sigma_H = 0.4 \cdot 50 = 20$.
- $\mathrm{Cov}(C, H) = -0.4 \cdot 150 = -60$.
- $\rho_{C,H} = \dfrac{-60}{4 \cdot 20} = -\dfrac{3}{4} = -0.75$, the same size with the sign flipped.

**Key idea:** covariance picks up both scale factors, while correlation keeps only their signs.

### Problem 8. The smaller and the larger of two dice

**(a)** $M \ge k$ means both dice show at least $k$, so $P(M \ge k) = \left(\frac{7 - k}{6}\right)^2$. Then

$$P(M = k) = P(M \ge k) - P(M \ge k + 1) = \frac{(7 - k)^2 - (6 - k)^2}{36} = \frac{13 - 2k}{36},$$

that is, $11, 9, 7, 5, 3, 1$ out of 36 for $k = 1, \dots, 6$. So

$$E[M] = \frac{11 + 18 + 21 + 20 + 15 + 6}{36} = \frac{91}{36} \approx 2.528.$$

(The tail-sum formula from Session 3 agrees: $\sum_k P(M \ge k) = \frac{36 + 25 + 16 + 9 + 4 + 1}{36} = \frac{91}{36}$.)

**(b)** $\lbrace M, L \rbrace = \lbrace D_1, D_2 \rbrace$ as a pair of numbers, so $M + L = D_1 + D_2$ and

$$E[L] = 7 - \frac{91}{36} = \frac{161}{36} \approx 4.472.$$

**(c)** For the same reason, $ML = D_1 D_2$. The dice are independent, so $E[ML] = E[D_1]\,E[D_2] = \frac{49}{4} = 12.25$, and

$$\mathrm{Cov}(M, L) = \frac{49}{4} - \frac{91}{36} \cdot \frac{161}{36} = \frac{15876 - 14651}{1296} = \frac{1225}{1296} \approx 0.9452.$$

**(d)** $E[M^2] = \frac{11 \cdot 1 + 9 \cdot 4 + 7 \cdot 9 + 5 \cdot 16 + 3 \cdot 25 + 1 \cdot 36}{36} = \frac{301}{36}$, so

$$V(M) = \frac{301}{36} - \left(\frac{91}{36}\right)^2 = \frac{10836 - 8281}{1296} = \frac{2555}{1296} \approx 1.971.$$

$D_1' = 7 - D_1$ and $D_2' = 7 - D_2$ are again two independent fair dice, and $L = \max(D_1, D_2) = 7 - \min(D_1', D_2')$. So $L$ has the same distribution as $7 - M$, and $V(L) = V(7 - M) = V(M)$. Therefore

$$\rho_{M,L} = \frac{1225/1296}{2555/1296} = \frac{1225}{2555} = \frac{35}{73} \approx 0.4795.$$

**(e)** $V(M) + V(L) + 2\,\mathrm{Cov}(M, L) = \frac{2 \cdot 2555 + 2 \cdot 1225}{1296} = \frac{7560}{1296} = \frac{35}{6}$, which matches $V(D_1 + D_2) = 2 \cdot \frac{35}{12} = \frac{35}{6}$.

**Key idea:** symmetric functions of the pair (sum, product) are the same for $(M, L)$ and $(D_1, D_2)$, which avoids the joint PMF of $(M, L)$.

### Problem 9. Combining two sensors

**(a)** $\theta$ is a constant, so $V\big((R_1 + R_2)/2\big) = \frac{1}{4} V(\varepsilon_1 + \varepsilon_2)$, and $\mathrm{Cov}(\varepsilon_1, \varepsilon_2) = \rho\,\sigma_1\sigma_2 = 2\rho$:

$$V\left(\frac{R_1 + R_2}{2}\right) = \frac{1 + 4 + 2 \cdot 2\rho}{4} = \frac{5 + 4\rho}{4}.$$

This is below $V(R_1) = 1$ exactly when $5 + 4\rho < 4$, that is, $\rho < -1/4$. With independent errors the plain average has variance $5/4 = 1.25$: averaging with a noisier sensor hurts unless the errors are negatively correlated enough to cancel.

**(b)** $E[W_t] = t\theta + (1 - t)\theta + t\,E[\varepsilon_1] + (1 - t)\,E[\varepsilon_2] = \theta$. Also $W_t - \theta = t\varepsilon_1 + (1 - t)\varepsilon_2$, and expanding its variance with bilinearity gives

$$V(W_t) = t^2 \sigma_1^2 + (1 - t)^2 \sigma_2^2 + 2t(1 - t)\,\mathrm{Cov}(\varepsilon_1, \varepsilon_2),$$

with $\mathrm{Cov}(\varepsilon_1, \varepsilon_2) = \rho\,\sigma_1 \sigma_2$.

**(c)** With $\rho = 0$, $V(W_t) = t^2 + 4(1 - t)^2$. Setting the derivative $2t - 8(1 - t) = 10t - 8$ to 0 gives $t = 4/5$, and

$$V(W_{4/5}) = \frac{16}{25} + 4 \cdot \frac{1}{25} = \frac{4}{5} = 0.8.$$

The best weights, $4 : 1$, are inversely proportional to the variances, and the result beats both sensors ($1$ and $4$).

**(d)** With $\rho = 1/2$, $\mathrm{Cov}(\varepsilon_1, \varepsilon_2) = 1$ and

$$V(W_t) = t^2 + 4(1 - t)^2 + 2t(1 - t) = 3t^2 - 6t + 4.$$

The derivative $6t - 6$ vanishes at $t = 1$, where $V = 3 - 6 + 4 = 1$. So $W_1 = R_1$: the second sensor adds nothing. (In general $t^* = \dfrac{\sigma_2^2 - \rho\sigma_1\sigma_2}{\sigma_1^2 + \sigma_2^2 - 2\rho\sigma_1\sigma_2}$. For $\rho > \sigma_1/\sigma_2 = 1/2$ it exceeds 1, putting a negative weight on sensor 2 to cancel the shared error.)

**Key idea:** the variance of a linear combination involves every covariance; minimizing it is minimizing a quadratic in the weight.

---

## Challenge

### Problem 10. Why $\lvert \rho \rvert \le 1$

**(a)** $V(Z_X) = V(Z_Y) = 1$ and $\mathrm{Cov}(Z_X, Z_Y) = \rho$, so by the variance-of-sums formula

$$V(Z_X \pm Z_Y) = 1 + 1 \pm 2\rho = 2(1 \pm \rho).$$

Variances are nonnegative, so $1 + \rho \ge 0$ and $1 - \rho \ge 0$, that is, $-1 \le \rho \le 1$.

**(b)** If $\rho = 1$, then $V(Z_X - Z_Y) = 0$, so by Problem 3(a) $Z_X - Z_Y$ equals its mean, 0, with probability 1. Then $\frac{Y - \mu_Y}{\sigma_Y} = \frac{X - \mu_X}{\sigma_X}$, that is,

$$Y = \frac{\sigma_Y}{\sigma_X} X + \left(\mu_Y - \frac{\sigma_Y}{\sigma_X}\mu_X\right), \qquad a = \frac{\sigma_Y}{\sigma_X} > 0.$$

Conversely, if $Y = aX + b$ with $a > 0$, then $\mathrm{Cov}(X, Y) = a\,V(X)$ and $\sigma_Y = a\sigma_X$, so $\rho = \frac{a\sigma_X^2}{\sigma_X \cdot a\sigma_X} = 1$.

For $\rho = -1$: $\rho = -1$ if and only if $Y = aX + b$ with $a < 0$, and then $a = -\sigma_Y/\sigma_X$. The proof is the same, using $V(Z_X + Z_Y) = 0$.

**(c)** By linearity,

$$q(t) = E[U^2] - 2t\,E[UW] + t^2 E[W^2].$$

This quadratic opens upward, so its minimum is at $t_0 = E[UW]/E[W^2]$, where

$$0 \le q(t_0) = E[U^2] - \frac{\big(E[UW]\big)^2}{E[W^2]}.$$

Multiplying by $E[W^2] > 0$ gives $\big(E[UW]\big)^2 \le E[U^2]\,E[W^2]$. With $U = X - \mu_X$ and $W = Y - \mu_Y$ we have $E[UW] = \mathrm{Cov}(X, Y)$, $E[U^2] = \sigma_X^2$, and $E[W^2] = \sigma_Y^2$, so $\mathrm{Cov}(X, Y)^2 \le \sigma_X^2 \sigma_Y^2$, that is, $\lvert \mathrm{Cov}(X, Y) \rvert \le \sigma_X \sigma_Y$.

**(d)** By (b) with $\rho = -1$, $Z_Y = -Z_X$:

$$Y = \mu_Y - \frac{\sigma_Y}{\sigma_X}(X - \mu_X) = -\frac{3}{2}(X - 1) = -\frac{3}{2} X + \frac{3}{2}.$$

So $a = -3/2 = -1.5$ and $b = 3/2 = 1.5$. Check: $E[Y] = -\frac{3}{2} + \frac{3}{2} = 0$ and $\sigma_Y = \frac{3}{2} \cdot 2 = 3$.

**Key idea:** variances are nonnegative; apply that to the sum and the difference of the standardized variables.

### Problem 11. Matching hats

**(a)** Guest $i$ gets their own hat in $(n - 1)!$ of the $n!$ assignments, so $E[I_i] = P(I_i = 1) = \frac{1}{n}$. By linearity, $E[X] = n \cdot \frac{1}{n} = 1$, for every $n$.

**(b)** Guests $i$ and $j$ both get their own hats in $(n - 2)!$ assignments, so $P(I_i = 1, I_j = 1) = \frac{(n - 2)!}{n!} = \frac{1}{n(n - 1)}$. Since $I_i I_j$ is the indicator of that event,

$$\mathrm{Cov}(I_i, I_j) = \frac{1}{n(n - 1)} - \frac{1}{n^2} = \frac{n - (n - 1)}{n^2 (n - 1)} = \frac{1}{n^2(n - 1)} > 0.$$

The sign makes sense: once guest $i$ has their own hat, guest $j$'s hat is one of the $n - 1$ hats left for the other $n - 1$ guests, so guest $j$'s chance rises from $1/n$ to $1/(n - 1)$.

**(c)** Each $V(I_i) = \frac{1}{n}\left(1 - \frac{1}{n}\right)$, and there are $\binom{n}{2}$ pairs, so

$$V(X) = n \cdot \frac{1}{n}\left(1 - \frac{1}{n}\right) + 2\binom{n}{2} \cdot \frac{1}{n^2(n - 1)} = \frac{n - 1}{n} + \frac{n(n - 1)}{n^2(n - 1)} = \frac{n - 1}{n} + \frac{1}{n} = 1.$$

**(d)** Write an assignment as the hats received by guests 1, 2, 3:

| Assignment | 123 | 132 | 213 | 321 | 231 | 312 |
|---|---|---|---|---|---|---|
| $X$ | 3 | 1 | 1 | 1 | 0 | 0 |

So $P(X = 0) = 1/3$, $P(X = 1) = 1/2$, $P(X = 3) = 1/6$. Then $E[X] = \frac{3 + 3}{6} = 1$, $E[X^2] = \frac{3 + 9}{6} = 2$, and $V(X) = 2 - 1 = 1$.

**Key idea:** the variance of a count is the sum of the indicator variances plus twice the sum of all pairwise covariances.

### Problem 12. How negative can correlations be?

**(a)** Each pair has $\mathrm{Cov}(X_i, X_j) = \rho\,\sigma \cdot \sigma = \rho\sigma^2$, and there are $\binom{n}{2}$ pairs, so

$$V\Big(\sum_i X_i\Big) = \sum_i V(X_i) + 2\sum_{i < j} \mathrm{Cov}(X_i, X_j) = n\sigma^2 + n(n - 1)\rho\sigma^2 = n\sigma^2\big(1 + (n - 1)\rho\big).$$

A variance is nonnegative and $n\sigma^2 > 0$, so $1 + (n - 1)\rho \ge 0$, that is, $\rho \ge -\dfrac{1}{n - 1}$.

**(b)** $I_i \sim B_{1/n}$, so $V(I_i) = \frac{1}{n}\left(1 - \frac{1}{n}\right) = \frac{n - 1}{n^2}$. Only one ball is drawn, so $I_i I_j = 0$ for $i \ne j$ and

$$\mathrm{Cov}(I_i, I_j) = 0 - \frac{1}{n} \cdot \frac{1}{n} = -\frac{1}{n^2}, \qquad \rho_{I_i, I_j} = \frac{-1/n^2}{(n - 1)/n^2} = -\frac{1}{n - 1}.$$

This matches (a): $I_1 + \cdots + I_n = 1$ is a constant, so its variance is 0 and the bound holds with equality.

**(c)**

1. **False.** For $n = 3$, part (a) requires $\rho \ge -1/2$, and $-0.6 < -0.5$. Directly: $V(X_1 + X_2 + X_3) = 3\sigma^2\big(1 + 2(-0.6)\big) = -0.6\,\sigma^2 < 0$, which is impossible.
2. **True.** Part (b) with $n = 3$ gives three indicators whose pairwise correlations are exactly $-1/2$.

**Key idea:** a variance cannot be negative, and applied to a sum this constrains all the correlations together, not just each pair.
