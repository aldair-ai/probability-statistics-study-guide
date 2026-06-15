# Session 4 Cheatsheet: Variance, Covariance, Joint Distributions

## Variance and standard deviation

- **Variance:** $V(X) = E[(X - \mu)^2] = E[X^2] - \mu^2 \ge 0$, and $V(X) = 0$ iff $X$ is constant (with probability 1). **Std:** $\sigma_X = +\sqrt{V(X)}$, in the units of $X$.
- **Bernoulli** $B_p$: $V = pq$, $\sigma = \sqrt{pq}$, largest ($1/4$) at $p = 1/2$. Fair die: $V = 35/12$, $\sigma \approx 1.71$.

| Map | Mean | Variance | Std |
|---|---|---|---|
| $X + b$ | $\mu + b$ | $V(X)$ | $\sigma_X$ |
| $aX$ | $a\mu$ | $a^2\, V(X)$ | $\lvert a \rvert\, \sigma_X$ |
| $aX + b$ | $a\mu + b$ | $a^2\, V(X)$ | $\lvert a \rvert\, \sigma_X$ |

## Joint distributions

- **Joint PMF:** $p(x, y) = P(X = x, Y = y) \ge 0$ with $\sum_{x, y} p(x, y) = 1$. **Marginals:** $p_X(x) = \sum_y p(x, y)$ (row sums), $p_Y(y) = \sum_x p(x, y)$ (column sums). Marginals do not determine the joint.
- **LOTUS for pairs:** $E[g(X, Y)] = \sum_{x, y} g(x, y)\, p(x, y)$.
- **Uniform over a support $S$:** each point has probability $1/\lvert S \rvert$, and $P(X = x) = (\text{points of } S \text{ in row } x)/\lvert S \rvert$. Independent iff $S$ is a full rectangle $A \times B$. Slide 62: $\lbrace x \le y \rbrace$ has 15 points, $P(X = 3) = 2/15$.

## Covariance and correlation

| Fact | Formula |
|---|---|
| Covariance | $\mathrm{Cov}(X, Y) = E[(X - \mu_X)(Y - \mu_Y)] = E[XY] - \mu_X \mu_Y$ |
| Self, symmetry | $\mathrm{Cov}(X, X) = V(X)$, $\mathrm{Cov}(X, Y) = \mathrm{Cov}(Y, X)$ |
| Affine | $\mathrm{Cov}(aX + b,\, cY + d) = ac\, \mathrm{Cov}(X, Y)$ (shifts drop out) |
| Bilinear | $\mathrm{Cov}(X + Z, Y) = \mathrm{Cov}(X, Y) + \mathrm{Cov}(Z, Y)$: expand like a product |
| Sums | $V(X \pm Y) = V(X) + V(Y) \pm 2\,\mathrm{Cov}(X, Y)$; $V(\sum_i X_i) = \sum_i V(X_i) + 2\sum_{i<j} \mathrm{Cov}(X_i, X_j)$ |
| Correlation | $\rho_{X,Y} = \mathrm{Cov}(X, Y)/(\sigma_X \sigma_Y)$, unit free; $\rho_{aX+b,\, cY+d} = \mathrm{sign}(ac)\, \rho_{X,Y}$ |
| Bounds | $-1 \le \rho \le 1$, with $\rho = \pm 1$ iff $Y = aX + b$; proof: $V(Z_X \pm Z_Y) = 2(1 \pm \rho) \ge 0$ |

**Independent $\Rightarrow$ uncorrelated** ($E[XY] = E[X]\,E[Y]$, so $\mathrm{Cov} = 0$) $\Rightarrow$ variances add. The converse fails: $X$ uniform on $\lbrace -1, 0, 1 \rbrace$ and $Y = X^2$ give $\mathrm{Cov} = 0$, but $P(X = 0, Y = 0) = 1/3 \ne 1/9$.

**Slide 64 table** ($p(0,0) = 0.5$, $p(0,1) = 0$, $p(1,0) = 0.2$, $p(1,1) = 0.3$): $\mu_X = 0.5$, $\mu_Y = 0.3$, $E[XY] = 0.3$, $\mathrm{Cov} = 0.15$, $V(X + Y) = 0.76$, $\rho = \sqrt{3/7} \approx 0.655$.

## Which tool when

| Situation | Tool |
|---|---|
| Variance by hand | $E[X^2] - \mu^2$ with exact fractions; the definition if deviations are simple |
| 0/1 variable | $V = p(1 - p)$, since $I^2 = I$ |
| Shift, rescale, change units | affine rules: never recompute the distribution |
| Joint table | row and column sums for marginals; $E[XY]$ from the cells with $xy \ne 0$ |
| Uniform over a support | count points; sketch $S$ and $(\mu_X, \mu_Y)$ to predict the sign of Cov |
| Variance of a sum or a count | expand with bilinearity; for indicators, $\mathrm{Cov}(I_i, I_j) = P(\text{both}) - P(i)\,P(j)$ |
| Compare strengths of relationships | $\rho$, never the raw covariance |
| Prove dependence | one cell with $p(x, y) \ne p_X(x)\, p_Y(y)$, or $\mathrm{Cov} \ne 0$ |
| Prove an inequality | variance of a well-chosen combination is $\ge 0$ |

## Traps

1. **$V(aX + b) = a^2 V(X)$**, not $aV(X) + b$. So $V(-X) = V(X)$.
2. **Independent differences add:** $V(X - Y) = V(X) + V(Y)$, never $V(X) - V(Y)$.
3. **$\mathrm{Cov} = 0$ is not independence** ($Y = X^2$, symmetric supports such as a diamond).
4. **Stds do not add:** for uncorrelated variables, $\sigma_{X+Y} = \sqrt{\sigma_X^2 + \sigma_Y^2}$.
5. **Covariance depends on units:** $\lvert \rho \rvert$ measures how tightly points hug a line, not its slope.
