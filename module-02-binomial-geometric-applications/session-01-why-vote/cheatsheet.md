# Session 1 Cheatsheet: Why Vote, the Central Binomial Term and Stirling's Approximation

## Core formulas ($a_n = \binom{2n}{n}/4^n$)

| Quantity | Formula | Example |
|---|---|---|
| You decide among $2n + 1$ fair voters | $a_n = b_{1/2,\,2n}(n)$ | $n = 2$: $3/8$; $n = 10$: $\approx 0.176$ |
| Draw among $2n$ fair voters | $a_n$ (same number) | 23,216 votes: $\approx 0.0052$ |
| Walk at 0 after $2n$ steps | $a_n$ (0 impossible at odd times) | 20 steps: $\approx 0.176$ |
| Stirling | $n! \approx \sqrt{2\pi n}\,(n/e)^n$ (ratio $\to 1$) | $10!$: 0.83% low |
| Central term rate | $a_n \approx 1/\sqrt{\pi n}$ | 6,401 voters: $\approx 1/100$ |
| In terms of $N$ flips | $b_{1/2,\,N}(N/2) \approx \sqrt{2/(\pi N)}$ | $N = 100$: $\approx 0.0798$ |
| Biased voters | $\binom{2n}{n}(pq)^n \approx (4pq)^n/\sqrt{\pi n}$ | $p = 0.51$, $n = 3200$: $2.8 \times 10^{-3}$ |

## Stirling cancellation

$$\frac{(2n)!}{(n!)^2\, 2^{2n}} \approx \frac{\sqrt{4\pi n}\,(2n/e)^{2n}}{2\pi n\,(n/e)^{2n}\, 2^{2n}} = \frac{2\sqrt{\pi n}}{2\pi n} = \frac{1}{\sqrt{\pi n}}.$$

## Useful facts about $a_n$

- Recursion: $\dfrac{a_{n+1}}{a_n} = \dfrac{2n+1}{2n+2}$, and product form $a_n = \prod_{i=1}^{n} \frac{2i-1}{2i}$.
- Elementary bounds: $\dfrac{1}{2\sqrt{n}} \le a_n \le \dfrac{1}{\sqrt{2n+1}}$.
- Sharp bounds: $\dfrac{e^{-1/(8n)}}{\sqrt{\pi n}} \le a_n < \dfrac{1}{\sqrt{\pi n}}$, so the relative error is about $1/(8n)$ and the approximation is always high.
- Sum: $\sum_{n=0}^{N} a_n = (2N+1) a_N$, so a walk makes about $2\sqrt{N/\pi} - 1$ returns in $2N$ steps.

## Intuition for the rate

$\mu = n/2$ and $\sigma = \sqrt{npq} = \sqrt{n}/2$, so the likely values fill a range of width about $2\sigma = \sqrt{n}$. Each of those values gets about $1/\sqrt{n}$, so **the peak probability is about $1/\sigma$**. Near the center, $P(X = n + k)/P(X = n) \approx e^{-k^2/n}$ for $X \sim B_{1/2,\,2n}$.

## Which tool when

| Situation | Tool |
|---|---|
| "Does one vote change the result?" | condition on the others: even split |
| Exact small $n$ | $\binom{2n}{n}/4^n$, or the recursion from $a_0 = 1$ |
| Large $n$, $p = 1/2$ | $1/\sqrt{\pi n}$ |
| Large $n$, $p \ne 1/2$ | $(4pq)^n/\sqrt{\pi n}$ (exponentially small) |
| Ratio of factorials, large arguments | Stirling, then cancel powers first |
| A quick order of magnitude | $1/\sigma$ |
| Proof of a rate without asymptotics | telescoping product bounds |
| Multi-level vote | multiply the tie probability of each level |

## Traps

1. **$n$ versus $N$:** with $N = 2n + 1$ voters, $n \approx N/2$. For 6,401 voters, use $n = 3200$.
2. **$1/N$ is not the answer:** the rate is $1/\sqrt{N}$, because influence depends on the spread and not on the headcount.
3. **Equal likelihood matters:** a fixed bias gives exponential decay.
4. **Stirling is a ratio statement:** the absolute error grows, even as the relative error tends to 0.
5. **Random walk parity:** $P(S_m = 0) = 0$ for odd $m$.
