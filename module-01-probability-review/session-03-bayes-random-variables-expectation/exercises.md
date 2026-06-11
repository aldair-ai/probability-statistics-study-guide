# Session 3 Exercises: Bayes, Random Variables, Expectation

Solve these by hand, exam style, without code. Give probabilities and expectations as exact fractions. Unless a problem says otherwise, dice are fair six-sided dice, coins are fair, decks are standard 52-card decks that are well shuffled, and "at random" means every possible choice is equally likely.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 30 min |
| Exam-level | 5-9 | 66 min |
| Challenge | 10-12 | 60 min |

---

## Warm-up

### Problem 1. Three coins in a box

**Tests:** law of total probability, Bayes' rule. **Time:** 8 min.

A box holds three coins: a fair coin, a two-headed coin, and a bent coin that lands heads with probability $1/4$. You pick a coin at random and toss it.

(a) Find the probability that the toss lands heads.

(b) The toss lands heads. Find the probability that you picked each of the three coins.

(c) You toss the same coin a second time. Given that the first toss was heads, find the probability that the second toss is also heads. Is it equal to the answer to (a)? Explain in one sentence.

### Problem 2. Reading a CDF

**Tests:** PMF vs CDF, the difference between $<$ and $\le$, expectation. **Time:** 8 min.

A random variable $X$ has CDF

$$F(x) = \begin{cases} 0 & x < -1, \\ 1/5 & -1 \le x < 0, \\ 1/2 & 0 \le x < 2, \\ 9/10 & 2 \le x < 5, \\ 1 & x \ge 5. \end{cases}$$

(a) Sketch $F$ and find the PMF of $X$.

(b) Find $P(X = 1)$, $P(X \le 1)$, $P(0 < X \le 4)$, $P(X \ge 2)$, and $P(X > 2)$.

(c) Find $E[X]$.

### Problem 3. True or false

**Tests:** Bayes' rule, expectation, LOTUS, tail sums. **Time:** 8 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences (a short proof or a counterexample).

(a) If $P(A \mid B) = 0.9$, then $P(B \mid A) \ge 0.5$.

(b) The expected value of a random variable is always one of the values the variable can take.

(c) For every random variable $X$ with positive values, $E[1/X] = 1/E[X]$.

(d) If $X$ takes values in $\lbrace 0, 1, 2, \dots \rbrace$ and $P(X \ge i) \le 2^{-i}$ for every $i \ge 1$, then $E[X] \le 1$.

### Problem 4. A partly guessed quiz

**Tests:** Bernoulli expectation, linearity, $E[aX+b] = aE[X]+b$. **Time:** 6 min.

A quiz has 10 multiple-choice questions, each with 4 options. A student knows the answers to 6 questions and answers them correctly. On the other 4, the student guesses one option at random. Each correct answer earns 1 point and each wrong answer loses $1/3$ point. Let $C$ be the number of correct answers and $S$ the score.

(a) Find $E[C]$.

(b) Write $S$ in terms of $C$, and find $E[S]$.

(c) Show that a blind guess on a single question has expected score 0.

(d) Suppose that on each guessed question the student can first rule out one wrong option, then guesses at random among the remaining three. Find the new $E[S]$.

---

## Exam-level

### Problem 5. A rare disease

**Tests:** law of total probability, Bayes' rule, base rates. **Time:** 15 min.

A disease affects 1 in 200 people. A screening test detects the disease in 98% of people who have it (sensitivity), and gives a false positive for 3% of people who do not have it.

(a) A randomly chosen person takes the test. Find the probability that the test is positive.

(b) Find the probability that a person who tests positive has the disease. Explain in one or two sentences why the answer is so far below 98%.

(c) A person who tested positive takes the test a second time. Given the person's true status, the two results are independent. Find the probability that the person has the disease if both tests are positive.

(d) For what prevalence (fraction of people with the disease) would a single positive test make the disease exactly as likely as not?

### Problem 6. Adding a ball of the same color

**Tests:** chain rule, law of total probability, Bayes' rule, "show that". **Time:** 12 min.

An urn holds 3 red and 2 blue balls. A ball is drawn at random, its color is noted, and it is returned to the urn together with one *extra* ball of the same color. Then a second ball is drawn at random.

(a) Find the probability that the second ball is red.

(b) Given that the second ball is red, find the probability that the first ball was red.

(c) Now let the urn start with $r$ red and $b$ blue balls, with the same procedure. Show that the probability that the second ball is red is $\dfrac{r}{r+b}$, the same as for the first ball.

### Problem 7. Expectations of functions

**Tests:** LOTUS (two-step and one-step), linearity, $E[g(X)]$ vs $g(E[X])$. **Time:** 12 min.

A random variable $X$ has PMF

