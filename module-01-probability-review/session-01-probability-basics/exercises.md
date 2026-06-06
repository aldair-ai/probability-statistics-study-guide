# Session 1 Exercises: Probability Basics

Solve these by hand, exam style, without code. Give probabilities as exact fractions. Unless a problem says otherwise, dice are fair six-sided dice, decks are standard 52-card decks that are well shuffled, and "at random" means every possible choice is equally likely.

Worked solutions are in [solutions.md](solutions.md).

| Tier | Problems | Suggested total time |
|---|---|---|
| Warm-up | 1-4 | 28 min |
| Exam-level | 5-9 | 69 min |
| Challenge | 10-12 | 60 min |

---

## Warm-up

### Problem 1. Three dice

**Tests:** sample space, equiprobable spaces, ordered outcomes with replacement. **Time:** 8 min.

Three dice are rolled.

(a) Describe a sample space $\Omega$ for this experiment and find $|\Omega|$. Is your space equiprobable? Explain.

(b) Find the probability that all three dice show the same number.

(c) Find the probability that the sum of the three dice is 6.

(d) Find the probability that the three dice show three different numbers.

### Problem 2. One card

**Tests:** events in an equiprobable space, deck as a Cartesian product. **Time:** 6 min.

One card is drawn from a deck. Find the probability that the card is:

(a) a red face card (jack, queen, or king of hearts or diamonds);

(b) a spade whose rank is a number from 2 to 10;

(c) neither a heart nor a face card.

### Problem 3. True or false

**Tests:** modeling, ordered vs unordered counting. **Time:** 6 min.

Decide whether each statement is true or false, and justify your answer in one or two sentences.

(a) A coin is tossed twice. The number of heads can be 0, 1, or 2, so each of these values has probability $1/3$.

(b) The number of different 5-card poker hands equals $\dfrac{52 \cdot 51 \cdot 50 \cdot 49 \cdot 48}{5!}$.

(c) Five dice are rolled. The number of different outcomes when the order of the dice is ignored equals $6^5 / 5!$.

(d) In an equiprobable sample space, any two events with the same number of outcomes have the same probability.

### Problem 4. Officers vs committees

**Tests:** permutations, combinations, the factor $k!$. **Time:** 8 min.

A club has 10 members, including Dana and Eli.

(a) In how many ways can the club choose a president, a vice president, and a treasurer, if no one holds two offices?

(b) In how many ways can the club choose a 3-person committee?

(c) Explain, without computing either number, why the answer to (a) is exactly 6 times the answer to (b).

(d) A 3-person committee is chosen at random. Find the probability that both Dana and Eli are on it.

---

## Exam-level

### Problem 5. A mixed committee

**Tests:** combinations, product rule, counting the opposite event. **Time:** 12 min.

A department has 7 faculty members and 5 graduate students. A 4-person committee is chosen at random from these 12 people.

(a) Find the probability that the committee has exactly 2 faculty members and 2 students.

(b) Find the probability that the committee has at least one student.

(c) Two of the faculty members, X and Y, refuse to serve together. How many 4-person committees are acceptable? What is the probability that a randomly chosen committee is acceptable?

### Problem 6. Eight people in a row

**Tests:** permutations, block method, gap method, symmetry. **Time:** 15 min.

Eight people, including Ana, Ben, and Cal, line up in a random order.

(a) Find the probability that Ana and Ben stand next to each other.

(b) Find the probability that Ana stands somewhere to the left of Ben (not necessarily next to him).

(c) Find the probability that Ana, Ben, and Cal occupy three consecutive positions, in any order.

(d) Find the probability that no two of Ana, Ben, and Cal stand next to each other.

### Problem 7. Four dice

**Tests:** ordered outcomes with replacement, product rule, nested events. **Time:** 15 min.

Four dice are rolled.

(a) Find the probability that all four numbers are different.

(b) Find the probability of *exactly one pair*: one number appears exactly twice and the other two dice show two further numbers that differ from each other (for example 3, 5, 3, 1).

(c) Find the probability that the largest number rolled is at most 4.

(d) Find the probability that the largest number rolled is exactly 4.

### Problem 8. Five-card hands

**Tests:** combinations, splitting a hand by its shape, avoiding double counting. **Time:** 15 min.

A 5-card hand is dealt from a deck. Find the probability that the hand:

(a) contains exactly two aces;

(b) contains at least one card of every suit;

(c) contains no aces and no face cards.

### Problem 9. Show that: binomial identities by counting

**Tests:** combinations, one-to-one correspondence, counting a set two ways. **Time:** 12 min.

Give counting arguments (not algebra) for each identity.

(a) For $1 \le k \le n-1$, show that $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$.

(b) Show that $\sum_{k=0}^{n} \binom{n}{k} = 2^n$.

(c) Show that $\binom{n}{k} = \binom{n}{n-k}$.

---

## Challenge

### Problem 10. Arranging STATISTICS

**Tests:** arrangements with repeated items, equiprobable modeling, block method, gap method. **Time:** 20 min.

The 10 letters of the word STATISTICS are written on 10 tiles. The tiles are shuffled and laid out in a row, producing a 10-letter word.

(a) How many different words can appear?

(b) Tiles with the same letter look identical, so several tile orders produce the same word. Explain why every different word is nevertheless equally likely.

(c) Find the probability that the three S's are next to each other.

(d) Find the probability that no two S's are next to each other.

### Problem 11. Sharing cookies

**Tests:** unordered selection with replacement, modeling, true/false with justification. **Time:** 20 min.

Ten identical cookies are shared among 4 children (Kai, Lea, Max, Noa). A *distribution* records only how many cookies each child gets, for example (Kai, Lea, Max, Noa) = (3, 3, 2, 2).

(a) How many distributions are possible if a child may receive no cookies?

(b) How many distributions give every child at least one cookie?

(c) Now the cookies are handed out one at a time, and each cookie goes to a child picked at random, so that all $4^{10}$ possible assignments (who gets the first cookie, who gets the second, and so on) are equally likely. True or false: every distribution from part (a) is then equally likely. Justify by computing the probabilities of the distributions (10, 0, 0, 0) and (3, 3, 2, 2).

### Problem 12. One ace each

**Tests:** arrangements of a full deck, symmetry, reducing to a smaller equiprobable space. **Time:** 20 min.

A deck is shuffled and dealt into four 13-card bridge hands for North, East, South, and West.

(a) How many different deals are there, where a deal records which 13 cards each named player receives?

(b) Show that the probability that each player receives exactly one ace is

$$\frac{4! \cdot 13^4}{52 \cdot 51 \cdot 50 \cdot 49},$$

and evaluate it.

(c) Give a second derivation of the same answer that looks only at the positions of the four aces in the shuffled deck.
