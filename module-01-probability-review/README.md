# Module 01: Probability Review

Five sessions that cover the 89 slides of the Probability Review lecture (ECE 225A, Alon Orlitsky, UCSD). Each session folder holds a runnable `notes.ipynb`, 12 exam-style `exercises.md`, worked `solutions.md`, and a one-page `cheatsheet.md`. Below are the main formulas of each session, with a link to its cheatsheet.

| Session | Slides | Cheatsheet |
|---|---|---|
| [01 Probability basics](session-01-probability-basics/) | 1-12 | [cheatsheet](session-01-probability-basics/cheatsheet.md) |
| [02 Conditional probability and independence](session-02-conditional-probability-independence/) | 13-33 | [cheatsheet](session-02-conditional-probability-independence/cheatsheet.md) |
| [03 Bayes, random variables, expectation](session-03-bayes-random-variables-expectation/) | 34-54 | [cheatsheet](session-03-bayes-random-variables-expectation/cheatsheet.md) |
| [04 Variance, covariance, joint distributions](session-04-variance-covariance-joint/) | 55-69 | [cheatsheet](session-04-variance-covariance-joint/cheatsheet.md) |
| [05 Distribution families and continuous variables](session-05-distribution-families/) | 70-89 | [cheatsheet](session-05-distribution-families/cheatsheet.md) |

## 01 Probability basics

- Axioms on a sample space $\Omega$: $P(x) \ge 0$, $\sum_{x \in \Omega} P(x) = 1$, $P(E) = \sum_{x \in E} P(x)$. Equiprobable: $P(E) = \lvert E \rvert / \lvert \Omega \rvert$.
- Choosing $k$ of $n$: ordered with replacement $n^k$; ordered without replacement $n!/(n-k)!$; unordered without replacement $\binom{n}{k}$; unordered with replacement $\binom{n+k-1}{k}$.
- Poker: $\binom{52}{5} = 2{,}598{,}960$ hands; choose the hand's shape, then fill it.

## 02 Conditional probability and independence

- $P(A \cup B) = P(A) + P(B) - P(A \cap B)$, $P(A^c) = 1 - P(A)$, and De Morgan's laws.
- Conditional probability: $P(F \mid E) = P(E \cap F)/P(E)$. Chain rule: $P(E_1 \cap \cdots \cap E_n) = P(E_1)\, P(E_2 \mid E_1) \cdots P(E_n \mid E_1 \cap \cdots \cap E_{n-1})$.
- Independence: $P(E \cap F) = P(E)\, P(F)$. Three events need all three pairs and $P(E \cap F \cap G) = P(E)\, P(F)\, P(G)$.
- Birthday paradox: $P(\text{all } n \text{ birthdays differ}) = \prod_{i=0}^{n-1} \left(1 - \frac{i}{365}\right)$, so a shared birthday is more likely than not from $n = 23$ on.

## 03 Bayes, random variables, expectation

- Total probability: $P(D) = \sum_i P(F_i)\, P(D \mid F_i)$. Bayes: $P(F_i \mid D) = P(F_i)\, P(D \mid F_i) / P(D)$.
- PMF $p(x) = P(X = x)$, CDF $F(x) = P(X \le x)$, and $P(a < X \le b) = F(b) - F(a)$.
- $E[X] = \sum_x x\, p(x)$; tail sums $E[X] = \sum_{i \ge 1} P(X \ge i)$ for $X \in \lbrace 0, 1, \dots \rbrace$; LOTUS $E[g(X)] = \sum_x g(x)\, p(x)$.
- Linearity $E[aX + bY + c] = aE[X] + bE[Y] + c$, with no independence needed; indicators give $E[\mathbf{1}_A] = P(A)$.

## 04 Variance, covariance, joint distributions

- $V(X) = E[(X - \mu)^2] = E[X^2] - \mu^2$, $\sigma = \sqrt{V}$, $V(aX + b) = a^2 V(X)$.
- Marginals from a joint PMF: $p_X(x) = \sum_y p(x, y)$. $\mathrm{Cov}(X, Y) = E[XY] - \mu_X \mu_Y$.
- $V(X + Y) = V(X) + V(Y) + 2\,\mathrm{Cov}(X, Y)$. Independent implies uncorrelated, but not the other way around.
- $\rho = \mathrm{Cov}(X, Y)/(\sigma_X \sigma_Y) \in [-1, 1]$, with $\lvert \rho \rvert = 1$ exactly for a linear relation.

## 05 Distribution families and continuous variables

- $B_p$: mean $p$, variance $pq$. $B_{p,n}$: $\binom{n}{k} p^k q^{n-k}$, mean $np$, variance $npq$.
- $P_\lambda$: $e^{-\lambda} \lambda^k / k!$, mean and variance $\lambda$, and $B_{\lambda/n,\,n} \to P_\lambda$. $G_p$: $q^{n-1} p$, $P(X > n) = q^n$, mean $1/p$, variance $q/p^2$, memoryless.
- PDF: $f \ge 0$, $\int f = 1$, $P(A) = \int_A f$, $f = F'$, $P(X = x) = 0$; $E[g(X)] = \int g(x) f(x)\, dx$; $E[X] = \sum_i P(A_i)\, E[X \mid A_i]$.
- $Y = g(X)$: CDF method $F_Y(y) = P(g(X) \le y)$, or $f_Y(y) = \sum_{x \in g^{-1}(y)} f_X(x)/\lvert g'(x) \rvert$.
