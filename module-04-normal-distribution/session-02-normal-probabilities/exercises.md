# Session 2 Exercises: Normal Distribution Probabilities

Solve these by hand, exam style, without code. Use this excerpt from the Z table. Notation follows the notes: $\Phi(z) = P(Z \le z)$ for $Z \sim N(0, 1)$, and $\phi$ is its density.

| $z$ | 0.50 | 0.75 | 1.00 | 1.25 | 1.28 | 1.50 | 1.645 | 1.96 | 2.00 | 2.33 | 3.00 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $\Phi(z)$ | .6915 | .7734 | .8413 | .8944 | .8997 | .9332 | .9500 | .9750 | .9772 | .9901 | .9987 |

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 30 min |
| Exam-level | 5-9 | 66 min |
| Challenge | 10-12 | 55 min |

---

## Warm-up

### Problem 1. Reading the table

**Tests:** the three interval types, negative values, absolute values. **Time:** 8 min.

Let $Z \sim N(0, 1)$. Find each probability.

(a) $P(Z \le 1.25)$.

(b) $P(Z > 0.5)$.

(c) $P(Z \le -1.5)$.

(d) $P(Z > -0.75)$.

(e) $P(-1 < Z \le 2)$.

(f) $P(0.5 < Z < 1.5)$.

(g) $P(\lvert Z \rvert \le 1.96)$.

(h) $P(\lvert Z \rvert > 1.28)$.

### Problem 2. Exam scores

**Tests:** standardizing, comparing across different scales. **Time:** 7 min.

Scores on an exam are $X \sim N(70, 100)$.

(a) Find $P(X \le 85)$.

(b) Find $P(X > 60)$.

(c) Find $P(65 \le X \le 80)$.

(d) Another student scored 33 on a different exam, with scores distributed as $N(25, 16)$. Who did relatively better, that student or one with 85 on this exam?

### Problem 3. True or false

**Tests:** symmetry, the rule's scope, tails, scaling of probabilities. **Time:** 8 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) $\Phi(a) + \Phi(-a) = 1$ for every real $a$.

(b) Every random variable with finite variance satisfies $P(\lvert X - \mu \rvert \le \sigma) \ge 0.68$.

(c) For $X \sim N(\mu, \sigma^2)$, the value of $P(X \le \mu + \sigma)$ depends on $\sigma$.

(d) $P(Z > 3) \approx 0.3\%$.

(e) If $X$ is normal and $P(X \le 10) = \frac{1}{2}$, then $E[X] = 10$.

(f) $P(\lvert Z \rvert \le 2) = 2 P(\lvert Z \rvert \le 1)$.

### Problem 4. Heights and cutoffs

**Tests:** using the table in reverse. **Time:** 7 min.

Heights in a population are $X \sim N(170, 64)$, in centimeters.

(a) Find the height above which the tallest 10% lie.

(b) Find the height below which the shortest 5% lie.

(c) Find the interval, centered at the mean, that contains the middle 95%.

---

## Exam-level

### Problem 5. Finding parameters

**Tests:** solving for $\mu$ and $\sigma$ from probabilities. **Time:** 13 min.

(a) A machine fills bottles with an amount $X \sim N(\mu, 25)$, in milliliters. Find the setting $\mu$ such that only 1% of bottles hold less than 500 ml.

(b) A better machine has $\sigma = 2$. How much lower can $\mu$ be set, with the same guarantee?

(c) A normal variable has $P(X \le 60) = 0.1587$ and $P(X \ge 90) = 0.0228$. Find $\mu$ and $\sigma$.

### Problem 6. Quality control

**Tests:** normal probabilities combined with binomial and geometric models. **Time:** 13 min.

A bolt's diameter is $X \sim N(10, 0.04)$, in millimeters. A bolt is defective if $\lvert X - 10 \rvert > 0.3$. Bolts are independent.

(a) Find the probability that a bolt is defective.

(b) Find the probability that a box of 5 bolts has no defective bolt, and the expected number of defective bolts in the box.

(c) Find the expected number of bolts inspected up to and including the first defective one.

(d) What tolerance $\pm t$ would make about 99.74% of bolts acceptable?

### Problem 7. Rectangles and trapezoids

**Tests:** area bounds, concavity deciding the direction of an estimate. **Time:** 13 min.

Use $\phi(0) = 0.3989$, $\phi(0.5) = 0.3521$, $\phi(1) = 0.2420$, and $\phi(2) = 0.0540$.

