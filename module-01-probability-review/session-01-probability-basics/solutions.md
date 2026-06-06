# Session 1 Solutions: Probability Basics

Worked solutions to [exercises.md](exercises.md), in the same numbering. Final probabilities are given as an exact fraction and a decimal (rounded to 4 significant digits). Try each problem first.

---

## Warm-up

### Problem 1. Three dice

**(a)** Record the dice in order: $\Omega = \lbrace (a, b, c) : a, b, c \in \lbrace 1, \dots, 6 \rbrace \rbrace$. By the product rule, $|\Omega| = 6 \cdot 6 \cdot 6 = 216$. Fair dice favor no ordered triple, so the space is equiprobable. (Recording only the unordered outcome, such as "two 1s and a 5", would not give an equiprobable space: {1, 1, 5} arises from 3 ordered triples, while {1, 1, 1} arises from only 1.)

**(b)** The favorable triples are $(1,1,1), (2,2,2), \dots, (6,6,6)$, so there are 6.

$$P = \frac{6}{216} = \frac{1}{36} \approx 0.02778.$$

**(c)** List the ordered triples with sum 6 by their unordered pattern:

- $\lbrace 4, 1, 1 \rbrace$: the 4 can be on any of 3 dice, so 3 triples.
- $\lbrace 3, 2, 1 \rbrace$: all different, so $3! = 6$ triples.
- $\lbrace 2, 2, 2 \rbrace$: 1 triple.

That gives $3 + 6 + 1 = 10$ triples.

$$P = \frac{10}{216} = \frac{5}{108} \approx 0.04630.$$

**(d)** Choose the numbers die by die: 6 options for the first, 5 for the second, 4 for the third, so $6 \cdot 5 \cdot 4 = 120$ triples.

$$P = \frac{120}{216} = \frac{5}{9} \approx 0.5556.$$

**Key idea:** for dice, count ordered tuples, because those are the equally likely outcomes.

### Problem 2. One card

The space is the 52 cards, equiprobable. Each event below is a "sub-grid": a set of allowed suits times a set of allowed ranks.

**(a)** 2 red suits times 3 face ranks gives $2 \cdot 3 = 6$ cards.

$$P = \frac{6}{52} = \frac{3}{26} \approx 0.1154.$$

**(b)** 1 suit times 9 ranks (2 through 10) gives 9 cards.

$$P = \frac{9}{52} \approx 0.1731.$$

**(c)** The suit must be clubs, diamonds, or spades (3 choices) and the rank must be ace or 2 through 10 (10 choices), so $3 \cdot 10 = 30$ cards.

$$P = \frac{30}{52} = \frac{15}{26} \approx 0.5769.$$

**Key idea:** "suit in $S$ and rank in $R$" is a product set with $|S| \cdot |R|$ cards.

### Problem 3. True or false

**(a) False.** The equiprobable space is $\lbrace HH, HT, TH, TT \rbrace$. Zero heads is $\lbrace TT \rbrace$, one head is $\lbrace HT, TH \rbrace$, two heads is $\lbrace HH \rbrace$, so the probabilities are $1/4 = 0.25$, $1/2 = 0.5$, $1/4 = 0.25$. The three values are outcomes of a space that is not equiprobable.

**(b) True.** The numerator counts ordered 5-card deals. Each hand can be dealt in $5! = 120$ orders, so dividing by $5!$ counts each hand once: $\binom{52}{5} = 2{,}598{,}960$.

**(c) False.** $6^5 / 5! = 7776/120 = 64.8$ is not even an integer. Dividing by $5!$ assumes every unordered outcome comes from exactly $5!$ ordered ones, which fails when values repeat (all five dice showing 1 comes from a single ordered outcome). The correct count is the number of size-5 multisets from 6 values, $\binom{6+5-1}{5} = \binom{10}{5} = 252$.

**(d) True.** In an equiprobable space, $P(E) = |E|/|\Omega|$ depends on $E$ only through $|E|$. (This fails in spaces that are not equiprobable.)

**Key idea:** dividing by $k!$ is valid only when every unordered outcome has exactly $k!$ orderings.

### Problem 4. Officers vs committees

**(a)** Ordered selection without replacement: $10 \cdot 9 \cdot 8 = 720$.

**(b)** Unordered selection without replacement: $\binom{10}{3} = \dfrac{10 \cdot 9 \cdot 8}{3!} = 120$.

