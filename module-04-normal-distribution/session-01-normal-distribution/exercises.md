# Session 1 Exercises: The Normal Distribution

Solve these by hand, exam style, without code. Give answers as exact expressions, with decimals where they help. Notation follows the notes: $N(\mu, \sigma^2)$ has density $\frac{1}{\sqrt{2\pi\sigma^2}}\, e^{-(x - \mu)^2/(2\sigma^2)}$, and $Z \sim N(0, 1)$ has density $\phi$ and CDF $\Phi$. You may use $\int_{-\infty}^{\infty} e^{-z^2/2}\, dz = \sqrt{2\pi}$.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 30 min |
| Exam-level | 5-9 | 68 min |
| Challenge | 10-12 | 60 min |

---

## Warm-up

### Problem 1. Reading a density

**Tests:** identifying parameters, the peak, inflection points. **Time:** 7 min.

A density is given by $f(x) = \frac{1}{3\sqrt{2\pi}}\, e^{-(x - 4)^2/18}$.

(a) Identify $\mu$ and $\sigma^2$.

(b) Find the location and the height of the peak.

(c) Find $f(1)/f(4)$.

(d) Find the inflection points.

### Problem 2. Affine maps

**Tests:** closure under affine maps, negative slopes, how the peak changes. **Time:** 7 min.

Let $X \sim N(10, 9)$. Find the distribution of each variable.

(a) $Y = 2X - 5$.

(b) $W = (X - 10)/3$.

(c) $V = -X$.

(d) $T = 20 - X/3$.

(e) Compare the peak height of the density of $Y$ with that of $X$.

### Problem 3. True or false

**Tests:** density versus probability, parameters, sums, non-affine maps. **Time:** 9 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) The density of $N(0, \sigma^2)$ can exceed 1.

(b) For a normal distribution, the mean, the median, and the mode coincide.

(c) If $X \sim N(0, 1)$, then $X + X \sim N(0, 2)$.

(d) If $X \sim N(\mu, \sigma^2)$, then $P(X = \mu) = f(\mu)$.

(e) If $g(Z)$ is normal, where $Z \sim N(0, 1)$, then $g$ must be affine.

(f) For $X \sim N(\mu, \sigma^2)$ and $a \ne 0$, the standard deviation of $aX + b$ is $a\sigma$.

### Problem 4. Temperature conversion

**Tests:** affine maps in context, invariance of the standardized value. **Time:** 7 min.

A daily temperature in Celsius is $C \sim N(20, 25)$. In Fahrenheit, it is $F = 1.8C + 32$.

(a) Find the distribution of $F$, including its standard deviation.

(b) Show that $\frac{F - E[F]}{\sigma_F} = \frac{C - E[C]}{\sigma_C}$.

(c) Let $D = 100 - C$. Find its distribution, and relate its standardized value to that of $C$.

---

## Exam-level

### Problem 5. Completing the square

**Tests:** recognizing a normal density, recovering a constant. **Time:** 13 min.

(a) Let $f(x) = c\, e^{-x^2 + 6x}$ be a density. Complete the square to show that it is normal, and find $\mu$, $\sigma^2$, the constant $c$, and the peak height.

(b) For $a > 0$, show that $c\, e^{-ax^2 + bx}$ is a normal density with $\mu = \frac{b}{2a}$ and $\sigma^2 = \frac{1}{2a}$.

(c) Is $c\, e^{x^2}$ a normal density for some $c$? Is $c\, e^{-\lvert x \rvert}$? Explain.

### Problem 6. Gaussian integrals

**Tests:** reducing integrals to known ones, by scaling and by interpreting them as moments. **Time:** 13 min.

Evaluate each integral, using the Gaussian integral or facts about normal distributions, and not by finding antiderivatives where none exist.

(a) $\int_{-\infty}^{\infty} e^{-x^2}\, dx$.

(b) $\int_0^\infty e^{-x^2/2}\, dx$.

(c) $\int_{-\infty}^{\infty} x^2 e^{-x^2}\, dx$.

(d) $\int_0^\infty x e^{-x^2/2}\, dx$.

(e) $E\lvert Z \rvert$ for $Z \sim N(0, 1)$.

### Problem 7. Higher moments

**Tests:** integration by parts, an induction, transferring from $Z$ to $X$. **Time:** 14 min.

(a) Show that $E[Z^n] = (n - 1) E[Z^{n-2}]$ for $n \ge 2$.

(b) Find $E[Z^3]$, $E[Z^4]$, and $E[Z^6]$.

