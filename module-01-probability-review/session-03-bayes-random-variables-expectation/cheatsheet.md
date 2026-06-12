# Session 3 Cheatsheet: Bayes, Random Variables, Expectation

## Total probability and Bayes

- **Partition:** $F_1, \dots, F_k$ disjoint with union $\Omega$ (two-piece case: $E, E^c$).
- **Total probability:** $P(D) = \sum_i P(F_i)\,P(D \mid F_i)$, e.g. $P(F) = P(E)P(F \mid E) + P(E^c)P(F \mid E^c)$.
- **Bayes:** $P(E \mid F) = \dfrac{P(E)\,P(F \mid E)}{P(F)}$, and with a partition $P(F_i \mid D) = \dfrac{P(F_i)\,P(D \mid F_i)}{\sum_j P(F_j)\,P(D \mid F_j)}$.

> **Bayes in 3 steps**
> 1. **List** the hypotheses $H_i$ (a partition) with priors $P(H_i)$ and likelihoods $P(\text{evidence} \mid H_i)$.
> 2. **Multiply** to get weights $w_i = P(H_i)\,P(\text{evidence} \mid H_i)$; their sum is $P(\text{evidence})$.
> 3. **Normalize:** $P(H_i \mid \text{evidence}) = w_i / \sum_j w_j$. Check that the posteriors sum to 1.
>
> Phones: weights $0.5 \cdot 0.04,\ 0.3 \cdot 0.10,\ 0.2 \cdot 0.05 = 0.02, 0.03, 0.01$, total $0.06$, posteriors $1/3, 1/2, 1/6$.

## Random variables, PMF, CDF

| | PMF $p(x)$ | CDF $F(x)$ |
|---|---|---|
| Meaning | $P(X = x)$, the mass **at** $x$ | $P(X \le x) = \sum_{u \le x} p(u)$, the mass **up to** $x$ |
| Defined on | the values of $X$ (0 elsewhere) | all of $\mathbb{R}$, even for discrete $X$ |
| Shape | spikes summing to 1 | nondecreasing staircase from 0 to 1, jump at $x$ = $p(x)$ |
| Intervals | add spikes | $P(a < X \le b) = F(b) - F(a)$, $P(X < x) = F(x^-)$ |

**Bernoulli** $B_p$: $P(1) = p$, $P(0) = 1 - p = q$; $E[X] = p$.

## Expectation

| Tool | Formula | Notes |
|---|---|---|
| Definition | $E[X] = \sum_x x\,p(x)$ | a constant (not random); long-run average |
| Tail sums | $E[X] = \sum_{i \ge 1} P(X \ge i)$ | only for $X \in \lbrace 0, 1, 2, \dots \rbrace$ |
| LOTUS | $E[g(X)] = \sum_x g(x)\,p(x)$ | no need for the PMF of $g(X)$ |
| Linearity | $E[aX + bY + c] = aE[X] + bE[Y] + c$ | **no independence needed** |
| Indicator | $E[\mathbf{1}_A] = P(A)$ | $\mathbf{1}_A \sim B_{P(A)}$ |

Examples: 3 coins $E = 3/2$; queen of hearts position $53/2$; first red queen $53/3$; first of $k$ special cards in $n$: $\frac{n+1}{k+1}$; $X$ uniform on $\lbrace -2, \dots, 2 \rbrace$: $E[X^2] = 2 \ne (E[X])^2 = 0$. Hockey stick: $\sum_{i=k}^{n} \binom{i}{k} = \binom{n+1}{k+1}$.

> **Indicator method recipe**
> 1. **Split** the count: $X = \sum_j I_j$, one indicator per item that might be counted (day, couple, position).
> 2. **Find** $E[I_j] = P(\text{item } j \text{ counted})$ for one item; symmetry often makes them all equal.
> 3. **Add:** $E[X] = \sum_j P(A_j)$ ($= m \cdot p$ if all $m$ are equal). Ignore dependence.
>
> Birthdays: $I_d = 1$ if someone is born on day $d$, $E[I_d] = 1 - (364/365)^n$, so $E[D] = 365\left(1 - (364/365)^n\right)$.

## Which tool when

| Situation | Tool |
|---|---|
| Given $P(\text{effect} \mid \text{cause})$ for several causes, want $P(\text{effect})$ | total probability (tree) |
| Want $P(\text{cause} \mid \text{effect})$ | Bayes in 3 steps |
| $X \ge 0$ integer, tails easy ("wait until", min, "all above $i$") | tail sums |
| PMF symmetric about $c$ | $E[X] = c$ |
| Need $E[g(X)]$ | LOTUS (one step) |
| $X$ is a count of things that happen | indicators + linearity |

## Traps

1. **Flipping the conditional:** $P(D \mid F_2) = 10\%$ but $P(F_2 \mid D) = 50\%$; a 98% accurate test can give $P(\text{sick} \mid +) \approx 14\%$. Use the prior.
2. **$E[g(X)] \ne g(E[X])$** unless $g$ is affine: $E[X^2] \ne (E[X])^2$, $E[1/X] \ne 1/E[X]$.
3. **$<$ vs $\le$ at a jump:** $P(X \ge 2) = 1 - F(2^-)$, not $1 - F(2)$.
4. **Shortcut without its hypothesis:** the uniform or symmetry shortcut fails when the PMF is not flat or not symmetric (first red queen); tail sums need nonnegative integers.
5. **"Indicators must be independent":** false; linearity always holds, but it gives only the mean, not the distribution.
