# Session 1 Solutions: Why Vote, the Central Binomial Term and Stirling's Approximation

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final answers are given exactly (as a fraction, or as an expression when no fraction exists) and as a decimal rounded to 4 significant digits. Try each problem first.

---

## Warm-up

### Problem 1. A small committee

**(a)** With $2n + 1$ members, you decide exactly when the other $2n$ split evenly, which has probability $a_n = \binom{2n}{n}/4^n$.

$$a_3 = \frac{20}{64} = \frac{5}{16} = 0.3125, \qquad a_4 = \frac{70}{256} = \frac{35}{128} \approx 0.2734, \qquad a_5 = \frac{252}{1024} = \frac{63}{256} \approx 0.2461.$$

**(b)** The approximation $1/\sqrt{\pi n}$ gives

$$\frac{1}{\sqrt{3\pi}} \approx 0.3257, \qquad \frac{1}{\sqrt{4\pi}} \approx 0.2821, \qquad \frac{1}{\sqrt{5\pi}} \approx 0.2523.$$

**(c)** It is above the exact value in all three cases, by about 4.2%, 3.2%, and 2.5%. Problem 11 proves that it is always above.

**Key idea:** the event is an even split of the others, so the answer is a central binomial term.

### Problem 2. Testing Stirling by hand

**(a)**

$$5! \approx \sqrt{10\pi}\left(\frac{5}{e}\right)^5 = 5.605 \cdot \frac{3125}{148.413} \approx 118.0, \qquad \text{relative error } 1 - \frac{118.02}{120} \approx 1.65\%.$$

$$10! \approx \sqrt{20\pi}\left(\frac{10}{e}\right)^{10} = 7.927 \cdot \frac{10^{10}}{22026.47} \approx 3{,}598{,}696, \qquad \text{relative error } 1 - \frac{3{,}598{,}696}{3{,}628{,}800} \approx 0.83\%.$$

The relative error roughly halves as $n$ doubles, which fits the known first-order error $1/(12n)$.

**(b)** With $n = 10$:

$$\binom{20}{10} \approx \frac{4^{10}}{\sqrt{10\pi}} = \frac{1{,}048{,}576}{5.605} \approx 187{,}079.$$

The relative error is $187{,}079/184{,}756 - 1 \approx 1.26\%$ above the exact value.

**Key idea:** Stirling is excellent in ratio, even at small $n$.

### Problem 3. True or false

**(a) False.** It is about $1/\sqrt{\pi n}$, which is far larger. For $n = 3200$, this is about $1/100$ rather than $1/6401$.

**(b) True.** Your vote is decisive among $2n + 1$ voters exactly when the other $2n$ would tie by themselves, and both events have probability $b_{1/2,\,2n}(n)$.

**(c) True.** "Decisive" is a statement about the count of the others, which has nothing to do with the value of $p$. Only the probability of that event changes, not the event itself.

**(d) False.** The probability scales as $1/\sqrt{n}$, so doubling the electorate divides it by $\sqrt{2} \approx 1.41$.

**(e) False.** The ratio tends to 1, but the difference grows without bound. At $n = 10$, the difference is already about $30{,}104$. Relative error shrinks while absolute error grows.

**(f) False.** Each step changes the parity of the position, so after an odd number of steps the position is odd. It cannot be 0.

**Key idea:** the event, the probability, and the kind of error are three separate questions.

### Problem 4. How many voters?

**(a)** Solve $1/\sqrt{\pi n} = \varepsilon$, so $n = 1/(\pi \varepsilon^2)$.

- $\varepsilon = 0.01$: $n = 10^4/\pi \approx 3183$, so about $2n + 1 \approx 6{,}367$ voters.
- $\varepsilon = 0.001$: $n = 10^6/\pi \approx 318{,}310$, so about $636{,}621$ voters.

**(b)** Here $n = 1{,}500{,}000$, so

