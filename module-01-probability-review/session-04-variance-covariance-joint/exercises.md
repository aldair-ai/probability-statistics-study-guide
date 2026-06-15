# Session 4 Exercises: Variance, Covariance, Joint Distributions

Solve these by hand, exam style, without code. Give answers as exact fractions, with decimals where they help. Unless a problem says otherwise, dice are fair six-sided dice, separate dice are independent, and every random variable has a finite variance.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 34 min |
| Exam-level | 5-9 | 67 min |
| Challenge | 10-12 | 58 min |

---

## Warm-up

### Problem 1. A carnival wheel

**Tests:** variance by definition and by shortcut, standard deviation, affine transformations. **Time:** 8 min.

A carnival wheel pays $X$ dollars, where $X = 0$ with probability $1/2$, $X = 2$ with probability $1/3$, and $X = 6$ with probability $1/6$.

(a) Find $E[X]$, then find $V(X)$ from the definition $V(X) = E[(X - \mu)^2]$.

(b) Recompute $V(X)$ as $E[X^2] - (E[X])^2$, and find $\sigma_X$.

(c) A spin costs 3 dollars. Your net gain is $G = X - 3$ and the operator's net gain is $H = 3 - X$. Find the mean, variance, and standard deviation of $G$ and of $H$.

(d) During a promotion, the payout is doubled but a spin costs 4 dollars. Find the mean and standard deviation of your new net gain. Is the promotion better for you on average? Is it riskier?

### Problem 2. The variance of an indicator

**Tests:** Bernoulli variance, its dependence on $p$, covariance of indicators. **Time:** 6 min.

Let $I$ be the indicator of an event $A$ with $P(A) = p$.

(a) Show that $I^2 = I$, and use this to show that $V(I) = p(1 - p)$.

(b) Show that $V(I) \le 1/4$ for every $p$, with equality only at $p = 1/2$.

(c) Find every $p$ for which $V(I) = 3/16$.

(d) Show that $\mathrm{Cov}(I, 1 - I) = -p(1 - p)$, and that $\rho_{I,\,1 - I} = -1$ when $0 < p < 1$. Explain in one sentence why $-1$ is the value you should expect.

### Problem 3. True or false

**Tests:** variance, independence vs uncorrelated, variance of sums, correlation. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences (a short proof or a counterexample).

(a) If $V(X) = 0$, then $X = E[X]$ with probability 1.

(b) If $X$ and $Y$ are independent, then $V(X - Y) = V(X) - V(Y)$.

(c) If $\mathrm{Cov}(X, Y) = 0$, then $X$ and $Y$ are independent.

(d) For all random variables $X$ and $Y$, $\sigma_{X+Y} \le \sigma_X + \sigma_Y$.

(e) If $\mathrm{Cov}(X, Y) > \mathrm{Cov}(U, W)$, then $\rho_{X,Y} > \rho_{U,W}$.

### Problem 4. Uniform over a triangle

**Tests:** uniform distribution over a support, marginals, the sign of a covariance, independence. **Time:** 10 min.

The pair $(X, Y)$ is uniform over the support

$$S = \lbrace (x, y) : x, y \in \lbrace 1, 2, 3 \rbrace,\ x + y \le 4 \rbrace.$$

(a) List the points of $S$ and find the probability of each one.

(b) Find the marginal PMFs of $X$ and of $Y$.

(c) Sketch $S$ and mark the point $(\mu_X, \mu_Y)$. Predict the sign of $\mathrm{Cov}(X, Y)$ from the sketch, then compute $\mathrm{Cov}(X, Y)$ and $\rho_{X,Y}$.

(d) Are $X$ and $Y$ independent? Justify your answer with a single cell.

---

## Exam-level

### Problem 5. Running partners

**Tests:** joint PMF from a table, marginals, covariance, correlation, variance of sums, independence. **Time:** 15 min.

Each weekend, Ana goes running on $X$ of the two days and her friend Ben on $Y$ of the two days. Over many weekends, the joint PMF of $(X, Y)$ is

| | $y = 0$ | $y = 1$ | $y = 2$ |
|---|---|---|---|
| $x = 0$ | 0.10 | 0.10 | 0 |
| $x = 1$ | 0.10 | 0.20 | 0.10 |
| $x = 2$ | 0 | 0.10 | 0.30 |

