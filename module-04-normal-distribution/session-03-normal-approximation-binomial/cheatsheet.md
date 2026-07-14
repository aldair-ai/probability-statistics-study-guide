# Session 3 Cheatsheet: Normal Approximation of the Binomial

## De Moivre-Laplace theorem

For $X \sim B_{p,n}$ with $\mu = np$, $V = npq$, $\sigma = \sqrt{npq}$: for every $p \in (0, 1)$ and $c > 0$, as $n \to \infty$, for all $k$ with $\lvert k - np \rvert \le c\sqrt{npq}$,

$$B_{p,n}(k) \simeq N_{np,npq}(k) = \frac{1}{\sqrt{2\pi npq}}\, e^{-\frac{(k - np)^2}{2npq}}, \qquad \text{where } \simeq \text{ means the ratio tends to } 1.$$

## Three levels of approximation

For $X \sim B_{p,n}$ and $Y \sim N_{np,npq}$:

| Target | Approximation | Example $B_{0.5,\,100}$ ($\mu = 50$, $\sigma = 5$) |
|---|---|---|
| $P(X = k)$, density | $N_{np,npq}(k)$ | $P(X = 60)$: $0.010798$, exact $0.010844$ |
| $P(X = k)$, probability | $P(k - \frac{1}{2} \le Y \le k + \frac{1}{2})$ | $\Phi(2.1) - \Phi(1.9) \approx 0.0108$ |
| $P(k \le X \le \ell)$ | $P(k - \frac{1}{2} \le Y \le \ell + \frac{1}{2})$ | $P(42 \le X \le 53) \approx 0.7134$, exact $0.7136$ |

In Z form: $P\left(\frac{k - np - 1/2}{\sqrt{npq}} \le Z \le \frac{\ell - np + 1/2}{\sqrt{npq}}\right)$.

## Continuity correction

List the integers in the event, and then extend half a unit beyond each end.

| $X$ event | $Y$ event |
|---|---|
| $X = 20$ | $19.5 < Y < 20.5$ |
| $X \in \lbrace 17, 18 \rbrace$ | $16.5 < Y < 18.5$ |
| $X \ge 24$ | $Y > 23.5$ |
| $X > 26$, that is, $X \ge 27$ | $Y > 26.5$ |
| $X < 15$, that is, $X \le 14$ | $Y < 14.5$ |
| $11 < X \le 13$ | $11.5 < Y < 13.5$ |
| $19 < X < 21$, that is, $X = 20$ | $19.5 < Y < 20.5$ |
| $30 < X < 31$ | empty: probability 0 |

Example: $B_{1/3,\,90}$ is approximated by $N_{30,20}$.

## Why it works

- **Proof at $k = np$:** Stirling on $\binom{n}{pn} p^{pn} q^{qn}$, and all powers cancel, leaving $\frac{1}{\sqrt{2\pi pqn}}$, the normal's peak.
- **Exponent:** the ratio of consecutive terms gives $B_{p,n}(np + J) \approx B_{p,n}(np)\, e^{-J^2/(2npq)}$.
- **Density to probability:** on a unit interval a smooth $f$ is nearly linear, so $\int_{k - 1/2}^{k + 1/2} f \approx f(k) + \frac{1}{24} f''(k)$.
- **Intervals:** adjacent unit intervals join, so the sum collapses to one difference of $\Phi$ values.

## Useful formulas

- Peak: $P(X = np) \approx \frac{1}{\sqrt{2\pi npq}} \approx \frac{0.4}{\sigma}$. Fair coin: $\sqrt{2/(\pi n)}$. A tie among $2m$ voters: $\frac{1}{\sqrt{\pi m}}$.
- Proportion: $P(\lvert \hat{p} - p \rvert \le \varepsilon) \approx 2\Phi\big(\varepsilon\sqrt{n/(pq)}\big) - 1$.
- Sample size for $\pm\varepsilon$ with 95%, at worst-case $p = \frac{1}{2}$: $n \ge \left(\frac{1.96 \cdot 0.5}{\varepsilon}\right)^2$. For 3%: 1068.
- Random walk: $S_n = 2X - n$, with mean 0 and variance $n$.

## Which tool when

| Situation | Tool |
|---|---|
| Exact value, small $n$ | $\binom{n}{k} p^k q^{n-k}$ |
| One value, large $npq$ | the density formula, no table needed |
| An interval, large $npq$ | continuity correction, then Z table |
| $n$ large, $p$ small, $np$ moderate | Poisson |
| Rule of thumb for the normal | $npq \ge 10$ |
| Solving for $n$ | set the Z score to the target, then solve in $\sqrt{n}$ |

## Traps

1. **$P(Y = k) = 0$:** a binomial probability matches a density, or an interval, but never a point of $Y$.
2. **Correct the integers, not the symbols:** $X > 26$ gives $Y > 26.5$, while $X \ge 26$ gives $Y > 25.5$.
3. **$\sqrt{npq}$ in the Z score,** not $npq$.
4. **Ratio, near the mean:** far tails can have huge relative errors. For $p = \frac{1}{2}$ and $k = n$, the ratio tends to 0.
5. **Skew:** for $p$ far from $\frac{1}{2}$, the normal is off even after the correction (overbooking: 214 tickets versus the exact 215).
