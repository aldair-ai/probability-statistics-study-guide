# Module 03: Uniform and Exponential Distributions

Two sessions on the first specific continuous families (ECE 225A, Alon Orlitsky, UCSD). Each session folder holds a runnable `notes.ipynb`, 12 exam-style `exercises.md`, worked `solutions.md`, and a one-page `cheatsheet.md`. Below are the main formulas of each session, with a link to its cheatsheet.

| Session | Deck | Slides | Cheatsheet |
|---|---|---|---|
| [01 Uniform distribution](session-01-uniform-distribution/) | 4.Uniform_distribution | 1-13 | [cheatsheet](session-01-uniform-distribution/cheatsheet.md) |
| [02 Exponential distribution and service times](session-02-exponential-distribution/) | 5.Exponential_distribution, 6.Exponential_service_times | 1-19, 1-10 | [cheatsheet](session-02-exponential-distribution/cheatsheet.md) |

Deck 6 is a short application of memorylessness with one main result, so it is the last part of Session 2 and not a session of its own.

## 01 Uniform distribution

- $U_{[a,b]}$: density $\frac{1}{b - a}$ on $[a, b]$, and CDF $\frac{x - a}{b - a}$ on $[a, b]$.
- Probabilities are ratios of lengths, after clipping an interval to the domain.
- Closure: $cX + d$ is uniform, with density reduced by $\lvert c \rvert$.
- Moments: $\mu = \frac{a + b}{2}$, $V = \frac{(b - a)^2}{12}$, and $\sigma = \frac{b - a}{2\sqrt{3}} \approx 0.29(b - a)$.

## 02 Exponential distribution and service times

- $E_\lambda$ is the limit of geometric waiting times: $(1 - \lambda/n)^{nx} \to e^{-\lambda x}$, with rate $\lambda = np$.
- Density $\lambda e^{-\lambda x}$, tail $P(X > x) = e^{-\lambda x}$, and $P(a \le X \le b) = e^{-\lambda a} - e^{-\lambda b}$.
- $\mu = \sigma = 1/\lambda$, $V = 1/\lambda^2$, and the median is $\ln 2 \cdot \mu \approx 0.7\mu$.
- Scaling: $aX \sim E_{\lambda/a}$ for $a > 0$.
- Memoryless: $P(X \ge a + b \mid X \ge a) = P(X \ge b)$, and $E[X \mid X \ge a] = E[X] + a$. It is the only such distribution on $\mathbb{R}^+$.
- Service times: if you are last in line at $s$ servers, $P(\text{you finish last})$ is 1 for constant service, but only $1/s$ for exponential service.
