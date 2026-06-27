# Session 1 Solutions: The Uniform Distribution

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. Waiting for a shuttle

**(a)** $f(w) = \frac{1}{12}$ on $[0, 12]$, and 0 elsewhere. The CDF is $F(w) = 0$ for $w < 0$, $F(w) = w/12$ for $0 \le w < 12$, and $F(w) = 1$ for $w \ge 12$.

**(b)** Length over domain length: $P(W > 8) = \frac{4}{12} = \frac{1}{3} \approx 0.3333$, and $P(3 < W \le 5) = \frac{2}{12} = \frac{1}{6} \approx 0.1667$.

**(c)** $E[W] = 6$, $V(W) = \frac{12^2}{12} = 12$, and $\sigma_W = 2\sqrt{3} \approx 3.464$.

**Key idea:** every uniform probability is a ratio of lengths.

### Problem 2. An interval that crosses zero

**(a)** The domain has length 8.

- $P(X > 0) = \frac{6}{8} = \frac{3}{4} = 0.75$.
- $P(\lvert X \rvert < 1) = \frac{2}{8} = \frac{1}{4} = 0.25$, from the interval $(-1, 1)$.
- $P(X = 1) = 0$.
- $P(X < 10) = 1$, since the interval must be clipped to $[-2, 6]$.

**(b)** $E[X] = 2$, $V(X) = \frac{64}{12} = \frac{16}{3} \approx 5.333$, and $\sigma_X = \frac{8}{2\sqrt{3}} \approx 2.309$.

**(c)** $\frac{t + 2}{8} = \frac{1}{4}$ gives $t = 0$.

**(d)** $P(X > 5 \mid X > 0) = \frac{P(X > 5)}{P(X > 0)} = \frac{1/8}{6/8} = \frac{1}{6} \approx 0.1667$.

**Key idea:** clip each event to the domain first, then take a ratio of lengths.

### Problem 3. True or false

**(a) True.** The density is $1/(1/4) = 4$ on the whole domain. A density can exceed 1, as long as the area is 1.

**(b) False.** Every single point has probability 0, including the midpoint.

**(c) True.** $g(x) = -x$ is affine with $\lvert g' \rvert = 1$, so the density stays $\frac{1}{b - a}$, and the map sends $[a, b]$ to $[-b, -a]$.

**(d) False.** $F_{X^2}(y) = P(X \le \sqrt{y}) = \sqrt{y}$ is not linear in $y$. The density is $\frac{1}{2\sqrt{y}}$, which is not constant, and $E[X^2] = 1/3 \ne 1/2$.

**(e) False.** The variance is $(b - a)^2/12$, so $\sigma = (b - a)/(2\sqrt{3})$.

**(f) True.** The interval $[\mu - \sigma, \mu + \sigma]$ has length $2\sigma = (b - a)/\sqrt{3}$ and lies inside $[a, b]$. So the probability is $1/\sqrt{3} \approx 0.5774$, for every $a, b$.

**Key idea:** density is not probability, and closure under affine maps makes many facts universal across the family.

### Problem 4. A room's temperature

**(a)** $C$ is an affine function of $F$, so it is uniform. The endpoints map as $68 \mapsto 20$ and $77 \mapsto 25$, so $C \sim U_{[20,\,25]}$, with density $\frac{1}{5}$. Check with the formula: $\frac{1}{5/9} \cdot \frac{1}{9} = \frac{1}{5}$.

**(b)** $E[C] = 22.5$, and $\sigma_C = \frac{5}{2\sqrt{3}} \approx 1.443$.

**(c)** $\sigma_F = \frac{9}{2\sqrt{3}} \approx 2.598$, so $\sigma_C/\sigma_F = 5/9$.

**Key idea:** the slope scales the standard deviation by $\lvert a \rvert$ and the density by $1/\lvert a \rvert$.

---

## Exam-level

### Problem 5. A decreasing map

**(a)** The map is decreasing, with $4 \mapsto 2$ and $1 \mapsto 8$, so $Y \in [2, 8]$.

**(b)** For $2 \le y \le 8$, reversing the inequality:

$$F_Y(y) = P(10 - 2X \le y) = P\left(X \ge \frac{10 - y}{2}\right) = \frac{4 - \frac{10 - y}{2}}{3} = \frac{y - 2}{6}.$$

