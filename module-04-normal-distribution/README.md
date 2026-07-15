# Module 04: The Normal Distribution

Three sessions on the normal distribution, from its definition to its role in approximating the binomial (ECE 225A, Alon Orlitsky, UCSD). Each session folder holds a runnable `notes.ipynb`, 12 exam-style `exercises.md`, worked `solutions.md`, and a one-page `cheatsheet.md`. Below are the main formulas of each session, with a link to its cheatsheet.

| Session | Deck | Slides | Cheatsheet |
|---|---|---|---|
| [01 Normal distribution](session-01-normal-distribution/) | 7.Normal_distribution | 1-16 | [cheatsheet](session-01-normal-distribution/cheatsheet.md) |
| [02 Normal probabilities](session-02-normal-probabilities/) | 8.Normal_distribution-probabilities | 1-17 | [cheatsheet](session-02-normal-probabilities/cheatsheet.md) |
| [03 Normal approximation of the binomial](session-03-normal-approximation-binomial/) | 9.Normal_approximation_binomial_distribution | 1-17 | [cheatsheet](session-03-normal-approximation-binomial/cheatsheet.md) |

## 01 Normal distribution

- $N(\mu, \sigma^2)$: density $\frac{1}{\sqrt{2\pi\sigma^2}}\, e^{-(x - \mu)^2/(2\sigma^2)}$, symmetric around $\mu$, with peak $\frac{1}{\sqrt{2\pi\sigma^2}}$ and inflection points at $\mu \pm \sigma$.
- Closure: $aX + b \sim N(a\mu + b, a^2\sigma^2)$, so every normal is $X = \sigma Z + \mu$ with $Z \sim N(0, 1)$.
- Gaussian integral, by squaring and polar coordinates: $\int_{-\infty}^{\infty} e^{-z^2/2}\, dz = \sqrt{2\pi}$.
- $E[Z] = 0$ and $V(Z) = 1$, hence $E[X] = \mu$ and $V(X) = \sigma^2$.

## 02 Normal probabilities

- $\Phi(z) = P(Z \le z)$ has no closed form, so we use the Z table or a program. Symmetry gives $\Phi(-a) = 1 - \Phi(a)$.
- Standardizing: $Z = \frac{X - \mu}{\sigma}$, so $P(a \le X \le b) = \Phi\big(\frac{b - \mu}{\sigma}\big) - \Phi\big(\frac{a - \mu}{\sigma}\big)$.
- $P(\lvert X - \mu \rvert \le \alpha\sigma) = 2\Phi(\alpha) - 1$ depends only on $\alpha$, which gives the 68-95-99.7 rule.
- Tails fall quickly: a daily sample takes about 3 weeks to pass $2\sigma$, a year to pass $3\sigma$, and over a million years to pass $6\sigma$.

## 03 Normal approximation of the binomial

- De Moivre-Laplace: for $\lvert k - np \rvert \le c\sqrt{npq}$, $\;B_{p,n}(k) \simeq N_{np,npq}(k)$ as $n \to \infty$, meaning that the ratio tends to 1.
- At the center, by Stirling: $B_{p,n}(np) \simeq \frac{1}{\sqrt{2\pi npq}}$.
- Continuity correction, for $Y \sim N_{np,npq}$: $P(k \le X \le \ell) \approx P(k - \frac{1}{2} \le Y \le \ell + \frac{1}{2})$.
- To translate an event, list its integers, and then extend half a unit beyond each end.
