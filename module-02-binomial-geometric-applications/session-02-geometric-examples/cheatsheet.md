# Session 2 Cheatsheet: Geometric Examples, Odd Odds and a Rocket

## Geometric review ($X \sim G_p$, $q = 1 - p$)

| Quantity | Formula | Example |
|---|---|---|
| PMF, tail, mean | $q^{n-1}p$, $\;P(X > n) = q^n$, $\;1/p$ | $G_{1/6}$: mean 6 |
| $P(X \text{ odd})$ | $\dfrac{p}{1 - q^2} = \dfrac{1}{1 + q} = \dfrac{1}{2 - p}$ | $p = 1/2$: $2/3$; $p = 1/6$: $6/11$ |
| $P(X \text{ even})$ | $q \cdot P(\text{odd}) = \dfrac{q}{2 - p}$ | $p = 1/2$: $1/3$ |
| $P(X \text{ multiple of } m)$ | $\dfrac{p\,q^{m-1}}{1 - q^m}$ (tends to $1/m$ as $p \to 0$) | $p = 1/3$, $m = 3$: $4/19$ |
| $E[X \mid X \text{ odd}]$ | $\dfrac{1 + q^2}{p(1 + q)}$, and $E[X \mid \text{even}]$ is 1 more | $p = 1/2$: $5/3$ and $8/3$ |

## Games with turns

| Game | First player wins with |
|---|---|
| 2 players, same $p$ | $\dfrac{1}{2 - p}$ |
| $k$ players, same $p$ | $\dfrac{p}{1 - q^k}$ (each later player: multiply by $q$) |
| 2 players, skills $a$ (first) and $b$ | $\dfrac{a}{1 - (1-a)(1-b)}$; fair if $a = \dfrac{b}{1 + b}$ |
| First to 2 points, $h = \frac{1}{2-p}$ | $2h - 3h^2 + 2h^3$ (fair coin: $16/27$) |

Expected length with skills $a, b$: $\dfrac{2 - a}{1 - (1-a)(1-b)}$.

## Worst-case risk over an unknown $p$

| Program | Probability | Worst $p$ | Maximum |
|---|---|---|---|
| Fail exactly on flight $n$ | $q^{n-1}p$ | $1/n$ | $\dfrac{(1 - 1/n)^n}{n - 1} \le \dfrac{1}{e(n - 1)}$ |
| $t$ tests, then $k$ crewed flights | $q^t(1 - q^k)$ | $q^k = \frac{t}{t+k}$ | $\left(\frac{t}{t+k}\right)^{t/k} \frac{k}{t+k} \le \dfrac{k}{e\,t}$ |
| $t$ tests with detection rate $d$ | $(1 - pd)^t p$ | $\frac{1}{d(t+1)}$ if at most 1 | $\le \dfrac{1}{d\,e\,t}$, else $(1 - d)^t$ |
| Exactly $k$ of $m$ succeed | $\binom{m}{k} p^k q^{m-k}$ | $k/m$ | $k = 1$: $(1 - 1/m)^{m-1} > 1/e$ |

Numbers: $n = 11$: maximum $0.0350$, bound $1/(10e) \approx 0.0368$. For a 1% bound: $t = 37$. With $t = k = 10$: worst case $1/4$. With $p$ uniform on $[0,1]$: joint $\frac{1}{(t+1)(t+2)}$, conditional $\frac{1}{t+2}$.

## Which tool when

| Situation | Tool |
|---|---|
| Players alternate until a first success | parity or residue of $G_p$ |
| Avoid an infinite sum | relate the series: $P(\text{even}) = q\,P(\text{odd})$ |
| The game restarts after a round | first-step analysis: one equation for the unknown |
| Conditioning on a failure | memorylessness: $X = 1 + X'$ |
| Check a formula | inequality, limits $p \to 0, 1$, monotonicity, and sum to 1 |
| An unknown $p$ with a bad outcome in the middle | maximize over $p$ with calculus, then check the endpoints |

## Traps

1. **Joint versus conditional:** the bound is on "clean tests and then a mishap", not on "a mishap given clean tests".
2. **Argmax is $1/n$:** in $q^{n-1}p$, the maximum is at $1/n$, not $1/(n-1)$.
3. **The worst case is not the largest $p$:** high-risk rockets fail during testing and never fly the crew.
4. **Only one crewed flight:** the bound grows in proportion to the number of crewed flights $k$.
5. **Assumptions:** independent flights with one common $p$. Fixing defects or shared flaws breaks the model.