So $f_Y(y) = \frac{1}{6}$ on $[2, 8]$. With the formula: $\frac{f_X(x)}{\lvert g'(x) \rvert} = \frac{1/3}{2} = \frac{1}{6}$. Thus $Y \sim U_{[2,8]}$.

**(c)** From $Y$: $E[Y] = 5$ and $V(Y) = \frac{36}{12} = 3$. From $X$: $E[X] = \frac{5}{2}$ and $V(X) = \frac{9}{12} = \frac{3}{4}$, so $E[Y] = 10 - 2 \cdot \frac{5}{2} = 5$ and $V(Y) = 4 \cdot \frac{3}{4} = 3$.

**(d)** From $Y$: $P(Y > 6) = \frac{2}{6} = \frac{1}{3} \approx 0.3333$. From $X$: $Y > 6 \iff X < 2$, with probability $\frac{1}{3}$.

**(e)** $cX + d$ must map $[1, 4]$ onto $[0, 1]$. There are two options:

- Increasing: $1 \mapsto 0$ and $4 \mapsto 1$, so $c = \frac{1}{3}$ and $d = -\frac{1}{3}$.
- Decreasing: $1 \mapsto 1$ and $4 \mapsto 0$, so $c = -\frac{1}{3}$ and $d = \frac{4}{3}$.

**Key idea:** a decreasing map flips the inequality and the endpoints, but the density is still flat.

### Problem 6. The morning commute

**(a)** Let $A$ be the arrival time, $U_{[10,40]}$, with domain length 30.

- $T < 5$ when $A$ is in the last 5 minutes before a train and in the domain: $(10, 15)$ and $(25, 30)$. Also $(40, 45)$ lies outside the domain. So $P(T < 5) = \frac{10}{30} = \frac{1}{3} \approx 0.3333$.
- $T > 10$ when $A$ is in the first 5 minutes after a train: $(15, 20)$ and $(30, 35)$. So $P(T > 10) = \frac{10}{30} = \frac{1}{3} \approx 0.3333$.

**(b)** Condition on which train you catch. Given each case, $A$ is uniform on that interval, so $T$ is too.

| Train | $A \in$ | Probability | Wait is uniform on | Mean wait |
|---|---|---|---|---|
| :15 | $(10, 15)$ | $1/6$ | $(0, 5)$ | $2.5$ |
| :30 | $(15, 30)$ | $1/2$ | $(0, 15)$ | $7.5$ |
| :45 | $(30, 40)$ | $1/3$ | $(5, 15)$ | $10$ |

$$E[T] = \frac{1}{6}(2.5) + \frac{1}{2}(7.5) + \frac{1}{3}(10) = \frac{5}{12} + \frac{15}{4} + \frac{10}{3} = \frac{15}{2} = 7.5.$$

**(c)** With arrivals uniform on full cycles, $T \sim U_{[0,15]}$ and the mean is also $7.5$. Here they agree because the window of length 30 is exactly two cycles, and the wait function repeats with period 15, so shifting the window does not change the average. The distribution of $T$ is $U_{[0,15]}$ in both cases, and this also explains why both answers in (a) are $1/3$.

**Key idea:** split the event at the train times, then use total expectation across the pieces.

### Problem 7. All the moments

**(a)** $E[X^k] = \int_0^1 x^k\, dx = \frac{1}{k + 1}$.

**(b)**

$$E[Y^2] = \frac{1}{b - a} \int_a^b y^2\, dy = \frac{b^3 - a^3}{3(b - a)} = \frac{a^2 + ab + b^2}{3}.$$

Then

$$V(Y) = \frac{a^2 + ab + b^2}{3} - \frac{(a + b)^2}{4} = \frac{4a^2 + 4ab + 4b^2 - 3a^2 - 6ab - 3b^2}{12} = \frac{(b - a)^2}{12}.$$

Check at $a = 1$, $b = 3$: $E[Y^2] = \frac{13}{3}$, $(E[Y])^2 = 4$, and $V(Y) = \frac{1}{3} = \frac{4}{12}$.

**(c)** By LOTUS: $E[e^X] = \int_0^1 e^x\, dx = e - 1 \approx 1.718$, and $E\big[\frac{1}{1+X}\big] = \int_0^1 \frac{dx}{1+x} = \ln 2 \approx 0.6931$.

**(d)** $e^{E[X]} = \sqrt{e} \approx 1.649 < 1.718$, and $\frac{1}{1 + E[X]} = \frac{2}{3} \approx 0.6667 < 0.6931$. In both cases, $E[g(X)] > g(E[X])$. The functions $e^x$ and $\frac{1}{1+x}$ are convex on $[0, 1]$, and for a convex function, the average of the values exceeds the value at the average.

**Key idea:** use LOTUS for $E[g(X)]$. In general, $E[g(X)] \ne g(E[X])$.

### Problem 8. Breaking a stick

**(a)** For $\frac{1}{2} \le \ell \le 1$, $L \le \ell$ means that both $X \le \ell$ and $1 - X \le \ell$, that is, $1 - \ell \le X \le \ell$. Thus $F_L(\ell) = 2\ell - 1$, a ramp with density 2 on $[\frac{1}{2}, 1]$. So $L \sim U_{[1/2,\,1]}$, and $S = 1 - L \sim U_{[0,\,1/2]}$ by closure.

$E[L] = \frac{3}{4}$, $E[S] = \frac{1}{4}$, and $V(L) = \frac{(1/2)^2}{12} = \frac{1}{48} \approx 0.02083$.

**(b)** For $0 \le r \le 1$, using $S = 1 - L$:

$$F_R(r) = P\left(\frac{1 - L}{L} \le r\right) = P\left(L \ge \frac{1}{1 + r}\right) = \frac{1 - \frac{1}{1+r}}{1/2} = \frac{2r}{1 + r}.$$

Differentiating: $f_R(r) = \frac{2}{(1 + r)^2}$ on $[0, 1]$.

**(c)** $P(R \le \frac{1}{2}) = \frac{2 \cdot \frac{1}{2}}{3/2} = \frac{2}{3} \approx 0.6667$. For the mean:

$$E[R] = \int_0^1 \frac{2r}{(1 + r)^2}\, dr = 2\int_0^1 \left(\frac{1}{1 + r} - \frac{1}{(1 + r)^2}\right) dr = 2\left(\ln 2 - \frac{1}{2}\right) = 2\ln 2 - 1 \approx 0.3863.$$

**(d)** No. $E[S]/E[L] = \frac{1/4}{3/4} = \frac{1}{3} \approx 0.3333$, which differs from $0.3863$. The expectation of a ratio is not the ratio of expectations.

**Key idea:** $\max(X, 1 - X)$ is many-to-one, but its CDF is still simple, because $\lbrace L \le \ell \rbrace$ is a single interval for $X$.

### Problem 9. Conditioning and memory

**(a)** For $4 < x \le 10$, $P(X \le x \mid X > 4) = \frac{P(4 < X \le x)}{P(X > 4)} = \frac{(x - 4)/10}{6/10} = \frac{x - 4}{6}$, which is the CDF of $U_{(4,\,10]}$. In general, a uniform variable conditioned on a subinterval is uniform on that subinterval, since the flat density stays flat and is rescaled.

**(b)** $E[X \mid X > 4] = 7$ and $E[X \mid X \le 4] = 2$. Total expectation: $0.4 \cdot 2 + 0.6 \cdot 7 = 5 = E[X]$.

**(c)** $P(X > 6 \mid X > 4) = \frac{4}{6} = \frac{2}{3} \approx 0.6667$, while $P(X > 2) = \frac{8}{10} = \frac{4}{5} = 0.8$. So they differ.

**(d)** $P(X > s + 2 \mid X > s) = \frac{10 - s - 2}{10 - s} = \frac{8 - s}{10 - s}$. This is $\frac{4}{5}$ at $s = 0$, $\frac{2}{3}$ at $s = 4$, and $\frac{1}{2}$ at $s = 6$. It decreases with $s$, so an older part has a *worse* chance of lasting 2 more years. A part with this distribution ages. The next session studies the one distribution that does not age.

**Key idea:** conditioning a uniform on an interval gives a uniform, and comparing conditional tails tests for aging.

---

## Challenge

### Problem 10. From discrete to continuous

**(a)** $E[D_n] = \frac{1}{n} \sum_{k=1}^{n} \frac{k}{n} = \frac{1}{n^2} \cdot \frac{n(n+1)}{2} = \frac{n + 1}{2n}$. Next,

$$E[D_n^2] = \frac{1}{n} \sum_{k=1}^{n} \frac{k^2}{n^2} = \frac{(n + 1)(2n + 1)}{6n^2},$$

$$V(D_n) = \frac{(n + 1)(2n + 1)}{6n^2} - \frac{(n + 1)^2}{4n^2} = \frac{(n + 1)\big[2(2n + 1) - 3(n + 1)\big]}{12n^2} = \frac{(n + 1)(n - 1)}{12n^2} = \frac{n^2 - 1}{12n^2}.$$

**(b)** The limits are $\frac{1}{2}$ and $\frac{1}{12}$, which are the mean and variance of $U_{[0,1]}$. Values: $V(D_2) = \frac{1}{16} = 0.0625$, $V(D_5) = \frac{2}{25} = 0.08$, and $V(D_{10}) = \frac{33}{400} = 0.0825$.

**(c)** For $0 \le x \le 1$, the number of points $k/n$ at most $x$ is $\lfloor nx \rfloor$, so $F_n(x) = \lfloor nx \rfloor / n$. Since $nx - 1 < \lfloor nx \rfloor \le nx$, we have $x - \frac{1}{n} < F_n(x) \le x$, so $F_n(x) \to x$. Outside $[0, 1]$, both CDFs are constant and equal (0 for $x < 0$, 1 for $x > 1$).

**(d)** The discrete uniform on a fine grid has almost the same CDF, and so almost the same interval probabilities, as $U_{[0,1]}$. But convergence happens for CDFs, not for single points. $P(D_n = x) = \frac{1}{n} \to 0$, which does match $P(X = x) = 0$, but it is the interval probabilities that carry the information.

**Key idea:** a finer grid approaches the continuous distribution in terms of CDFs and interval probabilities.

### Problem 11. How spread out can a bounded variable be?

**(a)** $\sigma = \frac{b - a}{2\sqrt{3}}$. The event $\lvert X - \mu \rvert < t\sigma$ is an interval of length $2t\sigma = \frac{t}{\sqrt{3}}(b - a)$, which fits inside the domain if $t \le \sqrt{3}$. Thus

$$P(\lvert X - \mu \rvert \ge t\sigma) = \begin{cases} 1 - t/\sqrt{3} & 0 < t \le \sqrt{3} \\ 0 & t > \sqrt{3}. \end{cases}$$

At $t = 1$: $1 - \frac{1}{\sqrt{3}} \approx 0.4226$. At $t = 1.5$: $1 - \frac{\sqrt{3}}{2} \approx 0.1340$. For $t > \sqrt{3} \approx 1.732$, the probability is 0: a uniform value is never more than about $1.73\sigma$ from the mean.

**(b)** Write $Z - c = (Z - \mu) + (\mu - c)$. The cross term has mean 0, so

$$E[(Z - c)^2] = V(Z) + (\mu - c)^2 \ge V(Z).$$

**(c)** With $c = \frac{a + b}{2}$, we have $\lvert Z - c \rvert \le \frac{b - a}{2}$ always, so $V(Z) \le E[(Z - c)^2] \le \frac{(b - a)^2}{4}$. Equality holds for the two-point distribution with $P(Z = a) = P(Z = b) = \frac{1}{2}$.

**(d)** The ratio is

$$\frac{(b - a)/(2\sqrt{3})}{(b - a)/2} = \frac{1}{\sqrt{3}} \approx 0.5774.$$

The uniform spreads probability evenly, so it uses only about 58% of the largest possible standard deviation, which puts all the probability at the two extremes.

**Key idea:** the mean minimizes $E[(Z - c)^2]$, and that gives a sharp variance bound for any bounded variable.

### Problem 12. Maps that do and do not preserve uniformity

**(a)** $T = 2X$ for $X \le \frac{1}{2}$ and $T = 2 - 2X$ for $X \ge \frac{1}{2}$. Each $t \in (0, 1)$ has two preimages, $\frac{t}{2}$ and $1 - \frac{t}{2}$, and $\lvert g' \rvert = 2$ at both. Therefore

$$f_T(t) = \frac{1}{2} + \frac{1}{2} = 1 \quad \text{on } (0, 1),$$

so $T \sim U_{[0,1]}$.

**(b)** $F(y) = \sqrt{y}$, so $f(y) = \frac{1}{2\sqrt{y}}$ on $(0, 1]$. The mean by LOTUS is $E[X^2] = \frac{1}{3}$, and from the density, $\int_0^1 \frac{y}{2\sqrt{y}}\, dy = \frac{1}{2} \cdot \frac{2}{3} = \frac{1}{3}$. The second moment is $E[X^4] = \frac{1}{5}$, or $\int_0^1 \frac{y^2}{2\sqrt{y}}\, dy = \frac{1}{2} \cdot \frac{2}{5} = \frac{1}{5}$. So $V(X^2) = \frac{1}{5} - \frac{1}{9} = \frac{4}{45} \approx 0.08889$. Finally, $P(X^2 \le \frac{1}{4}) = P(X \le \frac{1}{2}) = \frac{1}{2}$.

**(c)** For $y \ge 0$: $P(Y > y) = P(1 - X < e^{-y}) = e^{-y}$, since $1 - X \sim U_{[0,1]}$. So $f_Y(y) = e^{-y}$ for $y \ge 0$. By LOTUS,

$$E[Y] = \int_0^1 -\ln(1 - x)\, dx = \int_0^1 -\ln u\, du = \big[u - u \ln u\big]_0^1 = 1.$$

This $Y$ is the exponential distribution with rate 1, which is the topic of the next session.

**(d)** The general formula is $f_Y(y) = \sum_{x \in g^{-1}(y)} \frac{1}{\lvert g'(x) \rvert}$ for $X \sim U_{[0,1]}$. So $f_Y$ is flat exactly when this sum is constant in $y$. A one-to-one map needs $\lvert g' \rvert$ constant, that is, an affine map. A many-to-one map can have a flat result if the slopes balance out across preimages, as the tent map does. Typical maps do not satisfy this.

**Key idea:** a flat output needs the sum of $1/\lvert g' \rvert$ over the preimages to be constant, which is possible without being affine.
