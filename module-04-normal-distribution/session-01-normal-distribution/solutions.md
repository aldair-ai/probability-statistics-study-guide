# Session 1 Solutions: The Normal Distribution

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. Reading a density

**(a)** Matching $2\sigma^2 = 18$ gives $\sigma^2 = 9$, and $\sqrt{2\pi\sigma^2} = 3\sqrt{2\pi}$ agrees. So $\mu = 4$ and $\sigma^2 = 9$.

**(b)** The peak is at $x = 4$, with height $\frac{1}{3\sqrt{2\pi}} \approx 0.1330$.

**(c)** $f(1)/f(4) = e^{-9/18} = e^{-1/2} \approx 0.6065$.

**(d)** At $\mu \pm \sigma$, that is, $x = 1$ and $x = 7$. So part (c) says that the curve at an inflection point has height $e^{-1/2}$ times the peak.

**Key idea:** the $2\sigma^2$ in the exponent and the constant in front must agree, so one gives a check on the other.

### Problem 2. Affine maps

Use $aX + b \sim N(a\mu + b, a^2\sigma^2)$.

**(a)** $Y \sim N(2 \cdot 10 - 5, 4 \cdot 9) = N(15, 36)$.

**(b)** $W \sim N(0, 1)$, the standard normal.

**(c)** $V \sim N(-10, 9)$.

**(d)** $T \sim N\left(20 - \frac{10}{3}, \frac{1}{9} \cdot 9\right) = N\left(\frac{50}{3}, 1\right)$, with $\frac{50}{3} \approx 16.67$.

**(e)** $\sigma_Y = 6$ is double $\sigma_X = 3$, so the peak is halved: $\frac{1}{6\sqrt{2\pi}} \approx 0.06649$ against $\frac{1}{3\sqrt{2\pi}} \approx 0.1330$.

**Key idea:** the mean transforms like a value, the variance picks up $a^2$, and the peak height scales by $1/\lvert a \rvert$.

### Problem 3. True or false

**(a) True.** The peak is $\frac{1}{\sigma\sqrt{2\pi}}$, which exceeds 1 when $\sigma < \frac{1}{\sqrt{2\pi}} \approx 0.3989$. A density is not a probability.

**(b) True.** The density is symmetric around $\mu$ with its single peak there, so all three equal $\mu$.

**(c) False.** $X + X = 2X \sim N(0, 4)$. The rule "variances add" applies to independent variables, and $X$ is not independent of itself.

**(d) False.** $P(X = \mu) = 0$, while $f(\mu) > 0$.

**(e) False.** The map $g(z) = z$ for $\lvert z \rvert < 2$ and $g(z) = -z$ otherwise is not affine, but $g(Z) \sim N(0, 1)$, by the symmetry of $\phi$.

**(f) False.** It is $\lvert a \rvert \sigma$, since a standard deviation is never negative.

**Key idea:** most of the traps here confuse a density with a probability, or the variance with the standard deviation.

### Problem 4. Temperature conversion

**(a)** $F \sim N(1.8 \cdot 20 + 32, 1.8^2 \cdot 25) = N(68, 81)$, so $\sigma_F = 9$.

**(b)** $F - 68 = 1.8(C - 20)$ and $\sigma_F = 1.8\, \sigma_C$, so the factor 1.8 cancels, and $\frac{F - 68}{9} = \frac{C - 20}{5}$.

**(c)** $D \sim N(80, 25)$. Its standardized value is $\frac{D - 80}{5} = \frac{20 - C}{5} = -\frac{C - 20}{5}$. A decreasing map flips the sign of the standardized value.

**Key idea:** the standardized value does not depend on units, except for the sign of the slope.

---

## Exam-level

### Problem 5. Completing the square

**(a)** $-x^2 + 6x = -(x - 3)^2 + 9$, so $f(x) = c\, e^{9}\, e^{-(x - 3)^2}$. Matching $2\sigma^2 = 1$ gives $\sigma^2 = \frac{1}{2}$ and $\mu = 3$. The constant must then be

