# Session 1 Cheatsheet: The Uniform Distribution

## $X \sim U_{[a,b]}$, $a < b$

| Quantity | Formula | $U_{[0,1]}$ | Example $U_{[2,6]}$ |
|---|---|---|---|
| PDF | $\frac{1}{b - a}$ on $[a, b]$, else 0 | $1$ | $1/4$ |
| CDF on $[a, b]$ | $\frac{x - a}{b - a}$ (0 before, 1 after) | $x$ | $(x - 2)/4$ |
| Mean | $\frac{a + b}{2}$ | $1/2$ | $4$ |
| Variance | $\frac{(b - a)^2}{12}$ | $1/12$ | $4/3$ |
| Std | $\frac{b - a}{2\sqrt{3}} \approx 0.29(b - a)$ | $\approx 0.29$ | $\approx 1.155$ |

Why $c = \frac{1}{b - a}$: the rectangle has area $c(b - a) = 1$. A density can exceed 1: $U_{[0,\,1/4]}$ has density 4.

## Interval probabilities ($a \le \alpha \le \beta \le b$)

| Interval | CDF difference | Probability |
|---|---|---|
| $(\alpha, \beta]$ | $F(\beta) - F(\alpha)$ | $\frac{\beta - \alpha}{b - a}$ |
| $(\beta, \infty)$ | $1 - F(\beta)$ | $\frac{b - \beta}{b - a}$ |
| $\lbrace \alpha \rbrace$ | $F(\alpha) - F(\alpha)$ | $0$ |

In words: length over domain length. Clip any interval to $[a, b]$ first.

## Affine maps

For $c \ne 0$, $Y = cX + d$ is uniform, with

$$f_Y(y) = \frac{1}{\lvert c \rvert} f_X\!\left(\frac{y - d}{c}\right).$$

- $X \sim U_{[0,1]}$, $c > 0$: $Y \sim U_{[d,\,c + d]}$. With $c < 0$: $Y \sim U_{[c + d,\,d]}$.
- $(b - a)X + a$ turns $U_{[0,1]}$ into $U_{[a,b]}$. Likewise, $\frac{X - a}{b - a}$ goes back.
- Moments: $E[cX + d] = cE[X] + d$, and $V(cX + d) = c^2 V(X)$.
- Celsius $U_{[0,1]}$ maps to Fahrenheit $U_{[32,\,33.8]}$, with density $5/9$.

## Other useful facts

- Conditioning on a subinterval gives a uniform on that subinterval.
- $E[X^k] = \frac{1}{k + 1}$ for $U_{[0,1]}$, and $E[Y^2] = \frac{a^2 + ab + b^2}{3}$ for $U_{[a,b]}$.
- $P(\lvert X - \mu \rvert \le \sigma) = 1/\sqrt{3} \approx 0.577$ for every uniform, and $\lvert X - \mu \rvert \le \sqrt{3}\,\sigma$ always.
- Any variable on $[a, b]$ has $V \le \frac{(b - a)^2}{4}$, attained by two equal spikes at the ends.
- Aging: $P(X > s + t \mid X > s) = \frac{b - s - t}{b - s}$ decreases with $s$, so a uniform lifetime is not memoryless.
- Not uniform: $X^2$ has density $\frac{1}{2\sqrt{y}}$. Uniform despite being non-affine: tent map $1 - \lvert 2X - 1 \rvert$.
- $-\ln(1 - X)$ has tail $e^{-y}$, which is exponential with rate 1.

## Which tool when

| Situation | Tool |
|---|---|
| A probability for a uniform | ratio of lengths, after clipping |
| Distribution of $cX + d$ | closure: map the endpoints, density $1/\lvert c \rvert$ |
| Moments of a general uniform | $U_{[0,1]}$ moments, then linearity and the variance rule |
| Non-affine $g(X)$ | CDF method, or sum $1/\lvert g' \rvert$ over the preimages |
| Event split across cycles | union of intervals, then total expectation |

## Traps

1. **Density is not probability:** it can exceed 1, and points have probability 0.
2. **Clip intervals:** $P(X \le 10)$ for $U_{[-2,\,6]}$ is 1.
3. **Variance has a square:** $(b - a)^2/12$, not $(b - a)/12$.
4. **Flip endpoints for a negative slope.**
5. **Unknown does not mean uniform:** the model needs a real reason to expect equal likelihood.