$$P(\text{decide}) \approx \frac{1}{\sqrt{1{,}500{,}000\,\pi}} \approx 4.607 \times 10^{-4},$$

or about 1 in 2,171. This is about 1,382 times larger than $1/N \approx 3.333 \times 10^{-7}$.

**(c)** Since the probability scales as $1/\sqrt{n}$, a factor of 10 in the probability needs a factor of **100** in the electorate.

**Key idea:** because of the square root, big changes in probability need much bigger changes in population.

---

## Exam-level

### Problem 5. A recursion for the central term

**(a)** Use $\binom{2n+2}{n+1} = \dfrac{(2n+2)(2n+1)}{(n+1)^2}\binom{2n}{n}$. Then

$$\frac{a_{n+1}}{a_n} = \frac{1}{4} \cdot \frac{(2n+2)(2n+1)}{(n+1)^2} = \frac{2(n+1)(2n+1)}{4(n+1)^2} = \frac{2n+1}{2n+2}.$$

**(b)** The ratio is below 1, so $a_n$ is strictly decreasing. Starting from $a_0 = 1$:

$$a_1 = \tfrac{1}{2} = 0.5, \quad a_2 = \tfrac{3}{8} = 0.375, \quad a_3 = \tfrac{5}{16} = 0.3125, \quad a_4 = \tfrac{35}{128} \approx 0.2734, \quad a_5 = \tfrac{63}{256} \approx 0.2461.$$

**(c)** Telescope from $a_0 = 1$, using (a) with $i = n + 1$:

$$a_n = \prod_{i=1}^{n} \frac{a_i}{a_{i-1}} = \prod_{i=1}^{n} \frac{2(i-1) + 1}{2(i-1) + 2} = \prod_{i=1}^{n} \frac{2i - 1}{2i}.$$

**(d)** Two new voters multiply the probability by $(2n+1)/(2n+2) = 1 - \frac{1}{2n+2}$. For a large electorate, this is almost no change.

**Key idea:** a ratio of consecutive terms gives monotonicity and a product form at the same time.

### Problem 6. The rate without Stirling

**(a)** The inequality holds because $(2i-1)(2i+1) = 4i^2 - 1 \le 4i^2$. Square the product and replace one copy of each factor:

$$a_n^2 = \prod_{i=1}^{n} \frac{2i-1}{2i} \cdot \frac{2i-1}{2i} \le \prod_{i=1}^{n} \frac{2i-1}{2i} \cdot \frac{2i}{2i+1} = \prod_{i=1}^{n} \frac{2i-1}{2i+1} = \frac{1}{2n+1},$$

since the last product telescopes.

**(b)** For $i \ge 2$, the inequality holds because $(2i-1)^2 = 4i^2 - 4i + 1 \ge 4i^2 - 4i = 2i(2i-2)$. Keep the $i = 1$ factor separate, since $a_1 = 1/2$:

$$a_n^2 = \frac{1}{4} \prod_{i=2}^{n} \frac{2i-1}{2i} \cdot \frac{2i-1}{2i} \ge \frac{1}{4} \prod_{i=2}^{n} \frac{2i-1}{2i} \cdot \frac{2i-2}{2i-1} = \frac{1}{4} \prod_{i=2}^{n} \frac{2i-2}{2i} = \frac{1}{4} \cdot \frac{2}{2n} = \frac{1}{4n}.$$

**(c)** Taking square roots gives the result. At $n = 100$:

$$\frac{1}{2\sqrt{100}} = 0.05 \le a_{100} \le \frac{1}{\sqrt{201}} \approx 0.07053.$$

The true value $a_{100} \approx 0.05635$ lies inside the interval, and is close to $1/\sqrt{100\pi} \approx 0.05642$.

**Key idea:** telescoping proves the $1/\sqrt{n}$ rate with no asymptotics. Stirling is needed only for the exact constant.

### Problem 7. A lopsided electorate