(a) Find the marginal PMFs of $X$ and $Y$.

(b) Find $E[X]$, $E[Y]$, $V(X)$, and $V(Y)$.

(c) Find $E[XY]$ and $\mathrm{Cov}(X, Y)$.

(d) Find the correlation coefficient $\rho_{X,Y}$.

(e) Let $T = X + Y$ be the total number of runs in a weekend and $D = X - Y$. Find $V(T)$ and $V(D)$ from your answers to (b) and (c). Then check $V(D)$ by finding the PMF of $D$ directly.

(f) Are $X$ and $Y$ independent?

### Problem 6. Sum and difference of two dice

**Tests:** bilinearity of covariance, uncorrelated vs independent, variance of sums. **Time:** 12 min.

(a) Show that for any random variables $X$ and $Y$, $\mathrm{Cov}(X + Y,\, X - Y) = V(X) - V(Y)$.

(b) Roll two dice $D_1$ and $D_2$, and let $S = D_1 + D_2$ and $T = D_1 - D_2$. Find $V(S)$, $V(T)$, and $\mathrm{Cov}(S, T)$.

(c) Show that $S$ and $T$ are not independent.

(d) True or false: if $V(X) = V(Y)$, then $X + Y$ and $X - Y$ are independent. Justify.

### Problem 7. Weather and drink sales

**Tests:** standardized variables, affine transformations of covariance and correlation, invariance to units. **Time:** 10 min.

For a random variable $X$ with $\sigma_X > 0$, the **standardized** variable is $Z_X = (X - \mu_X)/\sigma_X$.

(a) Show that $E[Z_X] = 0$ and $V(Z_X) = 1$.

(b) Show that $\rho_{X,Y} = E[Z_X Z_Y]$.

(c) At a beach kiosk, the daily high temperature $C$ (degrees Celsius) has mean 22 and standard deviation 4. The daily sales $S$ of iced drinks (cups) have mean 300 and standard deviation 50, and $\mathrm{Cov}(C, S) = 150$. Find $\rho_{C,S}$.

(d) The owner switches to Fahrenheit, $F = 1.8\,C + 32$, and counts sales in dozens, $D = S/12$. Find $E[F]$, $\sigma_F$, $\sigma_D$, $\mathrm{Cov}(F, D)$, and $\rho_{F,D}$.

(e) The kiosk's hot-drink sales are $H = 400 - 0.4\,S$ cups. Find $E[H]$, $\sigma_H$, $\mathrm{Cov}(C, H)$, and $\rho_{C,H}$.

### Problem 8. The smaller and the larger of two dice

**Tests:** joint distributions, LOTUS, covariance, correlation, variance of sums. **Time:** 15 min.

Roll two dice $D_1$ and $D_2$. Let $M = \min(D_1, D_2)$ and $L = \max(D_1, D_2)$.

(a) Show that $P(M = k) = \dfrac{13 - 2k}{36}$ for $k = 1, \dots, 6$, and find $E[M]$.

(b) Use the identity $M + L = D_1 + D_2$ to find $E[L]$ without finding the PMF of $L$.

(c) Show that $ML = D_1 D_2$. Use it to find $E[ML]$ and $\mathrm{Cov}(M, L)$.

(d) Find $V(M)$. Explain why $V(L) = V(M)$ (hint: $7 - D_1$ and $7 - D_2$ are also two independent fair dice). Then find $\rho_{M,L}$.

(e) Check your answers to (c) and (d) using $V(M + L) = V(D_1 + D_2)$.

### Problem 9. Combining two sensors

**Tests:** variance of a linear combination, covariance, optimization. **Time:** 15 min.

Two sensors measure the same unknown constant $\theta$. Their readings are $R_1 = \theta + \varepsilon_1$ and $R_2 = \theta + \varepsilon_2$, where the errors have mean 0, standard deviations $\sigma_1 = 1$ and $\sigma_2 = 2$, and correlation $\rho$.

(a) Find $V\big((R_1 + R_2)/2\big)$ as a function of $\rho$. For which values of $\rho$ is the plain average more precise (smaller variance) than sensor 1 alone?