$$c\, e^{9} = \frac{1}{\sqrt{2\pi \cdot \frac{1}{2}}} = \frac{1}{\sqrt{\pi}}, \qquad \text{so} \qquad c = \frac{e^{-9}}{\sqrt{\pi}} \approx 6.963 \times 10^{-5}.$$

The peak is $f(3) = \frac{1}{\sqrt{\pi}} \approx 0.5642$.

**(b)** $-ax^2 + bx = -a\left(x - \frac{b}{2a}\right)^2 + \frac{b^2}{4a}$. The last term goes into the constant, and $a = \frac{1}{2\sigma^2}$ gives $\sigma^2 = \frac{1}{2a}$, with $\mu = \frac{b}{2a}$.

**(c)** Neither one. $e^{x^2}$ grows without bound, so no constant makes it integrate to 1. $e^{-\lvert x \rvert}$ does integrate to a finite value (with $c = \frac{1}{2}$), but its exponent is not quadratic, so it is not normal.

**Key idea:** a normal density is exactly the exponential of a downward quadratic.

### Problem 6. Gaussian integrals

**(a)** Substitute $x = z/\sqrt{2}$: $\int e^{-x^2}\, dx = \frac{1}{\sqrt{2}} \int e^{-z^2/2}\, dz = \frac{\sqrt{2\pi}}{\sqrt{2}} = \sqrt{\pi} \approx 1.772$.

**(b)** Half of the whole line, by symmetry: $\frac{\sqrt{2\pi}}{2} = \sqrt{\pi/2} \approx 1.253$.

**(c)** $\frac{1}{\sqrt{\pi}} e^{-x^2}$ is the density of $N(0, \frac{1}{2})$, whose second moment is $\frac{1}{2}$. So the integral is $\sqrt{\pi} \cdot \frac{1}{2} = \frac{\sqrt{\pi}}{2} \approx 0.8862$.

**(d)** An antiderivative exists here: $\left[-e^{-x^2/2}\right]_0^\infty = 1$.

**(e)** By symmetry and (d): $E\lvert Z \rvert = 2 \int_0^\infty z \phi(z)\, dz = \frac{2}{\sqrt{2\pi}} \cdot 1 = \sqrt{2/\pi} \approx 0.7979$.

**Key idea:** recognize the integrand as a normal density or moment, and read the answer off.

### Problem 7. Higher moments

**(a)** Take $u = z^{n-1}$ and $dv = z e^{-z^2/2}\, dz$, so $du = (n - 1) z^{n-2}\, dz$ and $v = -e^{-z^2/2}$. The boundary term vanishes, which gives

$$E[Z^n] = \frac{1}{\sqrt{2\pi}} \int (n - 1) z^{n-2} e^{-z^2/2}\, dz = (n - 1) E[Z^{n-2}].$$

**(b)** $E[Z^3] = 2 E[Z] = 0$. $E[Z^4] = 3 E[Z^2] = 3$. $E[Z^6] = 5 E[Z^4] = 15$.

**(c)** Expand $X = \sigma Z + \mu$ and use the odd moments being 0:

- $E[X^2] = \sigma^2 E[Z^2] + \mu^2 = \mu^2 + \sigma^2$.
- $E[X^3] = \sigma^3 E[Z^3] + 3\sigma^2\mu\, E[Z^2] + 3\sigma\mu^2 E[Z] + \mu^3 = \mu^3 + 3\mu\sigma^2$.
- $E[(X - \mu)^4] = \sigma^4 E[Z^4] = 3\sigma^4$.

**(d)** At $\mu = 1$, $\sigma = 2$: $E[X^2] = 5$, $E[X^3] = 13$, and $E[(X - \mu)^4] = 48$.

**Key idea:** the same integration by parts as for $V(Z)$ gives a recursion for all moments.

### Problem 8. The CDF method and a squared normal

**(a)** For $a < 0$, dividing by $a$ flips the inequality:

$$F_Y(y) = P(aX + b \le y) = P\left(X \ge \frac{y - b}{a}\right) = 1 - F_X\left(\frac{y - b}{a}\right).$$

