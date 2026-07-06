# Session 1 Cheatsheet: The Normal Distribution

## $X \sim N(\mu, \sigma^2)$

$$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}\, e^{-\frac{(x - \mu)^2}{2\sigma^2}}, \qquad -\infty < x < \infty.$$

| Feature | Value | Example $N(15, 4)$ |
|---|---|---|
| Mean, median, mode | $\mu$ | 15 |
| Variance, std | $\sigma^2$, $\;\sigma$ | 4, 2 |
| Peak height $f(\mu)$ | $\frac{1}{\sigma\sqrt{2\pi}} \approx \frac{0.4}{\sigma}$ | $\approx 0.1995$ |
| Inflection points | $\mu \pm \sigma$ | 13, 17 |
| $f(\mu \pm \sigma)/f(\mu)$ | $e^{-1/2} \approx 0.6065$ | same |

Standard normal: $Z \sim N(0, 1)$, with density $\phi(z) = \frac{1}{\sqrt{2\pi}}\, e^{-z^2/2}$.

## Affine maps ($a \ne 0$)

$$aX + b \sim N(a\mu + b,\, a^2\sigma^2), \qquad \text{std } \lvert a \rvert\sigma, \qquad X = \sigma Z + \mu.$$

Proof: $f_Y(y) = \frac{1}{\lvert a \rvert} f_X\big(\frac{y - b}{a}\big)$, and then simplify.

## The reduction to $Z$

| Show for $Z$ | Then for $X = \sigma Z + \mu$ | How |
|---|---|---|
| $\int \phi = 1$ | $\int f_X = 1$ | square it, use polar coordinates |
| $E[Z] = 0$ | $E[X] = \mu$ | symmetry, or $\int z e^{-z^2/2}\, dz = -e^{-z^2/2}$ |
| $V(Z) = 1$ | $V(X) = \sigma^2$ | by parts: $u = z$, $dv = z e^{-z^2/2}\, dz$ |

Polar trick: $I^2 = \iint e^{-(x^2 + y^2)/2}\, dx\, dy = \int_0^\infty\!\int_0^{2\pi} e^{-r^2/2}\, r\, d\theta\, dr = 2\pi$, so $I = \sqrt{2\pi}$.

## Integrals and moments

- $\int_{-\infty}^{\infty} e^{-ax^2 + bx}\, dx$: complete the square. Then $\mu = \frac{b}{2a}$, $\sigma^2 = \frac{1}{2a}$.
- $\int_{-\infty}^{\infty} e^{-ax^2}\, dx = \sqrt{\pi/a}$, and $\int_{-\infty}^{\infty} x^2 e^{-ax^2}\, dx = \frac{\sqrt{\pi}}{2} a^{-3/2}$.
- $E[Z^n] = (n - 1)E[Z^{n-2}]$: $\;E[Z^2] = 1$, $E[Z^4] = 3$, $E[Z^6] = 15$, and odd moments are 0.
- $E\lvert Z \rvert = \sqrt{2/\pi} \approx 0.798$. $\;E[(X - \mu)^4] = 3\sigma^4$.
- $E[e^{tX}] = e^{\mu t + \sigma^2 t^2/2}$, so $E[e^Z] = \sqrt{e} \approx 1.649$.
- $Z^2$ has density $\frac{1}{\sqrt{2\pi y}}\, e^{-y/2}$, mean 1, and variance 2. $\;Z_1^2 + Z_2^2 \sim E_{1/2}$.

## Sign-flip quiz

$X = Z$ if $\lvert Z \rvert < 1$, and $X = -Z$ otherwise. Then $X \sim N(0, 1)$, though $X$ is not affine in $Z$. But $X + Z$ equals 0 with probability about $0.32$, so it is **not** normal.

## Which tool when

| Situation | Tool |
|---|---|
| Identify parameters from a formula | match $2\sigma^2$ in the exponent, check the constant |
| Density proportional to $e^{\text{quadratic}}$ | complete the square |
| Distribution of $aX + b$ | closure: transform the mean and the variance |
| Integral of $e^{-ax^2}$ with powers of $x$ | recognize a normal moment |
| Non-monotone $g(Z)$ | sum over preimages, or the CDF method |
| Is it normal? | check the support, the peak, and $E[(X - \mu)^4] = 3\sigma^4$ |

## Traps

1. **$N(15, 4)$ has $\sigma = 2$,** not 4.
2. **Std of $aX + b$ is $\lvert a \rvert\sigma$,** not $a\sigma$.
3. **$X + X = 2X \sim N(0, 4)$,** not $N(0, 2)$. Variances add only for independent variables.
4. **Density is not probability:** $f(\mu)$ can exceed 1, and $P(X = \mu) = 0$.
5. **Keep the $r$** in $dx\, dy = r\, dr\, d\theta$, and remember that the trick works only over the whole line.
