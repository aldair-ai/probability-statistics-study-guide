# Session 2 Cheatsheet: Normal Distribution Probabilities

## The standard normal CDF

$$\Phi(z) = P(Z \le z) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{z} e^{-u^2/2}\, du \qquad \text{(no closed form: use a table or a program)}$$

| $z$ | 0 | 0.5 | 1 | 1.28 | 1.5 | 1.645 | 1.96 | 2 | 2.33 | 2.5 | 3 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $\Phi(z)$ | .5000 | .6915 | .8413 | .8997 | .9332 | .9500 | .9750 | .9772 | .9901 | .9938 | .9987 |

Reading the table: a row for the first decimal, and a column for the second, so $\Phi(1.82)$ is row 1.8, column .02.

## $Z$ probabilities ($a, b \ge 0$)

| Event | Probability | Example |
|---|---|---|
| $Z \le a$ | $\Phi(a)$ | $P(Z \le 1) \approx 0.84$ |
| $Z \ge a$ | $1 - \Phi(a)$ | $P(Z \ge 1) \approx 0.16$ |
| $a \le Z \le b$ | $\Phi(b) - \Phi(a)$ | $P(1 \le Z \le 2) \approx 0.1359$ |
| $Z \le -a$ | $\Phi(-a) = 1 - \Phi(a)$ | $P(Z \le -1) \approx 0.16$ |
| $Z \ge -a$ | $\Phi(a)$ | $P(Z \ge -1) \approx 0.84$ |
| $-a \le Z \le b$ | $\Phi(a) + \Phi(b) - 1$ | $P(-2 \le Z \le 1) \approx 0.8185$ |
| $\lvert Z \rvert \le a$ | $2\Phi(a) - 1$ | $P(\lvert Z \rvert \le 1.96) = 0.95$ |
| $\lvert Z \rvert > a$ | $2(1 - \Phi(a))$ | $P(\lvert Z \rvert > 2) \approx 0.0456$ |

## General normal

$$Z = \frac{X - \mu}{\sigma} \sim N(0, 1), \qquad P(a \le X \le b) = \Phi\left(\frac{b - \mu}{\sigma}\right) - \Phi\left(\frac{a - \mu}{\sigma}\right), \qquad x = \mu + z\sigma.$$

Example: $X \sim N(15, 4)$, $P(11 \le X \le 17) = P(-2 \le Z \le 1) \approx 0.8185$.

## Deviation from the mean

$P(\lvert X - \mu \rvert \le \alpha\sigma) = 2\Phi(\alpha) - 1$ depends only on $\alpha$, for every normal. For other distributions it varies widely: at $\alpha = 1$, $P(\lvert X - \mu \rvert \ge \sigma) = 1$ for two spikes, and $\frac{1}{n^2}$ for three spikes.

| $\alpha$ | Within | Outside | Daily sample: first time outside ($1/p$) |
|---|---|---|---|
| 1 | 68.27% | 31.73% | 3 days |
| 2 | 95.45% | 4.55% | 3 weeks |
| 3 | 99.73% | 0.27% | 1 year |
| 4 | 99.994% | $6.3 \times 10^{-5}$ | 43 years |
| 5 | 99.99994% | $5.7 \times 10^{-7}$ | 4800 years |
| 6 | 99.9999998% | $2.0 \times 10^{-9}$ | 1.4 million years |

## Quick bounds

- One $\sigma$ by rectangles: $\sqrt{2/(\pi e)} \approx 0.48 \le P(\lvert Z \rvert \le 1) \le \sqrt{2/\pi} \approx 0.80$. The house gives $0.64$, a lower bound by concavity. True: $0.6827$.
- $\phi$ is concave on $\lvert z \rvert < 1$ and convex outside. Chords lie below it inside, and above it outside.
- Tail bound: $P(Z > a) \le \phi(a)/a$.
- Any distribution: $P(\lvert X - \mu \rvert \ge \alpha\sigma) \le 1/\alpha^2$, with equality for three spikes.

## Which tool when

| Situation | Tool |
|---|---|
| A normal probability | standardize, then the table |
| A cutoff or percentile | table in reverse, then $x = \mu + z\sigma$ |
| Unknown $\mu$ or $\sigma$ | turn each probability into a linear equation in $z$ |
| Within $\alpha\sigma$ of the mean | $2\Phi(\alpha) - 1$ |
| Repeated independent draws | binomial for counts, geometric for waits, $\Phi^n$ for a maximum |
| Very far tails | a program, not the table |

## Traps

1. **Divide by $\sigma$, not $\sigma^2$:** for $N(15, 4)$, use 2.
2. **The table gives the left area:** $P(Z \ge a) = 1 - \Phi(a)$.
3. **$\Phi(-a) = 1 - \Phi(a)$,** never $-\Phi(a)$.
4. **One tail or two:** $P(Z > 3) \approx 0.13\%$, while $P(\lvert Z \rvert > 3) \approx 0.27\%$.
5. **The rule is for normals only:** a uniform has $0.577$ within one $\sigma$.