(c) For $X = \sigma Z + \mu$, find $E[X^2]$, $E[X^3]$, and $E[(X - \mu)^4]$ in terms of $\mu$ and $\sigma$.

(d) Evaluate those three at $\mu = 1$, $\sigma = 2$.

### Problem 8. The CDF method and a squared normal

**Tests:** a second proof of closure, a many-to-one map. **Time:** 14 min.

(a) The notes prove closure with the change-of-variables formula. For $a < 0$, prove it again with the CDF method: express $F_Y(y)$ for $Y = aX + b$ through $F_X$, and differentiate.

(b) Use this for $X \sim N(2, 4)$ and $Y = 3 - 2X$.

(c) Let $Y = Z^2$. Find its density, using the two preimages $\pm\sqrt{y}$.

(d) Find $E[Y]$ and $V(Y)$, using Problem 7. Explain why $Y$ cannot be normal.

### Problem 9. Exponentials of normals

**Tests:** completing the square inside an expectation, a skewed transform. **Time:** 14 min.

(a) Show that $E[e^{tZ}] = e^{t^2/2}$ for every real $t$.

(b) Use this to show that $E[e^{tX}] = e^{\mu t + \sigma^2 t^2/2}$ for $X \sim N(\mu, \sigma^2)$.

(c) Find $E[e^Z]$, $E[e^{2Z}]$, and $V(e^Z)$.

(d) Find the median of $e^Z$, and compare it with the mean. What does this say about the shape of its distribution?

---

## Challenge

### Problem 10. A family of sign flips

**Tests:** non-affine normal-preserving maps, uncorrelated but dependent variables. **Time:** 20 min.

For $c > 0$, let $X_c = Z$ if $\lvert Z \rvert < c$, and $X_c = -Z$ if $\lvert Z \rvert \ge c$.

(a) Show that $X_c \sim N(0, 1)$ for every $c > 0$.

(b) Show that $Z + X_c$ is not normal. Evaluate $P(Z + X_c = 0)$ for $c = 1$, given $\Phi(1) = 0.8413$.

(c) Show that $E[Z X_c] = 2 E\big[Z^2\, \mathbf{1}_{\lvert Z \rvert < c}\big] - 1$, and that $E\big[Z^2\, \mathbf{1}_{\lvert Z \rvert < c}\big] = 2\Phi(c) - 1 - 2c\,\phi(c)$.

(d) Find the equation that $c$ must satisfy for $Z$ and $X_c$ to be uncorrelated. Check that $c \approx 1.54$ nearly solves it, given $\Phi(1.54) = 0.9382$ and $\phi(1.54) = 0.1219$.

(e) For that $c$, are $Z$ and $X_c$ independent? Justify your answer.

### Problem 11. More from the polar trick

**Tests:** scaling, differentiating under the integral, a link to the exponential. **Time:** 20 min.

(a) Show that $\int_{-\infty}^{\infty} e^{-ax^2}\, dx = \sqrt{\pi/a}$ for $a > 0$.

(b) Differentiate (a) with respect to $a$ to find $\int_{-\infty}^{\infty} x^2 e^{-ax^2}\, dx$. Use the result with $a = \frac{1}{2\sigma^2}$ to confirm the variance of $N(0, \sigma^2)$.

(c) Let $Z_1, Z_2$ be independent standard normals, with joint density $\frac{1}{2\pi} e^{-(x^2 + y^2)/2}$. Using polar coordinates, show that $P(Z_1^2 + Z_2^2 \le r^2) = 1 - e^{-r^2/2}$.

(d) Conclude that $R^2 = Z_1^2 + Z_2^2$ is exponential. Find its rate, its mean, and $P(R > 2)$. Check the mean against $E[Z_1^2] + E[Z_2^2]$.

### Problem 12. Telling normal from not

**Tests:** normalization by substitution, self-maps, testing a mixture. **Time:** 20 min.

(a) Show directly by the substitution $z = (x - \mu)/\sigma$ that the $N(\mu, \sigma^2)$ density integrates to 1, assuming only that $\phi$ does.

(b) Find all affine maps $x \mapsto ax + b$ that send $N(\mu, \sigma^2)$ to itself.

(c) Let $X = Z + S$, where $S = \pm 1$ with probability $\frac{1}{2}$ each, independent of $Z$. Find its density, mean, and variance.

(d) Show that $X$ is not normal in two ways: by comparing $f_X(0)$ with the peak of the normal having the same mean and variance, and by comparing $E[X^4]$ with $3\sigma^4$. Use $\phi(1) = 0.2420$.