**(c)** Every committee of 3 people can be turned into a slate of officers by assigning the three offices to its members, which can be done in $3! = 6$ ways. Every slate arises this way from exactly one committee (forget the titles). So the slates split into 120 groups of 6, and $720 = 6 \cdot 120$.

**(d)** A committee containing both Dana and Eli is determined by its third member, chosen from the other 8 people: 8 committees.

$$P = \frac{8}{120} = \frac{1}{15} \approx 0.06667.$$

**Key idea:** ordered count = unordered count times $k!$, because each set has $k!$ orderings.

---

## Exam-level

### Problem 5. A mixed committee

The space is all 4-person subsets of 12 people: $|\Omega| = \binom{12}{4} = 495$, equiprobable.

**(a)** Choose 2 of 7 faculty and 2 of 5 students: $\binom{7}{2}\binom{5}{2} = 21 \cdot 10 = 210$.

$$P = \frac{210}{495} = \frac{14}{33} \approx 0.4242.$$

**(b)** Count the committees with *no* student instead: all 4 members from the 7 faculty, $\binom{7}{4} = 35$. Every other committee has at least one student, so there are $495 - 35 = 460$.

$$P = \frac{460}{495} = \frac{92}{99} \approx 0.9293.$$

A common mistake is "pick one student ($5$ ways), then any 3 others ($\binom{11}{3}$ ways)", which gives $825 > 495$. A committee with two students is counted once for each student who could have been "the" chosen one.

**(c)** The unacceptable committees contain both X and Y, plus 2 of the other 10 people: $\binom{10}{2} = 45$. So $495 - 45 = 450$ committees are acceptable.

$$P = \frac{450}{495} = \frac{10}{11} \approx 0.9091.$$

**Key idea:** for "at least one" or "not both", count the opposite case and subtract from the total.

### Problem 6. Eight people in a row

The space is all orders of the 8 people: $|\Omega| = 8! = 40{,}320$, equiprobable.

**(a) Block method.** Glue Ana and Ben into one block. There are now 7 units, which can be ordered in $7!$ ways, and the block can be "Ana, Ben" or "Ben, Ana".

$$P = \frac{2 \cdot 7!}{8!} = \frac{2}{8} = \frac{1}{4} = 0.25.$$

Check: the pair of positions Ana and Ben occupy is equally likely to be any of the $\binom{8}{2} = 28$ pairs, and 7 of those are adjacent, giving $7/28 = 1/4$.

**(b)** Swapping Ana and Ben turns every order with Ana on the left into one with Ben on the left, and back. This one-to-one correspondence shows the two cases have the same size, and together they make up all of $\Omega$.

$$P = \frac{1}{2} = 0.5.$$

**(c)** Glue the three into one block: 6 units give $6!$ orders, and the block has $3!$ internal orders.

$$P = \frac{3! \cdot 6!}{8!} = \frac{6 \cdot 720}{40{,}320} = \frac{3}{28} \approx 0.1071.$$

**(d) Gap method.** First order the other 5 people: $5! = 120$ ways. They create 6 gaps (before the first person, between neighbors, after the last). Put Ana, Ben, and Cal into 3 different gaps, one per gap, which keeps them apart. Since they are distinct people, the gaps are assigned in order: $6 \cdot 5 \cdot 4 = 120$ ways.

$$P = \frac{120 \cdot 120}{40{,}320} = \frac{14{,}400}{40{,}320} = \frac{5}{14} \approx 0.3571.$$

**Key idea:** "must be together" means glue them into a block; "must be apart" means place the others first and drop them into gaps.

### Problem 7. Four dice

The space is ordered 4-tuples: $|\Omega| = 6^4 = 1296$, equiprobable.

**(a)** $6 \cdot 5 \cdot 4 \cdot 3 = 360$.

$$P = \frac{360}{1296} = \frac{5}{18} \approx 0.2778.$$

**(b)** Build the outcome in stages:

1. the value that appears twice: 6 ways;
2. which two of the four dice show it: $\binom{4}{2} = 6$ ways;
3. the remaining two dice, read left to right, get two different values, neither equal to the pair value: $5 \cdot 4 = 20$ ways.

That gives $6 \cdot 6 \cdot 20 = 720$.

$$P = \frac{720}{1296} = \frac{5}{9} \approx 0.5556.$$

Check by listing every pattern: all different 360, one pair 720, two pairs $\binom{6}{2}\binom{4}{2} = 90$, three of a kind $6 \cdot 4 \cdot 5 = 120$, four of a kind 6. Total $360 + 720 + 90 + 120 + 6 = 1296$.

