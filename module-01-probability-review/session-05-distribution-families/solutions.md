# Session 5 Solutions: Distribution Families and Continuous Random Variables

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression such as $5e^{-2}$ when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. Name that distribution

**(a) Binomial $B_{0.04,\,15}$**, mean $15 \cdot 0.04 = 0.6$. There is a fixed number of trials (15 chips), the trials are independent, and each has the same "success" (defect) probability 0.04.

**(b) Geometric $G_{0.2}$**, mean $1/0.2 = 5$. The event that ends the wait is a miss, so the "success" probability is $0.2$, even though a miss is bad news for the player. $X$ counts the trials up to and including that event.

**(c) Poisson $P_{3.5}$**, mean (and variance) $3.5$. The count is of rare, independent events among a huge number of chances, which is exactly the regime where $B_{p,n}$ with large $n$, small $p$, and $np = 3.5$ is approximately $P_{3.5}$.

**(d) None of the four.** The committee is drawn without replacement, so the "trials" (seats) are dependent: given that the first seat went to a woman, the second does with probability $5/11$, and given that it went to a man, with probability $6/11$. The mean still follows from indicators: $E[X] = 4 \cdot \frac{6}{12} = 2$. (This is a hypergeometric distribution, which is not covered here.)

**(e) Bernoulli $B_{0.55}$**, mean $0.55$. It is one yes/no trial.

**(f) None of the four.** There is a fixed number of days, 365, but the days are not independent (wet days cluster in storms), and $p$ is far from constant (San Diego is much wetter in winter than in summer). Neither binomial condition holds.

**Key idea:** check the three binomial conditions (fixed $n$, independence, a common $p$) before using any formula. A count of rare events among many chances is Poisson, and a count of attempts until the first occurrence is geometric.

### Problem 2. Guessing on a quiz

$X \sim B_{1/4,\,6}$: 6 independent questions, each correct with probability $1/4$.

**(a)**

$$P(X = 2) = \binom{6}{2} \left(\frac{1}{4}\right)^2 \left(\frac{3}{4}\right)^4 = 15 \cdot \frac{1}{16} \cdot \frac{81}{256} = \frac{1215}{4096} \approx 0.2966.$$

**(b)** Use the complement:

$$P(X \ge 1) = 1 - P(X = 0) = 1 - \left(\frac{3}{4}\right)^6 = 1 - \frac{729}{4096} = \frac{3367}{4096} \approx 0.8220.$$

**(c)**

$$E[X] = np = \frac{3}{2} = 1.5, \qquad V(X) = npq = 6 \cdot \frac{1}{4} \cdot \frac{3}{4} = \frac{9}{8} = 1.125, \qquad \sigma_X = \sqrt{\frac{9}{8}} = \frac{3\sqrt{2}}{4} \approx 1.061.$$

**(d)** The ratio of consecutive probabilities is

$$\frac{b(k)}{b(k - 1)} = \frac{n - k + 1}{k} \cdot \frac{p}{q} = \frac{7 - k}{3k}.$$

It equals $2$ at $k = 1$ (so the PMF rises) and $5/6$ at $k = 2$ (so it falls from there on). The most likely value is $X = 1$, with

$$P(X = 1) = 6 \cdot \frac{1}{4} \cdot \left(\frac{3}{4}\right)^5 = \frac{1458}{4096} = \frac{729}{2048} \approx 0.3560.$$

Next, $P(X = 0) = \frac{729}{4096} \approx 0.1780$ and

$$P(X \ge 3) = 1 - \frac{729 + 1458 + 1215}{4096} = \frac{694}{4096} = \frac{347}{2048} \approx 0.1694.$$

So getting nothing right is slightly more likely than getting at least half right.

**Key idea:** "at least one" goes through the complement, and the ratio $b(k)/b(k-1)$ locates the peak without computing every term.

### Problem 3. True or false

**(a) False.** Only areas are probabilities, so only areas are bounded by 1. The density $3x^2$ on $(0, 1]$ reaches $3$ at $x = 1$, and the uniform density on $[0, 1/4]$ equals $4$ everywhere on that interval.

