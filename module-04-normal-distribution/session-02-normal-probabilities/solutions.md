# Session 2 Solutions: Normal Distribution Probabilities

Worked solutions to [exercises.md](exercises.md), in the same numbering. Values come from the table excerpt, so they carry its 4-digit rounding. Exact decimals from a program may differ in the last digit. Try each problem first.

---

## Warm-up

### Problem 1. Reading the table

**(a)** $\Phi(1.25) = 0.8944$.

**(b)** $1 - \Phi(0.5) = 1 - 0.6915 = 0.3085$.

**(c)** $\Phi(-1.5) = 1 - \Phi(1.5) = 1 - 0.9332 = 0.0668$.

**(d)** $P(Z > -0.75) = \Phi(0.75) = 0.7734$.

**(e)** $\Phi(2) - \Phi(-1) = \Phi(2) + \Phi(1) - 1 = 0.9772 + 0.8413 - 1 = 0.8185$.

**(f)** $\Phi(1.5) - \Phi(0.5) = 0.9332 - 0.6915 = 0.2417$.

**(g)** $2\Phi(1.96) - 1 = 2(0.9750) - 1 = 0.9500$.

**(h)** $2(1 - \Phi(1.28)) = 2(0.1003) = 0.2006$.

**Key idea:** the table gives the area to the left. Everything else follows from the complement and from symmetry.

### Problem 2. Exam scores

**(a)** $z = \frac{85 - 70}{10} = 1.5$, so $P(X \le 85) = \Phi(1.5) = 0.9332$.

**(b)** $z = -1$, so $P(X > 60) = \Phi(1) = 0.8413$.

**(c)** $z$ runs from $-0.5$ to $1$: $\Phi(1) + \Phi(0.5) - 1 = 0.8413 + 0.6915 - 1 = 0.5328$.

**(d)** The Z scores are $1.5$ for 85 on this exam, and $\frac{33 - 25}{4} = 2$ for 33 on the other. The student with 33 did relatively better, since that score is at about the 97.7th percentile, against the 93.3rd.

**Key idea:** a Z score removes the units and the location, which makes scores on different scales comparable.

### Problem 3. True or false

**(a) True.** This is $\Phi(-a) = 1 - \Phi(a)$, and it holds for all $a$ by symmetry.

**(b) False.** A uniform has $P(\lvert X - \mu \rvert \le \sigma) = 1/\sqrt{3} \approx 0.577$.

**(c) False.** Standardizing gives $\Phi(1) = 0.8413$, whatever $\mu$ and $\sigma$ are.

**(d) False.** $P(Z > 3) = 1 - 0.9987 = 0.0013$, or $0.13\%$. The $0.3\%$ is the two-sided $P(\lvert Z \rvert > 3)$.

**(e) True.** A normal has its median at $\mu$, and the CDF is strictly increasing, so $\mu = 10$.

**(f) False.** $P(\lvert Z \rvert \le 2) = 0.9544$, while $2 P(\lvert Z \rvert \le 1) = 2(0.6826) = 1.3652$, which is not even a probability.

**Key idea:** the fixed values of the rule come from standardizing, and they belong to the normal family alone.

### Problem 4. Heights and cutoffs

**(a)** We need $\Phi(z) = 0.90$, so $z \approx 1.28$, and the height is $170 + 1.28(8) = 180.24$ cm.

**(b)** We need $\Phi(z) = 0.05$. By symmetry, $z = -1.645$, and the height is $170 - 1.645(8) = 156.84$ cm.

**(c)** We need $2\Phi(z) - 1 = 0.95$, so $\Phi(z) = 0.975$ and $z = 1.96$. The interval is $170 \pm 1.96(8)$, that is, from $154.32$ to $185.68$ cm.

**Key idea:** to go in reverse, find $z$ in the table, and then undo the standardizing: $x = \mu + z\sigma$.

---

## Exam-level

### Problem 5. Finding parameters

**(a)** We need $P\left(Z < \frac{500 - \mu}{5}\right) = 0.01$. Since $\Phi(2.33) = 0.9901$, we have $\Phi(-2.33) \approx 0.01$, so $\frac{500 - \mu}{5} = -2.33$, and $\mu = 500 + 2.33(5) = 511.65$ ml.

**(b)** Now $\mu = 500 + 2.33(2) = 504.66$ ml, which is $6.99$ ml lower.