**(c)** Every die must show 1 to 4: $4^4 = 256$ outcomes.

$$P = \frac{256}{1296} = \frac{16}{81} \approx 0.1975.$$

**(d)** "Largest is exactly 4" means "all dice at most 4" but not "all dice at most 3". The second set sits inside the first, so the count is $4^4 - 3^4 = 256 - 81 = 175$.

$$P = \frac{175}{1296} \approx 0.1350.$$

**Key idea:** "maximum at most $m$" is a product set of size $m^n$; "maximum exactly $m$" is the difference of two nested product sets.

### Problem 8. Five-card hands

The space is 5-card subsets: $|\Omega| = \binom{52}{5} = 2{,}598{,}960$, equiprobable.

**(a)** Choose 2 of the 4 aces and 3 of the 48 non-aces: $\binom{4}{2}\binom{48}{3} = 6 \cdot 17{,}296 = 103{,}776$.

$$P = \frac{103{,}776}{2{,}598{,}960} = \frac{2162}{54{,}145} \approx 0.03993.$$

**(b)** Five cards covering all four suits must have the shape "one suit twice, the other three suits once each". Fill that shape:

1. the doubled suit: 4 ways;
2. its two ranks: $\binom{13}{2} = 78$ ways;
3. one rank in each of the other three suits: $13^3 = 2197$ ways.

That gives $4 \cdot 78 \cdot 2197 = 685{,}464$.

$$P = \frac{685{,}464}{2{,}598{,}960} = \frac{2197}{8330} \approx 0.2637.$$

A tempting wrong count is "one card from each suit ($13^4$), then any fifth card (48)", which gives $1{,}370{,}928$, exactly twice the right answer. Each valid hand is produced twice, because either card of the doubled suit can play the role of "the fifth card".

**(c)** The allowed cards are ranks 2 through 10: $9 \cdot 4 = 36$ cards. Choose 5 of them: $\binom{36}{5} = 376{,}992$.

$$P = \frac{376{,}992}{2{,}598{,}960} = \frac{66}{455} \approx 0.1451.$$

**Key idea:** identify the shape of the hand first, then fill the shape stage by stage, so that every hand is built exactly once.

### Problem 9. Show that: binomial identities by counting

**(a)** Count the $k$-person committees from a group of $n$ people. Fix one person, Pat. Every committee either includes Pat or does not, and not both.

- With Pat: the other $k-1$ members come from the remaining $n-1$ people, $\binom{n-1}{k-1}$ ways.
- Without Pat: all $k$ members come from the remaining $n-1$ people, $\binom{n-1}{k}$ ways.

Adding the two cases counts every committee exactly once, so $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$. (Example: $\binom{5}{2} = 10 = 4 + 6$.)

**(b)** Count all subsets of an $n$-element set in two ways.

- Decide element by element whether it is in the subset: 2 choices each, so $2^n$ subsets by the product rule.
- Group the subsets by their size $k$: there are $\binom{n}{k}$ of size $k$, for $k = 0, 1, \dots, n$.

Both methods count the same collection, so $\sum_{k=0}^{n} \binom{n}{k} = 2^n$.

**(c)** Send each $k$-element subset $A$ to its complement, the $n-k$ elements not in $A$. Taking the complement again returns $A$, so this is a one-to-one correspondence between $k$-subsets and $(n-k)$-subsets, and the two collections have the same size. (Choosing the 5 cards in a hand is the same as choosing the 47 cards left in the deck.)

**Key idea:** prove an identity by counting one set in two ways, or by exhibiting a one-to-one correspondence.

---

## Challenge

### Problem 10. Arranging STATISTICS

The letters are S three times, T three times, I twice, A once, C once (10 in total).

**(a)** Order the 10 tiles in $10!$ ways, then divide out the rearrangements of identical letters, which do not change the word:

$$\frac{10!}{3! \cdot 3! \cdot 2! \cdot 1! \cdot 1!} = \frac{3{,}628{,}800}{72} = 50{,}400.$$

**(b)** The tiles are physically distinct, so all $10!$ tile orders are equally likely. A given word is produced by exactly $3! \cdot 3! \cdot 2! = 72$ tile orders: permute the three S tiles among the S positions, the three T tiles among the T positions, and the two I tiles among the I positions. Every word has the same number of tile orders behind it, so every word has probability $72/10! = 1/50{,}400$.