**(b) True.** $\lbrace X > 5 \rbrace \subseteq \lbrace X > 2 \rbrace$, so $P(X > 5 \mid X > 2) = \dfrac{q^5}{q^2} = q^3 = P(X > 3)$. This is memorylessness in tail form.

**(c) True.** $n - X$ counts the failures. Each trial fails with probability $1 - p$, independently, so the number of failures is $B_{1-p,\,n}$. With the PMF: $P(n - X = k) = P(X = n - k) = \binom{n}{n-k} p^{n-k} q^{k} = \binom{n}{k} q^k p^{n-k}$.

**(d) False.** The ratio $P_\lambda(k)/P_\lambda(k - 1) = \lambda/k$ equals 1 at $k = \lambda$, so $P_\lambda(\lambda - 1) = P_\lambda(\lambda)$, and both are maximal. For example, with $\lambda = 1$, $P(0) = P(1) = e^{-1} \approx 0.3679$.

**(e) False.** $F_Y(y) = P(2X \le y) = F_X(y/2)$, so $f_Y(y) = \frac{1}{2} f_X(y/2)$. Doubling stretches every interval by 2 and spreads the same probability over twice the length, so the density halves. Counterexample to the claim: for $X$ uniform on $[0, 1]$, the claimed $f_Y = 2$ on $[0, 2]$ has area 4.

**(f) True.** $P(a \le X \le b) = P(a < X < b) + P(X = a) + P(X = b)$, and both point probabilities are 0 for a continuous variable.

**Key idea:** a density is probability per unit length, so it can be large and it rescales under stretching. Single points carry no probability.

### Problem 4. A hump-shaped density

**(a)** The total area must be 1:

$$\int_0^2 x(2 - x)\, dx = \left[x^2 - \frac{x^3}{3}\right]_0^2 = 4 - \frac{8}{3} = \frac{4}{3}, \qquad c = \frac{3}{4} = 0.75.$$

**(b)** For $0 \le x \le 2$,

$$F(x) = \frac{3}{4} \int_0^x (2u - u^2)\, du = \frac{3}{4}\left(x^2 - \frac{x^3}{3}\right) = \frac{3x^2 - x^3}{4}.$$

In full: $F(x) = 0$ for $x < 0$, $F(x) = (3x^2 - x^3)/4$ for $0 \le x \le 2$, and $F(x) = 1$ for $x > 2$. As a check, $F(2) = (12 - 8)/4 = 1$.

**(c)** $F(3/2) = \frac{1}{4}\left(\frac{27}{4} - \frac{27}{8}\right) = \frac{27}{32}$ and $F(1/2) = \frac{1}{4}\left(\frac{3}{4} - \frac{1}{8}\right) = \frac{5}{32}$, so

$$P\left(\tfrac{1}{2} < X \le \tfrac{3}{2}\right) = \frac{27}{32} - \frac{5}{32} = \frac{22}{32} = \frac{11}{16} = 0.6875.$$

**(d)**

$$E[X] = \frac{3}{4} \int_0^2 (2x^2 - x^3)\, dx = \frac{3}{4}\left(\frac{16}{3} - 4\right) = 1, \qquad E[X^2] = \frac{3}{4} \int_0^2 (2x^3 - x^4)\, dx = \frac{3}{4}\left(8 - \frac{32}{5}\right) = \frac{6}{5},$$

$$V(X) = \frac{6}{5} - 1^2 = \frac{1}{5} = 0.2.$$

The mean could be predicted by symmetry: $f(1 + t) = \frac{3}{4}(1 + t)(1 - t) = \frac{3}{4}(1 - t^2) = f(1 - t)$, so the density is symmetric about 1, and its balance point is 1.

**Key idea:** normalize first, then every probability is a difference of CDF values. A density that is symmetric about $c$ has mean $c$.

---

## Exam-level

### Problem 5. Spare hard drives

**(a)** $X \sim B_{0.004,\,500}$, with $E[X] = 500 \cdot 0.004 = 2$ and $V(X) = 500 \cdot 0.004 \cdot 0.996 = 1.992$.

**(b)** Using $\binom{500}{2} = 124{,}750$,