**(c)** $P(X \le 60) = 0.1587 = 1 - \Phi(1)$ gives $\frac{60 - \mu}{\sigma} = -1$. $P(X \ge 90) = 0.0228 = 1 - \Phi(2)$ gives $\frac{90 - \mu}{\sigma} = 2$. Subtracting, $\frac{30}{\sigma} = 3$, so $\sigma = 10$ and $\mu = 70$.

**Key idea:** each probability gives a linear equation in $\mu$ and $\sigma$, through its $z$ value.

### Problem 6. Quality control

Here $\sigma = 0.2$.

**(a)** $P(\lvert X - 10 \rvert > 0.3) = P(\lvert Z \rvert > 1.5) = 2(1 - 0.9332) = 0.1336$.

**(b)** $P(\text{no defective}) = (1 - 0.1336)^5 = 0.8664^5 \approx 0.4882$. The expected number is $5(0.1336) = 0.668$.

**(c)** The wait for the first defective is geometric, with mean $\frac{1}{0.1336} \approx 7.485$ bolts.

**(d)** $2\Phi(\alpha) - 1 = 0.9974$ at $\alpha = 3$, so $t = 3\sigma = 0.6$ mm.

**Key idea:** the normal gives a single probability, and from there it is a binomial and geometric problem.

### Problem 7. Rectangles and trapezoids

**(a)** On $[-\frac{1}{2}, \frac{1}{2}]$, the density runs between $\phi(0.5)$ and $\phi(0)$, so the width-1 rectangles give

$$0.3521 \le P(\lvert Z \rvert \le \tfrac{1}{2}) \le 0.3989.$$

The house estimate is $\frac{0.3521 + 0.3989}{2} = 0.3755$. The table gives $2(0.6915) - 1 = 0.3830$, so the house lies below the true area.

**(b)** On $[1, 2]$, the density falls from $\phi(1)$ to $\phi(2)$, so

$$0.0540 \le P(1 \le Z \le 2) \le 0.2420.$$

The trapezoid estimate is $\frac{0.2420 + 0.0540}{2} = 0.1480$. The table gives $0.9772 - 0.8413 = 0.1359$, so the trapezoid lies above the true area.

**(c)** $\phi'' < 0$ for $\lvert z \rvert < 1$, so $\phi$ is concave there and bulges above a straight chord. Hence the house is too small. $\phi'' > 0$ for $\lvert z \rvert > 1$, so $\phi$ is convex there and sags below its chord. Hence the trapezoid is too big.

**Key idea:** the inflection points at $\pm 1$ decide whether a straight-line estimate is low or high.

### Problem 8. What symmetry alone gives

**(a)** Reflection through $c$ preserves probability, so $P(X \le c - a) = P(X \ge c + a) = 1 - F(c + a)$.

**(b)** $F(1) = F(3 - 2) = 1 - F(5) = 0.2$. $P(1 < X \le 5) = 0.8 - 0.2 = 0.6$. $P(\lvert X - 3 \rvert > 2) = 1 - 0.6 = 0.4$.

**(c)** $F(-x) = \frac{1}{1 + e^{x}} = \frac{e^{-x}}{e^{-x} + 1} = 1 - \frac{1}{1 + e^{-x}} = 1 - F(x)$. So

$$P(\lvert X \rvert \le 1) = 2F(1) - 1 = \frac{2}{1 + e^{-1}} - 1 = \frac{e - 1}{e + 1} \approx 0.4621.$$

**(d)** It generalizes $\Phi(-a) = 1 - \Phi(a)$. What is special to the normal is that $P(\lvert X - \mu \rvert \le \alpha\sigma)$ is the same for every member of the family, and also that one table serves all of them. That comes from closure under affine maps, and not from symmetry.

**Key idea:** the negative half of the table needs only symmetry, while the one-table-for-all result needs the affine closure.

### Problem 9. Two groups

**(a)** The Z scores are $\frac{175 - 170}{5} = 1$ and $\frac{175 - 160}{5} = 3$. Total probability gives

$$0.4(1 - 0.8413) + 0.6(1 - 0.9987) = 0.06348 + 0.00078 = 0.06426.$$

**(b)** $P(A \mid \text{taller than } 175) = \frac{0.06348}{0.06426} \approx 0.9879$.

**(c)** We need $0.4\, f_A(x) = 0.6\, f_B(x)$. The common constant cancels, and taking logarithms,