**(c)** Glue SSS into a single block. The units are now [SSS], T, T, T, I, I, A, C: 8 units with T repeated 3 times and I repeated twice.

$$\frac{8!}{3! \cdot 2!} = \frac{40{,}320}{12} = 3360, \qquad P = \frac{3360}{50{,}400} = \frac{1}{15} \approx 0.06667.$$

**(d)** Arrange the 7 non-S letters (T three times, I twice, A, C) first: $\dfrac{7!}{3! \cdot 2!} = 420$ ways. They leave 8 gaps. Put the three S's into 3 different gaps. The S's are identical, so only the set of gaps matters: $\binom{8}{3} = 56$ ways.

$$P = \frac{420 \cdot 56}{50{,}400} = \frac{23{,}520}{50{,}400} = \frac{7}{15} \approx 0.4667.$$

**Key idea:** distinct words are equally likely because each has the same number of tile orders behind it; then block and gap methods work as usual, dividing by repeats.

### Problem 11. Sharing cookies

**(a)** Write the 10 cookies as stars and separate the 4 children's shares with 3 bars, for example `***|***|**|**` for (3, 3, 2, 2). Each distribution is one arrangement of 10 stars and 3 bars in 13 slots, so choose the bar positions:

$$\binom{13}{3} = 286.$$

**(b)** Give every child one cookie first. The remaining 6 cookies can then be shared freely: $\binom{6+3}{3} = \binom{9}{3} = 84$.

**(c) False.** Now the equally likely outcomes are the $4^{10} = 1{,}048{,}576$ assignment sequences.

- (10, 0, 0, 0) happens only if every cookie goes to Kai: 1 sequence.

$$P = \frac{1}{1{,}048{,}576} \approx 9.537 \times 10^{-7}.$$

- (3, 3, 2, 2) happens for every sequence that names Kai 3 times, Lea 3 times, Max twice, and Noa twice: $\dfrac{10!}{3! \cdot 3! \cdot 2! \cdot 2!} = 25{,}200$ sequences.

$$P = \frac{25{,}200}{1{,}048{,}576} = \frac{1575}{65{,}536} \approx 0.02403.$$

The second distribution is 25,200 times as likely as the first, so the 286 distributions are far from equally likely.

**Key idea:** stars and bars counts multisets, but under random assignment the equally likely objects are the ordered sequences, not the multisets.

### Problem 12. One ace each

**(a)** Choose North's 13 cards, then East's from the remaining 39, then South's from the remaining 26; West gets the rest:

$$\binom{52}{13}\binom{39}{13}\binom{26}{13} = \frac{52!}{(13!)^4} = 53{,}644{,}737{,}765{,}488{,}792{,}839{,}237{,}440{,}000 \approx 5.364 \times 10^{28}.$$

**(b)** All deals are equally likely. Count the favorable ones in two stages:

1. give one ace to each player: $4!$ ways;
2. deal the 48 non-aces, 12 to each player: $\dfrac{48!}{(12!)^4}$ ways.

$$P = \frac{4! \cdot 48! / (12!)^4}{52! / (13!)^4} = 4! \cdot \left(\frac{13!}{12!}\right)^4 \cdot \frac{48!}{52!} = \frac{4! \cdot 13^4}{52 \cdot 51 \cdot 50 \cdot 49}.$$

Evaluating: $\dfrac{24 \cdot 28{,}561}{6{,}497{,}400} = \dfrac{685{,}464}{6{,}497{,}400} = \dfrac{2197}{20{,}825} \approx 0.1055$.

**(c)** Think of the shuffled deck as 52 positions: positions 1-13 go to North, 14-26 to East, 27-39 to South, 40-52 to West. For any particular set of 4 positions, the number of deck orders with the aces in exactly those positions is $4! \cdot 48!$, the same for every set. So the set of ace positions is equally likely to be any of the $\binom{52}{4} = 270{,}725$ sets. Each player gets one ace exactly when there is one ace position in each block of 13, which can happen in $13^4 = 28{,}561$ ways.

$$P = \frac{13^4}{\binom{52}{4}} = \frac{28{,}561}{270{,}725} = \frac{2197}{20{,}825} \approx 0.1055.$$

This agrees with (b) because $\binom{52}{4} = \dfrac{52 \cdot 51 \cdot 50 \cdot 49}{4!}$.

**Key idea:** when only a few cards matter, look only at their positions; symmetry makes that smaller space equiprobable.