Differentiating, $f_Y(y) = -\frac{1}{a} f_X\left(\frac{y - b}{a}\right) = \frac{1}{\lvert a \rvert} f_X\left(\frac{y - b}{a}\right)$. This is the same expression as in the notes, and the algebra from there is identical.

**(b)** $Y \sim N(3 - 2 \cdot 2, 4 \cdot 4) = N(-1, 16)$.

**(c)** For $y > 0$, the preimages are $\pm\sqrt{y}$, and $\lvert g'(x) \rvert = 2\sqrt{y}$ at both:

$$f_Y(y) = \frac{\phi(\sqrt{y}) + \phi(-\sqrt{y})}{2\sqrt{y}} = \frac{\phi(\sqrt{y})}{\sqrt{y}} = \frac{1}{\sqrt{2\pi y}}\, e^{-y/2}.$$

**(d)** $E[Y] = E[Z^2] = 1$, and $V(Y) = E[Z^4] - 1 = 2$. $Y$ cannot be normal because $Y \ge 0$, and every normal gives positive probability to negative values.

**Key idea:** a non-monotone map needs one term for each preimage, and a non-affine map rarely keeps a normal normal.

### Problem 9. Exponentials of normals

**(a)** Complete the square: $tz - \frac{z^2}{2} = -\frac{(z - t)^2}{2} + \frac{t^2}{2}$. So

$$E[e^{tZ}] = e^{t^2/2} \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}}\, e^{-(z - t)^2/2}\, dz = e^{t^2/2},$$

since the integrand is the density of $N(t, 1)$.

**(b)** $E[e^{tX}] = E[e^{t\sigma Z}]\, e^{t\mu} = e^{\sigma^2 t^2/2}\, e^{\mu t}$.

**(c)** $E[e^Z] = e^{1/2} \approx 1.649$, $E[e^{2Z}] = e^{2} \approx 7.389$, and $V(e^Z) = e^2 - e \approx 4.671$.

**(d)** Since $e^z$ is increasing, the median of $e^Z$ is $e^0 = 1$. The mean of about $1.649$ is well above it, so the distribution is skewed to the right, with a long upper tail.

**Key idea:** completing the square moves the $t$ out of the integral and leaves a density behind.

---

## Challenge

### Problem 10. A family of sign flips

**(a)** The map is its own inverse, with slope $\pm 1$. So $f_{X_c}(x) = \phi(x)$ for $\lvert x \rvert < c$, and $f_{X_c}(x) = \phi(-x) = \phi(x)$ for $\lvert x \rvert \ge c$.

**(b)** $Z + X_c = 2Z$ on $\lvert Z \rvert < c$, and $Z + X_c = 0$ on $\lvert Z \rvert \ge c$. So it equals 0 with probability $P(\lvert Z \rvert \ge c) > 0$, which is impossible for a continuous distribution. For $c = 1$: $2(1 - 0.8413) = 0.3174$.

**(c)** $Z X_c = Z^2$ on $\lvert Z \rvert < c$, and $Z X_c = -Z^2$ otherwise. Hence

$$E[Z X_c] = E[Z^2 \mathbf{1}_{\lvert Z \rvert < c}] - E[Z^2 \mathbf{1}_{\lvert Z \rvert \ge c}] = 2 E[Z^2 \mathbf{1}_{\lvert Z \rvert < c}] - E[Z^2] = 2 E[Z^2 \mathbf{1}_{\lvert Z \rvert < c}] - 1.$$