(a) Bound $P(\lvert Z \rvert \le \frac{1}{2})$ between two rectangles of width 1. Find the house estimate, which is their average, and compare all of these with the table's value.

(b) Bound $P(1 \le Z \le 2)$ between two rectangles of width 1. Find the trapezoid estimate, and compare with the table's value.

(c) In (a) the house lies below the true area, but in (b) the trapezoid lies above it. Explain why, using $\phi''(z) = (z^2 - 1)\phi(z)$.

### Problem 8. What symmetry alone gives

**Tests:** symmetric densities in general. **Time:** 13 min.

(a) Let $X$ have a density symmetric around $c$, and CDF $F$. Show that $F(c - a) = 1 - F(c + a)$ for all $a$.

(b) Such an $X$ has $c = 3$ and $F(5) = 0.8$. Find $F(1)$, $P(1 < X \le 5)$, and $P(\lvert X - 3 \rvert > 2)$.

(c) The logistic distribution has $F(x) = \frac{1}{1 + e^{-x}}$. Verify that $F(-x) = 1 - F(x)$, and find $P(\lvert X \rvert \le 1)$ exactly.

(d) Which formula from the notes does (a) generalize? Which property is special to the normal, and not to all symmetric densities?

### Problem 9. Two groups

**Tests:** total probability and Bayes with normal components. **Time:** 14 min.

In a population, 40% belong to group $A$, with height $N(170, 25)$, and 60% belong to group $B$, with height $N(160, 25)$.

(a) Find the probability that a random person is taller than 175.

(b) Given that a person is taller than 175, find the probability that the person is from group $A$.

(c) At what height are the two groups equally likely, given that exact height? Use the densities, and compare the answer with the midpoint 165. Explain why it differs.

---

## Challenge

### Problem 10. Rare events and six sigma

**Tests:** geometric waiting times, a tail bound. **Time:** 20 min.

(a) A normal sample is drawn every day. Using $P(\lvert Z \rvert > 2) = 0.0456$ and $P(\lvert Z \rvert > 3) = 0.0027$, find the expected number of days until the first sample outside $2\sigma$, and outside $3\sigma$.

(b) Find the probability of no day outside $3\sigma$ during a 365-day year.

(c) In manufacturing, a process with tolerance $\pm 6\sigma$ is often assumed to drift by $1.5\sigma$ from its target. Given $P(Z > 4.5) \approx 3.4 \times 10^{-6}$, find the defect rate, and explain why the other tail is negligible.

(d) For $a > 0$, show that $P(Z > a) \le \phi(a)/a$, by bounding $1 \le z/a$ inside the integral. Evaluate the bound at $a = 3$ and $a = 6$, given $\phi(3) = 4.432 \times 10^{-3}$ and $\phi(6) = 6.076 \times 10^{-9}$. Compare with the true values $1.350 \times 10^{-3}$ and $9.866 \times 10^{-10}$.

### Problem 11. A bound for every distribution

**Tests:** a general deviation inequality, its tightness. **Time:** 15 min.

(a) For any $X$ with mean $\mu$ and variance $\sigma^2$, and any $\alpha > 0$, show that $P(\lvert X - \mu \rvert \ge \alpha\sigma) \le 1/\alpha^2$. Start from $\sigma^2 = E[(X - \mu)^2]$, and keep only the part of the expectation where $\lvert X - \mu \rvert \ge \alpha\sigma$.

(b) For $\alpha > 1$, find a distribution with three spikes that attains this bound with equality.

(c) Compare the bound with the normal value at $\alpha = 2$ and $\alpha = 3$, using the table.

(d) Why can the bound not be improved for general distributions, even though it is so loose for the normal?

### Problem 12. Looking at many measurements

**Tests:** extremes of independent normals, multiple looks at data. **Time:** 20 min.

Let $Z_1, \dots, Z_n$ be independent standard normals.

(a) Show that $P(\max_i Z_i \le z) = \Phi(z)^n$.

(b) For $n = 10$, find $P(\max_i Z_i \le 2)$.

(c) For $n = 10$, find the median of $\max_i Z_i$. You may use $2^{-1/10} = 0.9330$, and read off the closest value in the table.

(d) You check 20 independent measurements, each normal. Using $P(\lvert Z \rvert \le 2) = 0.9544$, find the probability that at least one lies outside $2\sigma$, and the expected number that do.

(e) What does (d) say about one "surprising" $2\sigma$ result among many checks?
