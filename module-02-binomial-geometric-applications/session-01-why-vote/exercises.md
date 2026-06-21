# Session 1 Exercises: Why Vote, the Central Binomial Term and Stirling's Approximation

Solve these by hand, exam style, without code. Give answers as exact fractions or exact expressions, with decimals where they help. Unless a problem says otherwise, each voter picks one of two options independently and with equal probability. Notation follows the notes: $a_n = b_{1/2,\,2n}(n) = \binom{2n}{n}/4^n$, $q = 1 - p$, and Stirling's approximation is $n! \approx \sqrt{2\pi n}\,(n/e)^n$.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 33 min |
| Exam-level | 5-9 | 70 min |
| Challenge | 10-12 | 55 min |

---

## Warm-up

### Problem 1. A small committee

**Tests:** the even-split event, the exact formula, comparing exact and approximate values. **Time:** 7 min.

(a) A committee has 7 members, and you are one of them. Find the exact probability that your vote decides a yes/no question. Repeat for 9 and for 11 members.

(b) Compare each answer with $1/\sqrt{\pi n}$, where the committee has $2n + 1$ members. You may use $\sqrt{3\pi} \approx 3.070$, $\sqrt{4\pi} \approx 3.545$, and $\sqrt{5\pi} \approx 3.963$.

(c) Is the approximation above or below the exact value in these cases?

### Problem 2. Testing Stirling by hand

**Tests:** evaluating Stirling's approximation, relative error. **Time:** 8 min.

You may use $e^5 \approx 148.413$, $e^{10} \approx 22026.47$, $\sqrt{10\pi} \approx 5.605$, and $\sqrt{20\pi} \approx 7.927$.

(a) Approximate $5!$ and $10!$ with Stirling, and find each relative error.

(b) Approximate $\binom{20}{10}$ with the formula $\binom{2n}{n} \approx 4^n/\sqrt{\pi n}$, and find the relative error. The exact value is $184{,}756$.

### Problem 3. True or false

**Tests:** the even-split event, monotonicity, scaling, the meaning of an asymptotic statement. **Time:** 10 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) With $2n + 1$ fair voters, the probability that your vote decides is about $1/(2n + 1)$.

(b) The probability that your vote decides among $2n + 1$ voters equals the probability of a draw among $2n$ voters.

(c) If every voter (other than you) instead votes for option D with the same probability $p \ne 1/2$, your vote is still decisive exactly when the others split evenly.

(d) Doubling the size of a large electorate cuts the decisive probability in half.

(e) Because Stirling's approximation has ratio tending to 1, the difference $n! - \sqrt{2\pi n}\,(n/e)^n$ tends to 0.

(f) A symmetric random walk can be at 0 after 7 steps.

### Problem 4. How many voters?

**Tests:** using $1/\sqrt{\pi n}$ forward and backward, comparison with $1/N$. **Time:** 8 min.

(a) About how many voters give a 1% chance of being decisive? A 0.1% chance?

(b) A state has about 3,000,001 voters in a perfectly even race. Estimate the decisive probability, and compare it with $1/N$.

(c) By what factor must the electorate grow for the decisive probability to fall by a factor of 10?

---

## Exam-level

### Problem 5. A recursion for the central term

**Tests:** ratio of consecutive terms, monotonicity, a product formula. **Time:** 13 min.

(a) Show that $\dfrac{a_{n+1}}{a_n} = \dfrac{2n + 1}{2n + 2}$.

(b) Deduce that $a_n$ is strictly decreasing, and compute $a_1, \dots, a_5$ exactly with the recursion, starting from $a_0 = 1$.

(c) Deduce that $a_n = \displaystyle\prod_{i=1}^{n} \frac{2i - 1}{2i}$.

(d) Interpret (a) in words. By what factor does the chance of being decisive drop when two voters join a large electorate?

### Problem 6. The rate without Stirling

**Tests:** elementary inequalities on a product, a rigorous proof of the $1/\sqrt{n}$ rate. **Time:** 15 min.

Start from the product in Problem 5(c).

(a) Use $\dfrac{2i - 1}{2i} \le \dfrac{2i}{2i + 1}$ to show that $a_n^2 \le \dfrac{1}{2n + 1}$.

(b) Use $\dfrac{2i - 1}{2i} \ge \dfrac{2i - 2}{2i - 1}$ for $i \ge 2$ to show that $a_n^2 \ge \dfrac{1}{4n}$.

(c) Conclude that $\dfrac{1}{2\sqrt{n}} \le a_n \le \dfrac{1}{\sqrt{2n + 1}}$. Evaluate both bounds at $n = 100$, and compare with $1/\sqrt{100\pi} \approx 0.0564$.

### Problem 7. A lopsided electorate

**Tests:** the general binomial term, Stirling with $p \ne 1/2$, exponential decay. **Time:** 15 min.

Suppose each of the other $2n$ voters picks D independently with probability $p$, and let $q = 1 - p$.

(a) Show that $P(\text{you decide}) = \binom{2n}{n}(pq)^n$, and use Stirling to show that it is approximately $\dfrac{(4pq)^n}{\sqrt{\pi n}}$.

(b) Show that $4pq \le 1$, with equality only at $p = 1/2$.