**(a)** You decide exactly when $X = n$, where $X \sim B_{p,\,2n}$, so $P(\text{decide}) = \binom{2n}{n} p^n q^n = \binom{2n}{n} (pq)^n$. Since $\binom{2n}{n} = 4^n a_n \approx 4^n/\sqrt{\pi n}$,

$$P(\text{decide}) \approx \frac{4^n (pq)^n}{\sqrt{\pi n}} = \frac{(4pq)^n}{\sqrt{\pi n}}.$$

**(b)** $1 - 4pq = (p + q)^2 - 4pq = (p - q)^2 \ge 0$, with equality only at $p = q = 1/2$.

**(c)**

- $p = 0.51$: $4pq = 0.9996$, and $0.9996^{3200} \approx e^{-1.28} \approx 0.278$. So $P \approx 0.278 \cdot 0.00997 \approx 2.77 \times 10^{-3}$, about 1 in 361.
- $p = 0.55$: $4pq = 0.99$, and $0.99^{3200} \approx e^{-32.2} \approx 1.08 \times 10^{-14}$. So $P \approx 1.08 \times 10^{-16}$.

**(d)** The rate $1/\sqrt{\pi n}$ applies only to a truly even contest: a one-point lean costs about a factor of 3.6 here, and a five-point lean makes the event effectively impossible.

**Key idea:** the factor $(4pq)^n$ is exponential in $n$, so any fixed bias eventually dominates the $1/\sqrt{n}$.

### Problem 8. Returns of a random walk

**(a)** If $u$ of the $2n$ steps are $+1$, then $S_{2n} = 2u - 2n$. So $S_{2n} = 2k$ exactly when $u = n + k$, and $u \sim B_{1/2,\,2n}$ gives $P(S_{2n} = 2k) = \binom{2n}{n+k}/4^n$. The steps have mean 0 and variance 1 and are independent, so $E[S_{2n}] = 0$ and $V(S_{2n}) = 2n$.

**(b)** With $I_n = \mathbf{1}\lbrace S_{2n} = 0 \rbrace$, we have $R_N = \sum_{n=1}^{N} I_n$, so by linearity $E[R_N] = \sum_{n=1}^{N} P(S_{2n} = 0) = \sum_{n=1}^{N} a_n$. The $I_n$ are dependent, but linearity does not care.

**(c)** At $N = 0$, both sides are 1. Assuming the identity for $N$, Problem 5(a) gives

$$\sum_{n=0}^{N+1} a_n = (2N + 1) a_N + a_{N+1} = (2N + 2) a_{N+1} + a_{N+1} = (2N + 3) a_{N+1},$$

where we used $(2N + 1) a_N = (2N + 2) a_{N+1}$.

**(d)** Subtract the $n = 0$ term: $E[R_N] = (2N + 1) a_N - 1$. With $a_N \approx 1/\sqrt{\pi N}$,

$$E[R_N] \approx \frac{2N}{\sqrt{\pi N}} - 1 = 2\sqrt{\frac{N}{\pi}} - 1.$$

At $N = 100$, the exact value is $201 \cdot 0.05635 - 1 \approx 10.33$, and the approximation gives $2\sqrt{100/\pi} - 1 \approx 10.28$.

There are only about $\sqrt{N}$ returns because the walk typically wanders a distance of about $\sqrt{N}$ from the origin. Each time $2n$ contributes only $a_n \approx 1/\sqrt{\pi n}$, and those terms sum to order $\sqrt{N}$, not $N$.

**Key idea:** dependence does not matter for means, so $E[R_N]$ is a plain sum of central terms.

### Problem 9. How flat is the top?

**(a)**

$$\frac{P(X = n + k)}{P(X = n)} = \frac{\binom{2n}{n+k}}{\binom{2n}{n}} = \frac{n!\,n!}{(n+k)!\,(n-k)!} = \frac{n}{n+1} \cdot \frac{n-1}{n+2} \cdots \frac{n-k+1}{n+k} = \prod_{i=1}^{k} \frac{n-i+1}{n+i}.$$

