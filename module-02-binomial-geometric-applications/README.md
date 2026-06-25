# Module 02: Binomial and Geometric Applications

Two sessions that put the binomial and geometric distributions from Module 01 to work (ECE 225A, Alon Orlitsky, UCSD). Each session folder holds a runnable `notes.ipynb`, 12 exam-style `exercises.md`, worked `solutions.md`, and a one-page `cheatsheet.md`. Below are the main formulas of each session, with a link to its cheatsheet.

| Session | Deck | Slides | Cheatsheet |
|---|---|---|---|
| [01 Why vote](session-01-why-vote/) | 2.Why_vote | 1-12 | [cheatsheet](session-01-why-vote/cheatsheet.md) |
| [02 Geometric examples](session-02-geometric-examples/) | 3.Geometric_examples | 1-9 | [cheatsheet](session-02-geometric-examples/cheatsheet.md) |

## 01 Why vote

- With $2n + 1$ fair voters, your vote decides the result with probability $a_n = \binom{2n}{n}/4^n$, the central binomial term.
- Stirling: $n! \approx \sqrt{2\pi n}\,(n/e)^n$, with the ratio tending to 1.
- Rate: $a_n \approx 1/\sqrt{\pi n}$, so influence falls like $1/\sqrt{N}$ in the number of voters, and not like $1/N$. The peak probability is about $1/\sigma$.
- With biased voters: $\binom{2n}{n}(pq)^n \approx (4pq)^n/\sqrt{\pi n}$, which is exponentially small.

## 02 Geometric examples

- For $X \sim G_p$: $P(X \text{ odd}) = \frac{1}{2 - p}$, so the first player wins an alternating game with that probability.
- $P(X \text{ even}) = q\, P(X \text{ odd})$ avoids an infinite sum.
- With $k$ players, the first one wins with probability $\frac{p}{1 - q^k}$.
- Rocket risk: the probability of clean tests followed by a failure on flight $n$ is $q^{n-1}p$. Its maximum over $p$ is at $p = 1/n$, and it is at most $\frac{1}{e(n - 1)}$.
- With $t$ tests and $k$ crewed flights: $q^t(1 - q^k) \le \frac{k}{e\,t}$.