(c) Take $n = 3200$. Evaluate the approximation at $p = 0.51$ and at $p = 0.55$. You may use $\ln(0.9996) \approx -0.0004$ and $\ln(0.99) \approx -0.01005$, and $1/\sqrt{3200\pi} \approx 0.00997$.

(d) In one sentence, what does this say about the conclusion of the notes?

### Problem 8. Returns of a random walk

**Tests:** the walk's distribution, linearity with indicators, a summation identity. **Time:** 15 min.

Let $S_m$ be a symmetric random walk started at $S_0 = 0$, with independent steps $\pm 1$.

(a) Show that $P(S_{2n} = 2k) = \binom{2n}{n+k}/4^n$ for $-n \le k \le n$, and find $E[S_{2n}]$ and $V(S_{2n})$.

(b) Let $R_N$ be the number of returns to 0 in the first $2N$ steps, that is, the number of $n \in \lbrace 1, \dots, N \rbrace$ with $S_{2n} = 0$. Use indicators to write $E[R_N]$ as a sum.

(c) Show by induction that $\displaystyle\sum_{n=0}^{N} a_n = (2N + 1)\,a_N$.

(d) Conclude that $E[R_N] = (2N + 1)a_N - 1 \approx 2\sqrt{N/\pi} - 1$. Evaluate at $N = 100$, using $a_{100} \approx 0.05635$. Why does a linear number of steps give only about $\sqrt{N}$ returns?

### Problem 9. How flat is the top?

**Tests:** ratios of binomial terms away from the center, the "about $\sqrt{n}$ similar values" claim. **Time:** 12 min.

Let $X \sim B_{1/2,\,2n}$, so $\mu = n$ and $\sigma = \sqrt{n/2}$.

(a) Show that $\dfrac{P(X = n + k)}{P(X = n)} = \displaystyle\prod_{i=1}^{k} \frac{n - i + 1}{n + i}$ for $1 \le k \le n$.

(b) Take $n = 10$. Find the exact value of $P(\lvert X - 10 \rvert \le 1)$, using $a_{10} = 46189/262144$.

(c) Take $n = 100$. It is known that the ratio in (a) is about $0.780$ at $k = 5$ and about $0.369$ at $k = 10$, while $e^{-k^2/n}$ gives $0.779$ and $0.368$. How does this support the claim in the notes that about $\sqrt{n}$ values have probability comparable to the peak?

---

## Challenge

### Problem 10. Does a larger jury get it right more often?

**Tests:** conditioning on a decisive voter pair, an exact difference formula, the role of $p > 1/2$. **Time:** 18 min.

A jury of $2n + 1$ members decides by majority. Each juror is right with probability $p > 1/2$, independently. Let $M_n$ be the probability that the majority is right.

(a) Let $X \sim B_{p,\,2n+1}$ be the number of correct jurors among the first $2n + 1$, and add two more jurors. Explain why the majority changes only when $X \in \lbrace n, n + 1 \rbrace$, and show that

$$M_{n+1} - M_n = \binom{2n + 1}{n} (pq)^{n+1} (p - q).$$

(b) Conclude that $M_n$ increases with $n$. What happens at $p = 1/2$?

(c) Compute $M_0, M_1, M_2$ exactly at $p = 3/5$, both directly and from the formula in (a).

### Problem 11. How good is $1/\sqrt{\pi n}$?

**Tests:** monotonicity of a corrected sequence, telescoping, an explicit error bound. **Time:** 20 min.

Let $c_n = a_n \sqrt{n}$. Stirling gives $c_n \to 1/\sqrt{\pi}$.

(a) Show that $\dfrac{c_{n+1}^2}{c_n^2} = 1 + \dfrac{1}{4n(n+1)}$. Deduce that $c_n$ is increasing, and therefore that $a_n < 1/\sqrt{\pi n}$ for every $n \ge 1$.

(b) Use (a), the inequality $\ln(1 + x) \le x$, and telescoping to show that $\dfrac{1}{\pi c_n^2} \le e^{1/(4n)}$.

(c) Conclude that

$$\frac{e^{-1/(8n)}}{\sqrt{\pi n}} \le a_n < \frac{1}{\sqrt{\pi n}}.$$

(d) Evaluate the lower bound at $n = 10$, using $e^{-1/80} \approx 0.98758$ and $1/\sqrt{10\pi} \approx 0.17841$. Compare it with $a_{10} \approx 0.17620$. What is the relative error of the approximation, to first order, in terms of $n$?

### Problem 12. A two-tier election

**Tests:** independence across levels, combining central terms, comparing two systems. **Time:** 17 min.

A federation has $m$ districts ($m$ odd), each with $2n + 1$ voters. Each district elects one delegate by majority, and the delegates decide by majority. All voters are fair and independent.

(a) Show that your vote decides the final result with probability $a_n \cdot a_{(m-1)/2}$.

(b) Use the approximation $a_n \approx 1/\sqrt{\pi n}$ for both factors, with $n$ large and $m$ large. Compare with a direct vote among all $N = m(2n + 1)$ voters, and show that the ratio of the two decisive probabilities tends to $\sqrt{2/\pi} \approx 0.8$.

(c) Evaluate both probabilities for $m = 51$ and $2n + 1 = 100{,}001$. You may use $a_{25} \approx 0.11228$.

(d) Explain in words why the two-tier system changes the decisive probability by only a constant factor, even though it looks very different from a direct vote.