$$P(X = 0) = 0.996^{500}, \qquad P(X \le 2) = 0.996^{500} + 500 \cdot 0.004 \cdot 0.996^{499} + 124{,}750 \cdot 0.004^2 \cdot 0.996^{498}.$$

Numerically, $0.996^{500} = e^{500 \ln 0.996} \approx e^{-2.004} \approx 0.1348$. The three terms add up to $P(X \le 2) \approx 0.6767$.

**(c)** $n = 500$ is large, $p = 0.004$ is small, and $np = 2$ is moderate, so $X$ is approximately $P_2$:

$$P(X = 0) \approx e^{-2} \approx 0.1353, \qquad P(X \le 2) \approx e^{-2}\left(1 + 2 + \frac{2^2}{2}\right) = 5e^{-2} \approx 0.6767.$$

The exact value of $P(X = 0)$ is $0.1348$, off by about 0.4%. For $P(X \le 2)$, the two models agree to six decimals ($0.676677$ vs $0.676676$).

**(d)**

$$\frac{P(Y = k)}{P(Y = k - 1)} = \frac{e^{-\lambda} \lambda^k / k!}{e^{-\lambda} \lambda^{k-1} / (k - 1)!} = \frac{\lambda}{k}.$$

The PMF rises while $\lambda/k > 1$ ($k < \lambda$), stays level at $k = \lambda$, and falls for $k > \lambda$.

- $\lambda = 2$: the ratios are $2, 1, 2/3, \dots$, so there is a tie: the most likely values are 1 and 2, each with probability $2e^{-2} \approx 0.2707$.
- $\lambda = 2.5$: the ratios are $2.5, 1.25, 0.833, \dots$, so the unique most likely value is 2, with probability $\frac{2.5^2}{2} e^{-2.5} = 3.125\, e^{-2.5} \approx 0.2565$.

**(e)** With $\lambda = 2$, the terms are $e^{-2}$ times $1, 2, 2, \frac{4}{3}, \frac{2}{3}, \frac{4}{15}, \dots$ Adding them up:

| $s$ | $P(X \le s)$ | $P(X > s)$ |
|---|---|---|
| 3 | $\frac{19}{3} e^{-2} \approx 0.8571$ | $\approx 0.1429$ |
| 4 | $7 e^{-2} \approx 0.9473$ | $\approx 0.0527$ |
| 5 | $\frac{109}{15} e^{-2} \approx 0.9834$ | $\approx 0.0166$ |

Four spares are not quite enough ($0.0527 > 0.05$), so the answer is $s = 5$. The exact binomial gives the same answer ($P(X > 4) \approx 0.0523$, $P(X > 5) \approx 0.0163$).

**Key idea:** many independent rare chances give a Poisson count with $\lambda = np$, and the ratio $\lambda/k$ gives the shape of the PMF at a glance.

### Problem 6. Loot boxes

**(a)** $X \sim G_{1/20}$. $X > n$ exactly when the first $n$ boxes all lack the item, which by independence has probability $(19/20)^n$. So

$$F(n) = P(X \le n) = 1 - \left(\frac{19}{20}\right)^n, \qquad n = 0, 1, 2, \dots,$$

and in general $F(x) = 1 - (19/20)^{\lfloor x \rfloor}$ for $x \ge 0$ and $F(x) = 0$ for $x < 0$.

**(b)**

$$P(X = 5) = \left(\frac{19}{20}\right)^4 \cdot \frac{1}{20} = \frac{130{,}321}{3{,}200{,}000} \approx 0.04073,$$

$$P(X > 20) = \left(\frac{19}{20}\right)^{20} \approx 0.3585, \qquad P(5 < X \le 20) = P(X > 5) - P(X > 20) = \left(\frac{19}{20}\right)^5 - \left(\frac{19}{20}\right)^{20} \approx 0.7738 - 0.3585 = 0.4153.$$

**(c)** By tail sums,

$$E[X] = \sum_{i=1}^{\infty} P(X \ge i) = \sum_{i=1}^{\infty} P(X > i - 1) = \sum_{i=1}^{\infty} \left(\frac{19}{20}\right)^{i-1} = \frac{1}{1 - 19/20} = 20.$$