By parts over $[-c, c]$, with $u = z$ and $v = -\phi(z)$ (note $\phi'(z) = -z\phi(z)$):

$$\int_{-c}^{c} z^2 \phi(z)\, dz = \Big[-z\phi(z)\Big]_{-c}^{c} + \int_{-c}^{c} \phi(z)\, dz = -2c\,\phi(c) + 2\Phi(c) - 1.$$

**(d)** Both means are 0, so "uncorrelated" means $E[Z X_c] = 0$, that is, $2\Phi(c) - 1 - 2c\,\phi(c) = \frac{1}{2}$. At $c = 1.54$:

$$2(0.9382) - 1 - 2(1.54)(0.1219) = 0.8764 - 0.3755 = 0.5009 \approx \frac{1}{2}.$$

**(e)** No. They are uncorrelated, but $\lvert X_c \rvert = \lvert Z \rvert$ always. Knowing $Z$ determines $X_c$ exactly, so they are completely dependent.

**Key idea:** normal marginals say nothing about how two variables combine, and uncorrelated does not mean independent.

### Problem 11. More from the polar trick

**(a)** Substitute $z = x\sqrt{2a}$: $\int e^{-ax^2}\, dx = \frac{1}{\sqrt{2a}} \int e^{-z^2/2}\, dz = \frac{\sqrt{2\pi}}{\sqrt{2a}} = \sqrt{\pi/a}$.

**(b)** Differentiating both sides with respect to $a$: $-\int x^2 e^{-ax^2}\, dx = -\frac{\sqrt{\pi}}{2} a^{-3/2}$, so

$$\int_{-\infty}^{\infty} x^2 e^{-ax^2}\, dx = \frac{\sqrt{\pi}}{2} a^{-3/2}.$$

With $a = \frac{1}{2\sigma^2}$, the second moment of $N(0, \sigma^2)$ is

$$\frac{1}{\sigma\sqrt{2\pi}} \cdot \frac{\sqrt{\pi}}{2} (2\sigma^2)^{3/2} = \frac{1}{\sigma\sqrt{2\pi}} \cdot \frac{\sqrt{\pi}}{2} \cdot 2\sqrt{2}\, \sigma^3 = \sigma^2.$$

**(c)** Integrate the joint density over the disc of radius $r$:

$$P(Z_1^2 + Z_2^2 \le r^2) = \int_0^r \int_0^{2\pi} \frac{1}{2\pi} e^{-\rho^2/2} \rho\, d\theta\, d\rho = \int_0^r \rho e^{-\rho^2/2}\, d\rho = 1 - e^{-r^2/2}.$$

**(d)** With $t = r^2$, $P(R^2 \le t) = 1 - e^{-t/2}$. So $R^2 \sim E_{1/2}$, with mean 2. This matches $E[Z_1^2] + E[Z_2^2] = 1 + 1$. Also, $P(R > 2) = P(R^2 > 4) = e^{-2} \approx 0.1353$.

**Key idea:** the same polar computation that proves normalization shows that the squared distance of a two-dimensional normal point is exponential.

### Problem 12. Telling normal from not

**(a)** With $z = (x - \mu)/\sigma$, we have $dx = \sigma\, dz$, and

$$\int_{-\infty}^{\infty} \frac{1}{\sigma\sqrt{2\pi}}\, e^{-(x - \mu)^2/(2\sigma^2)}\, dx = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}}\, e^{-z^2/2}\, dz = 1.$$

**(b)** The map must satisfy $a\mu + b = \mu$ and $a^2\sigma^2 = \sigma^2$. So $a = \pm 1$, which gives $(a, b) = (1, 0)$, the identity, or $(a, b) = (-1, 2\mu)$, the reflection through $\mu$.

**(c)** By total probability, $f_X(x) = \frac{1}{2}\phi(x - 1) + \frac{1}{2}\phi(x + 1)$. The mean is 0, and $V(X) = V(Z) + V(S) = 1 + 1 = 2$.

**(d)** At 0, by symmetry, $f_X(0) = \phi(1) \approx 0.2420$. The peak of $N(0, 2)$ is $\frac{1}{\sqrt{4\pi}} \approx 0.2821$. They differ, so $X$ is not normal.

For the fourth moment, using independence, $E[S] = E[S^3] = 0$, and $S^2 = S^4 = 1$:

$$E[X^4] = E[Z^4] + 6 E[Z^2] E[S^2] + E[S^4] = 3 + 6 + 1 = 10,$$

while a normal with $\sigma^2 = 2$ would have $3\sigma^4 = 12$.

**Key idea:** a mixture of normals is generally not normal, and comparing the peak or the fourth moment detects this.
