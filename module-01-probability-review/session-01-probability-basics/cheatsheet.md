# Session 1 Cheatsheet: Probability Basics

## The model

- **Experiment** gives one **outcome** $x$. **Sample space** $\Omega$ = all outcomes. **Event** $E \subseteq \Omega$; it occurs when the random outcome $X \in E$.
- **Probability:** $P(x) \ge 0$, $\sum_{x \in \Omega} P(x) = 1$, and $P(E) = \sum_{x \in E} P(x)$.
- **Equiprobable space:** $P(x) = \dfrac{1}{|\Omega|}$ and $P(E) = \dfrac{|E|}{|\Omega|}$. Probability becomes counting.

## Counting: choose $k$ from $n$ distinct items

| | Ordered (sequences) | Unordered (sets) |
|---|---|---|
| **With replacement** | $n^k$ | $\binom{n+k-1}{k}$ (multisets, stars and bars) |
| **Without replacement** | $\dfrac{n!}{(n-k)!}$ | $\binom{n}{k} = \dfrac{n!}{k!(n-k)!}$ |

- **Product rule:** $k$ stages with $n_1, \dots, n_k$ options give $n_1 n_2 \cdots n_k$. Also $|A \times B| = |A| \cdot |B|$.
- **Ordered to unordered:** divide by $k!$, valid only when the $k$ items are distinct.
- **Words with repeated letters:** $\dfrac{n!}{n_1! n_2! \cdots n_r!}$ for letter counts $n_1, \dots, n_r$.
- **Identities:** $\binom{n}{k} = \binom{n}{n-k}$; $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$; $\sum_{k} \binom{n}{k} = 2^n$.

## Cards and poker

52 cards = 4 suits x 13 ranks (A, 2-10, J, Q, K). Face cards: 12. The ace is high or low in straights, with no wraparound. Number of 5-card hands: $\binom{52}{5} = 2{,}598{,}960$.

| Hand | Count | Probability | Hand | Count | Probability |
|---|---|---|---|---|---|
| Straight flush | 40 | 0.00154% | Three of a kind | 54,912 | 2.11% |
| Four of a kind | 624 | 0.0240% | Two pair | 123,552 | 4.75% |
| Full house | 3,744 | 0.144% | One pair | 1,098,240 | 42.3% |
| Flush | 5,108 | 0.197% | High card | 1,302,540 | 50.1% |
| Straight | 10,200 | 0.3925% | | | |

Straight: $10 \cdot (4^5 - 4)$. Full house: $13 \binom{4}{3} \cdot 12 \binom{4}{2}$. Two pair: $\binom{13}{2} \binom{4}{2}^2 \cdot 44$.

## Which tool when

| Situation | Tool |
|---|---|
| Outcomes are symmetric (fair dice, shuffled deck) | $P(E) = \lvert E \rvert / \lvert \Omega \rvert$ |
| Dice, coins, any sampling with replacement | count **ordered** tuples ($n^k$) |
| Hands, committees, sampling without replacement | $\binom{n}{k}$, or ordered counts on top and bottom |
| Several sequential choices | product rule |
| "At least one", "not both" | count the opposite case, subtract from the total |
| Items must be together | block: glue them, multiply by internal orders |
| Items must be apart | gaps: place the others, choose gaps |
| "Maximum is exactly $m$" | $m^n - (m-1)^n$ |
| One specific item in a random $k$-subset of $n$ | symmetry: $k/n$ |
| Hand with a mixed shape (all 4 suits, 2 aces...) | choose the shape, then fill it |

## Traps

1. **Non-equiprobable $\Omega$:** sums of dice, number of heads, and unordered dice outcomes are not equally likely.
2. **Mixed conventions:** numerator and denominator must both be ordered or both be unordered.
3. **Same role vs different roles:** two pair uses $\binom{13}{2}$ (interchangeable ranks); full house uses $13 \cdot 12$ (triple rank differs from pair rank).
4. **Hidden double counting:** "one from each suit, then any fifth card" counts each hand twice.
5. **Dividing by $k!$ with repeats:** $6^5/5!$ is not an integer; use $\binom{n+k-1}{k}$ to count multisets.