$V(X) = \dfrac{19/20}{(1/20)^2} = 380$, so $\sigma_X = \sqrt{380} \approx 19.49$, almost as large as the mean. The number of boxes a player needs is very unpredictable.

**(d)** By memorylessness, given $X > 30$ the remaining count $X - 30$ is again $G_{1/20}$. So

$$E[X \mid X > 30] = 30 + 20 = 50, \qquad P(X > 50 \mid X > 30) = P(X > 20) = \left(\frac{19}{20}\right)^{20} \approx 0.3585.$$

The 30 unlucky boxes do not make the item any closer.

**(e)** $F(n) \ge 1/2$ means $(19/20)^n \le 1/2$, that is,

$$n \ge \frac{\ln 2}{-\ln 0.95} \approx \frac{0.6931}{0.05129} \approx 13.51.$$

So the median is $14$. As a check, $F(13) \approx 0.4867 < 1/2 \le F(14) \approx 0.5123$. The median is well below the mean because the PMF is skewed to the right. The rare, very long waits pull the mean up, while the median only depends on where the halfway mark falls.

**Key idea:** for a geometric, the tail $q^n$ gives the CDF, the mean (by tail sums), and every conditional statement (by memorylessness).

### Problem 7. Binomial moments the long way, and what independence buys

**(a)** For $1 \le k \le n$,

$$k\binom{n}{k} = \frac{k \cdot n!}{k!\,(n - k)!} = \frac{n!}{(k - 1)!\,(n - k)!} = n \cdot \frac{(n - 1)!}{(k - 1)!\,\big((n - 1) - (k - 1)\big)!} = n\binom{n-1}{k-1}.$$

The $k = 0$ term of $E[X]$ is 0. Using the identity, then substituting $j = k - 1$:

$$E[X] = \sum_{k=1}^{n} n\binom{n-1}{k-1} p^k q^{n-k} = np \sum_{j=0}^{n-1} \binom{n-1}{j} p^j q^{(n-1)-j} = np\,(p + q)^{n-1} = np.$$

**(b)** Applying (a) twice gives $k(k - 1)\binom{n}{k} = n(n - 1)\binom{n-2}{k-2}$ for $2 \le k \le n$, and the terms with $k = 0, 1$ vanish. With $j = k - 2$:

$$E[X(X - 1)] = n(n - 1)p^2 \sum_{j=0}^{n-2} \binom{n-2}{j} p^j q^{(n-2)-j} = n(n - 1)p^2.$$

So $E[X^2] = n(n - 1)p^2 + np$, and

$$V(X) = n(n - 1)p^2 + np - n^2p^2 = np - np^2 = npq.$$

**(c)** The cards are dealt without replacement, so the draws are dependent: the second card is a heart with probability $12/51$ if the first was a heart and $13/51$ if it was not. Write $X = I_1 + \cdots + I_5$, where $I_j = 1$ if card $j$ is a heart. By symmetry, every position is equally likely to hold any card, so $P(I_j = 1) = 13/52 = 1/4$ and

$$E[X] = 5 \cdot \frac{1}{4} = \frac{5}{4} = 1.25.$$

Linearity does not care about the dependence.

**(d)** Each $V(I_j) = \frac{1}{4} \cdot \frac{3}{4} = \frac{3}{16}$. For $i \ne j$, $P(I_i = I_j = 1) = \frac{13}{52} \cdot \frac{12}{51} = \frac{1}{17}$, so

$$\mathrm{Cov}(I_i, I_j) = \frac{1}{17} - \frac{1}{16} = -\frac{1}{272}.$$

With $\binom{5}{2} = 10$ pairs,

$$V(X) = 5 \cdot \frac{3}{16} + 2 \cdot 10 \cdot \left(-\frac{1}{272}\right) = \frac{15}{16} - \frac{5}{68} = \frac{255 - 20}{272} = \frac{235}{272} \approx 0.8640,$$

compared with $V = npq = 15/16 = 0.9375$ for $B_{1/4,\,5}$. The variance is smaller because the indicators are negatively correlated: each heart dealt leaves fewer hearts in the deck, which pulls the count back toward its mean. (The ratio is $\frac{235/272}{15/16} = \frac{47}{51} = \frac{52 - 5}{52 - 1}$.)