**(b)** Using (a) with $k = 1$, $P(X = 11) = P(X = 9) = \frac{10}{11} a_{10}$. So

$$P(\lvert X - 10 \rvert \le 1) = a_{10}\left(1 + \frac{20}{11}\right) = \frac{31}{11} \cdot \frac{46189}{262144} = \frac{130169}{262144} \approx 0.4966.$$

Just three values out of 21 carry about half of the probability.

**(c)** At $n = 100$, $\sigma = \sqrt{50} \approx 7.1$. Values within $k = 5$ of the center have at least 78% of the peak probability, and values at $k = 10$ still have 37%. So the PMF stays comparable to the peak over a window of about $\sqrt{n}$ on each side. Beyond several multiples of $\sqrt{n}$, the factor $e^{-k^2/n}$ makes it negligible. That is why "about $\sqrt{n}$ similar values" describes the top of the distribution.

**Key idea:** the shape near the center is $e^{-k^2/n}$, and its scale is $\sqrt{n}$.

---

## Challenge

### Problem 10. Does a larger jury get it right more often?

**(a)** With two new jurors, the correct count becomes $X + W$, where $W \in \lbrace 0, 1, 2 \rbrace$. The majority of $2n + 3$ needs at least $n + 2$ correct, and the old majority needed $X \ge n + 1$.

- If $X \le n - 1$, then $X + W \le n + 1$, so the majority stays wrong.
- If $X \ge n + 2$, the majority stays right.
- If $X = n$ (wrong before), it becomes right only when both new jurors are right, with probability $p^2$.
- If $X = n + 1$ (right before), it becomes wrong only when both new jurors are wrong, with probability $q^2$.

Therefore

$$M_{n+1} - M_n = P(X = n)\,p^2 - P(X = n + 1)\,q^2.$$

Now use $P(X = n) = \binom{2n+1}{n} p^n q^{n+1}$ and $P(X = n + 1) = \binom{2n+1}{n+1} p^{n+1} q^n$, and note that the two binomial coefficients are equal:

$$M_{n+1} - M_n = \binom{2n+1}{n} \left(p^{n+2} q^{n+1} - p^{n+1} q^{n+2}\right) = \binom{2n+1}{n} (pq)^{n+1} (p - q).$$

**(b)** For $p > 1/2$, we have $p - q > 0$, so $M_n$ strictly increases. At $p = 1/2$, every difference is 0, and $M_n = 1/2$ for every jury size: more voters do not help when no one has information.

**(c)** At $p = 3/5$, $pq = 6/25$ and $p - q = 1/5$.

$$M_0 = \frac{3}{5} = 0.6, \qquad M_1 = 3 \cdot \frac{9}{25} \cdot \frac{2}{5} + \frac{27}{125} = \frac{81}{125} = 0.648, \qquad M_2 = \frac{2133}{3125} = 0.68256.$$

From the formula: $M_1 - M_0 = 1 \cdot \frac{6}{25} \cdot \frac{1}{5} = \frac{6}{125}$, and $\frac{3}{5} + \frac{6}{125} = \frac{81}{125}$. Also, $M_2 - M_1 = 3 \cdot \frac{36}{625} \cdot \frac{1}{5} = \frac{108}{3125}$, and $\frac{81}{125} + \frac{108}{3125} = \frac{2133}{3125}$.

**Key idea:** the outcome changes only when the pre-existing jury is one vote from flipping, which is the decisive event again.

### Problem 11. How good is $1/\sqrt{\pi n}$?

**(a)** Using Problem 5(a),

$$\frac{c_{n+1}^2}{c_n^2} = \frac{(2n+1)^2}{(2n+2)^2} \cdot \frac{n+1}{n} = \frac{(2n+1)^2}{4n(n+1)} = \frac{4n^2 + 4n + 1}{4n(n+1)} = 1 + \frac{1}{4n(n+1)}.$$