$$\ln\frac{0.4}{0.6} = \frac{(x - 170)^2 - (x - 160)^2}{50} = \frac{3300 - 20x}{50}.$$

So $20x = 3300 - 50 \ln\frac{2}{3} = 3320.27$, and $x \approx 166.01$. This is above the midpoint 165, because group $B$ is larger, so it takes more evidence for group $A$ to catch up.

**Key idea:** far from the center, a small shift in the Z score changes the tail greatly, so the far tail is dominated by one group.

---

## Challenge

### Problem 10. Rare events and six sigma

**(a)** The first such day is geometric, with mean $1/p$: $\frac{1}{0.0456} \approx 21.93$ days (about 3 weeks), and $\frac{1}{0.0027} \approx 370.4$ days (about a year).

**(b)** $(1 - 0.0027)^{365} \approx 0.3728$. So a whole year without a $3\sigma$ day is less likely than not, which fits with the mean wait of about a year.

**(c)** With the mean moved by $1.5\sigma$ toward one limit, that limit is $4.5\sigma$ away, and the other is $7.5\sigma$ away. The defect rate is $P(Z > 4.5) + P(Z < -7.5) \approx 3.4 \times 10^{-6}$, or about 3.4 per million. The second term is about $10^{-14}$, which is negligible.

**(d)** For $z \ge a$, we have $1 \le z/a$, so

$$P(Z > a) = \int_a^\infty \phi(z)\, dz \le \frac{1}{a} \int_a^\infty z\phi(z)\, dz = \frac{1}{a} \Big[-\phi(z)\Big]_a^\infty = \frac{\phi(a)}{a}.$$

At $a = 3$: the bound is $1.477 \times 10^{-3}$, against $1.350 \times 10^{-3}$. At $a = 6$: the bound is $1.013 \times 10^{-9}$, against $9.866 \times 10^{-10}$. The bound gets relatively tighter as $a$ grows.

**Key idea:** tail probabilities become waiting times through the geometric mean, and $\phi(a)/a$ shows why they fall so quickly.

### Problem 11. A bound for every distribution

**(a)** Since $(X - \mu)^2 \ge 0$ everywhere,

$$\sigma^2 = E[(X - \mu)^2] \ge E\big[(X - \mu)^2\, \mathbf{1}_{\lvert X - \mu \rvert \ge \alpha\sigma}\big] \ge \alpha^2\sigma^2\, P(\lvert X - \mu \rvert \ge \alpha\sigma).$$

Dividing by $\alpha^2\sigma^2$ gives the bound.

**(b)** Take $p(\pm\alpha) = \frac{1}{2\alpha^2}$ and $p(0) = 1 - \frac{1}{\alpha^2}$. Then $\mu = 0$ and $\sigma^2 = 2 \cdot \frac{1}{2\alpha^2} \cdot \alpha^2 = 1$, and $P(\lvert X \rvert \ge \alpha) = \frac{1}{\alpha^2}$. This is the three-spike example from the notes.

**(c)** At $\alpha = 2$: the bound is $\frac{1}{4} = 0.25$, while the normal has $2(1 - 0.9772) = 0.0456$. At $\alpha = 3$: the bound is $\frac{1}{9} \approx 0.1111$, while the normal has $2(1 - 0.9987) = 0.0026$.

**(d)** Part (b) gives a distribution that attains the bound for each $\alpha$, so no smaller bound can hold for all distributions. The normal's tails are simply much lighter than the worst case.

**Key idea:** knowing only $\mu$ and $\sigma$ gives a weak guarantee, so the 68-95-99.7 numbers are real information about the normal shape.

### Problem 12. Looking at many measurements

**(a)** The maximum is at most $z$ exactly when every $Z_i \le z$. By independence, this has probability $\Phi(z)^n$.

**(b)** $0.9772^{10} \approx 0.7940$.

**(c)** The median $m$ satisfies $\Phi(m)^{10} = \frac{1}{2}$, so $\Phi(m) = 2^{-1/10} = 0.9330$. The closest table value is $\Phi(1.50) = 0.9332$, so $m \approx 1.5$.

**(d)** $1 - 0.9544^{20} \approx 0.6068$, and the expected number is $20(0.0456) = 0.912$.

**(e)** Looking at 20 measurements, a $2\sigma$ result is more likely than not, even if nothing unusual is happening. A single "surprising" value among many checks is weak evidence.

**Key idea:** independence turns statements about a maximum into powers of $\Phi$, and many looks make rare events common.