| $x$ | $-1$ | $0$ | $1$ | $2$ | $3$ |
|---|---|---|---|---|---|
| $p(x)$ | $1/10$ | $1/10$ | $3/10$ | $3/10$ | $1/5$ |

Let $Y = (X-1)^2$.

(a) Find $E[X]$.

(b) Find the PMF of $Y$, and use it to compute $E[Y]$ (two steps).

(c) Compute $E[Y]$ again in one step, directly from the PMF of $X$.

(d) Find $E[X^2]$, and confirm your answer to (b) by expanding $(X-1)^2$ and using linearity.

(e) Find $E[2^X]$ and compare it with $2^{E[X]}$. Which is larger?

### Problem 8. The smallest of three dice

**Tests:** expectation via tail sums, "show that", linearity. **Time:** 15 min.

(a) Let $X$ take values in $\lbrace 0, 1, 2, \dots \rbrace$. Show that $E[X] = \sum_{i=1}^{\infty} P(X \ge i)$.

(b) Three dice are rolled and $M$ is the smallest of the three numbers. Find $P(M \ge i)$ for $i = 1, \dots, 6$, and use (a) to find $E[M]$.

(c) Use your tail probabilities to find $P(M = 2)$.

(d) Let $L$ be the largest of the three numbers. Find $E[L]$ without computing any new sums. (Hint: what is the distribution of $7 - D$ when $D$ is a fair die?)

### Problem 9. Couples side by side

**Tests:** indicator method, linearity without independence. **Time:** 12 min.

Ten couples (20 people) sit down at random in a row of 20 chairs. Let $N$ be the number of couples whose two members sit next to each other.

(a) Explain briefly why computing $P(N = k)$ for every $k$ would be hard.

(b) Find $E[N]$.

(c) Repeat (b) for a round table with 20 seats, where the first and last seats are also neighbors.

(d) True or false: the indicator method works here because the events "couple $i$ sits together" are independent. Justify.

---

## Challenge

### Problem 10. Waiting for the first ace

**Tests:** tail sums, hockey-stick identity, indicator method. **Time:** 20 min.

Cards are turned over one at a time from a shuffled deck. Let $X$ be the position of the first ace (so $X \in \lbrace 1, \dots, 49 \rbrace$).

(a) Show that $P(X \ge i) = \dfrac{\binom{53-i}{4}}{\binom{52}{4}}$ for $i = 1, \dots, 49$.

(b) Use the tail-sum formula and the hockey-stick identity $\sum_{j=k}^{n} \binom{j}{k} = \binom{n+1}{k+1}$ to show that $E[X] = 53/5$.

(c) Give a second derivation with indicators: write $X - 1$ as the number of non-aces that come before every ace, and find the probability that a given non-ace does.

(d) Generalize: a deck of $n$ cards contains $k$ special cards. Show that the expected position of the first special card is $\dfrac{n+1}{k+1}$, and use it to find the expected position of the first heart in a standard deck.

### Problem 11. Records

**Tests:** indicator method, symmetry, "show that", true/false with justification. **Time:** 20 min.

A hiring manager interviews $n$ candidates in random order. All $n$ candidates have different scores, and all $n!$ interview orders are equally likely. Candidate number $i$ in the order is a *record* if their score beats everyone interviewed before them (the first candidate is always a record). Let $R$ be the number of records.

(a) For $n = 3$, list the 6 orders and find $E[R]$ directly.

(b) Show that the $i$-th candidate is a record with probability $1/i$.

(c) Show that $E[R] = 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n}$, and evaluate it for $n = 10$.

(d) True or false: with $n = 1000$ candidates, the expected number of records exceeds 10. Justify using the bound $\frac{1}{i} \le \int_{i-1}^{i} \frac{dx}{x}$ for $i \ge 2$.

### Problem 12. Three versions of the game-show host

**Tests:** Bayes' rule with several hypotheses, law of total probability, modeling assumptions. **Time:** 20 min.

A car is hidden behind one of three doors, each equally likely; goats are behind the other two. You pick door 1. The host then opens door 2 or door 3, and you may switch to the other closed door.

(a) **Informed host.** The host knows where the car is, never opens your door, and always reveals a goat. When both doors 2 and 3 hide goats, he picks one of them at random. He opens door 3. Find the probability that the car is behind door 1, and behind door 2.

(b) **Informed host with a habit.** Same as (a), except that when both doors 2 and 3 hide goats he opens door 3 with probability $q$. He opens door 3. Show that the car is behind door 1 with probability $\dfrac{q}{1+q}$, and conclude that switching is never worse than staying.

(c) **Uninformed host.** The host does not know where the car is and opens door 2 or door 3 at random. He opens door 3, and it happens to hide a goat. Show that now the car is behind door 1 with probability $1/2$.

(d) True or false: in every version, the probability that the car is behind your door stays at $1/3$ after the host acts, because the host never opens your door. Justify.