(b) For a weight $t$, let $W_t = t R_1 + (1 - t) R_2$. Show that $E[W_t] = \theta$ for every $t$, and that

$$V(W_t) = t^2 \sigma_1^2 + (1 - t)^2 \sigma_2^2 + 2t(1 - t)\,\rho\,\sigma_1 \sigma_2.$$

(c) Let $\rho = 0$. Find the weight $t$ that minimizes $V(W_t)$, and the minimum variance.

(d) Let $\rho = 1/2$. Show that the best weight is $t = 1$: the second sensor does not help at all.

---

## Challenge

### Problem 10. Why $\lvert \rho \rvert \le 1$

**Tests:** proof of the correlation bounds, standardized variables, variance of sums, Cauchy-Schwarz inequality. **Time:** 20 min.

Let $X$ and $Y$ have positive variances, and let $Z_X$ and $Z_Y$ be their standardized versions (Problem 7), so that $\mathrm{Cov}(Z_X, Z_Y) = \rho_{X,Y}$, written $\rho$ below.

(a) Show that $V(Z_X + Z_Y) = 2(1 + \rho)$ and $V(Z_X - Z_Y) = 2(1 - \rho)$. Conclude that $-1 \le \rho \le 1$.

(b) Show that $\rho = 1$ if and only if $Y = aX + b$ with probability 1 for some constants $a > 0$ and $b$. (You may use Problem 3(a).) State the corresponding result for $\rho = -1$.

(c) A second proof. Let $U$ and $W$ be random variables with $E[W^2] > 0$. For every real $t$, $q(t) = E[(U - tW)^2] \ge 0$. Expand $q(t)$ as a quadratic in $t$ and use its minimum value to prove the **Cauchy-Schwarz inequality** $\big(E[UW]\big)^2 \le E[U^2]\,E[W^2]$. Apply it to $U = X - \mu_X$ and $W = Y - \mu_Y$ to show $\lvert \mathrm{Cov}(X, Y) \rvert \le \sigma_X \sigma_Y$.

(d) Suppose $\mu_X = 1$, $\sigma_X = 2$, $\mu_Y = 0$, $\sigma_Y = 3$, and $\rho = -1$. Find the constants $a$ and $b$ with $Y = aX + b$.

### Problem 11. Matching hats

**Tests:** indicator method, covariance of indicators, variance of a sum of dependent variables. **Time:** 20 min.

At a party, $n \ge 2$ guests check their hats. At the end the hats are handed back in a uniformly random order (each of the $n!$ assignments is equally likely). Let $X$ be the number of guests who get their own hat back.

(a) Write $X = I_1 + \cdots + I_n$, where $I_i$ is the indicator that guest $i$ gets their own hat. Find $E[I_i]$ and $E[X]$.

(b) For $i \ne j$, find $P(I_i = 1, I_j = 1)$, and show that $\mathrm{Cov}(I_i, I_j) = \dfrac{1}{n^2(n - 1)}$. Is the covariance positive or negative? Explain in one sentence why that sign makes sense.

(c) Show that $V(X) = 1$ for every $n \ge 2$.

(d) Check (a) and (c) for $n = 3$ by listing all six assignments.

### Problem 12. How negative can correlations be?

**Tests:** variance of a sum, correlation bounds, true/false with justification. **Time:** 18 min.

Let $X_1, \dots, X_n$ ($n \ge 2$) each have variance $\sigma^2 > 0$, and suppose every pair has the same correlation: $\rho_{X_i, X_j} = \rho$ for all $i \ne j$.

(a) Show that $V(X_1 + \cdots + X_n) = n\sigma^2\big(1 + (n - 1)\rho\big)$. Deduce that $\rho \ge -\dfrac{1}{n - 1}$.

(b) Show that the bound is attained. An urn holds $n$ balls labeled $1, \dots, n$, and one ball is drawn at random. Let $I_i$ be the indicator that ball $i$ is drawn. Find $V(I_i)$, $\mathrm{Cov}(I_i, I_j)$ for $i \ne j$, and $\rho_{I_i, I_j}$.

(c) True or false, with justification:

1. There exist three random variables whose pairwise correlations all equal $-0.6$.
2. There exist three random variables whose pairwise correlations all equal $-0.5$.