This exceeds 1, so $c_n$ is strictly increasing. Its limit is $1/\sqrt{\pi}$, so $c_n < 1/\sqrt{\pi}$ for every $n$, which is the same as $a_n < 1/\sqrt{\pi n}$.

**(b)** Write the limit as an infinite product. Since $1/\pi = \lim_{m \to \infty} c_m^2$,

$$\frac{1}{\pi c_n^2} = \prod_{m=n}^{\infty} \frac{c_{m+1}^2}{c_m^2} = \prod_{m=n}^{\infty} \left(1 + \frac{1}{4m(m+1)}\right).$$

Take logarithms, use $\ln(1 + x) \le x$, and telescope with $\frac{1}{m(m+1)} = \frac{1}{m} - \frac{1}{m+1}$:

$$\ln \frac{1}{\pi c_n^2} \le \sum_{m=n}^{\infty} \frac{1}{4m(m+1)} = \frac{1}{4n}.$$

**(c)** From (b), $c_n \ge e^{-1/(8n)}/\sqrt{\pi}$. Dividing by $\sqrt{n}$ gives $a_n \ge e^{-1/(8n)}/\sqrt{\pi n}$. The upper bound is (a).

**(d)** The lower bound at $n = 10$ is $0.98758 \cdot 0.17841 \approx 0.17619$, while $a_{10} \approx 0.17620$. The two agree to four decimal places. To first order, $e^{-1/(8n)} \approx 1 - \frac{1}{8n}$, so **the relative error is about $\frac{1}{8n}$**, which is $1.25\%$ at $n = 10$. This matches the "about 1% above" on the slide.

**Key idea:** the correct $\sqrt{n}$ scaling makes the sequence monotone, and telescoping turns that into an explicit error bound.

### Problem 12. A two-tier election

**(a)** Your vote changes your district's delegate exactly when the other $2n$ voters in your district split evenly, with probability $a_n$. That delegate changes the final decision exactly when the other $m - 1$ delegates split evenly. The delegates of other districts are independent fair coins, by symmetry, and are independent of your district. So that event has probability $a_{(m-1)/2}$, and the product rule gives $a_n \cdot a_{(m-1)/2}$.

**(b)** The approximations give

$$P_{\text{two-tier}} \approx \frac{1}{\sqrt{\pi n}} \cdot \frac{1}{\sqrt{\pi (m-1)/2}}.$$

A direct vote among $N = m(2n + 1)$ voters has half-size $(N - 1)/2 \approx mn$ for large $n$, so $P_{\text{direct}} \approx 1/\sqrt{\pi m n}$. Their ratio is

$$\frac{P_{\text{two-tier}}}{P_{\text{direct}}} \approx \frac{\sqrt{\pi m n}}{\pi \sqrt{n (m-1)/2}} = \sqrt{\frac{2m}{\pi (m-1)}} \to \sqrt{\frac{2}{\pi}} \approx 0.798.$$

**(c)** With $n = 50{,}000$ and $m = 51$:

$$a_{50000} \approx \frac{1}{\sqrt{50000\pi}} \approx 0.002523, \qquad P_{\text{two-tier}} \approx 0.002523 \cdot 0.11228 \approx 2.833 \times 10^{-4}.$$

For the direct vote, $N = 5{,}100{,}051$ and

$$P_{\text{direct}} \approx \frac{1}{\sqrt{\pi \cdot 2{,}550{,}025}} \approx 3.533 \times 10^{-4}.$$

The ratio is about $0.802$, close to the limit in (b).

**(d)** A decisive vote needs a tie at each level. The chance of a tie at each level scales as one over the square root of that level's size, and the sizes multiply to the total electorate. So the square roots multiply to the same $\sqrt{N}$ scale as a direct vote, and only the constant changes.

**Key idea:** $\sqrt{n}$ and $\sqrt{m}$ multiply to $\sqrt{nm}$, so tiers change the constant but not the rate.