**Key idea:** the mean $np$ needs only linearity, but the variance $npq$ needs independence. Dependence enters through the covariance terms.

### Problem 8. A reciprocal

**(a)** $X \in (0, 1]$, so $Y = 1/X \in [1, \infty)$. On $(0, 1]$, $F_X(x) = \int_0^x 2u\, du = x^2$. The map $g(x) = 1/x$ is decreasing, so the inequality flips. For $y \ge 1$,

$$F_Y(y) = P\left(\frac{1}{X} \le y\right) = P\left(X \ge \frac{1}{y}\right) = 1 - F_X\left(\frac{1}{y}\right) = 1 - \frac{1}{y^2},$$

and $F_Y(y) = 0$ for $y < 1$. Differentiating,

$$f_Y(y) = \frac{2}{y^3} \quad \text{for } y \ge 1, \qquad f_Y(y) = 0 \text{ otherwise}.$$

**(b)** $g'(x) = -1/x^2$ and $x = g^{-1}(y) = 1/y$, so

$$f_Y(y) = \frac{f_X(x)}{\lvert g'(x) \rvert}\, \bigg\vert_{x = 1/y} = \frac{2x}{1/x^2}\, \bigg\vert_{x = 1/y} = 2x^3\, \Big\vert_{x = 1/y} = \frac{2}{y^3}. \checkmark$$

Without the absolute value the formula gives $-2/y^3 < 0$, which cannot be a density. The minus sign records that $g$ reverses order, which the CDF method handles with the $1 - F_X$.

**(c)** By LOTUS, $E[Y] = \int_0^1 \frac{1}{x} \cdot 2x\, dx = \int_0^1 2\, dx = 2$. From $f_Y$, $E[Y] = \int_1^\infty y \cdot \frac{2}{y^3}\, dy = \int_1^\infty \frac{2}{y^2}\, dy = 2$. Both give $E[Y] = 2$.

**(d)**

$$E[Y^2] = \int_1^\infty y^2 \cdot \frac{2}{y^3}\, dy = \int_1^\infty \frac{2}{y}\, dy = \lim_{M \to \infty} 2\ln M = \infty.$$

(LOTUS agrees: $\int_0^1 \frac{1}{x^2} \cdot 2x\, dx = \int_0^1 \frac{2}{x}\, dx$ diverges at 0.) Hence $V(Y) = E[Y^2] - (E[Y])^2 = \infty$. The tail $2/y^3$ decays fast enough for the mean to exist, but not for the second moment.

**(e)** $P(Y > 2) = 1 - F_Y(2) = \frac{1}{4} = 0.25$, which matches $P(X < 1/2) = (1/2)^2$. For the median, solve $1 - 1/m^2 = 1/2$: $m = \sqrt{2} \approx 1.414$.

**Key idea:** for a decreasing map, $F_Y(y) = 1 - F_X(g^{-1}(y))$. The absolute value in $\lvert g'(x) \rvert$ does the same job in the PDF formula.

### Problem 9. Squaring a lopsided uniform

**(a)** $X \in [-1, 2]$, so $Y = X^2 \in [0, 4]$. For $0 < y \le 1$, both roots $\pm\sqrt{y}$ lie in $[-1, 2]$, so there are two preimages. For $1 < y \le 4$, the root $-\sqrt{y} < -1$ falls outside, so only $+\sqrt{y}$ remains. (At $y = 0$ the only preimage is $x = 0$.)

**(b)**

- For $0 \le y \le 1$: $F_Y(y) = P(-\sqrt{y} \le X \le \sqrt{y}) = \dfrac{2\sqrt{y}}{3}$.
- For $1 \le y \le 4$: $F_Y(y) = P(-1 \le X \le \sqrt{y}) = \dfrac{\sqrt{y} + 1}{3}$.
- $F_Y(y) = 0$ for $y < 0$, and $F_Y(y) = 1$ for $y > 4$.

The pieces agree at $y = 1$ (both give $2/3$), and $F_Y(4) = 1$.

**(c)** Differentiating,

$$f_Y(y) = \begin{cases} \dfrac{1}{3\sqrt{y}}, & 0 < y < 1, \\ \dfrac{1}{6\sqrt{y}}, & 1 < y < 4, \\ 0, & \text{otherwise}. \end{cases}$$

With the formula, $g'(x) = 2x$, so $\lvert g'(\pm\sqrt{y}) \rvert = 2\sqrt{y}$. For $0 < y < 1$, two preimages give $\frac{1/3}{2\sqrt{y}} + \frac{1/3}{2\sqrt{y}} = \frac{1}{3\sqrt{y}}$. For $1 < y < 4$, one preimage gives $\frac{1/3}{2\sqrt{y}} = \frac{1}{6\sqrt{y}}$. The density halves at $y = 1$, where the left branch runs out.

The total area is $\int_0^1 \frac{dy}{3\sqrt{y}} + \int_1^4 \frac{dy}{6\sqrt{y}} = \frac{2}{3} + \frac{1}{3}(2 - 1) = 1$.

**(d)** By LOTUS on $X$, $E[Y] = E[X^2] = \frac{1}{3} \int_{-1}^{2} x^2\, dx = \frac{1}{3} \cdot \frac{8 + 1}{3} = 1$. From $f_Y$,

$$E[Y] = \int_0^1 \frac{\sqrt{y}}{3}\, dy + \int_1^4 \frac{\sqrt{y}}{6}\, dy = \frac{2}{9} + \frac{1}{6} \cdot \frac{2}{3}(8 - 1) = \frac{2}{9} + \frac{7}{9} = 1.$$

Finally, $P(Y \le 1/4) = F_Y(1/4) = \frac{2 \cdot (1/2)}{3} = \frac{1}{3} \approx 0.3333$, which matches $P(-1/2 \le X \le 1/2) = 1/3$.

**Key idea:** count the preimages for each $y$. The number can change across the support, and then $f_Y$ is piecewise.

---

## Challenge

### Problem 10. Where the Poisson comes from

**(a)** Write $p = \lambda/n$ and regroup:

$$b_{\lambda/n,\,n}(k) = \frac{n!}{k!\,(n - k)!} \cdot \frac{\lambda^k}{n^k} \left(1 - \frac{\lambda}{n}\right)^{n-k} = \frac{\lambda^k}{k!} \cdot \frac{n(n-1)\cdots(n-k+1)}{n^k} \cdot \left(1 - \frac{\lambda}{n}\right)^{n} \cdot \left(1 - \frac{\lambda}{n}\right)^{-k}.$$

As $n \to \infty$ with $k$ fixed:

- $\dfrac{n(n-1)\cdots(n-k+1)}{n^k} = \prod_{j=0}^{k-1}\left(1 - \dfrac{j}{n}\right) \to 1$, a product of a fixed number of factors that each tend to 1;
- $\left(1 - \frac{\lambda}{n}\right)^n \to e^{-\lambda}$;
- $\left(1 - \frac{\lambda}{n}\right)^{-k} \to 1$, a fixed power of a quantity that tends to 1.

Hence $b_{\lambda/n,\,n}(k) \to e^{-\lambda} \lambda^k / k!$.

**(b)** The terms with $k = 0, 1$ vanish, and $k(k - 1)/k! = 1/(k - 2)!$ for $k \ge 2$:

$$E[Y(Y - 1)] = \sum_{k=2}^{\infty} k(k - 1)\, e^{-\lambda} \frac{\lambda^k}{k!} = \lambda^2 e^{-\lambda} \sum_{k=2}^{\infty} \frac{\lambda^{k-2}}{(k - 2)!} = \lambda^2 e^{-\lambda} e^{\lambda} = \lambda^2.$$

So $E[Y^2] = \lambda^2 + \lambda$ and $V(Y) = \lambda^2 + \lambda - \lambda^2 = \lambda$.

**(c)** The mean of $B_{\lambda/n,\,n}$ is $\lambda$ for every $n$, and its variance $\lambda(1 - \lambda/n)$ tends to $\lambda$, the mean and variance of the limit $P_\lambda$. The binomial variance is $npq = \lambda q < \lambda$ because each trial's variance is $pq$, slightly less than its mean $p$. A bounded count of $n$ trials is a little more concentrated than the Poisson, which has no upper limit. As $p \to 0$, $q \to 1$ and the gap closes.

**(d)** $n = 3000$ and $p = 1/2000$, so $\lambda = 1.5$:

$$P(\text{at most 1 corrupted}) \approx e^{-1.5}(1 + 1.5) = 2.5\, e^{-1.5} \approx 0.5578.$$

The exact binomial value is

$$\left(\frac{1999}{2000}\right)^{3000} + 3000 \cdot \frac{1}{2000} \left(\frac{1999}{2000}\right)^{2999} \approx 0.5578,$$

and the two agree to about $4 \times 10^{-5}$.

**Key idea:** in $\binom{n}{k}p^k q^{n-k}$, the factor $q^n = (1 - \lambda/n)^n$ becomes $e^{-\lambda}$, and everything else is $\lambda^k/k!$ times factors that tend to 1.

### Problem 11. Memorylessness characterizes the geometric

**(a)** Let $t_n = P(X > n)$, so $t_0 = 1$. Since $\lbrace X > n + m \rbrace \subseteq \lbrace X > n \rbrace$, the hypothesis reads $t_{n+m}/t_n = t_m$, that is, $t_{n+m} = t_n t_m$. Taking $m = 1$ gives $t_{n+1} = t_1 t_n$, and by induction $t_n = t_1^n$. Let $q = t_1 = P(X > 1) = 1 - P(X = 1)$ and $p = 1 - q = P(X = 1)$. Then for $n \ge 1$,

$$P(X = n) = P(X > n - 1) - P(X > n) = q^{n-1} - q^n = q^{n-1}(1 - q) = q^{n-1} p.$$

The parameter is in range. $q > 0$ because $t_1 > 0$. And $q < 1$: if $q = 1$, then $P(X > n) = 1$ for every $n$, which is impossible for a variable with finite integer values, since $P(X > n) \to 0$. So $0 < p < 1$ and $X \sim G_p$.

**(b)** Let $M = \min(X, Y)$. The minimum exceeds $n$ exactly when both do, so by independence

$$P(M > n) = P(X > n)\, P(Y > n) = (1 - p)^n (1 - r)^n = (1 - s)^n, \qquad s = 1 - (1 - p)(1 - r).$$

The tail determines the PMF, since $P(M = n) = P(M > n - 1) - P(M > n)$. This is the tail of $G_s$, so $M \sim G_s$. In words: run the two sequences of trials side by side and call a round a success if at least one of them succeeds. Rounds are independent, each succeeds with probability $1 - (1 - p)(1 - r)$, and $M$ is the first successful round.

**(c)** $A, B \sim G_{1/6}$ are independent, so by (b), $\min(A, B) \sim G_{11/36}$ with $s = 1 - (5/6)^2 = 11/36$:

$$E[\min(A, B)] = \frac{36}{11} \approx 3.273.$$

Splitting on the value of $A$ (the law of total probability),

$$P(A < B) = \sum_{n=1}^{\infty} P(A = n)\, P(B > n) = \sum_{n=1}^{\infty} \left(\frac{5}{6}\right)^{n-1} \frac{1}{6} \left(\frac{5}{6}\right)^n = \frac{5}{36} \sum_{n=1}^{\infty} \left(\frac{25}{36}\right)^{n-1} = \frac{5/36}{11/36} = \frac{5}{11} \approx 0.4545,$$

$$P(A = B) = \sum_{n=1}^{\infty} \left(\frac{1}{6}\right)^2 \left(\frac{25}{36}\right)^{n-1} = \frac{1/36}{11/36} = \frac{1}{11} \approx 0.09091.$$

By symmetry $P(B < A) = 5/11$, and $\frac{5}{11} + \frac{5}{11} + \frac{1}{11} = 1$. A quicker view: look only at the first round in which someone rolls a six. In that round, "Ana only", "Ben only", and "both" have probabilities proportional to $5/36$, $5/36$, and $1/36$.

**Key idea:** a geometric is defined by its tail $q^n$. Tails multiply under independence, which makes minima easy.

### Problem 12. The CDF method in reverse

**(a)** On $(a, b)$, $F$ is continuous and strictly increasing from 0 to 1, so it has an increasing inverse $F^{-1} : (0, 1) \to (a, b)$, and $X \in (a, b)$ with probability 1. For $0 < u < 1$, strict monotonicity gives $F(X) \le u \iff X \le F^{-1}(u)$, so

$$P(U \le u) = P(F(X) \le u) = P\big(X \le F^{-1}(u)\big) = F\big(F^{-1}(u)\big) = u.$$

That is the uniform CDF on $(0, 1)$.

**(b)** For $x \in (a, b)$, $F^{-1}(U) \le x \iff U \le F(x)$, so $P(F^{-1}(U) \le x) = P(U \le F(x)) = F(x)$.

- PDF $3x^2$ on $(0, 1]$: $F(x) = x^3$, so $h(u) = F^{-1}(u) = u^{1/3}$.
- PDF $2y$ on $(0, 1]$: $F(y) = y^2$, so $k(u) = \sqrt{u}$.

This matches slide 87: $X^{3/2} = (U^{1/3})^{3/2} = U^{1/2}$ has the triangle density $2y$.

**(c)** $X \in (0, 1]$, so $2X - 1 \in (-1, 1]$ and $Z \in [0, 1]$. The map is two-to-one: for $0 < z < 1$, $(2x - 1)^2 = z$ gives $x = \frac{1 \pm \sqrt{z}}{2}$, and both roots lie in $(0, 1)$. For $0 \le z \le 1$,

$$F_Z(z) = P\big(\lvert 2X - 1 \rvert \le \sqrt{z}\big) = F_X\left(\frac{1 + \sqrt{z}}{2}\right) - F_X\left(\frac{1 - \sqrt{z}}{2}\right) = \frac{(1 + \sqrt{z})^3 - (1 - \sqrt{z})^3}{8}.$$

With $a = \sqrt{z}$, $(1 + a)^3 - (1 - a)^3 = 6a + 2a^3$, so

$$F_Z(z) = \frac{3\sqrt{z} + z^{3/2}}{4}, \qquad 0 \le z \le 1,$$

with $F_Z = 0$ below 0 and $F_Z = 1$ above 1. As a check, $F_Z(1) = 1$. Differentiating,

$$f_Z(z) = \frac{1}{4}\left(\frac{3}{2\sqrt{z}} + \frac{3}{2}\sqrt{z}\right) = \frac{3(1 + z)}{8\sqrt{z}}, \qquad 0 < z < 1.$$

The PDF formula agrees. $\lvert g'(x) \rvert = 4\lvert 2x - 1 \rvert = 4\sqrt{z}$ at both roots, and $f_X\left(\frac{1 \pm \sqrt{z}}{2}\right) = \frac{3(1 \pm \sqrt{z})^2}{4}$, so the sum is $\frac{3}{4} \cdot \frac{(1 + \sqrt{z})^2 + (1 - \sqrt{z})^2}{4\sqrt{z}} = \frac{3(1 + z)}{8\sqrt{z}}$. The total area is $\int_0^1 \frac{3}{8}\left(z^{-1/2} + z^{1/2}\right) dz = \frac{3}{8}\left(2 + \frac{2}{3}\right) = 1$.

**(d)** By linearity and the moments from the notes ($E[X] = 3/4$, $E[X^2] = 3/5$),

$$E[Z] = E[4X^2 - 4X + 1] = \frac{12}{5} - 3 + 1 = \frac{2}{5} = 0.4.$$

From $f_Z$: $\int_0^1 z \cdot \frac{3(1 + z)}{8\sqrt{z}}\, dz = \frac{3}{8} \int_0^1 \left(z^{1/2} + z^{3/2}\right) dz = \frac{3}{8}\left(\frac{2}{3} + \frac{2}{5}\right) = \frac{3}{8} \cdot \frac{16}{15} = \frac{2}{5}$.

**Key idea:** $F(X)$ is uniform and $F^{-1}(U)$ has CDF $F$. The CDF method runs in both directions, and a many-to-one map just adds up the pieces of $\lbrace g(X) \le z \rbrace$.
