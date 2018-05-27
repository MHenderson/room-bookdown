Room Squares
================
Matthew Henderson
May 27, 2018

-   [Introduction](#introduction)
    -   [Kirkman’s Schoolgirl Problem](#kirkmans-schoolgirl-problem)
    -   [Tournaments](#tournaments)
    -   [T.G. Room, (1902-86)](#t.g.-room-1902-86)
    -   [The Galois Field](#the-galois-field)
        -   [Example](#example)
-   [A graph-theoretic approach to constructing Room squares](#a-graph-theoretic-approach-to-constructing-room-squares)
    -   [Graph factorisations](#graph-factorisations)
        -   [Example 2.1.1](#example-2.1.1)
        -   [Example 2.1.2](#example-2.1.2)
        -   [Theorem 2.1.1](#theorem-2.1.1)
    -   [Hill-Climbing Algorithm for Room Squares](#hill-climbing-algorithm-for-room-squares)
        -   [An algorithm for One-Factorisations](#an-algorithm-for-one-factorisations)
        -   [An Algorithm for Room Squares](#an-algorithm-for-room-squares)
        -   [The Room Square Generator](#the-room-square-generator)
-   [Proving the existence of Room squares](#proving-the-existence-of-room-squares)
    -   [Introduction](#introduction-1)
    -   [Starters, Adders and Cyclic Room Squares](#starters-adders-and-cyclic-room-squares)
        -   [Finding a starter](#finding-a-starter)
        -   [Finding an adder](#finding-an-adder)
    -   [Strong Starters](#strong-starters)
        -   [Theorem 3.3.1](#theorem-3.3.1)
    -   [The Mullin-Nemeth Starters](#the-mullin-nemeth-starters)
        -   [Theorem 3.4.2 \[16\]](#theorem-3.4.2-16)
        -   [Theorem 3.4.3 \[16\]](#theorem-3.4.3-16)
    -   [The Trouble with Fermat Numbers](#the-trouble-with-fermat-numbers)
        -   [Theorem 3.5.1 \[6\]](#theorem-3.5.1-6)
    -   [A Multiplication Theorem](#a-multiplication-theorem)
        -   [Theorem 3.6.1](#theorem-3.6.1)
    -   [Summary](#summary)
    -   [n-tuplication of Room squares](#n-tuplication-of-room-squares)
        -   [Theorem 3.8.1\[25\]](#theorem-3.8.125)
        -   [Lemma 3.8.1](#lemma-3.8.1)
        -   [Lemma 3.8.2](#lemma-3.8.2)
        -   [Theorem 3.8.1 \[25\]](#theorem-3.8.1-25)
-   [Balanced Room squares](#balanced-room-squares)
    -   [BIBDs and BRBs](#bibds-and-brbs)
        -   [Example 5.1.1](#example-5.1.1)
    -   [Complete Balanced Howell Rotations](#complete-balanced-howell-rotations)
    -   [Starters and Adders for BRS and CBHR](#starters-and-adders-for-brs-and-cbhr)
        -   [Theorem 5.3.1](#theorem-5.3.1)
        -   [Theorem 5.3.2](#theorem-5.3.2)
        -   [Theorem 5.3.3](#theorem-5.3.3)
        -   [Corollary 5.3.1](#corollary-5.3.1)
        -   [Theorem 5.3.4](#theorem-5.3.4)
    -   [A Multiplicative Construction for BRS](#a-multiplicative-construction-for-brs)
        -   [Lemma 5.4.1](#lemma-5.4.1)
        -   [Theorem 5.4.1](#theorem-5.4.1)
        -   [Theorem 5.4.2](#theorem-5.4.2)
    -   [Symmetric Skew Balanced Starters](#symmetric-skew-balanced-starters)
        -   [Lemma 5.5.1](#lemma-5.5.1)
        -   [Theorem 5.5.2](#theorem-5.5.2)
        -   [Lemma 5.5.2](#lemma-5.5.2)
        -   [Corollary 5.5.2](#corollary-5.5.2)
        -   [Theorem 5.5.3](#theorem-5.5.3)
        -   [Corollory 5.5.3](#corollory-5.5.3)
-   [Closing Remarks](#closing-remarks)

Introduction
============

![Thomas Penyngton Kirkman](assets/kirkman.jpg)

Kirkman’s Schoolgirl Problem
----------------------------

In 1850 Thomas Penyngton Kirkman, an English mathematician from Bolton, published the following problem in the *Lady’s and Gentleman’s Diary.*

> *Fifteen young ladies of a school walk out three abreast for seven days in succession: it is required to arrange them daily so that no two shall walk abreast more than once*

In solving this problem Kirkman discovered the following square array, which he observed was a very "curious arrangement".

<table style="width:49%;">
<caption>Kirkman’s curious arrangement</caption>
<colgroup>
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
</colgroup>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td><p>hi</p></td>
<td><p>kl</p></td>
<td><p>mn</p></td>
<td><p>op</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>il</p></td>
<td><p>mo</p></td>
<td></td>
<td><p>np</p></td>
<td><p>hk</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>no</p></td>
<td><p>hl</p></td>
<td><p>mp</p></td>
<td></td>
<td></td>
<td><p>ik</p></td>
</tr>
<tr class="even">
<td><p>lp</p></td>
<td></td>
<td><p>in</p></td>
<td><p>ko</p></td>
<td><p>hm</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>im</p></td>
<td></td>
<td><p>kp</p></td>
<td></td>
<td></td>
<td><p>lo</p></td>
<td><p>hn</p></td>
</tr>
</tbody>
</table>

The curiosity of this square is that each of the letters h, i, k, l, m, n, o, p occurs precisely once in every column and row, while in the entire square each of the letters makes a pair with every other letter exactly once. Kirkman was able to employ this square to solve his Schoolgirl Problem. To each pair in the first column he added the element 1, to each pair in the second column 2 and so on. In addition he introduced the missing triple of numbers to each row. (e.g. row one has no elements in any of the first three columns so the numbers 1,2 and 3 would not appear hence he would add the triple 123). The seven rows of unique triples then corresponded to seven days in which the elements, corresponding to schoolgirls, were paired together exactly once throughout the arrangement. Thereby solving the problem.

<table style="width:53%;">
<caption>Kirkman's Schoolgirl's Solution</caption>
<colgroup>
<col width="11%" />
<col width="8%" />
<col width="8%" />
<col width="8%" />
<col width="8%" />
<col width="8%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">Day 1</td>
<td align="center">123</td>
<td align="center">hi4</td>
<td align="center">kl5</td>
<td align="center">mn6</td>
<td align="center">op7</td>
</tr>
<tr class="even">
<td align="center">Day 2</td>
<td align="center">147</td>
<td align="center">il2</td>
<td align="center">mo3</td>
<td align="center">np5</td>
<td align="center">hk6</td>
</tr>
<tr class="odd">
<td align="center">Day 3</td>
<td align="center">156</td>
<td align="center">no2</td>
<td align="center">hl3</td>
<td align="center">mp4</td>
<td align="center">ik7</td>
</tr>
<tr class="even">
<td align="center">Day 4</td>
<td align="center">267</td>
<td align="center">lo2</td>
<td align="center">in3</td>
<td align="center">ko4</td>
<td align="center">hm5</td>
</tr>
<tr class="odd">
<td align="center">Day 5</td>
<td align="center">245</td>
<td align="center">io2</td>
<td align="center">kp3</td>
<td align="center">lo6</td>
<td align="center">hn7</td>
</tr>
<tr class="even">
<td align="center">Day 6</td>
<td align="center">357</td>
<td align="center">ho2</td>
<td align="center">km2</td>
<td align="center">ln4</td>
<td align="center">ip6</td>
</tr>
<tr class="odd">
<td align="center">Day 7</td>
<td align="center">346</td>
<td align="center">ko2</td>
<td align="center">hp2</td>
<td align="center">io5</td>
<td align="center">lm7</td>
</tr>
</tbody>
</table>

Kirkman was a notable mathematician who is often regarded as the originator of the object in Figure 2, which has subsequently become known as a Room square (after T.G. Room).

Tournaments
-----------

Suppose the English Football Association proposed hosting a new type of international tournament to be staged as a one-off event in England. This tournament would involve eight national sides competing in a league that would be staged in various stadia around the country over two weeks. The structure of the tournament would be such that every team played every other team once, with the winner being the team which accumulated most points in the manner of a normal football league (3 points for a win, 1 for a draw).

To know which matches need playing is simple. Suppose the eight invited teams are:

<table style="width:29%;">
<caption>Teams</caption>
<colgroup>
<col width="16%" />
<col width="12%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">Argentina</td>
<td align="center">England</td>
</tr>
<tr class="even">
<td align="center">Brazil</td>
<td align="center">France</td>
</tr>
<tr class="odd">
<td align="center">Columbia</td>
<td align="center">Germany</td>
</tr>
<tr class="even">
<td align="center">Denmark</td>
<td align="center">Holland</td>
</tr>
</tbody>
</table>

If we write matches as alphabetic pairs in the obvious way, (e.g. ab denoting Argentina versus Brazil). The complete list of matches (the match set, M) is simply all unordered pairs from team set, T:
*T* = {*a*, *b*, *c*, *d*, *e*, *f*, *g*, *h*}.
 i.e.

*M* = {*a**b*, *a**c*, *a**d*, *a**e*, *a**f*, *a**g*, *a**h*, *b**c*, *b**d*, *b**e*, *b**f*, *b**g*, *b**h*, *c**d*, *c**e*, *c**f*, *c**g*, *c**h*, *d**e*, *d**f*, *d**g*, *d**h*, *e**f*, *e**g*, *e**h*, *f**g*, *f**h*, *g**h*}

It remains to be decided where and when the matches will be played.

The English F.A., for whatever reason (the financial cost of hosting eight teams, for example), has imposed a time limit of two weeks on the tournament. Realistically the treams can only manage to play on alternate days so it is decided to have, in effect, seven different "rounds" with each team competing once in each round. (Seven being the smallest number of rounds because each team has to play seven others).

For reasons of fairness the F.A. also demands the condition that each team will play once at each stadium. Can such a tournament exist? Suppose the stadia used are the following:

<table style="width:25%;">
<caption>Stadium</caption>
<colgroup>
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">Wembley</td>
</tr>
<tr class="even">
<td align="center">Highbury</td>
</tr>
<tr class="odd">
<td align="center">Villa Park</td>
</tr>
<tr class="even">
<td align="center">Stadium of Light</td>
</tr>
<tr class="odd">
<td align="center">Stamford Bridge</td>
</tr>
<tr class="even">
<td align="center">Old Trafford</td>
</tr>
<tr class="odd">
<td align="center">St. James Park</td>
</tr>
</tbody>
</table>

Then figure 4 provides a match schedule which is suitable for such a tournament.

<table style="width:61%;">
<caption>Fixture List for an International Soccer League</caption>
<colgroup>
<col width="12%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
</colgroup>
<thead>
<tr class="header">
<th align="center"> </th>
<th align="center">1</th>
<th align="center">2</th>
<th align="center">3</th>
<th align="center">4</th>
<th align="center">5</th>
<th align="center">6</th>
<th align="center">7</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="center"><strong>1</strong></td>
<td align="center"></td>
<td align="center"></td>
<td align="center"></td>
<td align="center">ab</td>
<td align="center">cd</td>
<td align="center">ef</td>
<td align="center">gh</td>
</tr>
<tr class="even">
<td align="center"><strong>2</strong></td>
<td align="center"></td>
<td align="center">bd</td>
<td align="center">eg</td>
<td align="center"></td>
<td align="center">fh</td>
<td align="center">ah</td>
<td align="center"></td>
</tr>
<tr class="odd">
<td align="center"><strong>3</strong></td>
<td align="center"></td>
<td align="center">fg</td>
<td align="center">ad</td>
<td align="center">eh</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">bc</td>
</tr>
<tr class="even">
<td align="center"><strong>4</strong></td>
<td align="center">dh</td>
<td align="center"></td>
<td align="center">bf</td>
<td align="center">cg</td>
<td align="center">ae</td>
<td align="center"></td>
<td align="center"></td>
</tr>
<tr class="odd">
<td align="center"><strong>5</strong></td>
<td align="center">be</td>
<td align="center"></td>
<td align="center">ch</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">bg</td>
<td align="center">af</td>
</tr>
<tr class="even">
<td align="center"><strong>6</strong></td>
<td align="center">ag</td>
<td align="center">ce</td>
<td align="center"></td>
<td align="center">df</td>
<td align="center"></td>
<td align="center">bh</td>
<td align="center"></td>
</tr>
<tr class="odd">
<td align="center"><strong>7</strong></td>
<td align="center">cf</td>
<td align="center">ah</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">bg</td>
<td align="center"></td>
<td align="center">de</td>
</tr>
</tbody>
</table>

Looking along the rows, each team plays once in each round. Looking down columns, each stadia hosts each team exactly once. And throughout the tournament as a whole each pair from the original match list appears exactly once, hence every team opposes every other team once. Figure 4 is another Room square of side 7. Alternatively, because the pairs are made from a set containing 8 elements, we say that this is a Room square of order 8.

T.G. Room, (1902-86)
--------------------

In 1955, Thomas Gerald Room, then Professor of Mathematics at the University of Sydney, published a brief note in the Mathematical Gazette entitled *A new type of magic square*.\[20\] In it he presented another example of a square array with the same properties as Kirkman’s. This square, Room explained, had been discovered as "a by-product of another investigation". It was preceded in the note by a particularly efficient statement of the properties of these squares, which have subsequently been known by his name.

> "The problem is to arrange the *n*(2*n* − 1) symbols *r**s* (which is the same as *s**r*) formed from all pairs of 2*n* digits such that in each row and each column there appear *n* symbols (and *n* − 1 blanks) which among them contain all 2*n* digits."

Room’s note went on to explain that while the trivial *n* = 1 Room square exists[1] , the non-existence of those with *n* = 2 (side 2) and *n* = 3 (side 5) is easily proven. Room considered the *n* = 2 proof so straightforward that it was omitted from this note, while for the *n* = 3 case he made reference to a graph-theoretic proof.

Consider the *n* = 2 case, we are required to place all the pairs of 4 digits in a 3x3 array. If we choose to use the set of non-negative integers {0, 1, 2, 3}, then we need to find somewhere to put each of the pairs {01, 02, 03, 12, 13, 23}. That we can swap the rows and columns of a Room square without damaging that square’s Room-ness is self-evident. Therefore there is no less of generality in assuming that a 3 × 3 Room square has the pair {0, 1} in cell (1, 1).

<table style="width:6%;">
<colgroup>
<col width="5%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">01</td>
</tr>
</tbody>
</table>

If we hope to make this array a Room square we must place the pair {2, 3} in the first row, while to complete the first column we must also place the same pair in either position (1, 2) or (1, 3), but each pair is only allowed to appear once. So there is no Room square of side 3, order 4.

For the *n* = 3, a Room square of side 5, case we consider the following array:

<table style="width:32%;">
<colgroup>
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="5%" />
<col width="5%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">01</td>
<td align="center">23</td>
<td align="center">45</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
<tr class="even">
<td align="center">24</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
<tr class="odd">
<td align="center">35</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
</tbody>
</table>

There is no loss in generality in using this array because we can reorder rows and columns to obtain the first row in this form and then the first column must contain either the pairs {01, 24, 35} or {01, 25, 34} and the latter can be converted into the former by the permutation (45)[2] which leaves the first row unchanged. We now show that completion of this square is impossible. The pairs {2, 5},{3, 4} must appear somewhere in the array other than the first three rows or columns. Also they must appear in separate rows/columns to prevent a forced recurrence of {0, 1}. Suppose we put {2, 5} in (4, 4) and {3, 4} in (5, 5), then we know that cells (4, 5) and (5, 4) are empty, as the only pair which could legally go in either would be {0, 1}.

Hence we know that cells (4, 2),(4, 3),(5, 2),(5, 3) each contain pairs. Take cell (5, 2), it could only contain {0, 5} or {1, 5}, and the latter becomes the former under (01), so assume it contains {0, 5}. We are now forced to fill in the other cells to give the array in Figure 8.

<table style="width:35%;">
<colgroup>
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="center">01</td>
<td align="center">23</td>
<td align="center">45</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
<tr class="even">
<td align="center">24</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
<tr class="odd">
<td align="center">35</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
<td align="center">-</td>
</tr>
<tr class="even">
<td align="center">-</td>
<td align="center">14</td>
<td align="center">03</td>
<td align="center">25</td>
<td align="center">-</td>
</tr>
<tr class="odd">
<td align="center">-</td>
<td align="center">05</td>
<td align="center">12</td>
<td align="center">-</td>
<td align="center">34</td>
</tr>
</tbody>
</table>

We still need to place the pairs {0, 2} and {0, 4}, which cannot be done because neither can appear in the second row and they cannot both appear in the third row. Hence there is no Room square of side 5, order 6.

The real significance of Room’s note was that mathematicians soon took on the task of determining the spectra of Room squares (those values of *n* for which Room squares exist). Research which cumulated 19 years later in the complete statement of the existence of Room squares, made by W.D. Wallis, that:

> *"Room squares exist for all odd positive integer sides except 3 and 5"* \[24\]

Proving this statement, which was suspected to be true from an early stage, turned out to be protracted and difficult.

The most significant breakthrough came in 1968 when Stanton and Mullin introduced the starter-adder method for constructing Room squares. This method reduces the problem of constructing Room squares to the problem of finding a certain type of initial row from which a Room square can be developed straightforwardly.

In this work much emphasis will be placed upon the proof of the existence of Room squares.

The Galois Field
----------------

Throughout this work much use will be made of a particular *finite field*, known as the Galois field, denoted by *G**F*(*p*<sup>*n*</sup>). Whenever *p*<sup>*n*</sup> is a prime (i.e. *n* = 1) the Galois field is precisely the integers under modulo p arithmetic, denoted *Z*<sub>*p*</sub>. The Galois field has a number of important properties which are used in many of the proofs that follow, we introduce some of these now.

-   Every Galois field (every finite field in fact) has a *primitive element*. An element, *x* say, is primitive in *G**F*(*q*) if *x*<sup>0</sup>, *x*<sup>1</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 1</sup> are all the non-zero members of *G**F*(*q*).

### Example

*x* = 2 is a primitive element in *G**F*(11) because,
$$x^0 = 1 \\hspace{0.5cm} x^1 = 2 \\hspace{0.5cm} x^2 = 4 \\hspace{0.5cm} x^3 = 8 \\hspace{0.5cm} x^4 = 5$$
$$x^5 = 10 \\hspace{0.5cm} x^6 = 9 \\hspace{0.5cm} x^7 = 7 \\hspace{0.5cm} x^8 = 3 \\hspace{0.5cm} x^9 = 6$$

-   It can be shown \[3\] that *x*<sup>*q* − 1</sup> = 1 is always true for any *G**F*(*q*) where *q* is odd, and *x*<sup>*i*</sup> ≠ 1 for any 1 ≤ *i* ≤ *q* − 1

-   *x*<sup>*q* − 1</sup> = 1 implies that $(x^{\\frac{1}{2}(q-1)}-1)(x^{\\frac{1}{2}(q-1)}+1)=0$, therefore either $x^{\\frac{1}{2}(q-1)}=1$ or $x^{\\frac{1}{2}(q-1)}=-1$. Clearly because of the previous remark, only the latter can be true.

-   If *b* is a non-zero residue modulo *p*, then *b* is a quadratic residue (or square) if *x*<sup>2</sup> ≡ *b*(mod *p*) has solutions, otherwise *b* is a quadratic non-residue (or non-square). So the non-zero squares are precisely the even powers of the primitive element, while the non-zero non-squares are the odd powers.

-   There are precisely $\\frac{1}{2}(p-1)$ squares mod *p*, and $\\frac{1}{2}(p-1)$ non-squares.

-   −1 is a square if *q* ≡ 1(mod 4), but not a square for *q* ≡ 3(mod 4)

    -   *q* ≡ 1(mod 4), then if *x*<sup>*i*</sup> is a square so is −*x*<sup>*i*</sup>.

    -   *q* ≡ 3(mod 4), then *x*<sup>*i*</sup> is a square −*x*<sup>*i*</sup> is a non-square.

A graph-theoretic approach to constructing Room squares
=======================================================

Graph factorisations
--------------------

A graph *G*(*V*, *E*) consists of two sets. The first *V*, is called the vertex-set, while the other *E* consists of unordered pairs of *V* and is called the edge set. Usually graphs are represented with diagrams where the members of *V* are drawn as points and the members of *E* as lines connecting points. Adjacency for two vertices means being connected by an edge. The **complete graph** *K*<sub>*n*</sub> is the graph on *n* vertices in which all distinct vertices are adjacent.

![*K*<sub>4</sub> and *K*<sub>5</sub>](README_files/figure-markdown_github/unnamed-chunk-9-1.png)

A **one-factor** *f*<sub>*i*</sub> is a set of edges in which each vertex appears exactly once.

#### Example 2.1.1

Two possible one-factors of *K*<sub>4</sub> are:
*f*<sub>1</sub> = {12, 34},*f*<sub>2</sub> = {13, 24}
 **Figure 10 Two one-factors of *K*<sub>4</sub>**

A **one-factorisation** of the complete graph is a set of one-factors in which all possible edges (i.e. all unordered pairs from the edge-set) appear exactly once.

![*K*<sub>6</sub>](README_files/figure-markdown_github/unnamed-chunk-10-1.png)

#### Example 2.1.2

Here *G* = *K*<sub>6</sub> the complete graph on 6 vertices with
*V* = {1, 2, 3, 4, 5, 6}
*E* = {12, 13, 14, 15, 16, 23, 24, 25, 26, 34, 35, 36, 45, 46, 56}
 The one-factors are
$$f\_1 = \\{12, 35, 46\\} \\hspace{0.5cm} f\_2 = \\{14, 23, 56\\} \\hspace{0.5cm} f\_3 = \\{16, 25, 34\\} 
\\hspace{0.5cm} f\_4 = \\{13, 26, 45\\} \\hspace{0.5cm}  f\_5 = \\{15, 24, 36\\}$$
 because *f*<sub>1</sub> ∪ *f*<sub>2</sub> ∪ *f*<sub>3</sub> ∪ *f*<sub>4</sub> ∪ *f*<sub>5</sub> = *E* *F* = {*f*<sub>1</sub>, *f*<sub>2</sub>, *f*<sub>3</sub>, *f*<sub>4</sub>, *f*<sub>5</sub>} is a one-factorisation of *G* shown in Figure 11.

``` r
E(g)[c(1, 11, 14)]$color <- "red"
E(g)[c(3, 6, 15)]$color <- "blue"
E(g)[c(5, 8, 10)]$color <- "green"
E(g)[c(2, 9, 13)]$color <- "yellow"
E(g)[c(4, 7, 12)]$color <- "black"

plot(g, layout = layout_in_circle(g), vertex.color = "white", vertex.size = 20)
```

![One-factorisation of *K*<sub>6</sub>](README_files/figure-markdown_github/unnamed-chunk-11-1.png)

Two one factors *f* and *l* are said to be ***orthogonal*** if *f* ∩ *l* contains at most one edge. Two one-factorisations *F* and *L* are orthogonal if every one-factor in *F* is orthogonal to every one-factor in *L*.

Once again consider the square array in Figure 2. If the individual elements within the array constituted the vertex set of a graph (call it *R*) and the pairs within each box of the array were edges, we know that each row is a one-factor and each column is a one-factor (because each member of *R* occurs precisely once in each row and once in each column). Further more, because all edges from the edge-set of the complete graph (i.e. all unordered pairs from *R*) appear once within the array, we know that the rows together form a one-factorisation and the columns form another, different, one-factorisation of *K*<sub>8</sub>. Also, because any row factor intersects any column factor in only one pair (edge), all the row factors are orthogonal to all the column factors and hence the two one-factorisations are orthogonal. We have demonstrated the following theorem, given in \[8\] and proven in \[19\].

#### Theorem 2.1.1

The existence of a Room square of side *n* is equivalent to the existence of two orthogonal one-factorisations of the complete graph *K*<sub>*n* + 1</sub>.

An example is given in figure 12 based on the Room square in Figure 2.

**Figure 12 Two orthogonal one-factorisations of *K*<sub>8</sub> based on Kirkman’s square of 1850.**

Hill-Climbing Algorithm for Room Squares
----------------------------------------

The idea behind Hill-climbing algorithms is to suppose there exists a **neighbourhood** of feasible solutions to some problem **instance**. With each **feasible** solution there is an associated **cost** (or profit) and finding an optimal solution becomes a matter of finding the solution with minimum cost (or maximum profit).

A hill-climbing algorithm non-deterministically selects a solution from the neighbourhood system such that the cost is less than that of some initial solution until its procedure fails, hence finding the locally optimal solution.

### An algorithm for One-Factorisations

Consider how to find a one-factorisation of the complete graph. Here the problem instance is simply the even integer *n* and vertex set *V*.
Recall:

-   A one-factor of *K*<sub>*n*</sub> is a set of *n*/2 edges (hence *n* is even) which partition *V*.

-   A one-factorisation of *K*<sub>*n*</sub> is a set of *n* − 1 one-factors which partitions the edge set of *K*<sub>*n*</sub>.

Suppose we choose to represent a one-factorisation by a set of $\\frac{n}{2}(n-1)=(n^2-n)/2$ pairs each of the form (*f*<sub>*i*</sub>, {*x*, *y*}), where *x* ≠ *y*, *i* = 1...*n* − 1, and the following two conditions hold.

1.  Every {*x*, *y*} occurs in a unique pair (*f*<sub>*i*</sub>, {*x*, *y*}).

2.  For every one-factor *f*<sub>*i*</sub> and every vertex *x*, there is a unique pair of the form (*f*<sub>*i*</sub>, {*x*, *y*}).

where *f*<sub>*i*</sub>s are one-factors.

Then we consider a feasible solution to be a partial one-factorisation, again represented by pairs having the same form but this time,

1.  Every {*x*, *y*} occurs in at most one pair *f*<sub>*i*</sub>, {*x*, *y*}).

2.  For every one-factor *f*<sub>*i*</sub> and every vertex *x* there is at most one pair of the form (*f*<sub>*i*</sub>, {*x*, *y*}).

Where the *f*<sub>*i*</sub>s are **partial one-factors**.

Which enables a definition for the cost of a feasible solution *F* to be given by:
*c*(*F*)=(*n*<sup>2</sup> − *n*)/2 − |*F*|
 So that *F* is a one-factorisation if and only if *c*(*F*)=0, i.e. |*F*|=(*n*<sup>2</sup> − *n*)/2

Now suppose that we can implement some procedure *X*, say, which either reduces the cost or leaves it unaffected (i.e. it never increases the cost) then the following "hill-climbing" algorithm, provided it terminates, will find a one-factorisation.

|                  |     |
|:-----------------|-----|
| While *c*(*F*)≠0 |     |
| Do *X*           |     |

A procedure such as *X* is called a heuristic. The following two heuristics (due to Dinitz & Stinson \[9\]) when used together are suitable for finding a one-factorisation.

Let *F* be a partial one-factorisation of *K*<sub>*n*</sub>:

Heuristic *H*<sub>1</sub> \[8\]

1.  Choose any vertex *x* such that *x* does not occur in every partial one-factor of *F* (such a vertex is said to be a **live point**).

2.  Choose any partial one-factor *f*<sub>*i*</sub> such that *x* does not occur in *f*<sub>*i*</sub>.

3.  Choose any *y* ≠ *x* such that there is no partial one-factor *f*<sub>*j*</sub> for which (*f*<sub>*j*</sub>, {*x*, *y*}) ∈ *F* (we say that *x* and *y* *do not occur together*).

4.  **if** *y* does not occur in *f*<sub>*i*</sub>, **then**

5.  $\\hspace{1cm}$ Replace *F* with *F* ∪ {(*f*<sub>*i*</sub>, {*x*, *y*})}.

6.  **Else** there is a pair in *F* of the form $(f\_i,\\{z,y\\}) \\hspace{0.5cm} (z \\neq x)$

7.  $\\hspace{1cm}$ Replace *F* with *F* ∪ {(*f*<sub>*i*</sub>, {*x*, *y*})}∖{(*f*<sub>*i*</sub>, {*z*, *y*})}.

Heutistic *H*<sub>2</sub> \[8\]

1.  Choose any partial one-factor *f*<sub>*i*</sub> which does not occur in exactly *n*/2 pairs in *F* (such a partial one-factor is said to be ***live***).

2.  Choose any *x* and *y* such that *x* and *y* do not occur together in *f*<sub>*i*</sub>.

3.  **if** *x* and *y* do not occur together, **then**

4.  $\\hspace{1cm}$ Replace *F* with *F* ∪ {(*f*<sub>*i*</sub>, {*x*, *y*})}.

5.  **Else** there is a pair in *F* of the form $(f\_j,\\{x,y\\}) \\hspace{0.5cm} (j \\neq i)$

6.  $\\hspace{1cm}$ Replace *F* with *F* ∪ {(*f*<sub>*i*</sub>, {*x*, *y*})}∖{(*f*<sub>*j*</sub>, {*x*, *y*})}.

#### Example

Suppose we are in the process of trying to find a one-factorisation for *K*<sub>6</sub>, and have generated a partial one-factorisation represented by the set *F*.
*F* = {(*f*<sub>1</sub>, {4, 6}), (*f*<sub>1</sub>, {3, 5}), (*f*<sub>2</sub>, {5, 6}), (*f*<sub>3</sub>{1, 6}), (*f*<sub>3</sub>{3, 4}), (*f*<sub>4</sub>, {2, 3}), (*f*<sub>4</sub>, {4, 5})}
 Now apply *H*<sub>1</sub>:

1.  Choose *x* = 2. Live, because it doesn’t appear in *f*<sub>1</sub>, *f*<sub>2</sub>, *f*<sub>3</sub> or *f*<sub>5</sub>.

2.  Of these four partial one factors, choose *f*<sub>1</sub>.

3.  2 only occurs together with 3 (in *f*<sub>4</sub>), so pick *y* = 5.

4.  5 already appears in *f*<sub>1</sub> so {*z*, *y*}={3, 5}. So replace *F* by *F* ∪ {(*f*<sub>1</sub>, {2, 5}) ∖ (*f*<sub>1</sub>, {3, 5})}

So we have extracted one edge from the one-factorisation and replaced it with another edge, leaving the cost unchanged. If in 3. we had picked 1 then according to the heuristic we should replace *F* with *F* ∪ (*f*<sub>1</sub>, {2, 1}), increasing |*F*| by one, and so decreasing the cost by the same. Because the cost cannot increase *H*<sub>1</sub> is a suitable heuristic for use in a hill-climbing algorithm.

Now apply *H*<sub>2</sub> to the new one-factorisation *F*<sub>1</sub> = *F* ∪ (*f*<sub>1</sub>, {2, 1})

1.  We can pick any of *f*<sub>2</sub>, *f*<sub>3</sub>, *f*<sub>4</sub>, *f*<sub>5</sub>, because all are live. Choose *f*<sub>2</sub>.

2.  Choose *x* = 2, *y* = 3, because neither appear in *f*<sub>2</sub>.

3.  2 and 3 occur together in *f*<sub>4</sub>. So replace *F*<sub>1</sub> with *F*<sub>1</sub> ∪ {(*f*<sub>2</sub>, {2, 3}) ∖ (*f*<sub>4</sub>, {2, 3})}

Again the cost remains unchanged by this procedure, and if in 2. we had chosen *x* = 1, *y* = 4 instead then we would have replaced *F*<sub>1</sub> with *F*<sub>1</sub> ∪ {(*f*<sub>2</sub>, {1, 4})} decreasing the cost by one. As with *H*<sub>1</sub>, the cost cannot increase, which makes *H*<sub>2</sub> a suitable heuristic. The hill-climbing algorithm for constructing one-factorisations which was first given in \[9\] has a very simple form.

1.  **While** *c*(*F*)≠0, **do**

2.  choose *r* = 1 or *r* = 2 with equal probability

3.  perform *H*<sub>*r*</sub>

### An Algorithm for Room Squares

To generate a Room square all that remains is to produce another one-factorisation *G*, say, which is orthogonal to *F*. This will inevitably require slight modifications to be made to *H*<sub>1</sub> and *H*<sub>2</sub>. Now if an array *R* is constructed in which the rows are labelled with the one-factors of *F*(*f*<sub>1</sub>, *f*<sub>2</sub>, ..., *f*<sub>*n* − 1</sub>), and the columns are labelled with the partial one-factors of *G*(*g*<sub>1</sub>, *g*<sub>2</sub>, ..., *g*<sub>*n* − 1</sub>). Then *R* will be a Room square if the (*f*<sub>*i*</sub>, *g*<sub>*j*</sub>) cell contains {*x*, *y*}, if and only if (*f*<sub>*i*</sub>, {*x*, *y*}) ∈ *F* and (*g*<sub>*j*</sub>, {*x*, *y*}) ∈ *G* and is empty otherwise.

Again these two heuristics are due to Dinitz & Stinson and originally presented in \[9\]. Although a necessary correction has been made as will become apparent.

*O**H*<sub>1</sub>

1.  Choose any live point *x*.

2.  Choose any partial one-factor *g*<sub>*i*</sub> such that *x* does not occur in *g*<sub>*i*</sub>.

3.  Choose any *y* ≠ *x* such that *x* and *y* do not occur together in *G*.

4.  Let *f*<sub>*j*</sub> be the one-factor of *F* which contains the edge {*x*, *y*}.

5.  **if** *R*(*f*<sub>*j*</sub>, *g*<sub>*i*</sub>) is not empty **then**

6.  *O**H*<sub>1</sub> fails.

7.  **Else if** *y* does not occur in *g*<sub>*i*</sub>, **then**

8.  $\\hspace{1cm}$ Replace *G* by *G* ∪ (*g*<sub>*i*</sub>, {*x*, *y*}).

9.  $\\hspace{1cm}$ Define *R*(*f*<sub>*j*</sub>, *g*<sub>*i*</sub>)={*x*, *y*}.

10. **Else** there is a pair in *G* of the form $(g\_i,\\{z,y\\}) \\hspace{0.5cm} z \\neq x$.

11. $\\hspace{1cm}$ Replace *G* by *G* ∪ (*g*<sub>*i*</sub>, {*x*, *y*}) ∖ (*g*<sub>*i*</sub>, {*z*, *y*}).

12. $\\hspace{1cm}$ Define *R*(*f*<sub>*k*</sub>, *g*<sub>*i*</sub>), to be empty**<sup>*i*</sup>, where (*f*<sub>*k*</sub>, {*z*, *y*}) ∈ *F*.

*O**H*<sub>2</sub>

1.  Choose any live partial one-factor *g*<sub>*i*</sub>.

2.  Choose any *x* and *y* ≠ *x* such that *x* and *y* do not occur together in *g*<sub>*i*</sub>.

3.  Let *f*<sub>*j*</sub> be the one-factor of *F* which contains the edge {*x*, *y*}.

4.  **if** *R*(*f*<sub>*j*</sub>, *g*<sub>*i*</sub>) is not empty **then**

5.  *O**H*<sub>2</sub> fails.

6.  **Else if** *x* and *y* do not occur together, **then**

7.  $\\hspace{1cm}$ Replace *G* by *G* ∪ (*g*<sub>*i*</sub>, {*x*, *y*}).

8.  $\\hspace{1cm}$ Define *R*(*f*<sub>*j*</sub>, *g*<sub>*i*</sub>)={*x*, *y*}.

9.  **Else** there is a pair in *G* of the form $(g\_k,\\{x,y\\}) \\hspace{0.5cm} (k \\neq i$)

10. $\\hspace{1cm}$ Replace *G* by *G* ∪ (*g*<sub>*i*</sub>, {*x*, *y*}) ∖ (*g*<sub>*k*</sub>, {*x*, *y*})

11. $\\hspace{1cm}$ Define *R*(*f*<sub>*j*</sub>, *g*<sub>*i*</sub>)={*x*, *y*}

12. $\\hspace{1cm}$ Define *R*(*f*<sub>*j*</sub>, *g*<sub>*k*</sub>) to be empty

#### *Example 2.2.1*

Suppose the factorisation *F* from the earlier example has been completed and is represented by the set:

$$ M={

|                                                                                                                                                                               |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (*f*<sub>1</sub>{1, 2}), (*f*<sub>1</sub>{3, 5}), (*f*<sub>1</sub>{4, 6}), (*f*<sub>2</sub>{1, 4}), (*f*<sub>2</sub>{2, 3}), (*f*<sub>2</sub>{5, 6}), (*f*<sub>3</sub>{1, 6}) |
| (*f*<sub>3</sub>{2, 5}), (*f*<sub>3</sub>{3, 4}), (*f*<sub>4</sub>{1, 3}), (*f*<sub>4</sub>{2, 6}), (*f*<sub>4</sub>{4, 5}), (*f*<sub>5</sub>{1, 5}), (*f*<sub>5</sub>{3, 6}) |

}

Notice that this is precisely the one-factorisation of *K*<sub>6</sub> given on page 9.

Now suppose we have established the following one-factors in *G*:
*G* = {(*g*<sub>1</sub>, {1, 4}), (*g*<sub>2</sub>, {1, 6}), (*g*<sub>3</sub>, {3, 6}), (*g*<sub>5</sub>{5, 6}), (*g*<sub>5</sub>{1, 2})}
 At this state *R* looks like

$$R=

|                 | *g*<sub>1</sub> | *g*<sub>2</sub> | *g*<sub>3</sub> | *g*<sub>4</sub> | *g*<sub>5</sub> |
|-----------------|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| *f*<sub>1</sub> |                 |                 |                 |                 |       1, 2      |
| *f*<sub>2</sub> |       1, 4      |                 |                 |                 |       5, 6      |
| *f*<sub>3</sub> |                 |       1, 6      |                 |                 |                 |
| *f*<sub>4</sub> |                 |                 |                 |                 |                 |
| *f*<sub>5</sub> |                 |                 |       3, 6      |                 |                 |

$$

**Figure 13**

Now apply *O**H*<sub>1</sub>:

1.  Choose *x* = 5, suitably live.

2.  Choose *g*<sub>3</sub>, in which 5 does not occur.

3.  5 does not occur together with 2 in *G*, so we are free to choose *y* = 2.

4.  In *F*, {2.5}∈*f*<sub>3</sub>.

5.  *f*<sub>3</sub>, *g*<sub>3</sub> is empty in *R*, also *y* = 2 ∉ *g*<sub>3</sub>.

6.  Replace *G* with *G* ∪ (*g*<sub>3</sub>, {5, 2}).

7.  Define *R*(*f*<sub>3</sub>, *g*<sub>3</sub>)={5, 2}.

This decreases the cost by one, alternatively we might have chosen, at stage 3. *y* = 3, in that case.

1.  {3, 5}∈*f*<sub>1</sub>.

2.  *f*<sub>1</sub>, *g*<sub>3</sub> is empty in *R*, also *y* ∈ *g*<sub>3</sub>, occurring in the pair (*g*<sub>3</sub>, {3, 6}), *z* = 6.

3.  Replace *G* with *G* ∪ (*g*<sub>3</sub>, {3, 5}) ∖ (*g*<sub>3</sub>, {3, 6}).

4.  Define *R*(*f*<sub>1</sub>, *g*<sub>3</sub>)={3, 5}.

5.  Define *R*(*f*<sub>5</sub>, *g*<sub>3</sub>) to be empty.

Which leaves the cost unaffected. Suppose now that *R* is the array after this second version of the application of *O**H*<sub>1</sub>:

$$R=

|                 | *g*<sub>1</sub> | *g*<sub>2</sub> | *g*<sub>3</sub> | *g*<sub>4</sub> | *g*<sub>5</sub> |
|-----------------|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| *f*<sub>1</sub> |                 |                 |       3, 5      |                 |       1, 2      |
| *f*<sub>2</sub> |       1, 4      |                 |                 |                 |       5, 6      |
| *f*<sub>3</sub> |                 |       1, 6      |                 |                 |                 |
| *f*<sub>4</sub> |                 |                 |                 |                 |                 |
| *f*<sub>5</sub> |                 |                 |                 |                 |                 |

$$

**Figure 14**

Now if we apply *O**H*<sub>2</sub>:

1.  Choose *g*<sub>4</sub>, a live partial one-factor.

2.  Choose *x* = 1, *y* = 2, neither of which occur in *g*<sub>4</sub>.

3.  (*f*<sub>1</sub>, {1, 2}) ∈ *F*.

4.  *f*<sub>1</sub>, *g*<sub>4</sub> is empty in *R*, also *x* and *y* do occur together, (*g*<sub>5</sub>, {1, 2}) ∈ *G*.

5.  Replace *G* with *G* ∪ (*g*<sub>4</sub>, {1, 2}) ∖ (*g*<sub>5</sub>, {1, 2})

6.  Define *R*(*f*<sub>1</sub>, *g*<sub>4</sub>)={1, 2}

7.  Define *R*(*f*<sub>1</sub>, *g*<sub>5</sub>) to be empty.

This procedure leaves the cost unaffected and if instead we had chosen at 2. *x* = 3, *y* = 4, then would have been required to replace *G* with *G* ∪ (*g*<sub>4</sub>, {3, 4}), and put {3, 4} in cell (*f*<sub>3</sub>, *g*<sub>4</sub>) of *R*, an action which reduces the cost by one. However, we know that two orthogonal one-factorisations of *K*<sub>6</sub> are equivalent to a Room square of side 5, which has been shown not to exist. Hence it would be futile to continue with this method in this particular case. Nevertheless the example shows how the heuristics work.

There is no guarantee of success with repeated use of these heuristics, although Dinitz & Stinson are quick to point out that the algorithm involving *H*<sub>1</sub> and *H*<sub>2</sub> has never[3] failed to produce the desired one-factorisation. If we hope to use the *O**H*<sub>1</sub> and *O**H*<sub>2</sub> in a similar algorithm then the possibility of failure becomes a real possibility. Two possibilities exist, either both heuristics fail or successive use of them leads to an infinite loop. In order to avoid both we introduce a ***threshold*** function, which simply arrests the progress of the algorithm after a certain number of iterations of the heuristics. Dinitz & Stinson found after experimentation that the following function is suitable.
*T*(*n*)=100*n*
 Then the hill-climbing algorithm for finding a Room square is as follows \[8\]:

1.  Use the previous hill climbing algorithm to construct *F*, a one-factorisation of *K*<sub>*n*</sub>.

2.  Number of iterations initialised to be 0

3.  While (number of iterations &lt;*T*(*n*)) and *c*(*G*)≠0, do

4.  $\\hspace{1cm}$ Choose *r* = 1 or *r* = 2 at random with equal probability

5.  $\\hspace{1cm}$ Perform *O**H*<sub>*r*</sub>

6.  $\\hspace{1cm}$ Increment number of iterations

### The Room Square Generator

Dinitz and Stinson choose to implement the above algorithm in Pascal, and ran in on an Amdahl 5850 workstation. It was very successful, finding many Room squares with sides ranging from 11 to 101. For each successful trial they had 9 or 10 failures (the program being stopped by the threshold function) and timings ranged from 0.09 seconds for an 11x11 Room square, to 7.3 on average for the 25 different 101x101 Room squares they found.

I chose to implement the hill-climbing algorithms in Visual Basic 6.0 on a Pentium III-450/Win 98 Desktop. Needless to say, it was slightly less successful – exhibiting a similar probability of success but unfortunately becoming very slow for Room squares bigger than 21. It found square of side 21 after an all-night search, but after 48 hours looking for one of 23x23 I decided to call the search off.

Despite the failures at higher order, the Room square generator was very successful in finding smaller squares. It found 7x7 Room squares in as little as 4 seconds, and even 15x15 squares only took a few minutes.

Annotated code for the Room square generator can be found along with some of the larger squares in Appendix I and below is a screen shot of the application having successfully located a 9x9 Room square in a little over one minute after 507 iterations of the heuristics *O**H*<sub>1</sub> and *O**H*<sub>2</sub>. The uppermost panel represents some of the one-factorisation generated by the algorithm involving *H*<sub>1</sub> and *H*<sub>2</sub>, while the second panel shows part of the orthogonal one-factorisation generated by *O**H*<sub>1</sub> and *O**H*<sub>2</sub>. The lower panel is a Room square of side 9.

**Figure 15 Screenshot of the Room Square Generator**

Proving the existence of Room squares
=====================================

Introduction
------------

The theorem which will ultimately be established in section 4 relies upon a fundamental theorem in number theory – in fact **the** fundamental theorem. The Fundamental Theorem of Arithmetic states that every positive integer, except 1, can be expressed uniquely as a product of primes.

Proof of this theorem can be found in \[11, section 2.10\].

The proof which established the existence of Room squares will rely upon various other theorems which collectively establish the existence of all Room squares with prime side, except 3 and 5. Then multiplication theorems will be developed to establish the existence of composite Room squares (those whose side is the product of two or more primes). Clearly if the prime Room squares can be proven to exist, and hence composite Room squares, the fundamental theorem will allow us to state that all Room squares exist with odd positive integer side. Apart from a few exceptional cases, this is basically what we wil be able to do.

Starters, Adders and Cyclic Room Squares
----------------------------------------

<table style="width:61%;">
<colgroup>
<col width="12%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
<col width="6%" />
</colgroup>
<thead>
<tr class="header">
<th align="center"> </th>
<th align="center">0</th>
<th align="center">1</th>
<th align="center">2</th>
<th align="center">3</th>
<th align="center">4</th>
<th align="center">5</th>
<th align="center">6</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="center"><strong>0</strong></td>
<td align="center">∞0</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">25</td>
<td align="center"></td>
<td align="center">16</td>
<td align="center">34</td>
</tr>
<tr class="even">
<td align="center"><strong>1</strong></td>
<td align="center">45</td>
<td align="center">∞1</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">36</td>
<td align="center"></td>
<td align="center">20</td>
</tr>
<tr class="odd">
<td align="center"><strong>2</strong></td>
<td align="center">31</td>
<td align="center">56</td>
<td align="center">∞2</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">40</td>
<td align="center"></td>
</tr>
<tr class="even">
<td align="center"><strong>3</strong></td>
<td align="center"></td>
<td align="center">42</td>
<td align="center">60</td>
<td align="center">∞3</td>
<td align="center"></td>
<td align="center"></td>
<td align="center">51</td>
</tr>
<tr class="odd">
<td align="center"><strong>4</strong></td>
<td align="center">62</td>
<td align="center"></td>
<td align="center">53</td>
<td align="center">01</td>
<td align="center">∞4</td>
<td align="center"></td>
<td align="center"></td>
</tr>
<tr class="even">
<td align="center"><strong>5</strong></td>
<td align="center"></td>
<td align="center">03</td>
<td align="center"></td>
<td align="center">64</td>
<td align="center">12</td>
<td align="center">∞5</td>
<td align="center"></td>
</tr>
<tr class="odd">
<td align="center"><strong>6</strong></td>
<td align="center"></td>
<td align="center"></td>
<td align="center">14</td>
<td align="center"></td>
<td align="center">05</td>
<td align="center">23</td>
<td align="center">∞6</td>
</tr>
</tbody>
</table>

**Figure 16 Cyclic Room square**

The Room square in Figure 16 has a special property. The pairs in any element of the array are obtained by simply adding 1 (mod 7) to the pair in the element immediately above and to the left; along with the condition that
∞ + 1 = ∞
 This special property means that the entire square can be determined by the pairs in the first row, with successive rows being developed in a cyclical manner according the simple addition rule. We call squares like the one in Figure 16 *cyclic* Room squares.
Also notice that {∞,*i*} occurs in position (*i*, *i*). A square with this property is said to be *standardised*. It is important to realise that any Room square can be standardised. As mentioned previously neither interchanging the rows or columns nor permuting the symbol-set on which the Room square is based has any effect of the \`\`Room"-ness of that square.
The significance of cyclic Room squares is that the problem of constructing a Room square is (potentially) reduced to that of finding an appropriate first row. These rows cannot be chosen arbitrarily, both the pairs used and the positions in which they appear need to satisfy certain criteria, but when they do exist a corresponding Room square always exists. So proving the existence of this subclass of Room squares is a matter only of proving the existence of these special first rows.

### Finding a starter

Suppose we wish to construct another Room square of the same size as Figure 16 based on the same symbols. This new square will also be standardized so we need only determine the three pairs that accompany {0, ∞} in the first row (the starter), and the positions they occupy.
The set we will use to build our starter will be {1,2,...,6}.
Each member of this set must occur exactly once in the pairs of the starter – in order to satisfy the row condition for a Room square. Because of the cyclical construction the condition is automatically true for successive rows if true for the first.
Consider the existence in Figure 16 of an arbitrary pair {*a*, *b*}. We know one of the following must be true.
Either:
$$\\{2+i,5+i\\}=\\{a,b\\} \\hspace{0.5cm} \\mathrm{or} \\hspace{0.5cm} \\{1+i,6+i\\}=\\{a,b\\} \\hspace{0.5cm} 
\\mathrm{or} \\hspace{0.5cm} \\{3+i,4+i\\}=\\{a,b\\} \\hspace{0.5cm} \\mathrm{for} \\hspace{0.1cm} i=0,1,2,...,6$$
 Say *a* − *b* = 1. Then {2 + *i*, 5 + *i*}={*a*, *b*} could never be true because (2 + *i*)−(5 + *i*)= − 3(mod $ 7)=4$ and (5 + *i*)−(2 + *i*)=3. Similarly, the differences in {1, 6} are ±5 so {*a*, *b*} couldn’t be generated from {1, 6}.
However, (4 + *i*)−(3 + *i*)=1 so {*a*, *b*} will inevitably be generated by {3, 4} for some value of *i* = 0, 1, ..., 6.
e.g. {2, 3}={3 + 6, 4 + 6}
Because *a* and *b* separately take on all values from {0, 1, 2, ..., 6}, their differences will similarly take on all these values (except 0 because there are no pairs of the form {*a*, *a*}) and so an essential property for the starter must be that the six differences generated by its three pairs contain all of {1, 2, ..., 6}.
When a starter satisfies this property, and the condition that the pairs contain in their union all of {1, 2, ..., 6}, it is clear that it will inevitably generate the correct pairs which populate a 7x7 Room square. There are three pairs in the starter, each generates seven unique pairs under cyclical construction, which along with the seven pairs generated by {0, ∞} counts for all the 28 unordered pairs from {∞,0, 1, ..., 6}.
A starter for larger Room squares of course has to obey the same criterion. We include a general definition based on \[8\]:
(1,0)<span>450</span>
*Definition:* If *G* is an additive Abelian group of order *g*, then a *starter* in *G* is a set of unordered pairs:
*S* = {{*s*<sub>*i*</sub>, *t*<sub>*i*</sub>}:1 ≤ *i* ≤ (*g* − 1)/2}
 which satisfies these properties:

1.  {*s*<sub>*i*</sub> : 1 ≤ *i* ≤ (*g* − 1)/2}∪{*t*<sub>*i*</sub> : 1 ≤ *i* ≤ (*g* − 1)/2}=*G* ∖ {0}

2.  { ± (*s*<sub>*i*</sub> − *t*<sub>*i*</sub>):1 ≤ *i* ≤ (*g* − 1)/2}=*G* ∖ {0}

(1,0)<span>450</span>
Whenever we have any *t* sets *D*<sub>1</sub>, ..., *D*<sub>*t*</sub> each of size *k* in which each non-zero member of an additive abelian group can be represented as a difference between members of the *D*<sub>*i*</sub>*λ* times, we say those sets form a ***difference system***.
Much use will be made of difference systems throughout this work.
Notice that the definition of a starter presumes standardization, and therefore that {∞,*i*} is in position (*i*, *i*).
The following pairs form a starter in *G* = {0, 1, 2, ..., 6} (an additive abelian group with order *g* = 7.)
$$\\{1,3\\} \\hspace{1cm} \\{2,6\\} \\hspace{1cm} \\{4,5\\}$$
 Property 1 is satisfied because {1, 3}∪{2, 6}∪{4, 5}=*G* ∖ {0}
Property 2 is also satisfied because
{1 − 3 = 5, 3 − 1 = 2, 2 − 6 = 3, 6 − 2 = 4, 4 − 5 = 6, 5 − 4 = 1}={1, 2, 3, 4, 5, 6}=*G* ∖ {0}
 Hence

|  ∞0 |  13 |  26 |  45 |
|:---:|:---:|:---:|:---:|
|  ∞1 |  24 |  30 |  56 |
|  ∞2 |  35 |  41 |  60 |
|  ∞3 |  46 |  52 |  01 |
|  ∞4 |  50 |  63 |  12 |
|  ∞5 |  61 |  04 |  23 |
|  ∞6 |  02 |  15 |  34 |

**Table 1**

are all the unordered pairs from {∞,0, 1, ...6} sorted into seven rows that contain each of {∞,0, 1, ..., 6} exactly once. ALl that remains is to determine the columns.

### Finding an adder

In constructing the starter we made use of the fact that each row has to contain each symbol exactly once and all unordered pairs from the symbol set have to occur exactly once in the whole array. The remaining condition – namely, that each symbol must occur once in each column – is now employed to finish the construction.
Again, because of the cyclical nature of Room squares generated from starters we can be sure that if one column contains each member of the symbol set, all columns will.
Also, because we have decided to construct a standardized Room Square we know that column *i* contains {∞,*i*}. So the final column (column 6) contains {∞,6}, and depending on where we place the starter pairs it will also include:
$$\\{1,3\\}+x \\hspace{1cm} \\{2,6\\}+y \\hspace{1cm} \\{4,5\\}+z$$
 For some distinct values of *x*, *y* and *z* (only one pair allowed per box).
Considering that the new pairs to form column 6 must contain in their union each of {0, 1, 2, ..., 5} we build the following table.

| *x* | 13 + *x* | *y* | 26 + *y* | *z* | 45 + *z* |
|:---:|:--------:|:---:|:--------:|:---:|:--------:|
|  0  |    13    |  0  |    26    |  0  |    45    |
|  1  |    24    |  1  |    30    |  1  |    56    |
|  2  |    35    |  2  |    41    |  2  |    60    |
|  3  |    46    |  3  |    52    |  3  |    01    |
|  4  |    50    |  4  |    63    |  4  |    12    |
|  5  |    61    |  5  |    04    |  5  |    23    |

**Table 2**

Our task is simply to determine three unique values for *x*, *y* and *z* such that 13 + *x*, 26 + *y* and 45 + *z* contain in their union each of {0, 1, 2, ..., 5}. These values will then determine the positions to place 13, 26 and 45 in row 1.
Choosing 4 from the first column corresponds to having 50 appear in the final column of the Room Square and forces the selection of *y* = 2 from the next column of the table, (41 being the only pair not containing any of the already used 5,6 or 0). 23 is the only possible choice from the final column, accompanied by a value of *z* = 5. These three numbers are known as an *adder* corresponding to the starter 13,26,45. This is not necessarily the only adder.
If 50 is to be generated in the final column of the Room square by the pair 13 in the first row, then 13 must go in column 7 − 4 = 3. Similarly 26 has to be put in column 7 − 2 = 5 and 45 in 7 − 5 = 2.
We can now construct our cyclic room square.

|  ∞0 |  45 |  13 |  -  |  26 |  -  |  -  |     |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|-----|
|  -  |  ∞1 |  56 |  24 |  -  |  30 |  -  |     |
|  -  |  -  |  ∞2 |  60 |  35 |  -  |  41 |     |
|  52 |  -  |  -  |  ∞3 |  01 |  46 |  -  |     |
|  -  |  63 |  -  |  -  |  ∞4 |  12 |  50 |     |
|  61 |  -  |  04 |  -  |  -  |  ∞5 |  23 |     |
|  34 |  02 |  -  |  15 |  -  |  -  |  ∞6 |     |

**Figure 17**

In general, we define an adder by considering the elements which must accompany {∞,0} in column 0. Therefore an adder is defined in the following way:
(1,0)<span>450</span>
An *adder* for a starter *S* = {{*s*<sub>*i*</sub>, *t*<sub>*i*</sub>}:1 ≤ *i* ≤ (*g* − 1)/2} is a set of (*g* − 1)/2 distinct non-zero elements *a*<sub>1</sub>, *a*<sub>2</sub>, ..., *a*<sub>(*g* − 1)/2</sub> of *G* such that: *s*<sub>1</sub> + *a*<sub>1</sub>, *t*<sub>1</sub> + *a*<sub>1</sub>, *s*<sub>2</sub> + *a*<sub>2</sub>, ..., *s*<sub>(*g* − 1)/2</sub> + *a*<sub>(*g* − 1)/2</sub>, *t*<sub>(*g* − 1)/2</sub> + *a*<sub>(*g* − 1)/2</sub> are precisely all the non-zero elements of *G*.
(1,0)<span>450</span>
The *starter-adder* method employed in the above example was introduced in 1968[4] by Stanton and Mullin \[23\], who used it to construct Room squares of side 11. They also went on to apply the method to larger squares and gave the first real suggestions that the number of Room squares is infinite.
Two simple Lemmas given by Stanton and Mullin demonstrated that the problem of finding starters for larger Room squares was straightforward. In fact they can be guaranteed always to exist, and the only difficulty comes from finding a corresponding adder, which is not guaranteed to exist.

#### Lemma 3.2.1

In an additive abelian group *G* of order *g* = 2*n* − 1, then pairs
{*n* − 1, *n*},{*n* − 2, *n* + 1},{*n* − 3, *n* + 2},{*n* − 4, *n* + 3},...{1, 2*n* − 2}
 are a starter for a Room square of side 2*n* − 1.
*Example 3.2*
A Room square of side 2*n* − 1 = 19.
*n* = 10, *G* = *Z*<sub>19</sub>
The set of pairs
*S*<sub>19</sub> = {{9, 10},{8, 11},{7, 12},{6, 13},{5, 14},{4, 15},{3, 16},{2, 17},{1, 18}}
is a starter.
Indeed, the differences are
{ ± (10 − 9), ± (11 − 8), ± (12 − 7), ± (13 − 6), ± (14 − 5), ± (3 − 16), ± (2 − 17), ± (18 − 1)}
={1, 18, 3, 16, 5, 14, 7, 12, 9, 10, 8, 11, 6, 13, 4, 15, 2, 17}=*G* ∖ {0}

#### Lemma 3.2.2

In the Galois field of order *k* − 1, with primitive root *a* the following pairs form a starter for a Room square of side *k*.
{*a*, *a*<sup>*n*</sup>},{*a*<sup>2</sup>, *a*<sup>*n* + 1</sup>},{*a*<sup>3</sup>, *a*<sup>*n* + 2</sup>},...,{*a*<sup>*n* − 1</sup>, *a*<sup>2*n* − 2</sup>}
 *Example 3.3*
A Room square of side 2*n* − 1 = 23. *n* = 12. *a* = 5.
The set of pairs
*S*<sub>23</sub> = {{5, 5<sup>12</sup>},{5<sup>2</sup>, 5<sup>13</sup>},{5<sup>3</sup>, 5<sup>14</sup>},...,{5<sup>11</sup>, 5<sup>22</sup>}}
={{5, 18},{2, 21},{10, 13},{4, 19},{20, 3},{8, 15},{17, 6},{16, 7},{11, 12},{9, 14},{22, 1}}
 is a starter.
On closer inspection the two types of starters are identical[5] , with a general element being of the form
{*j*, −*j*}
 Starters of this form are called *patterned* starters.
Stanton and Mullin went on to show that using the method outlined in Example 2.1 they could find adders corresponding to the patterned starters for *k* = 7, 11, 13, 15, 17. They had problems with 9 (but were able to construct one using a different method) and finding it too laborious for *k* &gt; 19 they developed an algorithm which, when implemented in Fortran, was able to find patterned starters with adders for all odd *k* up to 49, with no further gaps. Suggesting the possibility (which they conjectured) that there are Room squares for all odd side greater than 5.
They also found an interesting result regarding the number of Room Squares which could be obtained from patterned starters, summarised in Table 3.

| Value of *k* |                         Number of PRS                        |
|:------------:|:------------------------------------------------------------:|
|       7      |                               2                              |
|       9      |                               0                              |
|      11      |                               4                              |
|      13      |                               8                              |
|      15      |                              44                              |
|      17      |                              416                             |
|      19      | The programme was turned off after the production of 967 PRS |

**Table 3**

Stanton & Mullin’s results suggest that the number of PRS (patterned Room squares) increases very rapidly. Which, bearing in mind that the PRS are a sub-class of CRS (cyclic Room squares), which are in turn a sub-class of Room squares, implies that there are vast numbers of Room squares of large order.
Before introducing a class of starters for which the existence of a corresponding adder is guaranteed we quickly confirm that when a starter and adder exist then a Room square will always result. This seems obvious from the method outlined in the previous section, but now we prove it explicitly.

#### Theorem 3.2.1

\[17\]
If an Abelian group *G* of odd order 2*n* − 1 admits a starter and an adder, then there exists a Room square of order 2*n*.
*Proof*
A square is constructed on the set *G* ∪ {∞}, where *G* is an additive Abelian group of order 2*n* − 1.
*G* = {*g*<sub>0</sub> = 0, *g*<sub>1</sub>, *g*<sub>2</sub>, ..., *g*<sub>2*n* − 2</sub>}
 The columns and rows of the square are labelled as follows

|                 | *g*<sub>0</sub> | *g*<sub>1</sub> | *g*<sub>2</sub> | ... | *g*<sub>2*n* − 1</sub> |
|-----------------|:---------------:|:---------------:|:---------------:|:---:|:----------------------:|
| *g*<sub>0</sub> |                 |                 |                 |     |                        |
| *g*<sub>1</sub> |                 |                 |                 |     |                        |
| *g*<sub>2</sub> |                 |                 |                 |     |                        |

*g*<sub>0</sub>

**Figure 18**

If a starter {{*s*<sub>1</sub>, *t*<sub>1</sub>},{*s*<sub>2</sub>, *t*<sub>2</sub>}...{*s*<sub>*n* − 1</sub>, *t*<sub>*n* − 1</sub>}} and an adder {*a*<sub>1</sub>, *a*<sub>2</sub>, ..., *a*<sub>*n* − 1</sub>} can be ontained from *G* and if the square is populated by pairs of elements from *G* according to the following rules:

1.  {∞,*g*<sub>*i*</sub>} goes in (*g*<sub>*i*</sub>, *g*<sub>*i*</sub>)

2.  While {*s*<sub>*i*</sub> + *g*<sub>*i*</sub>, *t*<sub>*i*</sub> + *g*<sub>*i*</sub>} goes in (*g*<sub>*i*</sub>, *g*<sub>*i*</sub> − *a*<sub>*i*</sub>)

for all *g*<sub>*i*</sub> ∈ *G*. The remaining square will be a Room square on *G* ∪ {∞}.
*Proof*

1.  Row *g*<sub>0</sub> = 0, contains the pairs {*s*<sub>*i*</sub>, *t*<sub>*i*</sub>}:1 ≤ *i* ≤ *n* − 1, which are the elements of the starter, hence all of *G* ∖ {0}. These pairs are accompanied by {∞,0}, so row 0 contains all of *G* ∪ {∞}. Subsequent rows simple contain a permutation of the same elements, hence the *row property* of Room squares is satisfied for all rows.

2.  As mentioned before, the starter forms a difference system in *G* ∖ {0}, so all unordered pairs of this set occur along with all unordered pairs of the form {∞,*g*<sub>*i*</sub>}:1 ≤ *i* ≤ *n* − 1, hence *all unordered pairs from* *G* ∪ {∞} *occur* in the square exactly once.

3.  All pairs of the form {*s*<sub>*i*</sub> + *a*<sub>*i*</sub>, *t*<sub>*i*</sub> + *a*<sub>*i*</sub>} go in (*a*<sub>*i*</sub>, 0), i.e. column 0. According to the definition of a starter these pairs are all of *G* ∖ {0}, and we know that {∞,0} is also in column 0. So the first column, and hence all others, contains all of *G* ∪ {∞}, thus satisfying the *column property* of Room squares.

Strong Starters
---------------

The next state in proving the existence of Room squares came about, not by continuing to try to find adders for starters that were already known (the patterned starters, for example), but when Mullin & Nemeth in \[17\], discovered a class of starters that generated their own adders.

#### Theorem 3.3.1

\[17\]
*Suppose a starter* {{*s*<sub>1</sub>, *t*<sub>1</sub>},{*s*<sub>2</sub>, *t*<sub>2</sub>},...,{*s*<sub>(*g* − 1)/2</sub>, *t*<sub>(*g* − 1)/2</sub>}} *exists, such that the sums of each pair*
(*s*<sub>1</sub> + *t*<sub>1</sub>, *s*<sub>2</sub> + *t*<sub>2</sub>, *e**t**c*...) *are all distinct and non-zero, then that starter is said to be strong, and*
*A*(*S*)={*a*<sub>*i*</sub> = −(*s*<sub>*i*</sub> + *t*<sub>*i*</sub>):1 ≤ *i* ≤ (*g* − 1)/2}
 *is an adder for a starter.
Proof*

1.  *The *a*<sub>*i*</sub> are all distinct and non-zero*
    All the (*s*<sub>*i*</sub> + *t*<sub>*i*</sub>) are, by definition, distinct and non-zero. Therefore all the *a*<sub>*i*</sub> = −(*s*<sub>*i*</sub> + *t*<sub>*i*</sub>) are distinct and non-zero.

2.  *s*<sub>1</sub> + *a*<sub>1</sub>, *t*<sub>1</sub> + *a*<sub>1</sub>, *s*<sub>2</sub> + *a*<sub>2</sub>, ..., *s*<sub>(*g* − 1)/2</sub>, *t*<sub>(*g* − 1)/2</sub> + *a*<sub>(*g* − 1)/2</sub> *are precisely all the non-zero elements of* *G*.

    <span>l</span> *s*<sub>1</sub> + *a*<sub>1</sub> = *s*<sub>1</sub> − (*s*<sub>1</sub> + *t*<sub>1</sub>)= − *t*<sub>1</sub> = *t*<sub>(*g* − 1)/2</sub>
    *t*<sub>1</sub> + *a*<sub>1</sub> = *t*<sub>1</sub> − (*s*<sub>1</sub> + *t*<sub>1</sub>)= − *s*<sub>1</sub> = *s*<sub>(*g* − 1)/2</sub>
    *s*<sub>(*g* − 1)/2</sub> + *a*<sub>(*g* − 1)/2</sub> = −*t*<sub>(*g* − 1)/2</sub> = *t*<sub>1</sub>
    *t*<sub>(*g* − 1)/2</sub> + *a*<sub>(*g* − 1)/2</sub> = −*s*<sub>(*g* − 1)/2</sub> = *s*<sub>1</sub>
    Are all the non-zero elements of *G* in reverse order.

(Notice that the patterned starter is not strong, on the contrary, the sums of its pairs are all identical.)
*Example 3.3.1*
The pairs (5, 7)(11, 6)(2, 8)(9, 12)(10, 1)(3, 4), constitute a strong starter for a Room square of side 13, based on *G* = *Z*<sub>13</sub>
*Proof*
Firstly, the pairs satisfy the conditions for being a starter, as the union of all pairs is equal to *G* ∖ {0}, and similarly the differences are all of *G* ∖ {0}.
Secondly the sums of the pairs, respectively 12,4,10,8,11,7, are all distinct and non-zero.
Therefore an adder is { − 12, −4, −10, −8, −11, −7}={1, 9, 3, 5, 2, 6}
So the following is a legitimate first row for a cyclic Room square of order 14.

∞, 0 – – – 11,6 – – 3,4 9,12 – 2,8 1,10 5,7 ------------ --- --- --- ------ --- --- ----- ------ --- ----- ------ -----

Mullin and Nemeth originally discovered strong starters for Room squares embedded within another type of combinatorial design, known as a Steiner triple system. With these they were able to prove that Room squares exist for all sides *v* = 1 mod 6. Rather than examine this approach we move on to a type of starter which provides its own adder.

The Mullin-Nemeth Starters
--------------------------

If *x* is a primitive element in *G* = *G**F*(*p*<sup>*n*</sup>), then the elements *x*<sup>1</sup>, *x*<sup>2</sup>, ..., *x*<sup>*p*<sup>*n*</sup> − 1</sup> = 1 are, by definition, all of *G* ∖ {0}. Alternatively, we can write *G* ∖ {0}={*x*<sup>0</sup> = 1, *x*<sup>1</sup>, ..., *x*<sup>*p*<sup>*n*</sup> − 2</sup>}.
*Example 3.4.1*
The field *G**F*(23) has a primitive root *x* = 5, because
5<sup>0</sup> = 1, 5<sup>1</sup> = 5, 5<sup>2</sup> = 2, 5<sup>3</sup> = 10, 5<sup>4</sup> = 4, 5<sup>5</sup> = 20, 5<sup>6</sup> = 8, 5<sup>7</sup> = 17, 5<sup>8</sup> = 16, 5<sup>9</sup> = 11, 5<sup>10</sup> = 9, 5<sup>11</sup> = 22, 5<sup>12</sup> = 18, 5<sup>13</sup> = 21, 5<sup>14</sup> = 13, 5<sup>15</sup> = 19, 5<sup>16</sup> = 3, 5<sup>17</sup> = 15, 5<sup>18</sup> = 6, 5<sup>19</sup> = 7, 5<sup>20</sup> = 12, 5<sup>21</sup> = 14 are all the non-zero elements of *G**F*(23).
Mullin & Nemeth in \[17\] used the theory of primitive elements to create strong starters in the additive group of (nearly) any Galois Field of prime power order. Which, because Theorems 3.2.1 and 3.3.1 were already known, was equivalent to proving the existence of Room squares for (nearly) all orders *p*<sup>*n*</sup> + 1. Before introducing the general construction for these starters, we illustrate the basic method with a couple of examples of particular cases.
*Example 3.4.2*
We can create a strong starter from Example 2.5 simply by pairing the elements in the order in which they were generated.
i.e. *S* = {{1, 5},{2, 10},{4, 20},{8, 17},{16, 11},{9, 22},{18, 21},{13, 19},{3, 15},{6, 7},{12, 14}}
is a strong starter.
*Proof*
Obviously each member of *G**F*(23) occurs once, because of the definition of a primitive root.
The differences
{ ± 4, ±8, ±7, ±9, ±10, ±5, ±3, ±6, ±11, ±1, ±2}
 are similarly all of *G**F*(23), so *S* is a starter. The sums
{6, 12, 1, 2, 4, 8, 16, 9, 18, 13, 3}
 are all unique, and therefore *S* is strong and
*A* = {17, 11, 22, 21, 19, 15, 7, 14, 5, 10, 20}
 is an adder for *S*.
So, the following row will generate a Room square of order 24 under cyclic construction.

<span>-1.66cm</span>

∞, 0 4,20 8,17 12,14 16,11 - 1,5 - 9,22 13,19 - - 2,10 6,7 - - 18,21 - 3,15 - - - - ------------ ------ ------ ------- ------- --- ----- --- ------ ------- --- --- ------ ----- --- --- ------- --- ------ --- --- --- ---

This is an example of the simplest case of the general theorem of Mullith & Nemeth, where the Galois field is *Z*<sub>*p*</sub> (the integers mod *p*), with *p* = 23 = 3( mod 4) a prime.
\#\#\#\# Theorem 3.4.1 \[1\]

*If *p* = 4*m* + 3 is prime, *m* ≥ 1, then*
*S* = {{*x*<sup>0</sup>, *x*<sup>1</sup>},{*x*<sup>2</sup>, *x*<sup>3</sup>},...,{*x*<sup>4*m*</sup>, *x*<sup>4*m* + 1</sup>}}
 *is a strong starter in *Z*<sub>*p*</sub>, and hence a Room square of order *p* + 1 exists.*
Example 3.4.2 took *m* = 5 and *x* = 5.
A slightly more general version of Theorem 3.4.1, which we prove instead, involves any field of prime power order where *p*<sup>*n*</sup> = 2*t* + 1, with *t* &gt; 1 and odd. Of course, when *p*<sup>*n*</sup> is not prime, the field will no longer be the integers mod *p*, instead the primitive element will be an irreducible polynomial whose coefficients belong to *Z*<sub>*p*</sub>.

#### Theorem 3.4.2 \[16\]

If *p*<sup>*n*</sup> = 2*t* + 1 = 3(mod 4) then
*S* = {{*x*<sup>0</sup>, *x*<sup>1</sup>},{*x*<sup>2</sup>, *x*<sup>3</sup>},...,{*x*<sup>2*t* − 2</sup>, *x*<sup>2*t* − 1</sup>}}
 is a strong starter in *G**F*(*p*<sup>*n*</sup>),(*p*<sup>*n*</sup> ≠ 3)
*Proof*
*x* is a primitive element, so the elements in the starter are all the non-zero members of *G**F*(*P*<sup>*n*</sup>).
The differences are, respectively
±*x*<sup>0</sup>(1 − *x*), ± *x*<sup>2</sup>(1 − *x*),..., ± *x*<sup>2*t* − 2</sup>(1 − *x*)
 (1 − *x*) is a non-zero (*x* = 1 is not primitive) member of *G**F*(*p*<sup>*n*</sup>). So in order to show that these differences are all the 2*t* non-zero members of *G**F*(*p*<sup>*n*</sup>) we merely need to prove that the 2*t* differences are all distinct and non-zero.
All the differences can be written ±*x*<sup>2*i*</sup>(1 − *x*),0 ≤ *i* ≤ *t* − 1
(1 − *x*)≠0
*x*<sup>2*i*</sup>(1 − *x*)=*x*<sup>2*j*</sup>(1 − *x*)
⇒*x*<sup>2*i*</sup> = *x*<sup>2*j*</sup> ⇒ *i* = *j*,
because 0 ≤ 2*i*, 2*j* ≤ 2*t* − 2 &lt; *p*<sup>*n* − 1</sup>, and the primitive element, by definition, produces each element of *G**F*(*p*<sup>*n*</sup>) exactly once as the indices range from 0 to *p*<sup>*n* − 1</sup>.
Similarly −*x*<sup>2*i*</sup>(1 − *x*)= − *x*<sup>2*j*</sup>(1 − *x*) only when *i* = *j*.
So all the positive differences are unique, similarly the negative.
However, there remains a possibility for repetition when the signs are opposite:
$$x^{2i}(1-x)=-x^{2j}(1-x) \\hspace{1cm}...(1)$$
 Either *i* = *j* or *i* ≠ *j*
Let *i* = *j*, (1) becomes *x*<sup>2*i*</sup> + *x*<sup>2*i*</sup> = 0, ⇒2*x*<sup>2*i*</sup> = 0, bit *i* takes values 0...*t* − 1, so *x*<sup>2</sup> = 0 when *i* = 1, contradicting the order of the primitive element.
In the *i* ≠ *j* case, we assume (without loss of generality) that *i* &lt; *j* and write

*x*<sup>2*i*</sup> = −*x*<sup>2*j*</sup>
as *x*<sup>2*i*</sup>(1 + *x*<sup>2*j* − 2*i*</sup>)=0
⇒*x*<sup>2*j* − 2*i*</sup> = −1

but in *G**F*(2*t* + 1), $x^{\\frac{1}{2}(q-1)}=x^t=-1$
2*j* − 2*i* = *t*
 but this is a contradiction as we insisted that *t* be odd. So *S* is a starter.
To prove that *S* is strong we simply note that the sums can be written:

*x*<sup>0</sup>(1 + *x*), *x*<sup>2</sup>(1 + *x*), ..., *x*<sup>2*t* − 2</sup>(1 + *x*)

1 + *x* = 0 ⇒ *x* = −1 is only true when *p*<sup>*n*</sup> = 3. So (1 + *x*)≠0.
So *x*<sup>2*i*</sup>(1 + *x*)=*x*<sup>2*j*</sup>(1 + *x*)⇒*x*<sup>2*i*</sup> = *x*<sup>2*j*</sup>
We have already shown that
*x*<sup>2*i*</sup> = *x*<sup>2*j*</sup>
 is only true for *i* = *j*. So all the sums are unique, and the starter is strong.
Hence, by theorems 2.1 and 2.2, Room squares exist for all *p*<sup>*n*</sup> = 3(mod 4), and in the case when *p*<sup>*n*</sup> = 3(mod 4) is prime, these Room squares are based on *Z*<sub>*p*</sub>.
The most generalised case of Mullin & Nemeth’s theorem proves the existence of Room squares for all prime powers *p*<sup>*n*</sup> = 2<sup>*k*</sup>*t* + 1 where *k* &gt; 1 and *t* &gt; 1 is odd (*k* and *t*, both positive integers), and reduces to Theorem 3.4.2 when *k* = 1.

#### Theorem 3.4.3 \[16\]

A strong starter exists in *G**F*(*p*<sup>*n*</sup>), where *p*<sup>*n*</sup> = 2<sup>*k*</sup>*t* + 1 (with *k* &gt; 1 and *t* &gt; 1 is odd).
*Proof*
Let *d* = 2<sup>*k* − 1</sup>
Then the strong starter in question looks like this: $$ S={

|                                                 |                                          |         |                                                                    |
|:-----------------------------------------------:|:----------------------------------------:|:-------:|:------------------------------------------------------------------:|
|       (*x*<sup>0</sup>, *x*<sup>*d*</sup>)      | (*x*<sup>2*d*</sup>, *x*<sup>3*d*</sup>) | $ ... $ |     (*x*<sup>(2*t* − 2)*d*</sup>, *x*<sup>(2*t* − 1)*d*</sup>)     |
|     (*x*<sup>1</sup>, *x*<sup>*d* + 1</sup>)    |   $\\hspace{0.5cm}(x^{2d+1},x^{3d+1})$   | $ ... $ | (*x*<sup>(2*t* − 2)*d* + 1</sup>, *x*<sup>(2*t* − 1)*d* + 1</sup>) |
|                                                 |                                          | $ ... $ |                                                                    |
| (*x*<sup>*d* − 1</sup>, *x*<sup>2*d* − 1</sup>) |   $\\hspace{0.5cm}(x^{3d-1},x^{4d-1})$   | $ ... $ |    (*x*<sup>(2*t* − 1)*d* − 1</sup>, *x*<sup>2*t**d* − 1</sup>)    |

} $$ Where the pairs have been placed in an array to emphasise that, when read vertically, this is an exhaustive list of all the non-zero elements of *G**H*(*p*<sup>*n*</sup>), ordered according to powers. Of course, in the *k* = 1, *d* = 1 case this starter reduces to the one quoted in Theorem 3.4.2.
To prove that *S* is a starter we need also to show, as usual, that the differences between pairs are all of *G**F*(*p*<sup>*n*</sup>), and to show that the starter is strong we need to show that the sums of pairs are all distinct and non-zero.
The differences can be written in the following scheme:

|                                               |                                                |      |                                                         |
|:---------------------------------------------:|:----------------------------------------------:|:----:|:-------------------------------------------------------:|
|    *x*<sup>0</sup>(1 − *x*<sup>*d*</sup>),    |   *x*<sup>2*d*</sup>(1 − *x*<sup>*d*</sup>),   | ..., |   *x*<sup>(2*t* − 2)*d*</sup>(1 − *x*<sup>*d*</sup>),   |
|    *x*<sup>1</sup>(1 − *x*<sup>*d*</sup>),    | *x*<sup>2*d* + 1</sup>(1 − *x*<sup>*d*</sup>), | ..., | *x*<sup>(2*t* − 2)*d* + 1</sup>(1 − *x*<sup>*d*</sup>), |
|                                               |                                                |  ... |                                                         |
| *x*<sup>*d* − 1</sup>(1 − *x*<sup>*d*</sup>), | *x*<sup>3*d* − 1</sup>(1 − *x*<sup>*d*</sup>), | ..., |  *x*<sup>(2*t* − 1)*d* − 1</sup>(1 − *x*<sup>*d*</sup>) |

The order of *x* is *p*<sup>*n*</sup> − 1 = 2<sup>*k*</sup>*t* = 2<sup>*k* − 1</sup>2*t* = 2*t**d* &gt; *d*, (meaning *x*<sup>2*t**d*</sup> = 1 and *x*<sup>*α*</sup> ≠ 1 when 1 ≤ *α* &lt; 2*d**t*) and so *x*<sup>*d*</sup> ≠ 1, so (1 − *x*<sup>*d*</sup>)≠0.
We can write the differences in a general form:

$\\pm x^{2id+j}(1-x^d) \\hspace{0.5cm}$ where $\\hspace{0.5cm} 0 \\leq i \\leq t-1, \\hspace{0.5cm} 0 \\leq j \\leq d-1$

<span>: l :</span>→ If there were repetition, either of the form *D* = *D* or −*D* = −*D*, where *D* = *x*<sup>2*i**d* + *j*</sup>(1 − *x*<sup>*d*</sup>),
then the following must hold:
Cancelling by (1 − *x*<sup>*d*</sup>), legitimate because (1 − *x*<sup>*d*</sup>)≠0 gives:
dividing through by *x*<sup>2*I**d* + *j*</sup> leaves
But if *i* ≠ *I*, then the LHS has an index which is an integer multiple of *d*. The index in the RHS,
however, can never be an integer multiple of *d* because *J* and *j* range over the integers 0...*d* − 1.
So the only possibility for equality is when both indices are zero, i.e. *i* = *I* and *j* = *J*.
As in the previous proof we have to deal with the possibility of repetition for differences of opposite sign. For coincidence we require:
*x*<sup>2*i**d* + *j*</sup> = −*x*<sup>2*I**D* + *J*</sup>
*x*<sup>2*i**d* + *j*</sup> + *x*<sup>2*I**d* + *J*</sup> = 0
 We assume that 2*i**d* + *j* &lt; 2*I**d* + *J* and rewrite this expression as:
*x*<sup>2*i**d* + *j*</sup>(1 + *x*<sup>(2*I* − 2*i*)*d* + (*J* − *j*)</sup>)=0
 Which implies that *x*<sup>(2*I* − 2*i*)*d* + (*J* − *j*)</sup> = −1
But in $GF(q),x^{\\frac{1}{2}(q-1)}=-1$. Where, in this case *q* − 1 = 2<sup>*k*</sup>*t*, so $\\frac{1}{2}(q-1)=2^{k-1}t=dt$.
∴*x*<sup>*d**t*</sup> = −1
⇒(2*I* − 2*i*)*d* + (*J* − *j*)=*d**t*

⇒(*J* − *j*) is an integer multiple of *d* or zero.

But *J* and *j* both take only the values 0...*d* − 1, so (*J* − *j*) is in the interval \[1 − *d*, *d* − 1\] and hence must be zero, leaving
(2*I* − 2*i*)*d* = *d**t*
2*I* − 2*i* = *t*
 But *t* is strictly odd, and so we have reached a contradiction, hence the differences are all unique, belong to *G**F*(*p*<sup>*n*</sup>) and there are 2*t**d* of them, hence each member of *G**F*(*p*<sup>*n*</sup>) occurs exactly once as a difference. So *S* is a starter.
To prove that the starter is strong we write the sums as

|                                               |                                                |      |                                                         |
|:---------------------------------------------:|:----------------------------------------------:|:----:|:-------------------------------------------------------:|
|    *x*<sup>0</sup>(1 − *x*<sup>*d*</sup>),    |   *x*<sup>2*d*</sup>(1 − *x*<sup>*d*</sup>),   | ..., |   *x*<sup>(2*t* − 2)*d*</sup>(1 − *x*<sup>*d*</sup>),   |
|    *x*<sup>1</sup>(1 − *x*<sup>*d*</sup>),    | *x*<sup>2*d* + 1</sup>(1 − *x*<sup>*d*</sup>), | ..., | *x*<sup>(2*t* − 2)*d* + 1</sup>(1 − *x*<sup>*d*</sup>), |
|                                               |                                                |  ... |                                                         |
| *x*<sup>*d* − 1</sup>(1 − *x*<sup>*d*</sup>), | *x*<sup>3*d* − 1</sup>(1 − *x*<sup>*d*</sup>), | ..., |  *x*<sup>(2*t* − 1)*d* − 1</sup>(1 − *x*<sup>*d*</sup>) |

and notice that *x*<sup>*d*</sup> = −1 ⇒ *d* = *d**t* (because *x*<sup>*d**t*</sup> = −1)⇒*t* = 1, but instead we insisted that *t* be strictly greater than one (this being the reason why). So (1 + *x*<sup>*d*</sup>)≠0 and the above argument (denoted by →) involving (1 − *x*<sup>*d*</sup>) can be invoked, replacing (1 − *x*<sup>*d*</sup>) by (1 + *x*<sup>*d*</sup>). So *S* is a strong starter, and the general theorem of Mullin & Nemeth is proven, guaranteeing the existence of a vast class of Room Squares.

The Trouble with Fermat Numbers
-------------------------------

Unfortunately, in establishing the Mullin & Nemeth starters we were forced to exclude a similarly vast, potentially infinite, class of Room squares by insisting that *t* be strictly greater than one. These exceptional Room squares have side 2<sup>*k*</sup> + 1.
Rectifying this problem is essential if we are to prove the existence of Room squares. As mentioned previously, the proof relies on a multiplication theorem, so proving that all the ’prime’ Room squares exist is vital. Although the theorem of Mullin & Nemeth will take care of all squares with prime power side, the multiplication theorem is necessary for proving the existence of those whose side can be decomposed into prime factors different from each other. In fact, the multiplication theorem means that we can ignore the Mullin & Nemeth construction except in the prime case, resorting to multiplication to recover the prime power squares. Similarly we are only concerned with recovering the exceptional squares with side 2<sup>*k*</sup> + 1, when 2<sup>*k*</sup> + 1 is prime.
Primes of this form are known as **Fermat Numbers** or **Fermat Primes**, after Pierre de Fermat who, 360 years ago conjectured that numbers of the form 2<sup>*k*</sup> + 1 are always prime when *k* is a power of two.

|                                                     |
|:----------------------------------------------------|
| *F*<sub>*m*</sub> = 2<sup>2<sup>*m*</sup></sup> + 1 |
| *F*<sub>0</sub> = 2<sup>1</sup> + 1 = 3             |
| *F*<sub>1</sub> = 2<sup>2</sup> + 1 = 5             |
| *F*<sub>2</sub> = 2<sup>4</sup> + 1 = 17            |
| *F*<sub>3</sub> = 2<sup>8</sup> + 1 = 257           |
| *F*<sub>4</sub> = 2<sup>16</sup> + 1 = 65537        |

After the first four of Fermat’s numbers, all of which were known to him to be prime. Nearly one hundred years later Euler calculated the following,
*F*<sub>5</sub> = 2<sup>32</sup> + 1 = 4294967297 = 641 × 6700417
 and in doing so disproved Fermat’s conjecture.
Since Euler’s time, *F*<sub>6</sub>, *F*<sub>7</sub> and *F*<sub>8</sub> have all been factorised[6] . It is also known, although most of the factorisations remain unknown, that *F*<sub>*m*</sub> is composite for *m* = \[9...23\]. *F*<sub>24</sub>, a number with over 5 million digits, remains in doubt.
Whether there be an infinite number of Fermat primes or whether, as empirically seems to be the case, there are only finitely many (possibly just five) such primes, in order for the proof of the existence of Room squares for all odd side greater than 7 to be complete these Fermat prime Room squares must be included.
When the problem of Fermat Room squares was tackled first in the early 1970s, W.D.Wallis used a Theorem of J.D.Horton’s which adapted a famous result of E.H.Moore’s from the theory of Steiner triple systems.
Moore, in 1893, was able to prove that if Steiner triple systems of orders *v*<sub>1</sub>, *v*<sub>2</sub> and *v*<sub>3</sub> exist, where the *v*<sub>2</sub> system is a sub-system of the *v*<sub>3</sub> system, then an STS of order *v*<sub>1</sub>(*v*<sub>2</sub> − *v*<sub>3</sub>)+*v*<sub>3</sub> also exists. Horton\[12\] adapted this result to other combinatorial objects including Room squares and Wallis\[25\] was able to use this Moore-type construction method to include all of the Fermat primes, except *F*<sub>3</sub> = 257[7] .
*Example 3.5.1*
If Room squares with side *v*<sub>1</sub>, *v*<sub>2</sub> and *v*<sub>3</sub> exist, where the square of side *v*<sub>2</sub> is a subsquare of the square with side *v*<sub>3</sub>, then a Room square of side *F*<sub>4</sub> = 65537 exists. Room squares of side 7 and 11 exist, according to the theory of Mullin & Nemeth. Applying Horton’s theorem once, with *v*<sub>3</sub> = 0 gives a new square of side *v*<sub>1</sub>*v*<sub>2</sub> = 77 (note that Horton’s theorem reduces to the multiplication theorem when *v*<sub>3</sub> = 0).
The trivial Room square of side one exists, and the Mullin & Nemeth starters will provide a Room square of size 13. So we can apply Horton’s theorem once again to gain a Room square of side 989 because:
989 = 13(77 − 1)+1
 Finally we can use Mullin & Nemeth to produce a Room square of side 67, and a final application of Horton’s theorem gives:
65537 = 67(989 − 11)+11
 The proof of Horton’s theorem and also an explanation of Wallis’s application of that theorem to solving the Fermat prime problem is excluded because another solution was subsequently found. A year after Wallis had published his solution to the Fermat problem, Chong and Chan published their (independent) discovery of the strong starters which are known as the Mullin & Nemeth starters. Also included in their paper was an alternative solution to the same problem, but their solution continued to involve the starter-adder method. This theorem we prove instead.

#### Theorem 3.5.1 \[6\]

For every Galois field of order (2<sup>2<sup>*m*</sup></sup> + 1), where *m* ≥ 2, there exists a Room square of order (2<sup>2<sup>*m*</sup></sup> + 2).
*Proof*
The following pairs in *Z*<sub>*p*</sub> (where *p* = 2<sup>2<sup>*d*</sup></sup> + 1 and *d* = 2<sup>*m* − 1</sup>) constitute a strong starter.

1.  {*i* + (*r* − 1)2<sup>*d*</sup>, *i*2<sup>*d*</sup> − (*r* − 1}

2.  {(2<sup>*d*</sup> − *i*)2<sup>*d*</sup> + *r*, (2<sup>*d* − 1</sup> − *r*)2<sup>*d*</sup> + 2<sup>*d* − 1</sup> − *i* + 1}

3.  {2<sup>*d* − 1</sup> + *r* − 1)2<sup>*d*</sup> + 2<sup>*d* − 1</sup> + *i*, (2<sup>*d* − 1</sup> + *i* − 1)2<sup>*d*</sup> + 2<sup>*d* − 1</sup> − (*r* − 1)}

4.  {(2<sup>*d* − 1</sup> − *i*)2<sup>*d*</sup> + 2<sup>*d* − 1</sup> + *r*, (2<sup>*d*</sup> − *r* + 1)2<sup>*d*</sup> − *i* + 1}

Where 1 ≤ *r* ≤ 2<sup>*d* − 2</sup> and 1 ≤ *i* ≤ 2<sup>*d* − 1</sup>, so rather than just 4 pairs there are 4 ⋅ 2<sup>*d* − 2</sup> ⋅ 2<sup>*d* − 1</sup> = 2<sup>2*d* − 1</sup> pairs arranged in four different classes. Before completing the proof we pause for an example just to illustrate the real simplicity of these apparently complicated pairs.
*Example 3.5.2*
Suppose *p* = 2<sup>2 ⋅ 2</sup> + 1 = 17 = *F*<sub>2</sub>, then *d* = 2<sup>1</sup> ⇒ *m* = 2
*r* = 1, 1 ≤ *i* ≤ 2 and the following pairs should be a strong starter.
<span>-1.15cm</span>

|     | *i* = 1, *r* = 1                                                                                                           | *i* = 2, *r* = 1                                                                                                           |
|-----|:---------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| 1   | {1 + 0 ⋅ 2<sup>2</sup>, 1 ⋅ 2<sup>2</sup> − 0}={1, 4}                                                                      | {2 + 0 ⋅ 2<sup>2</sup>, 2 ⋅ 2<sup>2</sup> − 0}={2, 8}                                                                      |
| 2   | {(2<sup>2</sup> − 1)2<sup>2</sup> + 1, (2<sup>1</sup> − 1)2<sup>2</sup> + 2<sup>1</sup> − 1 + 1}={13, 6}                   | {(2<sup>2</sup> − 2)2<sup>2</sup> + 1, (2<sup>1</sup> − 1)2<sup>2</sup> + 2<sup>1</sup> − 2 + 1}={9, 5}                    |
| 3   | {(2<sup>1</sup> + 1 − 1)2<sup>2</sup> + 2<sup>1</sup> + 1, (2<sup>1</sup> + 1 − 1)2<sup>2</sup> + 2<sup>1</sup> − (1 − 1)} | {(2<sup>1</sup> + 1 − 1)2<sup>2</sup> + 2<sup>1</sup> + 2, (2<sup>1</sup> + 2 − 1)2<sup>2</sup> + 2<sup>1</sup> − (1 − 1)} |
|     | ={11, 10}                                                                                                                  | ={12, 14}                                                                                                                  |
| 4   | {(2<sup>1</sup> − 1)2<sup>2</sup> + 2<sup>1</sup> + 1, (2<sup>2</sup> − 1 + 1)2<sup>2</sup> − 1 + 1}                       | {(2<sup>1</sup> − 2)2<sup>2</sup> + 2<sup>1</sup> + 1, (2<sup>2</sup> − 1 + 1)2<sup>2</sup> − 2 + 1}                       |
|     | ={7, 16}                                                                                                                   | ={3, 15}                                                                                                                   |

**Table 4**

The pairs generated by this method contain each non-zero member of *Z*<sub>17</sub> exactly once in their union satisfying the first property of a starter.
The differences are { ± 3, ±7, ±1, ±8, ±6, ±4, ±2, ±5}=*Z*<sub>17</sub> ∖ {0}, satisfying the other necessary property of a starter.
The sums 5,2,4,6,10,14,9,1 are all unique, hence the starter is strong and the set
{ − 5, −2, −4, −6, −10, −14, −9, −1}={12, 15, 13, 11, 3, 8, 16} is an adder. So the following first row will generate a Room square under cyclic construction:

∞, 0 3,15 13,6 - 11,10 1,4 7,16 - - 12,14 2,8 - - - 9,5 - - ------------ ------ ------ --- ------- ----- ------ --- --- ------- ----- --- --- --- ----- --- ---

In order to prove that the pairs 1...4 are a strong starter from any *Z*<sub>*p*</sub> we need to prove the following:

1.  The union of all the pairs contains each non-zero member of *Z*<sub>*p*</sub> exactly once.

2.  The differences are all the non-zero members of *Z*<sub>*p*</sub> exactly once.

3.  The sums are all distinct and non-zero.

This is a formidable task, one that would take many pages to prove in full detail. So instead we sketch an outline of the proof, explicitly proving a few specific cases.
First we prove (a) completely.
The non-zero members of *Z*<sub>*P*</sub>, namely {1...2<sup>2*d*</sup>}, can be represented uniquely by:
$$C(u,v) = u2^d+v \\hspace{0.5cm} \\mathrm{where} \\hspace{0.5cm} 1 \\leq v \\leq 2^d
\\hspace{0.25cm} \\mathrm{and} \\hspace{0.25cm} 0 \\leq u \\leq 2^d-1$$
 *Proof*
Indeed if
*u*<sub>12</sub><sup>*d*</sup> + *v*<sub>1</sub> = *u*<sub>22</sub><sup>*d*</sup> + *v*<sub>2</sub>
 then
(*u*<sub>1</sub> − *u*<sub>2</sub>)2<sup>*d*</sup> = (*v*<sub>2</sub> − *v*<sub>1</sub>)
 The RHS takes integer values in the interval \[ − (2<sup>*d*</sup> − 1),2<sup>*d*</sup> − 1\], which is symmetric about the origin and smaller than 2<sup>*d*</sup> on both sides. Whereas the LHS takes integer multiple steps of size 2<sup>*d*</sup>, so the equality can only hold in the case when both sides equal zero. Which implies *u*<sub>1</sub> = *u*<sub>2</sub>, *v*<sub>1</sub> = *v*<sub>2</sub> and *C*(*u*, *v*) is unique representation the non-zero members of *Z*<sub>*p*</sub>. *u* takes 2<sup>*d*</sup> values and *v* takes 2<sup>*d*</sup> values so there are 2<sup>2*d*</sup> unique non-zero members of *Z*<sub>*p*</sub> represented in this way, so each member of *Z*<sub>*p*</sub> is represented.
The left and right hand members of each pair can be characterised by a range of values of *u* and *v* in the following manner.
Take, for instance, the left hand member of pair 1.
*i* + (*r* − 1)2<sup>*d*</sup>
 Here *v* = *i* and so 1 ≤ *v* ≤ 2<sup>*d* − 1</sup>, while *u* = (*r* − 1), so 0 ≤ *u* ≤ 2<sup>*d* − 2</sup> − 1. The full list of intervals for each member of each pair is tabulated below.

|      |        |                                                      |                                                      |
|:----:|:------:|:----------------------------------------------------:|:----------------------------------------------------:|
| Pair | Member |                          *u*                         |                          *V*                         |
|  1.  |    L   |            \[0, 2<sup>*d* − 2</sup> − 1\]            |              \[1, 2<sup>*d* − 1</sup>\]              |
|      |    R   |            \[0, 2<sup>*d* − 1</sup> − 1\]            |   \[3 ⋅ 2<sup>*d* − 2</sup> + 1, 2<sup>*d*</sup>\]   |
|  2.  |    L   |     \[2<sup>*d* − 1</sup>, 2<sup>*d*</sup> − 1\]     |              \[1, 2<sup>*d* − 2</sup>\]              |
|      |    R   |   \[2<sup>*d* − 2</sup>, 2<sup>*d* − 1</sup> − 1\]   |              \[1, 2<sup>*d* − 1</sup>\]              |
|  3.  |    L   | \[2<sup>*d* − 1</sup>, 3 ⋅ 2<sup>*d* − 2</sup> − 1\] |     \[1 + 2<sup>*d* − 1</sup>, 2<sup>*d*</sup>\]     |
|      |    R   |     \[2<sup>*d* − 1</sup>, 2<sup>*d*</sup> − 1\]     |   \[1 + 2<sup>*d* − 2</sup>, 2<sup>*d* − 1</sup>\]   |
|  4.  |    L   |            \[0, 2<sup>*d* − 1</sup> − 1\]            | \[1 + 2<sup>*d* − 1</sup>, 3 ⋅ 2<sup>*d* − 2</sup>\] |
|      |    R   |   \[3 ⋅ 2<sup>*d* − 2</sup>, 2<sup>*d*</sup> − 1\]   |     \[1 + 2<sup>*d* − 1</sup>, 2<sup>*d*</sup>\]     |

**Table 5**

It was mentioned earlier that there were 2<sup>2*d* − 1</sup> pairs, each of which has two members, so there are 2<sup>2*d*</sup> elements altogether in the pairs of the starter, which is the same as the number of elements in *Z*<sub>*p*</sub>. Because *C*(*u*, *v*) is a unique representation for each member of *Z*<sub>*p*</sub>, for an element of *Z*<sub>*p*</sub> to occur more than once in the starter requires repetition of both *u* and *v*. This cannot happen because when two intervals overlap (as they do in the values of *v* for 1L and 2R).
To prove (b) we need to show that the differences between two pairs of type 1 are all unique, similarly between two pairs of types 2,3 and 4. Moreover we need to show that there can be no repetition in differences between a pair of type 1 and a pair of type 2, also type 1 with types 3 in 4. Similarly for 2,3 and 4. All together there are ten cases to prove, tabulated below, where a pair of numbers represents the two types of pairs from the starter.

| (i)    |  11 | (ii) |  12 | (iii) |  13 | (iv) |  14 |
|:-------|:---:|:-----|:---:|:------|:---:|:-----|:---:|
| (v)    |  22 | (vi) |  23 | (vii) |  24 |      |     |
| (viii) |  33 | (ix) |  34 |       |     |      |     |
| (x)    |  44 |      |     |       |     |      |     |

**Table 6**

To illustrate, we prove (v), in other words that differences ebtween two different pairs, both of type 2 are always unique.
Type 2 have the form: {(2<sup>*d*</sup> − *i*)2<sup>*d*</sup> + *r*, (2<sup>*d* − 1</sup> − *r*)2<sup>*d*</sup> + 2<sup>*d* − 1</sup> − *i* + 1}. Therefore, a difference between the elements of a pair of type 2 has the form:
±{(2<sup>*d*</sup> − *i*)2<sup>*d*</sup> + *r* − (2<sup>*d* − 1</sup> − *r*)2<sup>*d*</sup> − 2<sup>*d* − 1</sup> + *i* − 1}
 If two different pairs had the same difference we could write:
$$(2^d-i)2^d+r-(2^{d-1}-r)2^d-2^{d-1}+i-1
\\equiv \\pm \\{(2^d-j)2^d +s-(2^{d-1}-s)2^d-2^{d-1}+j-1\\}(\\mathrm{mod} \\hspace{0.1cm} p)$$
 for some *i* ≠ *j*, *r* ≠ *s*. There are two cases to prove, firstly consider the one involving the + sign.
$$(2^d-i)2^d+r-(2^{d-1}-r)2^d-2^{d-1}+i-1 \\equiv (2^d-j)2^d + s -(2^{d-1}-s)2^d - 2^{d-1} + j -1 (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$\\cancel{(2^d}-i)2^d+r-(\\cancel{2^{d-1}}-r)2^d-\\cancel{2^{d-1}}+i\\cancel{-1} \\equiv \\cancel{(2^d}-j)2^d + s -(\\cancel{2^{d-1}}-s)2^d - \\cancel{2^{d-1}} + j \\cancel{-1} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 In this case we have been helped out with some very convenient cancelling, leaving just:
$$-i2^d+r+r \\cdot 2^d + i \\equiv -j \\cdot 2^d + s + s \\cdot 2^d + j \\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(-i+j)2^d + i -j \\equiv (s-r)(1+2^d) \\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(j-i)(2^d -1) \\equiv (s-r)(1+2^d) \\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 ×(2<sup>*d*</sup> + 1)
$$(j-i)(2^{2d} -1) \\equiv (s-r)(1+2 \\cdot 2^d + 2^{2d}) \\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 2<sup>2*d*</sup> + 1 = *p* $\\hspace{0.5cm}\\therefore$ 2<sup>2*d*</sup> − 1 ≡ −2 (mod *p*)
$$-2(j-i)\\equiv (s-r)2 \\cdot 2^d \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(i-j)\\equiv (s-r) 2^d \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p) \\hspace{2cm} ...(\\mathrm{A})$$
 1 ≤ *i*, *j* ≤ 2<sup>*d* − 1</sup>
∴(*i* − *j*) lies in the interval \[ − (2<sup>*d* − 1</sup> − 1),2<sup>*d* − 1</sup> − 1\], which is symmetric about the origin, with length 2 ⋅ 2<sup>*d* − 1</sup> − 2 = 2<sup>*d*</sup> − 2 &lt; *p* = 2<sup>2*d*</sup> + 1.
1 ≤ *s*, *r* ≤ 2<sup>*d* − 2</sup>
∴(*s* − *r*)2<sup>*d*</sup> lies in the interval \[ − (2<sup>*d* − 2</sup> − 1)2<sup>*d*</sup>, (2<sup>*d* − 2</sup> − 1)2<sup>*d*</sup>\], again symmetric about the origin with length 2<sup>2*d*</sup> − 2<sup>*d* + 1</sup> &lt; *p*.
So for A to hold requires that
(*i* − *j*)=(*s* − *r*)2<sup>*d*</sup>
 But the LHS has an interval with length 2<sup>*d*</sup> − 2 &lt; 2<sup>*d*</sup> whereas the RHS is some positive or negative integer multiple of 2<sup>*d*</sup>, so the two could only be equal when *i* = *j*, *r* = *s* contradicting the original hypothesis.
There is still the negative case to deal with:
$$(2^d-i)2^d+r-(2^{d-1}-r)2^d-2^{d-1}+i-1 \\equiv
-(2^d-j)2^d-s+(2^{d-1}-s)2^d+2^{d-1}-j+1\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(2^d-i)2^d-(2^{d}-j)2^d+i+j \\equiv
-s+(2^{d-1}-s)2^d + (2^{d-1} -r)2^d -r + 2 \\cdot 2^{d-1} + 2 \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$2 \\cdot 2^{2d} + (1-2^{d})(i+j) \\equiv
-(s+r)(1+2^d)+2^{2d}+1+2^d+1 \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 $2^{2d}+1=p \\therefore 2^{2d} \\equiv -1 \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$
$$-2+(1-2^d)(i+j) \\equiv -(s+r)(1+2^d)+1+2^d \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(1-2^d)(i+j) \\equiv -(s+r)(1+2^d)+3+2^d \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 Now multiply throughout by (1 + 2<sup>*d*</sup>), noting that:
$(1+2^d)(1-2^d) \\equiv 2(\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p),(1+2^d)(1+2^d) =1+2 \\cdot 2^d + 2^{2d} \\equiv 2^{d+1}\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$
and $(1+2^d)(3+2^d)=3+4 \\cdot 2^d+2^{2d} \\equiv 2^{d+2}+2 \\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$
$$2(i+j)\\equiv -2^{d+1}(s+r)+2^{d+2}+2\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(i+j)\\equiv -2^{d}(s+r)+2^{d+1}+1\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$2^d(s+r)\\equiv 2 \\cdot 2^{d}-(i+j)+1\\hspace{0.1cm} (\\mathrm{mod} \\hspace{0.1cm} p) \\hspace{1cm}... (\\mathrm{B})$$
 1 ≤ *s*, *r* ≤ 2<sup>*d* − 2</sup>
∴2 ⋅ 2<sup>*d*</sup> ≤ 2<sup>*d*</sup>(*s* + *r*)≤2<sup>*d*</sup>2<sup>*d* − 1</sup>
The LHS lies in the interval \[2<sup>*d* + 1</sup>, 2<sup>2*d* − 1</sup>\], which itself is located somewhere in the interval \[0, *p*\].
1 ≤ *i*, *j* ≤ 2<sup>*d* − 1</sup>
∴2 ≤ *i* + *j* ≤ 2<sup>*d*</sup>
2<sup>*d*</sup> ≤ 2 ⋅ 2<sup>*d*</sup> − (*i* + *j*)≤2<sup>*d* + 1</sup> − 2
So the RHS lies in the interval \[2<sup>*d*</sup> + 1, 2<sup>*d* + 1</sup> − 1\], again this is located with \[0, *p*\].
So for B to be satisfied requires that
2<sup>*d*</sup>(*s* + *r*)=2 ⋅ 2<sup>*d*</sup> − (*i* + *j*)+1
 But the RHS and LHS intervals are disjoint so this can never happen.
So the absence of repetition in the differences of two different pairs both of type 2 is proven. All cases involving different pairs of the same type are proven in this way {cases (i),(v),(viii),(x)}.
Finally we demonstrate how the other 6 cases are proven, those involving pairs of different types.
Inevitably the approach is very similar.
Consider a pair of type 1 and another pair of type 4 (case iv). If there were a repetition of differences between pairs of this type we could write:
$$i+(r-1)2^d-i2^d+(r-1) \\equiv \\pm \\{(2^{d-1}-j)2^d+2^{d-1}+s-(2^d-s+1)2^d+j-1\\}
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 Consider the + sign, then
$$i-i2^d-(2^{d-1}-j)2^d-j \\equiv -(r-1)2^d-(r-1)+s-(2^d-s+1)2^d+2^{d-1}-1
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(1-2^d)(i-j)-2^{2d-1} \\equiv -(2^d+1)(r-s)-2^{2d}+2^{d-1}
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 $2^{2d} \\equiv -1\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$
$$(1-2d)(i-j) \\equiv -(2^d+1)(r-s)+2^{d-1} + 2^{2d-1} + 1
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 ×2
$$2(1-2d)(i-j) \\equiv -2(2^d+1)(r-s)+2^{d} + 2^{2d} + 2
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$2(1-2d)(i-j) \\equiv -2(2^d+1)(r-s)+2^{d}+1
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 ×(2<sup>*d*</sup> + 1)
$$4(i-j) \\equiv -2 \\cdot 2^{d+1}(r-s)+2^{d+1}
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$(i-j) \\equiv -2^{d}(r-s)+2^{d-1}
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
$$2^d(r-s) \\equiv 2^{d-1}-(i-j)
\\hspace{0.3cm} (\\mathrm{mod} \\hspace{0.1cm} p)$$
 In this instance the LHS has interval \[2<sup>*d*</sup> − 2<sup>2*d* − 2</sup>, 2<sup>2*d* − 2</sup> − 2<sup>*d*</sup>\]. while the interval of the RHS is \[1, 2<sup>*d*</sup> − 1\]. Both are smaller than *p* in length, so for equality requires
2<sup>*d*</sup>(*r* − *s*)=2<sup>*d* − 1</sup> − (*i* − *j*)
 But this can never be true because the left side is always either zero or an integer multiple of 2<sup>*d*</sup>, whereas the interval of the right is \[1, 2<sup>*d*</sup> − 1\].
All other cases are dealt with in a very similar manner, and the proof of (c), namely that all sums are unique, is not very different.

A Multiplication Theorem
------------------------

Having a theorem which enables new Room squares to be composed from old Room squares is of vital importance to the proof of the existence of Room squares. With such a theorem, in conjunction with the Mullin-Nemeth starters, we will be able to construct Room squares of almost any order. The exceptions will be due to the non-existence of orders 4 and 6. The multiplication theorem that will be proven is:

#### Theorem 3.6.1

*If Room squares of side m and side n exist then a Room square of side mn also exists.*
This theorem was proposed initially in \[5\] but later a counter-example to this method was found \[15\]. The proof here is based upon \[1\], which in turn is based upon the proof in \[22\].
*Proof*
*M* and *N* are two Room squares. *M* is of side *m* and based on {0, 1, 2, ..., *m*}, while *N* is of side *n* and based on {0, 1, 2, ..., *n*}.
The join of two Latin squares *A* and *B* is the array whose (*i*, *j*)<sup>*t**h*</sup> entry contains the ordered pair formed from the (*i*, *j*)<sup>*t**h*</sup> entry of *A* taking the left position and the (*i*, *j*)<sup>*t**h*</sup> entry of *B* taking the right. If the join of two Latin squares contains *n*<sup>2</sup> unique ordered pairs, the two Latin squares *A* and *B* are said to be orthogonal.
*L*<sub>1</sub> and *L*<sub>2</sub> are two mutually Latin squares (MOLS) based on {1, 2, 3, ..., *n*}.
We construct the new Room square *R* = *M**N* by replacing each element of *M* by an *n* × *n* array according to the following flow diagram where (*i*, *j*) is a pair from *M*.

**Figure 19**

This procedure has replaced each pair in *m* by an *n* × *n* array, resulting in an *m**n* × *m**n* array. This array is based upon {0, *n* + 1, *n* + 2, ..., *n* + *m**n*}, and we now prove that it has the properties of a Room square, namely:

1.  Each element of the array is either empty or contains an unordered pair.

2.  Each row and column contains each of {0, *n* + 1, *n* + 2, ..., *n* + *m**n*} exactly once.

3.  Each pair from {0, *n* + 1, *n* + 2, ..., *n* + *m**n*} occurs exactly once in the array.

The first property is easily satisfied. The procedure followed did nothing but replace empty elements and unordered pairs with arrays containing nothing more than empty elements or pairs.
The second is similarly straightforward. Consider an arbitrary row of the new square *R*, call it *i*. This row arose from applying prescriptions (i),(ii), and (iii) to some row of *M*. This row of *M* contained the elements 0...*m* exactly once. One of these elements, call it *a*, was paired with 0. So in *i* from (ii) occur the numbers (0; 1 + *a**n*...*m* + *a**n*) exactly once. In the join of two MOLS the numbers 1...*n* occur twice per row, once in *L*<sub>1</sub> once in *L*<sub>2</sub>. These are replaced by (1 + *u**n*...*n* + *u**n*) and (1 + *v**n*...*n* + *v**n*) as *u* and *v* take on all values 1, 2, ..., *m* excluding
Together these two prescriptions produce the elements
{0; 1 + *n*, 2 + *n*, ..., *n* + *m**n*}
 exactly once per row and column.
To prove condition 3 is true we show that *R* contains the correct number of pairs and that
these pairs are distinct. Because we have shown 2 to be correct these pairs must be the right
Any Room square, of side *n*, contains $\\frac{1}{2}(n+1)$ pairs per row, therefore $\\frac{1}{2}n(n+1)$ pairs over
Room square of side *m**n* ought to contain $\\frac{1}{2}mn(mn+1)$ pairs.
In *M* there were *m* instances of {0, *k*}, each of these was replaced by a Room square of side
$\\frac{1}{2}n(n+1) \\cdot m$ pairs were contributed by (ii) to *R*.
In *M* there were $\\frac{1}{2}(m+1)-1 = \\frac{1}{2} (m-1)$ pairs per row of the form {*u*, *v*}, therefore $\\frac{1}{2}m(m$
of these pairs throughout *M*. These were replaced by MOLS of side *n*, containing *n*<sup>2</sup> pairs
each. So $\\frac{1}{2}m(m-1) \\cdot n^2$ pairs were contributed to *R* from (iii).
(i) contributed no pairs to *R*.
$$\\frac{1}{2} mn (n+1) + \\frac{1}{2}m(m-1)n^2$$
$$=\\frac{1}{2}mn\\{(n+1)+n(m-1)\\}$$
$$=\\frac{1}{2}mn(mn+1)$$
 So the number of pairs in *R* is correct.
To show that all the pairs are distinct consider *P*(*i*, *j*) which represents those pairs generated
from the element (*i*, *j*) of *M*. The pairs within *P*(*i*, *j*) are always distinct because they are
the pairs in a Room square or a join of 2 MOLS.
However we also need to show that *P*(*i*, *j*) and *P*(*h*, *k*) have no pairs in common when *i*, *j* ≠ *h*, *k*. There are 3 cases to consider. Both sets of pairs are chosen from the join of 2 M
both sets are from Room squares, or one set from each.
If both sets of pairs were generated from the join of two MOLS then the pairs have the form
{*u**n* + *l*<sub>1</sub>, *v**n* + *l*<sub>2</sub>}
 If this pair occurs in both *P*(*i*, *j*) and *P*(*h*, *k*) then (*l*<sub>1</sub>, *l*<sub>2</sub>) occurs in two different places in
joins of two MOLS which is a contradiction.
The case where both sets of pairs are generated by Room squares is easily dealt with, because
the Room squares used to construct *R* are based on different sets, so two could never contain
same pair.

Summary
-------

So far we have shown that all Room squares whose side can be expressed as a prime power
*p*<sup>*n*</sup> = 2<sup>*k*</sup>*t* + 1 can be constructed by using the Mullin-Nemeth starters. The Fermat Primes
shown to be an exception to the Mullin-Nemeth construction, but this was overcome by
introducing the theorem of Chong and Chan which provides a strong starter form all Room squares of side (2<sup>2<sup>*m*</sup></sup> + 1), encompassing the Fermat primes. So we have proven that all Room squares exist whose side is a prime number, other than 3 or 5. The multiplication theorem
enables us to state that all Room squares exist whose side can be factored as *p*<sub>1</sub>*p*<sub>2</sub>*p*<sub>3</sub>...*p*<sub>*n*</sub>
*p*<sub>*i*</sub> ≥ 7.
The non-existence of Room squares with sides 3 and 5, prevents us from constructing those
squares whose sides have a factor of 3 or 5. Within this class of exempt Room squares the Mullin & Nemeth starters will take care of the prime power sides. But for those whose side is not a prime power a final theorem, due to W.D. Wallis is needed to complete the proof.

n-tuplication of Room squares
-----------------------------

#### Theorem 3.8.1\[25\]

If *r* and *n* are odd integers such that *r* ≥ *n*, and if there is a Room square *R* of side *r*, then there is a Room square of side *r**n*.
*Example 3.8.1*
Before proving this theorem, we look at an example of triplication in order to introduce thisfairly complicated construction.
The approach taken is to take a Room square of side 7, create 9 arrays very similar in structure tothis Room square, and then arrange these 9 arrays into a 21x21 side array which is very
Room square.
Suppose we wished to triplicate the following Room square.

|  ∞0 |  -  |  -  |  25 |  -  |  16 |  34 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  45 |  ∞1 |  -  |  -  |  36 |  -  |  20 |
|  31 |  56 |  ∞2 |  -  |  -  |  40 |  -  |
|  -  |  42 |  60 |  ∞3 |  -  |  -  |  51 |
|  62 |  -  |  53 |  01 |  ∞4 |  -  |  -  |
|  -  |  03 |  -  |  64 |  12 |  ∞5 |  -  |
|  -  |  -  |  14 |  -  |  05 |  23 |  ∞6 |

**Figure 20**

Unfortunately, this row has simply too many elements. There should be only 11 pairs, not
and the new Room-ish square would be based on a set of 24 elements not 22 as we require.Wallis’s original idea had been to somehow merge the three ∞<sub>*i*</sub> into one element, but he eventually decided instead to go back to the original square and strip out the diagonal elements.Building a Room square is then a matter of arranging the following arrays, sometimes called frames,

$R\_{ij} = $

|                                |                                |                                | 2<sub>*i*</sub>5<sub>*j*</sub> |                                | 1<sub>*i*</sub>6<sub>*j*</sub> | 3<sub>*i*</sub>4<sub>*j*</sub> |
|--------------------------------|--------------------------------|--------------------------------|:------------------------------:|--------------------------------|:------------------------------:|:------------------------------:|
| 4<sub>*i*</sub>5<sub>*j*</sub> |                                |                                |                                | 3<sub>*i*</sub>6<sub>*j*</sub> |                                | 2<sub>*i*</sub>0<sub>*j*</sub> |
| 3<sub>*i*</sub>1<sub>*j*</sub> | 5<sub>*i*</sub>6<sub>*j*</sub> |                                |                                |                                | 4<sub>*i*</sub>0<sub>*j*</sub> |                                |
|                                | 4<sub>*i*</sub>2<sub>*j*</sub> | 6<sub>*i*</sub>0<sub>*j*</sub> |                                |                                |                                | 5<sub>*i*</sub>1<sub>*j*</sub> |
| 6<sub>*i*</sub>2<sub>*j*</sub> |                                | 5<sub>*i*</sub>3<sub>*j*</sub> | 0<sub>*i*</sub>1<sub>*j*</sub> |                                |                                |                                |
|                                | 0<sub>*i*</sub>3<sub>*j*</sub> |                                | 6<sub>*i*</sub>4<sub>*j*</sub> | 1<sub>*i*</sub>2<sub>*j*</sub> |                                |                                |
|                                |                                | 1<sub>*i*</sub>4<sub>*j*</sub> |                                | 0<sub>*i*</sub>5<sub>*j*</sub> | 2<sub>*i*</sub>3<sub>*j*</sub> |                                |

**Figure 21**

into a 21x21 array, and subsequently finding some way to fill in the missing two pairs from
row of the new square, with the aim of producing a Room square based on
*S* = {∞,0<sub>1</sub>, 1<sub>1</sub>, ..., 6<sub>1</sub>, 0<sub>2</sub>, 1<sub>2</sub>, ..., 6<sub>2</sub>, 0<sub>3</sub>, 1<sub>3</sub>, ..., 6<sub>3</sub>}
 Inevitably this approach leads to new problems.
Firstly consider how to arrange the frames appropriately. Suppose we put *R*<sub>12</sub> next to *R*<sub>13</sub>,
the left hand members of pairs in each row of *R*<sub>12</sub> will be repeated in the same row of the
21x21 square due to the placing of *R*<sub>13</sub>. The same would be true for any *R*<sub>*i**j*</sub> next to any *R*<sub>*i**k*</sub>,
next to *R*<sub>*k**j*</sub>. So for that reason, in the super-array of *R*<sub>*i**j*</sub>s we require in each super-row that
each value 1,2 and 3 and similarly that *j* takes on all these values. To satisfy the column
for our new Room square we also require that no *R*<sub>*i**j*</sub> occurs above or below an *R*<sub>*i**k*</sub> or *R*<sub>*k**j*</sub>, and
that reason we must also insist that for any super-column of *R*<sub>*i**j*</sub>s, *i* and *j* independently
values 1..3, so that each member of *S* ∖ {∞} occurs once in the corresponding 7 columns of
finished Room square – (except for the missing {*x*<sub>*i*</sub> : 0 ≤ *x* ≤ 6} from all columns *x*<sub>*i*</sub>).
Furthermore, as we are aiming for an array in which all the unordered pairs from *S* occur
once if we also insist that each value of *i* is paired with each value of *j* exactly once in
super-array then we should obtain most of these pairs. In fact, because *R*<sub>*i**j*</sub> ∪ *R*<sub>*j**i*</sub> contains
unordered pairs from {9<sub>*i*</sub>, *o*<sub>*j*</sub>, 1<sub>*i*</sub>, 1<sub>*j*</sub>, ..., 6<sub>*i*</sub>, 6<sub>*j*</sub>}, except those of the form {*x*<sub>*i*</sub>, *x*<sub>*j*</sub>} 1 ≤ *i*, *j* ≤ 3
shall obtain all the unordered pairs of *S* except those of the form
{∞,*x*<sub>1</sub>},{∞, *x*<sub>2</sub>},{∞, *x*<sub>3</sub>},{*x*<sub>1</sub>, *x*<sub>2</sub>},{*x*<sub>1</sub>, *x*<sub>3</sub>},{*x*<sub>2</sub>, *x*<sub>3</sub>},0 ≤ *x* ≤ 6
The ideal solution to this problem (because it solves the problem of missing pairs as well as completing rows/columns) would be to place pairs of the form {∞,*x*<sub>*j*</sub>} and {*x*<sub>*i*</sub>, *x*<sub>*j*</sub>} at the intersection of rows *x*<sub>*j*</sub> and column *x*<sub>*j*</sub>, but of course this intersection is a single box, and we don’t want two pairs in one box. Wallis’s solution to this problem was to permute the columns of some of the *R*<sub>*i**j*</sub>s from one super-column of the array of frames with the intention of arranging it so that the elements *x*<sub>*i*</sub> *x*<sub>*j*</sub> would be vacant from some column *y* ≠ *x*<sub>*j*</sub>. This enables us to put the {∞,*x*<sub>*j*</sub>} in column *x*<sub>*j*</sub> and the {*x*<sub>*i*</sub>, *x*<sub>*j*</sub>} in column *y*.
*Example,*
The elements missing from row 0<sub>1</sub>, $ , 0\_1, 0\_2, 0\_3$, are also missing from column 0<sub>1</sub> (due to the removal of the pair {∞,0} from the original Room square to create the frame). There is no problem in putting {∞,0<sub>1</sub>} in position (0<sub>1</sub>, 0<sub>1</sub>), but if we want to put {0<sub>2</sub>, 0<sub>3</sub>} in row 0<sub>1</sub> it must go in some other column of block *R*<sub>11</sub>, while remaining in column 1<sub>1</sub> of blocks *R*<sub>23</sub> and *R*<sub>32</sub>, this can be achieved through a column permutation applied only to *R*<sub>23</sub> and *R*<sub>32</sub>.
Notice that it would be of little use to swap columns 0<sub>1</sub> and 4<sub>1</sub> of blocks *R*<sub>23</sub> and *R*<sub>32</sub>, as the fourth column is occupied already in the first row of block *R*<sub>11</sub>. But we could swap 0<sub>1</sub> with any of 1<sub>1</sub>, 2<sub>1</sub>, 3<sub>1</sub> or 5<sub>1</sub> because all these columns are empty in row 0<sub>1</sub>. Clearly the essential property we require of any column permutation that we decide to use, call it *θ*, is that (*x*, *x**θ*) is unoccupied in the original Room square.

#### Lemma 3.8.1

Given a Room square *R* of side *r*, where *r* = 2*s* + 1, there are *s* permutations *ϕ*<sub>1</sub>, *ϕ*<sub>2</sub>, ..., *ϕ*<sub>*s*</sub> of {1, 2, ..., *r*} with the properties that *k**ϕ*<sub>*i*</sub> = *k**ϕ*<sub>*j*</sub> never occurs unless *i* = *j*, and that cell (*k*, *k**ϕ*<sub>*i*</sub>) is empty for 1 ≤ *k* ≤ *r*, 1 ≤ *i* ≤ *s*.
*Proof*
We define a matrix *M* in the following manner:
If position (*k*, *l*) is *empty* in *R* then the (*k*, *l*) position of *M* is 1, otherwise it is 0.
Because *M* is a matrix of 0s and 1s, whose every row and column sum is equal to *s*, it can be decomposed into *s* matrices, each of which having exactly one 1 in each row and column[8].
*M* = *P*<sub>1</sub> + *P*<sub>2</sub> + ... + *P*<sub>*s*</sub>
 These matrices ,when interpreted in the following or similar manner, are known as
**permutation matrices**:
Define *ϕ*<sub>*i*</sub> as the permutation corresponding to matrix *P*<sub>*i*</sub> such that if (*k*, *l*) is 1 in *P*<sub>*i*</sub> then *k**ϕ*<sub>*i*</sub> = *l*.
The definition of *M* ensures that the (*k*, *k**ϕ*<sub>*i*</sub>), so *M* would have an entry equal to 2 or more, contradicting the definition.
*Example* cont...,
The matrix *M* associated with the square from Figure 19 is:

$$\\begin{gathered}
M=
  \\begin{bmatrix}
  0 & 1 & 1 & 0 & 1 & 0 & 0\\\\
  0 & 0 & 1 & 1 & 0 & 1 & 0\\\\
  0 & 0 & 0 & 1 & 1 & 0 & 1\\\\
  1 & 0 & 0 & 0 & 1 & 1 & 0\\\\
  0 & 1 & 0 & 0 & 0 & 1 & 1\\\\
  1 & 0 & 1 & 0 & 0 & 0 & 1\\\\
  1 & 1 & 0 & 1 & 0 & 0 & 0\\\\
  \\end{bmatrix}\\end{gathered}$$

Which can be decomposed (not uniquely) into these permutation matrices:

$$\\begin{gathered}
M= P\_1 + P\_2 + P\_3 = 
  \\begin{bmatrix}
  0 & 1 & 0 & 0 & 0 & 0 & 0\\\\
  0 & 0 & 1 & 0 & 0 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 1 & 0 & 0\\\\
  1 & 0 & 0 & 0 & 0 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 0 & 1 & 0\\\\
  0 & 0 & 0 & 0 & 0 & 0 & 1\\\\
  0 & 0 & 0 & 1 & 0 & 0 & 0\\\\
  \\end{bmatrix}
  +
  \\begin{bmatrix}
  0 & 0 & 0 & 0 & 1 & 0 & 0\\\\
  0 & 0 & 0 & 1 & 0 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 0 & 0 & 1\\\\
  0 & 0 & 0 & 0 & 0 & 1 & 0\\\\
  0 & 1 & 0 & 0 & 0 & 0 & 0\\\\
  0 & 0 & 1 & 0 & 0 & 0 & 0\\\\
  1 & 0 & 0 & 0 & 0 & 0 & 0\\\\
  \\end{bmatrix}
  +
  \\begin{bmatrix}
  0 & 0 & 1 & 0 & 0 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 0 & 1 & 0\\\\
  0 & 0 & 0 & 1 & 0 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 1 & 0 & 0\\\\
  0 & 0 & 0 & 0 & 0 & 0 & 1\\\\
  1 & 0 & 0 & 0 & 0 & 0 & 0\\\\
  0 & 1 & 0 & 0 & 0 & 0 & 0\\\\
  \\end{bmatrix}\\end{gathered}$$

The permutations associated with these matrices are, in cycle notation:
*ϕ*<sub>1</sub> = (1235674),*ϕ*<sub>2</sub> = (1524637),*ϕ*<sub>3</sub> = (1345726)
 If we choose to apply *ϕ*<sub>1</sub> to the columns of blocks *R*<sub>23</sub> and *R*32 we get:

<span>|c|c|c|c|c|c|c|c|</span>

|      |
|:----:|
| Col/ |
|  Row |

& 0<sub>1</sub> & 1<sub>1</sub> & 2<sub>1</sub> & 3<sub>1</sub> & 4<sub>1</sub> & 5<sub>1</sub> & 6<sub>1</sub>
0<sub>1</sub> & & & & 2<sub>15<sub>1</sub></sub> & & 1<sub>16<sub>1</sub></sub> & 3<sub>14<sub>1</sub></sub>
1<sub>1</sub> & 4<sub>15<sub>1</sub></sub> & & & & 3<sub>16<sub>1</sub></sub> & & 2<sub>10<sub>1</sub></sub>
2<sub>1</sub> & 3<sub>11<sub>1</sub></sub> & 5<sub>16<sub>1</sub></sub> & & & & 4<sub>10<sub>1</sub></sub> &
3<sub>1</sub> & & 4<sub>12<sub>1</sub></sub> & 6<sub>10<sub>1</sub></sub> & & & & 5<sub>11<sub>1</sub></sub>
4<sub>1</sub> & 6<sub>12<sub>1</sub></sub> & & 5<sub>13<sub>1</sub></sub> & 0<sub>11<sub>1</sub></sub> & & &
5<sub>1</sub> & & 0<sub>13<sub>1</sub></sub> & & 6<sub>14<sub>1</sub></sub> & 1<sub>12<sub>1</sub></sub> & &
6<sub>1</sub> & & & 1<sub>14<sub>1</sub></sub> & & 0<sub>15<sub>1</sub></sub> & 2<sub>13<sub>1</sub></sub> &
0<sub>2</sub> & 2<sub>35<sub>2</sub></sub> & & & 3<sub>34<sub>2</sub></sub> & & & 1<sub>36<sub>2</sub></sub>
1<sub>2</sub> & & 4<sub>35<sub>2</sub></sub> & & 2<sub>30<sub>2</sub></sub> & & 3<sub>36<sub>2</sub></sub> &
2<sub>2</sub> & & 3<sub>31<sub>2</sub></sub> & 5<sub>36<sub>2</sub></sub> & & & & 4<sub>30<sub>2</sub></sub>
3<sub>2</sub> & & & 4<sub>32<sub>2</sub></sub> & 5<sub>31<sub>2</sub></sub> & 6<sub>30<sub>2</sub></sub>& &
4<sub>2</sub> & 0<sub>31<sub>2</sub></sub> & 6<sub>32<sub>2</sub></sub> & & & 5<sub>33<sub>2</sub></sub> & &
5<sub>2</sub> & 6<sub>34<sub>2</sub></sub> & & 0<sub>33<sub>2</sub></sub> & & & 1<sub>32<sub>2</sub></sub> &
6<sub>2</sub> & & & & & 1<sub>34<sub>2</sub></sub> & 0<sub>35<sub>2</sub></sub> & 2<sub>33<sub>2</sub></sub>
0<sub>3</sub> & 2<sub>25<sub>3</sub></sub> & & & 3<sub>24<sub>3</sub></sub> & & & 1<sub>26<sub>3</sub></sub>
1<sub>3</sub> & & 4<sub>25<sub>3</sub></sub> & & 2<sub>20<sub>3</sub></sub> & & 3<sub>26<sub>3</sub></sub> &
2<sub>3</sub> & & 3<sub>21<sub>3</sub></sub> & 5<sub>26<sub>3</sub></sub> & & & & 4<sub>20<sub>3</sub></sub>
3<sub>3</sub> & & & 4<sub>22<sub>3</sub></sub> & 5<sub>21<sub>3</sub></sub> & 6<sub>20<sub>3</sub></sub> & &
4<sub>3</sub> & 0<sub>21<sub>3</sub></sub> & 6<sub>22<sub>3</sub></sub> & & & 5<sub>23<sub>3</sub></sub> & &
5<sub>3</sub> & 6<sub>24<sub>3</sub></sub> & & 0<sub>23<sub>3</sub></sub> & & & 1<sub>22<sub>3</sub></sub> &
6<sub>3</sub> & & & & & 1<sub>24<sub>3</sub></sub> & 0<sub>25<sub>3</sub></sub> & 2<sub>23<sub>3</sub></sub>
**Figure 24**

Which leaves us free to put {∞,*x*<sub>1</sub>} into (*x*<sub>1</sub>, *x*<sub>1</sub>) and {*x*<sub>2</sub>, *x*<sub>3</sub>} into (*x*<sub>1</sub>, (*x**ϕ*<sub>1</sub>)<sub>1</sub>)
e.g. {1<sub>2</sub>, 1<sub>3</sub>} can go into (2<sub>1</sub>, (2*ϕ*<sub>1</sub>)<sub>1</sub>)=(2<sub>1</sub>, 3<sub>1</sub>). The permutation chosen ensures that cell (2, 3) of the original square is empty.
Filling in the rest of block *R*11 gives:

<span>|c|c|c|c|c|c|c|c|</span>

|      |
|:----:|
| Col/ |
|  Row |

& 0<sub>1</sub> & 1<sub>1</sub> & 2<sub>1</sub> & 3<sub>1</sub> & 4<sub>1</sub> & 5<sub>1</sub> & 6<sub>1</sub>
0<sub>1</sub> & ∞, 0<sub>1</sub> & 0<sub>20<sub>3</sub></sub> & & 2<sub>15<sub>1</sub></sub> & & 1<sub>16<sub>1</sub></sub> & 3<sub>14<sub>1</sub></sub>
1<sub>1</sub> & 4<sub>15<sub>1</sub></sub> & ∞, 1<sub>1</sub> & 1<sub>21<sub>3</sub></sub> & & 3<sub>16<sub>1</sub></sub> & & 2<sub>10<sub>1</sub></sub>
2<sub>1</sub> & 3<sub>11<sub>1</sub></sub> & 5<sub>16<sub>1</sub></sub> & ∞, 2<sub>1</sub> & & 2<sub>22<sub>3</sub></sub> & 4<sub>10<sub>1</sub></sub> &
3<sub>1</sub> & 3<sub>23<sub>3</sub></sub> & 4<sub>12<sub>1</sub></sub> & 6<sub>10<sub>1</sub></sub> & ∞, 3<sub>1</sub> & & & 5<sub>11<sub>1</sub></sub>
4<sub>1</sub> & 6<sub>12<sub>1</sub></sub> & & 5<sub>13<sub>1</sub></sub> & 0<sub>11<sub>1</sub></sub> & ∞, 4<sub>1</sub> & 4<sub>24<sub>3</sub></sub> &
5<sub>1</sub> & & 0<sub>13<sub>1</sub></sub> & & 6<sub>14<sub>1</sub></sub> & 1<sub>12<sub>1</sub></sub> & ∞, 5<sub>1</sub> & 5<sub>25<sub>3</sub></sub>
6<sub>1</sub> & & & 1<sub>14<sub>1</sub></sub> & 6<sub>26<sub>3</sub></sub> & 0<sub>15<sub>1</sub></sub> & 2<sub>13<sub>1</sub></sub> & ∞, 6<sub>1</sub>
**Figure 25**

Notice that this satisfies the row and column properties of a Room square for the first seven rows and columns.
Next we move onto the second diagonal block, because missing from row and column *x*<sub>2</sub> are the elements ∞, *x*<sub>1</sub>, *x*<sub>2</sub>, *x*<sub>3</sub>. However this time we try to find a home for pairs of the form {∞,*x*<sub>2</sub>} and {*x*<sub>1</sub>, *x*<sub>3</sub>}.
We can put pairs of the form {*x*<sub>1</sub>, *x*<sub>3</sub>} down the diagonal and permute the columns of block *R*<sub>22</sub> with a permutation from Lemma 3.8.1 to ensure that column (*x**ϕ*<sub>2</sub>)<sub>2</sub> has no *x*<sub>2</sub>, allowing us to put {∞,*x*<sub>2</sub>} in that column.
For instance, using *ϕ*<sub>2</sub> we can complete block *R*<sub>13</sub>, and the corresponding seven rows and columns, by putting:

{*x*<sub>1</sub>, *x*<sub>3</sub>} in *x*<sub>2</sub>, *x*<sub>2</sub>
and {∞,*x*<sub>2</sub>} in *x*<sub>2</sub>, (*x**ϕ*<sub>2</sub>)<sub>2</sub>
Taking the same approach with the third diagonal block we permute columns in *R*<sub>33</sub> using *ϕ*<sub>3</sub>[9] and fill-in by putting:

{*x*<sub>1</sub>, *x*<sub>2</sub>} in *x*<sub>3</sub>, *x*<sub>3</sub>
and {∞,*x*<sub>3</sub>} in *x*<sub>3</sub>, (*x**ϕ*<sub>3</sub>)<sub>3</sub>
Which results in a Room square of side 21 based on:
*S* = {∞,0<sub>1</sub>, 1<sub>1</sub>, ..., 6<sub>1</sub>, 0<sub>2</sub>, 1<sub>2</sub>, ..., 6<sub>2</sub>, 0<sub>3</sub>, 1<sub>3</sub>, ..., 6<sub>3</sub>}
 This square is straightforwardly transformed to a Room square based on {∞,0, 1, ..., 20}, Figure 26, by using:
*x*<sub>*i*</sub> = *x* + 7(*i* − 1)
 We could have done this from the beginning, but it is perhaps simpler to keep track of the missing elements by maintaining the subscript notation.
The preceding triplication was slightly contrived because the arrangement of frames at the beginning was so chosen because it satisfied a property as yet unexplained. This property being that the *R*<sub>*i**j*</sub> and *R*<sub>*j**i*</sub> occur in the same super-column of the array as frames. Clearly this must be so in order that permutations, when applied to both or neither of *R*<sub>*i**j*</sub> and *R*<sub>*j**i*</sub>, preserve the contents of the columns as far as is required.
That an arrangement of frames with this property can be guaranteed to exist for any odd integer is fundamental to the generalised theorem.

#### Lemma 3.8.2

For all odd *n* there exists an array with these properties:

1.  the entries of the array consist of all the ordered pairs of the set *N* = {1, 2, ..., *n*} once each.

2.  the entries of a given row or column contain between them every member of *N* once as a left member and once as a right member.

3.  if (*x*, *y*) occurs in a given column of the array (*y*, *x*) also occurs in that column.

*Proof*
*A*<sub>*n*</sub> is an *n* × *n* array whose (*i*, *j*) entry is the ordered pair (*j* − *i* + 1, *i* + *j* − 1) with both elements being reduced modulo *n* to lie on the interval \[1, *n*\].

1.  There are clearly *n*<sup>2</sup> ordered pairs obtainable from *N*. *A*<sub>*n*</sub> has *n*<sup>2</sup> cells, so it is only necessary to show that each cell contains a unique pair. For that reason consider any two pairs from different cells, (*x*<sub>1</sub>, *y*<sub>1</sub>) and (*x*<sub>2</sub>, *y*<sub>2</sub>), for these to be equal requires both,

    *x*<sub>1</sub> = *x*<sub>2</sub> and *y*<sub>1</sub> = *y*<sub>2</sub>

    Now, *x*<sub>1</sub> = *x*<sub>2</sub>
    ⇒*j*<sub>1</sub> − *i*<sub>1</sub> + 1 = *j*<sub>2</sub> − *i*<sub>2</sub> + 1
     While, *y*<sub>1</sub> = *y*<sub>2</sub>
    ⇒*i*<sub>1</sub> + *j*<sub>1</sub> − 1 = *i*<sub>2</sub> + *j*<sub>2</sub> − 1
     Together these imply,
    $$j\_1-i\_1=j\_2-i\_2 \\hspace{1cm}(1)$$
    $$i\_1+j\_1=i\_2+j\_2 \\hspace{1cm}(2)$$
     (2) gives, *j*<sub>2</sub> = *i*<sub>1</sub> + *j*<sub>1</sub> − *i*<sub>2</sub>, which on substitution in (1) gives,
    *j*<sub>1</sub> − *i*<sub>1</sub> = *i*<sub>1</sub> + *j*<sub>1</sub> − 2*i*<sub>2</sub>
    ⇒2*i*<sub>1</sub> − 2*i*<sub>2</sub> = 0
    ∴*i*<sub>1</sub> = *i*<sub>2</sub>
     Substituting this into either expression gives *j*<sub>1</sub> = *j*<sub>2</sub>.
    Thereby contradicting the assumption that the pairs occurred in different cells. Hence every cell contains a unique pair, so all the ordered pairs from *N* occur exactly once in *A*<sub>*n*</sub>.

2.  Consider row *i* of *A*<sub>*n*</sub>:

    |     *j* = 1    |       *j* = 2      | ... |      *j* = −1     |       *j* = 0      |
    |:--------------:|:------------------:|:---:|:-----------------:|:------------------:|
    | (2 − *i*, *i*) | (3 − *i*, *i* + 1) | ... | ( − *i*, *i* − 2) | (1 − *i*, *i* − 1) |

    Left hand members are {2 − *i*, 3 − *i*, ..., 1 − *i*}, while the right hand members are {*i*, *i* + 1, ..., *i* − 1}. Both sets contain *n* unique integers on the interval \[1, *n*\] and hence both sets must be *N*, Similarly, consider column *j*, the left hand positions are occupied by {*j*, *j* − 1, ..., *j* + 2, *j* + 1}, while the right contain {*j*, *j* + 1, ..., *j* − 2, *j* − 1}. For the same reasons both these sets are equal to *N*.

3.  Consider a pair (*x*, *y*), from the definition of *A*<sub>*n*</sub>,
    *x* = *j* − *i* + 1
    *y* = *i* + *j* − 1
    *x* + *y* = *j* − *i* + 1 + *i* + *j* − 1 = 2*j*
    $\\therefore j= \\frac{1}{2} (x+y)$
    So if (*x*, *y*) is in column *j* of *A*<sub>*n*</sub> then so is (*y*, *x*), since $\\frac{1}{2}(x+y)=\\frac{1}{2}(y+x)$.

We can now present the general result.

#### Theorem 3.8.1 \[25\]

If *r* and *n* are odd integers such that *r* ≥ *n*, and if there is a Room square *R* of side *r*, then there is a Room square of side *r**n*.
*Proof*
Let *r* = 2*d* + 1 and *n* = 2*t* + 1.
For a given *i* select *n* permutations as follows:

1.  *ϕ*<sub>*j**k*</sub> = *ϕ*<sub>*j**l*</sub> if, and only if, (*k*, *l*), and (*l*, *k*) appear in column *j* of *A*<sub>*n*</sub>.

2.  If cell (*j*, *j*) of *A*<sub>*n*</sub> contains (*x*, *y*) then *ϕ*<sub>*j**x*</sub> = *ϕ*<sub>*j**y*</sub> = *i**d* (the identity permutation).

3.  All the *ϕ*<sub>*j**k*</sub>(≠*i**d*) are selected from the permutations associated with *R*, according to Lemma 3.8.1

Now a Room square of side *r**n* is constructed by replacing each entry (*k*, *l*) of *A*<sub>*n*</sub> by *R*<sub>*k**l*</sub>*ϕ*<sub>*j**k*</sub> (the array *R*<sub>*k**l*</sub> under the column permutation *ϕ*<sub>*j**k*</sub>), where (*k*, *l*) is in column *j* of *A*<sub>*n*</sub>.
The resulting array has each element of,
*S* = {0<sub>1</sub>, 1<sub>1</sub>, ..., (*r* − 1)<sub>1</sub>, 0<sub>2</sub>, 1<sub>2</sub>, ..., (*r* − 1)<sub>2</sub>, 0<sub>*n*</sub>, 1<sub>*n*</sub>, ..., (*r* − 1)<sub>*n*</sub>}
 appearing exactly once in each row and column, except that *x*<sub>*j*</sub> is missing from row and column *x*<sub>*j*</sub>, $1 \\leq j \\leq n \\hspace{0.4cm} 0 \\leq x \\leq (r-1)$, and *x*<sub>*k*</sub> and *x*<sub>*l*</sub> are missing from column (*x**ϕ*<sub>*j**k*</sub>)<sub>*j*</sub> for each entry (*k*, *l*) in column *j* of *A*<sub>*n*</sub>.
The array also contains every unordered pair from *S* exactly once, except those of the form {*x*<sub>*k*</sub>, *x*<sub>*l*</sub>}.
Now, for each *k*, if (*k*, *l*) is an entry of column *j* of *A*<sub>*n*</sub> put {*x*<sub>*k*</sub>, *x*<sub>*l*</sub>} in (*x*<sub>*j*</sub>, (*x**ϕ*<sub>*j**k*</sub>)<sub>*j*</sub>), using {∞,*x*<sub>*j*</sub>} instead of {*x*<sub>*j*</sub>, *x*<sub>*j*</sub>} in every case.
The completed array contains each of {∞} ∪ *S* exactly once per row and column and every unordered pair from the same set exactly once.
Finally, map {∞} ∪ *S* onto {∞} ∪ *Z*<sub>*r**n*</sub> by replacing every *x*<sub>*i*</sub> by *x* + *r*(*i* − 1). The finished array is a Room square of side *r**n*.
*Example*
Looking back at the previous example of triplication.

$A\_3 = $

|     |  1  |  2  |  3  |
|-----|:---:|:---:|:---:|
| 1   | 1,1 | 2,2 | 3,3 |
| 2   | 3,2 | 1,3 | 2,1 |
| 3   | 2,3 | 3,1 | 1,2 |

Now, in column 1 (3,2) and (2,3) both appear, so
*ϕ*<sub>13</sub> = *ϕ*<sub>12</sub>
 While in column 2 occur both (1,3) and (3,1), so
*ϕ*<sub>21</sub> = *ϕ*<sub>23</sub>
 Furthermore, both (2,1) and (1,2) appear in the third column, so
*ϕ*<sub>32</sub> = *ϕ*<sub>31</sub>
 The diagonal pairs are (1,1),(1,3),(1,2) so *ϕ*<sub>11</sub> = *ϕ*<sub>21</sub> = *ϕ*<sub>23</sub> = *ϕ*<sub>31</sub> = *ϕ*<sub>32</sub> = *i**d*
The remaining permutations, *ϕ*<sub>12</sub>, *ϕ*<sub>13</sub>, *ϕ*<sub>22</sub>, *ϕ*<sub>33</sub> are chosen according to the Lemma 3.8.1 and the following array is the Room square in Fig 26 once the missing pairs have been placed and the transformation to {∞,0, 1, ..., 20} made.

| *R*<sub>11</sub>*ϕ*<sub>11</sub> | *R*<sub>22</sub>*ϕ*<sub>22</sub> | *R*<sub>33</sub>*ϕ*<sub>33</sub> |
|:--------------------------------:|:--------------------------------:|:--------------------------------:|
| *R*<sub>32</sub>*ϕ*<sub>13</sub> | *R*<sub>13</sub>*ϕ*<sub>21</sub> | *R*<sub>21</sub>*ϕ*<sub>32</sub> |
| *R*<sub>23</sub>*ϕ*<sub>12</sub> | *R*<sub>31</sub>*ϕ*<sub>23</sub> | *R*<sub>12</sub>*ϕ*<sub>31</sub> |

=

|      *R*<sub>11</sub>*i**d*     | *R*<sub>22</sub>*ϕ*<sub>2</sub> | *R*<sub>33</sub>*ϕ*<sub>3</sub> |
|:-------------------------------:|:-------------------------------:|:-------------------------------:|
| *R*<sub>32</sub>*ϕ*<sub>1</sub> |      *R*<sub>13</sub>*i**d*     |      *R*<sub>21</sub>*i**d*     |
| *R*<sub>23</sub>*ϕ*<sub>1</sub> |      *R*<sub>31</sub>*i**d*     |      *R*<sub>12</sub>*i**d*     |

Balanced Room squares
=====================

BIBDs and BRBs
--------------

A ***balanced incomplete block design (BIBD)*** is an arrangement of elements (varieties) from a set *S* of size *v*, into *b* subsets (blocks) each of size *k* such that each variety occurs in *r* blocks and any particular pair of distinct varieties occurs in *λ* blocks.

#### Example 5.1.1

{*a*, *b*, *c*},{*a*, *b*, *d*},{*a*, *c*, *e*},{*a*, *d*, *f*},{*a*, *e*, *f*},{*b*, *c*, *f*},{*b*, *d*, *e*},{*b*, *e*, *f*},{*c*, *d*, *e*},{*c*, *d*, *f*}
 This is a BIBD with parameters: *v* = 6, *b* = 10, *k* = 3, *r* = 5, *λ* = 2.

In any *B**I**B**D*(*v*, *b*, *r*, *k*, *λ*) there are *b* blocks each containing *k* elements, so *b**k* elements in total. Also, each of the *v* elements occurs *r* times, so there are *r**v* elements in total. Therefore:
*b**k* = *v**r*
 Also in a particular block, any element makes a pair with *k* − 1 other elements, and each element occurs in *r* blocks, so there are *r*(*k* − 1) pairs involving that element. Also, by definition, that element is paired with each of the other *v* − 1 members of *S* *λ* times, so:
*λ*(*v* − 1)=*r*(*k* − 1)
 The second expression rearranges to give *r* = *λ*(*v* − 1)/(*k* − 1), which can be substituted into the first expression to give *b* = *v**λ*(*v* − 1)/*k*(*k* − 1). So *b* amd *r* are both determined by the values of *v*, *k* and *λ*. For this reason we need only quote those three parameters when referring to a particular block design. The example was a *B**I**B**D*(6, 3, 2) (or (6, 3, 2)design).

In any Room square, the pairs {*x*, *y*} are unordered. If we replace these pairs by one of the ordered pairs (*x*, *y*) or (*y*, *x*) we call the resulting array an ***ordered Room square (ORS)***.

Consider the following ordered Room square:

|  ∞0 |  62 |  54 |     |  31 |     |     |
|:---:|:---:|:---:|-----|:---:|-----|-----|
|     |  ∞1 |  03 | 65  |     | 42  |     |
|     |     |  ∞2 | 14  |  06 |     | 53  |
|  64 |     |     | ∞3  |  25 | 10  |     |
|     |  05 |     |     |  ∞4 | 36  | 21  |
|  32 |     |  16 |     |     | ∞5  | 40  |
|  51 |  43 |     | 20  |     |     | ∞6  |

**Figure 27**

Suppose we extract the blocks of a design (not necessarily a BIBD) from this square in one of the two following ways:

1.  As *half-columns*. This means taking all left hand members of pairs from a particular column as the members of one block, and all right hand members as another block.

2.  By *half-rows*. Take all left members from a particular row as one block, and all right members as another block.

Notice that for this example, both methods generate exactly the same blocks.
{∞,6, 5, 3},{0, 2, 4, 1},{∞, 0, 6, 4},{1, 3, 5, 2},{∞, 1, 0, 5},{2, 4, 6, 3},{6, ∞, 2, 1},
{4, 3, 5, 0},{0, ∞, 3, 2},{5, 4, 6, 1},{3, 1, ∞, 4},{2, 6, 5, 0},{5, 4, 2, ∞},{1, 3, 0, 6}
 Certainly this design seems to have the appropriate parameters to qualify as a BIBD. The original Room square was based on 8 elements, hence *v* = 8. Also, the Room square’s seven rows each produced 2 blocks of 4 elements, hence *b* = 14 and *k* = 4. Finally, each element occurred once in each row of the Room square, therefore in half the total number of blocks, hence *r* = 7.
*b**k* = 4 ⋅ 14 = 7 ⋅ 8 = *v**r*
 So this design is a BIBD, provided:
$$\\lambda = \\frac{r(k-1)}{v-1} = \\frac{7(3)}{7}=3$$
 In other words, provided each pair of elements occurs in precisely 3 blocks.

By definition a ***balanced Room square \[*B**R**S*(*n*)\]*** is an ordered Room square based on *n* elements whose corresponding block design, derived as above, is a BIBD.

Complete Balanced Howell Rotations
----------------------------------

Edwin C. Howell is an enigmatic figure in the history of mathematics. The rotations named after him are designs for the scheduling of Bridge tournaments.

In a duplicate bridge tournament players compete in partnerships, two partnerships at a table. At the beginning of a round each table is given one from a certain number of duplicate boards each of which contains a pack of cards dealt evenly into four pockets. The boards are labelled north-south-east-west, and are aligned on the table so that one partnership plays north-south and the other east-west. After the game is finished the cards are returned to the pockets as they were dealt and the duplicate board is returned, to be used again in subsequent matches.

If one partnership plays directly against another at the same table, the two partnerships are said to *oppose* each other. If two partnerships play in the same direction on the same board in different rounds, they are said to *compete*.

In scoring, not only is the performance of teams in opposition considered, but also the performance of partnerships which compete.

A good tournament design would have the properties that each partnership opposed each other partnership at the same table exactly once and also that each partnership competed against each other partnership at the same number of times.

A \*\*\*\*complete balanced Howell rotation \[*C**B**H**R*(*n*)\]\*\*\*\*[10] is an array (based on *n* elements) of side *s*, where *s* = *n* for *n* odd, and *s* = *n* − 1 for *n* even, which satisfies the following properties:

1.  Each of the *s*<sup>2</sup> cells is empty or contains an ordered pair of distinct elements.

2.  Each of the *n* elements appears exactly once in each row and each column. (If *n* is odd, then one row and one column is excepted)

3.  Each unordered pair of distinct elements occurs in exactly one cell of the array.

4.  Each pair of distinct elements appears together in a block[11] exactly ⌊*n*/2⌋ − 1 times, where $$ means the integral part of *x*.

To interpret a CBHR as a duplicate bridge tournament schedule, we represent the partnerships by elements, the boards ny rows and the rounds of the tournament by columns.

Then an ordered pair (*x*, *y*) in position (*i*, *j*) of the array corresponds to partnership *x* opposing partnership *y* on board *i* in round *j*. We adopt the convention that *x* plays NS, *y* EW. The third property in the definition of a CBHR ensures that all partnerships are in opposition exactly once, while the fourth (with blocks of the associated BIBD representing partnerships in competition) ensures that each partnership competes against each other partnership the same number of times.

Notice that when *n* is even the definition of a CBHR is precisely that of a balanced Room square. So the BRS above is also a *C**B**H**R*(8). The reason for maintaining both definitions is that a CBHR is, according to conditions 2 and 4, allowed to have odd order. Also, an important construction for *B**R**S*(4*n*), which will be introduced, involves two *C**B**H**R*(2*n* − 1)s.

Unlike Room squares the question of the existence of balanced Room squares is far from resolved, but various proofs have shown there to be many infinite classes of these designs. The details of some of these proofs are given below.

Interestingly the existence problem for balanced Room squares (then known exclusively as CBHR) was brought to the attention of mathematicians, in 1955 by Parker and Mood, the very same year as T.G. Room published his original article. Either this problem has proved to be very much more difficult, or has aroused significantly less interest. The first general result, that of Hwang (1970), coming only a few years before the corresponding problem for Room squares was settled (1973).

In order to discuss these results the first step is to make the necessary adaptation of the starter-adder approach.

Starters and Adders for BRS and CBHR
------------------------------------

In deriving the definitions of a starter and adder for a Room square, the terminology of difference systems was introduced. We saw that a requirement of the starter was that each non-zero member of the relevant Galois field occurred exactly once as a difference between the members of some pair. This was so that each pair occurred exactly once in the Room square
BIBDs can be constructed from difference systems in much the same way, but with the difference that each element in the BIBD occurs occurs with each other element *λ* times, not necessarily just once.
*Example*
A BIBD on *G**F*(7) can be constructed from the sets {6, 5, 3}{2, 4, 1}.
{0, 6, 4},{1, 0, 5},{2, 1, 6},{3, 2, 0},{4, 3, 1},{5, 4, 2} are the blocks obtained from the left hand set.
{3, 5, 2},{4, 6, 3},{5, 0, 4},{6, 1, 5},{0, 2, 6},{1, 3, 0} are the blocks obtained from the right hand set.
Because the two sets are both triples, under cyclic construction the block design obtained will necessarily have *k* = *r* = 3.
The left hand set has each non-zero member of *G**F*(7) occurring exactly once as a difference between its members. So, taken with its translates (those blocks obtained from it under cyclic development), this set should form a BIBD with *r* = 3 and *λ* = 1. Similarly the right hand block forms a BIBD with *r* = 3 and *λ* = 1, and the two sets taken together as difference system therefore generate a BIBD with *r* = 6 and *λ* = 2.
If we add the ideal element ∞ to the left hand set and all its translates, and 0 to the right hand set (developing it cyclically along with the other members) then we obtain a new BIBD with *r* = 7 and *λ* = 3, whose blocks are:
{∞,6, 5, 3},{∞, 0, 6, 4},{∞, 1, 0, 5},{∞, 2, 1, 6},{∞, 3, 2, 0},{∞, 4, 3, 1},{∞, 5, 4, 2}
{0, 2, 4, 1},{1, 3, 5, 2},{2, 4, 6, 3},{3, 5, 0, 4},{4, 6, 1, 5},{5, 0, 2, 6},{6, 1, 3, 0}
 Which is precisely the BIBD obtained from the Room square at the beginning of this chapter. If the block design associated with a BRS, or a CBHR, is obtained by taking the left hand member of the pairs in the first row as one block and the left hand members in subsequent rows as the translates, and all right members of pairs as the remaining blocks of a BIBD, then clearly those two blocks, the left hand and the right hand, which belong to the starter must form a difference system.
The set of pairs (*x*<sub>1</sub>, *y*<sub>1</sub>),(*x*<sub>2</sub>, *y*<sub>2</sub>),...,(*x*<sub>*n* − 1</sub>, *y*<sub>*n* − 1</sub>) is a ***balanced starter*** in *G* = *G**F*(2*n* − 1) if

1.  the unordered pairs {*x*<sub>*i*</sub>, *y*<sub>*i*</sub>} form a starter in *G*, and

2.  the blocks {*x*<sub>1</sub>, *x*<sub>2</sub>, ..., *x*<sub>*n* − 1</sub>} and {*y*<sub>1</sub>, *y*<sub>2</sub>, ..., *y*<sub>*n* − 1</sub>} form a difference system.

A balanced starter is ***strong*** if *x*<sub>1</sub> + *y*<sub>1</sub>, *x*<sub>2</sub> + *y*<sub>2</sub>, ..., *x*<sub>*n* − 1</sub> + *y*<sub>*n* − 1</sub> are all distinct mod(2*n* − 1).

#### Theorem 5.3.1

Given a strong balanced starter on *G* = *G**F*(2*n* − 1), then a *C**B**H**R*(2*n* − 1) exists.
*Proof*
Assign the pair (*x*<sub>*i*</sub> + *g*, *y*<sub>*i*</sub> + *g*) to cell (*g*, *x*<sub>*i*</sub> + *y*<sub>*i*</sub> + *g*) for all *g* ∈ *G*. Condition (i) along with the strong-ness of the starter ensures that every *g* ∈ *G* occurs in every row and column exactly once except *g* does not occur in row or column *g* for all *g* ∈ *G* \[due to the absence in cell (0,0) of the pair {∞,0}\]. Condition (i) also ensures that each unordered pair of *G* occurs exactly once in the array, replace the unordered pairs with ordered pairs.
That the block design obtained is balanced follows from condition (ii).
Notice that each of the 2 blocks generates (*n* − 1)(*n* − 2) differences and these represent each of 2*n* − 2 members of *G* ∖ {0}, *λ* times. Therefore 2(*n* − 1)(*n* − 2)=*λ*(2*n* − 2), $ = n-2$.

#### Theorem 5.3.2

Given a strong balanced starter on *G* = *G**F*(2*n* − 1), then a *B**R**S*(2*n*) exists.
*Proof*
Assign the pair (*x*<sub>*i*</sub> + *g*, *y*<sub>*i*</sub> + *g*) to cell (*g*, *x*<sub>*i*</sub> + *y*<sub>*i*</sub> + *g*) for all *g* ∈ *G*, and (provided *n* is even), also assign the pair (∞,*g*) to cell (*g*, *g*) for all *g* ∈ *G*.
Again, condition (i) and the strong-ness of the starter ensure that an ORS based on *G* ∪ {∞} is obtained. The block design associated with this array has initial blocks,
{∞} ∪ {*x*<sub>1</sub>, *x*<sub>2</sub>, ..., *x*<sub>*n* − 1</sub>}
{0}∪{*y*<sub>1</sub>, *y*<sub>2</sub>, ..., *y*<sub>*n* − 1</sub>}
 Adjoining 0 to {*y*<sub>1</sub>, *y*<sub>2</sub>, ..., *y*<sub>*n* − 1</sub>} creates each non-zero member of *G* as a difference once more, either as *y*<sub>*i*</sub> − 0 or 0 − *y*<sub>*i*</sub>.
Adjoining ∞ to {*x*<sub>1</sub>, *x*<sub>2</sub>, ..,*x*<sub>*n* − 1</sub>} creates *n* − 1 pairs involving ∞ in this block, hence ∞ makes a pair with each member of *G* *n* − 1 times.
So the design is balanced with a concurrence number of *n* − 1.
It is a simple matter to derive the remaining parameters of the BIBD associated with either array.

|                                    |    *v*   |     *b*     |     *r*    |   *k*   |   *λ*   |
|------------------------------------|:--------:|:-----------:|:----------:|:-------:|:-------:|
| *C**B**H**R*(2*n* − 1)             | 2*n* − 1 | 2(2*n* − 1) | 2(*n* − 1) | *n* − 1 | *n* − 2 |
| *C**B**H**R*(2*n*)/*B**R**S*(2*n*) |   2*n*   | 2(2*n* − 1) |  2*n* − 1) |   *n*   | *n* − 1 |

**Table 7 BIBD parameters for BRS and CBHR**

The block design of a balanced Room square is *self-complementary*. This means that if a block *D* belongs to the design, then its complement $\\overline{D}$ also appears. If the left hand pairs in row *x* form one block then the right hand pairs in the same row are also a block, and the two blocks are complementary. Alternatively we can say that, in a self-complementary BIBD, the complementary design (obtained by replacing all blocks with their complements) is identical to the design itself.
Schellenberg proved an interesting result regarding self-complementary BIBDs.

#### Theorem 5.3.3

\[21\] In a self-complementary BIBD with parameters of the form,
(2*n*, 2(2*n* − 1)*t*, (2*n* − 1)*t*, *n*, (*n* − 1)*t*), every triple of elements is contained in *t*(*n* − 2)/2 blocks.
*Proof*
Suppose *B* is a self-complementary BIBD with parameters of the form above, based on a set of elements *V*. Denote by *S*<sub>*i*...*j*</sub> the set of blocks which contain *u* but not *v* or *w*. Because the design is self-complementary to each block of this set there corresponds a unique block which contains *v* and *w* but not *u*. The set of these blocks is *S*<sub>*v**w*</sub> − *S*<sub>*u*</sub> and clearly:
|*S*<sub>*u*</sub> − {*S*<sub>*v*</sub> ∪ *S*<sub>*w*</sub>}| = |*S*<sub>*v**w*</sub> − *S*<sub>*u*</sub>|
 Now,
|*S*<sub>*u*</sub> − {*S*<sub>*v*</sub> ∪ *S*<sub>*w*</sub>}| = |*S*<sub>*u*</sub>|−|*S*<sub>*u**v*</sub>|−|*S*<sub>*u**w*</sub>|+|*S*<sub>*u**v**w*</sub>| and,
|*S*<sub>*v**w*</sub> − *S*<sub>*u*</sub>|=|*S*<sub>*v**w*</sub>|−|*S*<sub>*u**v**w*</sub>|
∴|*S*<sub>*u*</sub>|−|*S*<sub>*u**v*</sub>|−|*S*<sub>*u**w*</sub>|+|*S*<sub>*u**v**w*</sub>|=|*S*<sub>*v**w*</sub>|−|*S*<sub>*u**v**w*</sub>|
2|*S*<sub>*u**v**w*</sub>|=|*S*<sub>*v**w*</sub>|+|*S*<sub>*u**v*</sub>|+|*S*<sub>*u**w*</sub>|−|*S*<sub>*U*</sub>|
 Because *B* is a *B**I**B**D*, each pair of elements occur together in *λ* = (*n* − 1)*t* blocks and each element occurs in *r* = (2*n* − 1)*t* blocks. So,
|*S*<sub>*v**w*</sub>|=|*S*<sub>*u**v*</sub>|=|*S*<sub>*u**w*</sub>|=(*n* − 1)*t*
 and
|*S*<sub>*u*</sub>|=(2*n* − 1)*t*
 Therefore,
2|*S*<sub>*u**v**w*</sub>|=3(*n* − 1)*t* − (2*n* − 1)*t* = (*n* − 2)*t*
 and so,
$$|S\_{uvw}| = \\frac{(n-2)t}{2}$$
 Since *u*, *v* and *w* are arbitrary this implies that each triple occurs in (*n* − 2)*t*/2 blocks. ▫
The implication of this result for balanced Room squares is that, because *t* = 1 for a *B**R**S*[12] and we require the LHS of this expression to be an integer, *n* is necessarily even. So writing *n* = 2*m*, we know the order of a *B**R**S* is always of the form 4*m*.

#### Corollary 5.3.1

A *B**R**S*(*n*) can only exist for *n* ≡ 0 mod 4.
We now present Hwang’s starter-adder construction for balanced Room squares.

#### Theorem 5.3.4

\[14\] There exists a *B**R**S* of order *q* + 1, where $q=p^r $ 3(mod 4) is a prime power strictly greater than 3.
*Proof*
We show that the pairs
$$X = \\left \\{(x^{2i+1},x^{2i}): 0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 form a balanced starter, where *x* is a primitive element in *G**F*(*q*), and the set
$$A(X) = \\left \\{-x^{2i}(1+x): 0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 is a corresponding adder.
Looking back at Theorem 2.4(?), we have already shown that the unordered pairs
$$\\left \\{\\{x^{2i},x^{2i+1}\\}: 0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 are those of a starter with adder *A*(*X*). So it remains to show that the starter is balanced which involves proving that the two blocks
$$B\_1 = \\{0,x,x^3,...,x^{q-2}\\} \\hspace{0.5cm} \\mathrm{and} \\hspace{0.5cm} B\_2 = \\{\\infty,x^0,x^2,...,x^{q-3}\\}$$
 generate a *B**I**B**D*. This result is due to R.C. Bose and makes use of the properties of the squares and non-squares of *G**F*(*q*) where *q* is an odd prime.
Let *R* and *N* denote the sets of non-zero square and non-squares in *G**F*(*q*), respectively.
*R* = {*x*<sup>2</sup>, *x*<sup>4</sup>, ..., *x*<sup>*q* − 1</sup>}
*N* = {*x*<sup>1</sup>, *x*<sup>3</sup>, ..., *x*<sup>*q* − 2</sup>}
 These sets both contain precisely $\\frac{1}{2}(q-1)$ elements.
So,
*B*<sub>1</sub> = {0}∪*N*,
 and because *x*<sup>*q* − 1</sup> = 1 = *x*<sup>0</sup>,
*B*<sub>2</sub> = {∞} ∪ *R*
 Also, if *a* is square then −*a* is a non-square[13], which implies that *R* = −*N*.
To show that the blocks with their translates form a *B**I**B**D* it is necessary to show that the differences between members of *B*<sub>1</sub> and *R* generate all the non-zero members of *G**F*(*q*) some number of times, then by adjoining the element ∞ to *R* and its translates will generate a *B**I**B**D*.
Firstly, suppose that 1, which belongs to *R*, can be expressed as a difference between members of *R* in a certain number of different ways,
1 = *x*<sup>2*a*<sub>1</sub></sup> − *x*<sup>2*b*<sub>1</sub></sup> = ...*x*<sup>2*a*<sub>*r*</sub></sup> − *x*<sup>2*b*<sub>*r*</sub></sup>
 Were this true, any member of *R* could be written as a difference in the same number of ways.
Multiply through by any *x*<sup>2*s*</sup> ∈ *R*.
*x*<sup>2*s*</sup> = *x*<sup>2(*a*<sub>1</sub> + *s*)</sup> − *x*<sup>2(*b*<sub>1</sub> + *s*)</sup> = ... = *x*<sup>2(*a*<sub>*r*</sub> + *s*)</sup> − *x*<sup>2(*b*<sub>*r*</sub> + *s*)</sup>
 But now suppose that any element of *R* can be expressed as a difference between members of *R* in a certain number of ways, i.e. assume this second expression holds. Then by dividing through by *x*<sup>2*s*</sup>, we recover the first expression and hence for each representation of 1 there is a corresponding representation of *x*<sup>2*s*</sup>, and vice versa. So there are an equal number of representations of every member of *R* as a difference of members of *R*. The remaining non-zero members of *G**F*(*q*), are all those *q* ∉ *R* where −*q* ∈ *R*, but each representation of −*r* gives a corresponding representation of *r*:
−*r* = *x*<sup>2*a*</sup> − *x*<sup>2*b*</sup>
*r* = *x*<sup>2*b*</sup> − *x*<sup>2*a*</sup>
 So every element of −*r* has the same number of representations as a difference between members of *R* as *R* does.
We know that *R* has $\\frac{1}{2}(q-1)$ elements, therefore there are
$\\frac{1}{2}(q-1) \\cdot \\frac{1}{2} (q-3) = \\frac{1}{4}(q-1)(q-3)$ differences between those elements, and if each of these differences generates each of the *q* − 1 non-zero members of *G**F*(*q*), *λ* times then:
$$\\lambda(q-1)=\\frac{1}{4}(q-1)(q-3)$$
$$\\lambda=\\frac{1}{4}(q-3)$$
 Also, because *N* = −*R*, we can say that all the non-zero members of *G**F*(*q*) arise as differences between members of *N*. Further, *B*<sub>1</sub> also gives the differences $0-n,n-0 \\hspace{0.5cm} n\\in N$, which are all the non-zero members of *G**F*(*q*), once again. So in total every non-zero member of *G**F*(*q*) occurs as a difference between elements of *B*<sub>1</sub> and *R*, $2 \\cdot \\frac{1}{4} (q-3) + 1 = \\frac{1}{2} (q-1)$ times.
Because *R* and its translates each contain $ (q-1)$ elements, each member of *G**F*(*q*) occurs $ (q-1)$ times in all those blocks. Therefore, adjoining ∞ to each block generates blocks of size $ (q-1)$, with ∞ making a pair with each member of *G**F*(*q*), $ (q-1)$ times.
So we can say that *B*<sub>1</sub>, *B*<sub>2</sub> and their translates for a $BIBD(q+1,\\frac{1}{2}(q+1), \\frac{1}{2}(q-1))$.
Therefore Hwang’s starter is balanced. ▫
The *B**R**S* in Figure 27 was obtained from Hwang’s starter, hence its block design was a *B**I**B**D*.
*Example 5.3.1*
A balanced starter in *G**F*(19) is:
*X* = {(2, 1),(8, 4),(13, 16),(14, 7),(18, 9),(15, 17),(3, 11),(12, 6),(10, 5)}
 Which has a corresponding adder:
*A*(*X*)={16, 7, 9, 17, 11, 6, 5, 1, 4}
 So the following row is an appropriate choice for a *B**R**S*(20):

∞, 0 - 14,7 2,1 15,7 - - - 18,9 - 13,16 - 8,4 - 3,11 10,5 - - 12,6 ------------ --- ------ ----- ------ --- --- --- ------ --- ------- --- ----- --- ------ ------ --- --- ------

A Multiplicative Construction for BRS
-------------------------------------

Although the Hwang starter-adder construction establishes the existence of an infinite class of *B**R**S*, like Mullin & Nemeth’s construction for Room squares, exceptions still remain.
Particularly all those *B**R**S* of order *q* + 1 where q is not a prime power, yet is congruent 3 modulo 4. For example, the existence of *B**R**S*(16) is not established yet, because 15 is not a prime power. One approach to resolving this problem would be to establish a multiplication theorem like those established for Room squares. The following doubling construction for *B**R**S* (due to Schellenberg), for example, enables to construction of a *B**R**S*(16) from two *B**R**S*(8).
Significantly, used along with Hwang’s starter-adder construction, it establishes the existence of another infinite class of *B**R**S*, those of order 2(*q* + 1), where *q* is subject to the conditions of Theorem 3.5.
Before presenting the doubling construction a few definitions need to be made, and another result regarding self-complementary block designs established.
The ***reduced*** Room square $\\hat{R}$, is obtained by taking a standardised Room square *R* and removing the pairs involving ∞, i.e. the diagonal pairs.
Two *O**R**S*, *R* and *S* (both of side *a*) are said to be a ***Latin pair*** if on forming the join of $\\hat{R}$ and $\\hat{S}$, and placing the pair (*i*, *i*) in cell (*i*, *i*) for 0 ≤ *i* ≤ *q* − 1 the join of two *M**O**L**S* is obtained, denoted by *R* ⊙ *S*.
A ***common traversal*** of *R* ⊙ *S* is a set of *q* cells, one from each row and each column, whose *n* ordered pairs have *n* distinct first elements and *n* distinct second elements.
Suppose we have a set of varieties *V* = {1, 2, 3, ...}, then by a set *V*′, we mean *V*′={1′,2′,3′,...}.

#### Lemma 5.4.1

\[21\] If
$$\\bigcup\\limits\_{i=1}^{2k-1} \\left \\{C\_i,\\bar{C\_i} \\right \\} \\hspace{0.5cm} \\mathrm{and} \\hspace{0.5cm} 
\\bigcup\\limits\_{i=1}^{2k-1} \\left \\{D\_i,\\bar{D\_i} \\right \\}$$
 are the blocks of two self-complementary *B**I**B**D*s, both defined on a set of elements *V*, where $\\bar{C}$ denotes the complement of *C*, with parameters (2*k*, 2(2*k* − 1),2*k* − 1, *k*, *k* − 1) then.
$$\\bigcup\\limits\_{i=1}^{2k-1} \\left \\{C\_i \\cup D'\_i, \\bar{C\_i} \\cup \\bar{D'\_i}, C\_i \\cup \\bar{D'\_i},
\\bar{C\_i} \\cup D'\_i  \\right \\} \\cup \\{V,V'\\}$$
 is the set of blocks of a self-complementary *B**I**B**D*, defined on the set of elements *V* ∪ *V*′, with parameters (4*k*, 2(4*k* − 1),4*k* − 1, 2*k*, 2*k* − 1).
*Proof*
Consider an arbitrary pair {*a*, *b*} in the new *B**I**B**D* where *a*, *b* ∈ *V*. The concurrence number of the original *B**I**B**D* was *k* − 1, so this pair occurred *k* − 1 times in the blocks $\\bigcup\\limits\_{i=1}^{2k-1} \\left \\{C\_i,\\bar{C\_i} \\right \\}$, but these blocks clearly appear twice each in the new *B**I**B**D*. Also the pair {*a*, *b*} occurs once in the block *V*, so the pair {*a*, *b*} occurs 2(*k* − 1)+1 = 2*k* − 1 times. The same would be true for any pair {*a*, *b*} when *a*, *b* ∈ *V*′.
Now consider an arbitrary pair {*a*, *b*} when *a* ∈ *V*, and *b* ∈ *V*′. From the definition of complementary blocks *a* occurs either *C* or $\\bar{C}$ and *b* in either *D*′ or $\\bar{D'}$, for some value of *i*, and because all pair combinations between *C*-blocks and *D*′-blocks are formed in the new design and because *i* takes 2*k* − 1 values in the new design so the pair makes 2*k* − 1 appearances.
Hence the new block design is a *B**I**B**D* with *λ* = 2*k* − 1. ▫

#### Theorem 5.4.1

Suppose we have two *B**R**S*(*q* + 1), *R* and *S* based on *G* = *G**F*(*q*), with the following properties:

1.  *R* and *S* are a *Latin pair* such that,

2.  *R* ⊙ *S* has a pair of disjoint *common transversals* *T*<sub>1</sub> and *T*<sub>2</sub> (with *T*<sub>2</sub> in *R*), which do not intersect the main diagonal, and

3.  the block designs obtained from *R* and *S*, call them *D*(*R*) and *D*(*S*) respectively, have the property that if {∞} ∪ *B*<sub>*i*</sub> and {*i*}∪*C*<sub>*i*</sub> are the blocks of *D*(*R*) obtained from row *i*, then {*i*}∪*B*<sub>*i*</sub> and {∞} ∪ *C*<sub>*i*</sub> are the blocks of *D*(*S*) obtained from row *i*.

Then a *B**R**S*(2(*q* + 1)) exists.
*Proof*
Define *A* to be the array obtained from the superposition of $\\hat{R}$ and $\\hat{S'}$. Where $\\hat{S'}$ is obtained by replacing the elements of *G* in $\\hat{S}$ (the reduced RS) by the corresponding elements of *G*′ and replacing ∞ by ∞′. *R* and *S* were *B**R**S* so each column and row of *A* contains each member of *G* ∪ *G*′∪{∞, ∞′}, except those elements *i*, *i*′,∞ and ∞′ which are missing from row and column *i* due to the reduction process. Further, *A* contains every pair $\\{i,j\\},\\{i',j'\\} \\hspace{0.25cm} i,j \\in G,i \\neq j$ exactly once.
Define *B* as the array obtained from *R* ⊙ *S* when each pair (*i*, *j*) is replaced by (*i*, *j*′).
Now, *D* is defined as the array obtained from *B* according to this procedure:
If cell (*m*, *n*),*m* ≠ *n* of *R* is not empty, replace (*i*, *j*′) in cell (*m*, *n*) of *B* by (*j*′,*i*). Because *R* ⊙ *S* is a pair of superposed orthogonal latin squares *D* contains each member of *G* ∪ *G*′ exactly once in each row and column. Also, the way in which we have repalced elements ensures that every unordered pair {*i*, *j*′} for all *i*, *j* ∈ *G* occurs exactly once in *D*.
Next, construct *C* by arranging the arrays *A* and *D* according to the following layout, in which *ϕ* is the *q* × *q* array with every cell empty, *θ* the 1 × *q* array of empty cells and *θ*<sup>*T*</sup> the transpose of *θ*:

*C*=

| *A* | *ϕ* | *θ*<sup>*T*</sup> |
|:---:|:---:|:-----------------:|
| *ϕ* | *D* | *θ*<sup>*T*</sup> |
| *θ* | *θ* |        ∞′,∞       |

The rows and columns of this new array are labelled 0, 1, 2, ..., *q* − 1, 0′,1′,2′,...,(*q* − 1)′, *l*. So that the pair (∞′, ∞) is in cell (*l*, *l*).
Let

*T*′<sub>*p*</sub> = {(*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>)|(*i*<sub>*m*</sub>, *j*<sub>*m*</sub>) *is a cell transversal* *T*<sub>*p*</sub>}

be the set of cells of *C*, corresponding to transversal $T\_p \\hspace{0.25cm}(p=1,2)$ of *R* ⊙ *S*.
Construct a new array *F*, based on *C* according to the following prescription:
Consider cell (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>)∈*T*′<sub>1</sub>. If cell (*i*<sub>*m*</sub>, *j*<sub>*m*</sub>) is not empty in *R* then (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>) of *C* contains a pair (*k*′,*n*), otherwise it contains a pair (*n*, *k*′). \[In either case $k,nm \\in G \\hspace{0.25cm} k \\neq n$ (the transversal does not intersect the diagonal)\]. Remove whichever pair appears in cell (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>) and put it in cell (*i*′<sub>*m*</sub>, *l*). Also place (∞′, *k*′), (∞,*n*) in cells (*k*, *j*′<sub>*m*</sub>),(*n*, *j*′<sub>*m*</sub>) respectively.
If (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>)∈*T*′<sub>2</sub> then a pair (*k*′,*n*) appears in cell (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>). Again remove it, but this time put it in (*l*, *j*′<sub>*m*</sub>). In addition pairs (*k*′,∞), (∞′, *n*) go in cells (*i*′<sub>*m*</sub>, *k*),(*i*′<sub>*m*</sub>, *n*) respectively.
*F* is a *B**R**S* because,

-   *A* and *D* between them intially contain all the unordered pairs {*i*, *j*},{*i*′,*j*′} *i*, *j* ∈ *G*, *i* ≠ *j* and {*i*, *j*′} for all *i*, *j* ∈ *G*. So *F* has an ordered pair corresponding to each of these.

-   The procedure in the preceding paragraph contributes the remaining ordered pairs
    (∞′, *k*′), (∞,*n*),(*k*′,∞), (∞′, *n*) for all $k,n \\in G \\hspace{0.25cm} k \\neq n$ in such a way that the elements missing from the first *q* rows and columns are suitably placed, and ∞ and ∞′ are placed in each row and column of *F*. Hence each row and column of *F* contains every member of {∞,∞′}∪*G* ∪ *G*′ exactly once.

The block design obtained from the rows of *F* has blocks:

$ .
} 0 i q-1 $

from rows 0,1,...,*q* − 1 blocks

$ .
} 0 i q-1 $

from rows 0′,1′,...,(*q* − 1)′, and the blocks
{∞} ∪ *F*, {∞′}∪*G*′
 obtained from row *l*.
According to condition 3 of Theorem 3.6 and Lemma 3.1, these blocks for a *B**I**B**D*. ▫
*Example 5.4.1*
Consider the following *B**R**S*(8)s

*R*=

|  ∞0 |  26 |  45 |     |  13 |     |     |
|:---:|:---:|:---:|-----|:---:|-----|-----|
|     |  ∞1 |  30 | 56  |     | 24  |     |
|     |     |  ∞2 | 41  |  60 |     | 35  |
|  46 |     |     | ∞3  |  52 | 01  |     |
|     |  50 |     |     |  ∞4 | 63  | 12  |
|  23 |     |  61 |     |     | ∞5  | 04  |
|  15 |  34 |     | 02  |     |     | ∞6  |

$\\hspace{0.5cm} S=$

|  ∞0 |     |     |  64 |     |  32 |  51 |
|:---:|-----|-----|:---:|-----|:---:|:---:|
|  62 | ∞1  |     |     | 05  |     |  43 |
|  54 | 03  | ∞2  |     |     |  16 |     |
|     | 65  | 14  |  ∞3 |     |     |  20 |
|  31 |     | 06  |  25 | ∞4  |     |     |
|     | 42  |     |  10 | 36  |  ∞5 |     |
|     |     | 53  |     | 21  |  40 |  ∞6 |

$\\hspace{3.5cm}$ **Figure 28** $\\hspace{6cm}$ **Figure 29**
These *B**R**S* satisfy all three properties required by Theorem 3.6. (We shall see why later).
Suppose we take the following two disjoint common transversals as *T*<sub>1</sub> (lighter grey shading) and *T*<sub>2</sub> (darker grey shading).

*R* ⊙ *S*=

|  00 |  26 |  45 |  64 |  13 |  32 |  51 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  62 |  11 |  30 |  56 |  05 |  24 |  43 |
|  54 |  03 |  22 |  41 |  60 |  16 |  35 |
|  46 |  65 |  14 |  33 |  52 |  01 |  20 |
|  31 |  50 |  06 |  25 |  44 |  63 |  12 |
|  23 |  42 |  61 |  10 |  36 |  55 |  04 |
|  15 |  34 |  53 |  02 |  21 |  40 |  66 |

**Figure 30**

Next we obtain *A* from the superposition of $\\hat{R}$ and $\\hat{S'}$:

$A = $

|      |  26  |  45  | 6′4′ |  13  | 3′2′ | 5′1′ |
|------|:----:|:----:|:----:|:----:|:----:|:----:|
| 6′2′ |      |  30  |  56  | 0′5′ |  24  | 4′3′ |
| 5′4′ | 0′3′ |      |  41  |  60  | 1′6′ |  35  |
| 46   | 6′5′ | 1′4′ |      |  52  |  01  | 2′0′ |
| 3′1′ |  50  | 0′6′ | 2′5′ |      |  63  |  12  |
| 23   | 4′2′ |  61  | 1′0′ | 3′6′ |      |  04  |
| 15   |  34  | 5′3′ |  02  | 2′1′ | 4′0′ |      |

**Figure 31**

Then we construct *B*, and after swapping the order of certain pairs, obtain *D*:

*B*=

| 00′ | 26′ | 45′ | 64′ | 13′ | 32′ | 51′ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 62′ | 11′ | 30′ | 56′ | 05′ | 24′ | 43′ |
| 54′ | 03′ | 22′ | 41′ | 60′ | 16′ | 35′ |
| 46′ | 65′ | 14′ | 33′ | 52′ | 01′ | 20′ |
| 31′ | 50′ | 06′ | 25′ | 44′ | 63′ | 12′ |
| 23′ | 42′ | 61′ | 10′ | 36′ | 55′ | 04′ |
| 15′ | 34′ | 53′ | 02′ | 21′ | 40′ | 66′ |

$\\hspace{0.5cm} \\Rightarrow D=$

| 00′ | 6′2 | 5′4 | 64′ | 3′1 | 32′ | 51′ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 62′ | 11′ | 0′3 | 6′5 | 05′ | 4′2 | 43′ |
| 54′ | 03′ | 22′ | 1′4 | 0′6 | 16′ | 5′3 |
| 6′4 | 65′ | 14′ | 33′ | 2′5 | 1′0 | 20′ |
| 31′ | 0′5 | 06′ | 25′ | 44′ | 3′6 | 2′1 |
| 3′2 | 42′ | 1′6 | 10′ | 36′ | 55′ | 4′0 |
| 5′1 | 4′3 | 53′ | 2′0 | 21′ | 40′ | 66′ |

$\\hspace{3.5cm}$ **Figure 32** $\\hspace{6cm}$ **Figure 33**
*C* is obtained by arranging *A* and *D* thus:

|     |   0  |   1  |   2  |   3  |   4  |   5  |   6  |  0′ |  1′ |  2′ |  3′ |  4′ |  5′ |  6′ | *l* |
|-----|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0   |      |  26  |  45  | 6′4′ |  13  | 3′2′ | 5′1′ |     |     |     |     |     |     |     |     |
| 1   | 6′2′ |      |  30  |  56  | 0′5′ |  24  | 4′3′ |     |     |     |     |     |     |     |     |
| 2   | 5′4′ | 0′3′ |      |  41  |  60  | 1′6′ |  35  |     |     |     |     |     |     |     |     |
| 3   |  46  | 6′5′ | 1′4′ |      |  52  |  01  | 2′0′ |     |     |     |     |     |     |     |     |
| 4   | 3′1′ |  50  | 0′6′ | 2′5′ |      |  63  |  12  |     |     |     |     |     |     |     |     |
| 5   |  23  | 4′2′ |  61  | 1′0′ | 3′6′ |      |  04  |     |     |     |     |     |     |     |     |
| 6   |  15  |  34  | 5′3′ |  02  | 2′1′ | 4′0′ |      |     |     |     |     |     |     |     |     |
| 0′  |      |      |      |      |      |      |      | 00′ | 6′2 | 5′4 | 64′ | 3′1 | 32′ | 51′ |     |
| 1′  |      |      |      |      |      |      |      | 62′ | 11′ | 0′3 | 6′5 | 05′ | 4′2 | 43′ |     |
| 2′  |      |      |      |      |      |      |      | 54′ | 03′ | 22′ | 1′4 | 0′6 | 16′ | 5′3 |     |
| 3′  |      |      |      |      |      |      |      | 6′4 | 65′ | 14′ | 33′ | 2′5 | 1′0 | 20′ |     |
| 4′  |      |      |      |      |      |      |      | 31′ | 0′5 | 06′ | 25′ | 44′ | 3′6 | 2′1 |     |
| 5′  |      |      |      |      |      |      |      | 3′2 | 42′ | 1′6 | 10′ | 36′ | 55′ | 4′0 |     |
| 6′  |      |      |      |      |      |      |      | 5′1 | 4′3 | 53′ | 2′0 | 21′ | 40′ | 66′ |     |
| *l* |      |      |      |      |      |      |      |     |     |     |     |     |     |     | ∞′∞ |

**Figure 34**

Finally we construct *F* according to the 2 presciptions in the final part of the construction. Which involves first replacing some of the pairs in those cells of *C* corresponding to *D*.
Consider
*T*′<sub>1</sub> = {(2′,6′), (3′,0′), (4′,1′), (5′,2′), (6′,3′), (0′,4′), (1′,5′)}
 In *R*, the cells (2, 6),(3, 0),(4, 1),(5, 2),(6, 3),(0, 4) and (1, 5) were all non-empty, so *C* contains pairs of the form (*k*′,*n*) in all cells (2′,6′), (3′,0′), ... All of these are removed and replaced in the final column of the same row. And, for each pair (*k*′,*n*), corresponding pairs of the form (∞′, *k*′), (∞,*n*) are put in cells (*k*, *j*′<sub>*m*</sub>),(*n*, *j*′<sub>*m*</sub>), respectively.
e.g.
(5′,3) appears in position (2′,6′) of *C*. So in *F*, (5′,3) appears in (2′,*l*) and the additional pairs (∞,3) and (∞′, 5′) appear in column 6′, in rows 3 and 5 respectively.
All of which makes the final columns appear like so:

|     |  0′  |  1′  |  2′  |  3′  |  4′  |  5′  |  6′  | *l* |
|-----|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:---:|
| 0   |      | ∞′0′ |      |  ∞0  |      |      |      |     |
| 1   |      |      | ∞′1′ |      |  ∞1  |      |      |     |
| 2   |      |      |      | ∞′2′ |      |  ∞2  |      |     |
| 3   |      |      |      |      | ∞′3′ |      |  ∞3  |     |
| 4   | $4 $ |      |      |      |      | ∞′4′ |      |     |
| 5   |      | $5 $ |      |      |      |      | ∞′5′ |     |
| 6   | ∞′6′ |      | $6 $ |      |      |      |      |     |
| 0′  |  00′ |  6′2 |  5′4 |  64′ |  3′1 |  32′ |  51′ | 3′1 |
| 1′  |  62′ |  11′ |  0′3 |  6′5 |  05′ |  4′2 |  43′ | 4′2 |
| 2′  |  54′ |  03′ |  22′ |  1′4 |  0′6 |  16′ |  5′3 | 5′3 |
| 3′  |  6′4 |  65′ |  14′ |  33′ |  2′5 |  1′0 |  20′ | 6′4 |
| 4′  |  31′ |  0′5 |  06′ |  25′ |  44′ |  3′6 |  2′1 | 0′5 |
| 5′  |  3′2 |  42′ |  1′6 |  10′ |  36′ |  55′ |  4′0 | 1′6 |
| 6′  |  5′1 |  4′3 |  53′ |  2′0 |  21′ |  40′ |  66′ | 2′0 |
| *l* |      |      |      |      |      |      |      | ∞′∞ |

**Figure 35**

Now consider:
*T*′<sub>2</sub> = {(4′,5′), (5′,6′), (6′,0′), (0′,1′), (1′,2′), (2′,3′), (3′,4′)}
 In each cell (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>) of *C*, where (*i*′<sub>*m*</sub>, *j*′<sub>*m*</sub>)∈*T*′<sub>2</sub>, occurs a pair (*k*′,*n*), we remove this and place it in cell (*l*, *j*′<sub>*m*</sub>), also putting pairs (*k*′,∞), (∞′, *n*) in cells (*i*′<sub>*m*</sub>, *k*),(*i*′<sub>*m*</sub>, *n*).
e.g.
(3′,6) appears in (4′,5′), so (3′,6) goes in (*l*, 5′) and (3′,∞), (∞′, 6) go in (4′,3),(4′,6) respectively.

|     |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  0′ |  1′ |  2′ |  3′ |  4′ |  5′ |  6′ | *l* |
|-----|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0′  |     |     | ∞′2 |     |     |     | 6′∞ | 00′ |     | 5′4 | 64′ |     | 32′ | 51′ | 3′1 |
| 1′  | 0′∞ |     |     | ∞′3 |     |     |     | 62′ | 11′ |     | 6′5 | 05′ |     | 43′ | 4′2 |
| 2′  |     | 1′∞ |     |     | ∞′4 |     |     | 54′ | 03′ | 22′ |     | 0′6 | 16′ |     | 5′3 |
| 3′  |     |     | 2′∞ |     |     | ∞′5 |     |     | 65′ | 14′ | 33′ |     | 1′0 | 20′ | 6′4 |
| 4′  |     |     |     | 3′∞ |     |     | ∞′6 | 31′ |     | 06′ | 25′ | 44′ |     | 2′1 | 0′5 |
| 5′  | ∞′0 |     |     |     | 4′∞ |     |     | 3′2 | 42′ |     | 10′ | 36′ | 55′ |     | 1′6 |
| 6′  |     | ∞′1 |     |     |     | 5′∞ |     |     | 4′3 | 53′ |     | 21′ | 40′ | 66′ | 2′0 |
| *l* |     |     |     |     |     |     |     | 5′1 | 6′2 | 0′3 | 1′4 | 2′5 | 3′6 | 4′0 | ∞′∞ |

**Figure 36**

So the following array, the completed *F*, is a *B**R**S*(16):

|      |  26  |  45  | 6′4′ |  13  | 3′2′ | 5′1′ |      | ∞′0′ |      |  ∞0  |      |      |      |     |
|------|:----:|:----:|:----:|:----:|:----:|:----:|------|:----:|------|:----:|------|------|------|-----|
| 6′2′ |      |  30  |  56  | 0′5′ |  24  | 4′3′ |      |      | ∞′1′ |      | ∞1   |      |      |     |
| 5′4′ | 0′3′ |      |  41  |  60  | 1′6′ |  35  |      |      |      | ∞′2′ |      | ∞2   |      |     |
| 46   | 6′5′ | 1′4′ |      |  52  |  01  | 2′0′ |      |      |      |      | ∞′3′ |      | ∞3   |     |
| 3′1′ |  50  | 0′6′ | 2′5′ |      |  63  |  12  | ∞4   |      |      |      |      | ∞′4′ |      |     |
| 23   | 4′2′ |  61  | 1′0′ | 3′6′ |      |  04  |      |  ∞5  |      |      |      |      | ∞′5′ |     |
| 15   |  34  | 5′3′ |  02  | 2′1′ | 4′0′ |      | ∞′6′ |      | ∞6   |      |      |      |      |     |
|      |      |  ∞′2 |      |      |      |  6′∞ | 00′  |      | 5′4  |  64′ |      | 32′  | 51′  | 3′1 |
| 0′∞  |      |      |  ∞′3 |      |      |      | 62′  |  11′ |      |  6′5 | 05′  |      | 43′  | 4′2 |
|      |  1′∞ |      |      |  ∞′4 |      |      | 54′  |  03′ | 22′  |      | 0′6  | 16′  |      | 5′3 |
|      |      |  2′∞ |      |      |  ∞′5 |      |      |  65′ | 14′  |  33′ |      | 1′0  | 20′  | 6′4 |
|      |      |      |  3′∞ |      |      |  ∞′6 | 31′  |      | 06′  |  25′ | 44′  |      | 2′1  | 0′5 |
| ∞′0  |      |      |      |  4′∞ |      |      | 3′2  |  42′ |      |  10′ | 36′  | 55′  |      | 1′6 |
|      |  ∞′1 |      |      |      |  5′∞ |      |      |  4′3 | 53′  |      | 21′  | 40′  | 66′  | 2′0 |
|      |      |      |      |      |      |      | 5′1  |  6′2 | 0′3  |  1′4 | 2′5  | 3′6  | 4′0  | ∞′∞ |

**Figure 37**

Schellenberg applied his multiplicative construction to the *B**R**S* generated by Hwang’s starter-adder construction, and in doing so was able to establish the following Theorem:

#### Theorem 5.4.2

\[21\] For *q* ≡ 3(mod 4), with *q* a prime power strictly greater than 3, there exists a *B**R**S*(2(*q* + 1)).
*Proof*
Construct *R* from the following balanced starter,
$$X = \\left \\{ (x^{2i},x^{2i+1}):0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 with adder,
$$A(X) = \\left \\{ -x^{2i}(1+x):0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 Clearly this is just the Hwang starter-adder of Theorem 5.3.4, although the elements in the starter pairs have swapped order. Now, construct *S* from the balanced starter,
$$Y = \\left \\{ (x^{2i-1},x^{2i}):0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
$$A(Y) = \\left \\{ -x^{2i-1}(1+x):0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
 *Y* has been obtained simply by swapping the pairs of *X* and multiplying them by *x*<sup>−1</sup>. Therefore, that *Y* is a balanced starter follows from the fact that *X* is balanced, as was established in Theorem 3.5.
It remains to show that *R* and *S* satisfy conditions 1,2 and 3 of Theorem 3.6:

1.  *R* and *S* are a Latin pair: The positions of the starter pais in the first row of each square are determined by the adder, so *A*(*X*)∩*A*(*Y*)=⌀[14] ensures that each cell of the first row, hence subsequent rows, of *R* ⊙ *S* contains only one pair.
    That *R* ⊙ *S* is a pair of superposed Latin squares requires that for the pairs in any row, the left hand members take all values 0...*q* − 1, and the right members also take values 0...*q* − 1.
    Clearly this property holds for all rows if it holds for the first. The pairs in the first row of *R* ⊙ *S* are:
    $$\\{(0,0)\\} \\cup \\left \\{ (x^{2i-1},x^{2i}),(x^{2i},x^{2i+1}) \\middle| 0 \\leq i \\leq \\frac{q-3}{2} \\right \\}$$
     So all (*q* − 1)/2 non-squares and all (*q* − 1)/2 squares occur as left hand members of pairs, and similarly as right hand members. So *R* ⊙ *S* is a pair of superposed Latin squares.
    For these Latin squares to be orthogonal requires that there is no repetition of ordered pairs. For a repetition to occur would require some repetition of ordered differences among the starter pairs.
    Either:
    $$x^{2i-1} - x^{2i} = x^{2i} - x^{2i+1} \\hspace{0.2cm} \\mathrm{or} \\hspace{0.2cm}
    x^{2i} - x^{2i-1} = x^{2i+1} - x^{2i} \\hspace{0.2cm} \\mathrm{i.e.}$$
    ±(*x*<sup>2*i* − 1</sup> + *x*<sup>2*i* + 1</sup>)= ± (*x*<sup>2*i*</sup> + *x*<sup>2*i*</sup>)
    *x*<sup>−1</sup> + *x* = 2 ⇒ *x* = 1
     Clearly false, so ordered differences are unique.

2.  *R* ⊙ *S* has a pair of disjoint *common transversals*:
    For any fixed non-zero *j* the cells (*i*, *i* + *j*), 0 ≤ *i* ≤ *q* − 1 form a common transversal which does not intersect the diagonal.

3.  The block designs for *R* and *S* are balanced:
    The starters *X* and *Y* are balanced starters hence the block designs for *R* and *S* are *B**I**B**D*s. ▫

So the Schellenberg multiplication construction establishes the existence of some new orders *q* + 1 where *q* is not necessarily a prime power.
e.g.
the orders in bold are now established which had not been under Hwang’s construction:

<span>|c|c|c|c|c|c|c|c|c|c|c|c|c|</span>

|                                                      |
|:----------------------------------------------------:|
|                    Hwang *B**R**S*                   |
| *p*<sup>*r*</sup> + 1 : *p*<sup>*r*</sup> ≡ 3(mod 4) |

& 8 & 12 & & 20 & 24 & 28 & 32 & & & 44 & 48 & ...
-------------- Schellenberg 2(*p*<sup>*r*</sup> + 1) --------------

& **16** & 24 & 32 & **40** & 48 & **56** & **64** & 72 & 80 & **88** & **96** & ...
**Table 8**

Even with both these theorems, there are obviously missing orders. The first exception, 36 occurs, for example, because 35 is not a prime power and because 17 is not congruent to 3 mod 4.
Schellenberg applied the multiplicative construction to the case when *p*<sup>*r*</sup> ≡ 1(mod 4) \[then, of course, 2(*p*<sup>*r*</sup> + 1)≡0(mod 4) as is required\] and was able to obtain further results. Although, as an interesting parallel to the Mullin-Nemeth construction, he also had problems with the Fermat primes and again they were treated separately. Rather than look at his approach we consider the later approach by Du, Yu, Hwang and Kang amongst others.

Symmetric Skew Balanced Starters
--------------------------------

If (*x*<sub>1</sub>, *y*<sub>1</sub>),(*x*<sub>2</sub>, *y*<sub>2</sub>),...,(*x*<sub>(*q* − 1)/2</sub>, *y*<sub>(*q* − 1)/2</sub>) are the pairs of a balanced starter in *G**F*(*q*) then we say that starter is ***skew*** if ±(*x*<sub>1</sub> + *y*<sub>1</sub>), ± (*x*<sub>2</sub> + *y*<sub>2</sub>),..., ± (*x*<sub>(*q* − 1)/2</sub>, *y*<sub>(*q* − 1)/2</sub>) are all distinct mod *q*.
Notice that a skew starter is necessarily a strong starter (all sums are distinct).
A balanced starter is ***symmetric*** if {*x*<sub>1</sub>, *x*<sub>2</sub>, ..., *x*<sub>(*q* − 1)/2</sub>}={−*x*<sub>1</sub>, −*x*<sub>2</sub>, ..., *x*<sub>(*q* − 1)/2</sub>}
In \[13\] it was claimed that Schellenberg’s multiplication theorem could be applied to two *C**B**H**R*(2*n* − 1)s, both obtained from *S**S**B**S*, to construct a *B**R**S*(4*n*). It was then shown that *S**S**B**S* exist for all prime powers 2*n* − 1 = 8*k* + 5 &gt; 5, and so the existence of *B**R**S*(4*n*) for these values was believed to be established.

|   k  |  1  |  3  |  4  |  6  |  7  |  12 |  13 |  16 |  18 |  19 | ... |
|:----:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 4*n* |  28 |  60 |  76 | 108 | 124 | 204 | 220 | 268 | 300 | 316 | ... |

**Table 9**

Recently, Anderson\[2\], has noticed a flaw in this approach and corrected it.
Suppose we wished to apply Schellenberg’s construction to two *C**B**H**R*(2*n* − 1)s, call them *P* and *Q*, then it would be necessary to make a slight alteration to Theorem 3.6 to accomodate the missing diagonal pairs, i.e. {∞,*i*} from row *i*.
**Theorem 5.5.1** Suppose we have two *C**B**H**R*(2*n* − 1), *P* and *Q* based on *G* = *G**F*(2*n* − 1), with the following properties:

1.  *P* and *Q* are a *Latin pair* such that,

2.  *P* ⊙ *Q* has a pair of disjoint *common transversals* *T*<sub>1</sub> and *T*<sub>2</sub> (with *T*<sub>2</sub> in *P*), which do not intersect that main diagonal, and

3.  the block designs obtained from *P* and *Q*, call them *D*(*P*) and *D*(*Q*) respectively, have the property that if *B*<sub>*i*</sub> and *C*<sub>*i*</sub> are the blocks from *D*(*P*) obtained from row *i*, then *B*<sub>*i*</sub> and *C*<sub>*i*</sub> are also the blocks of *D*(*Q*) obtained from row *i*.

Then a *B**R**S*(4*n*) exists.
*Proof*
As for Theorem 3.6
It was then claimed that the two *C**B**H**R*(2*n* − 1)s obtained from a *S**S**B**S* and its transpose satisfy the three conditions of Theorem 3.8. Hence implying the existence of a *B**R**S*(4*n*).
However, recently a counter-example has been found.

#### Lemma 5.5.1

\[2\] If *p* = 8*k* + 5 is a prime, *p* &gt; 5, then the pairs
$$(x^{4i},-x{4i+1}),(x^{4i+2},x^{4i+1})\\hspace{0.5cm} 0 \\leq i \\leq 2k$$
 form a *S**S**B**S* in *G**F*(*p*), provided *x*<sup>2</sup> − 1 is a square mod *p*.
*Proof*

1.  The elements in the starter pairs are a complete replication of *G**F*(*p*)∖{0}.
    $x^{\\frac{1}{2} (q-1)} = x^{4k+2} = -1$, therefore we can write the pairs as,
    $$(X^{4i},x^{4(k+i)+3}),(x^{4i+2},x^{4i+1}) \\hspace{0.5cm} 0 \\leq i \\leq 2k$$
     All the members of these pairs are clearly unique and there are 4(2*k* + 1)=8*k* + 4 of them, hence they must all of (*G**F*(*p*)∖{0}.

2.  The differences are similarly a complete replication of *G**F*(*p*)∖{0}.
    The differences are ±*x*<sup>4*i*</sup>(*x* + 1), ± *x*<sup>4*i* + 1</sup>(*x* − 1), which can be written as
    *x*<sup>4*i*</sup>(*x* + 1),*x*<sup>4(*i* + *k*)+2</sup>(*x* + 1),*x*<sup>4*i* + 1</sup>(*x* − 1),*x*<sup>4(*i* + *k*)+3</sup>(*x* − 1)
     Which are all unique provided (*x* + 1) and (*x* − 1) have the same quadratic character (meaning either both of neither are squares). This is true because (*x* + 1)(1 − *x*)=*x*<sup>2</sup> − 1 is a square.

3.  The starter is ***skew***, (the positive and negative sums are all distinct).
    The sums are ±*x*<sup>4*i*</sup>(1 − *x*), ± *x*<sup>4*i* + 1</sup>(*x* + 1) which again are all unique, provided (1 − *x*) and (*x* + 1) have the same quadratic character. True, because (1 − *x*)(*x* + 1)= − (*x*<sup>2</sup> − 1)=*x*<sup>4*k* + 2</sup>(*x*<sup>2</sup> − 1), is a square.

4.  The starter is ***symmetric***.
    Indeed, −*x*<sup>4*i*</sup> = *x*<sup>4(*i* + *k*)+2</sup>, generates the same elements as *x*<sup>4*i* + 2</sup> shifted by *k* places.

5.  The associated block design is balanced.
    The blocks in the first row are,
    {∞} ∪ *R*, due to the left hand members (where *R* is the set of squares).
    {0}∪*N*, due to the right hand members (where *N* is the set of non-squares).
    We can show that these blocks along with their translates form a *B**I**B**D*.
    Using an argument from Theorem 5.2.4, we can say that all elements of *R* are generated as differences of *R* from the same number of times (say *λ*<sub>1</sub> times). Also, a similar argument allows us to say that all the elements of *N* are generated as differences of *R* the same number of times (say *λ*<sub>2</sub>). Now, of course *N* = *x**R*. So we can say that to each difference of members of *R* which generates a square there is a difference of *N* which generates a non-square. Therefore every *r* ∈ *R* occurs as a difference in *N*, *λ*<sub>1</sub> times. For the same reason every *n* ∈ *N* occurs as a difference between members of *N*, *λ*<sub>2</sub> times. Therefore, each element of *G**F*(*p*)∖{0} occurs *λ*<sub>1</sub> + *λ*<sub>2</sub> times as a difference in *R* or *N*.
    Now, |*R*|=|*N*|=4*k* + 2. So each of the two sets, *R* and *N*, gives (4*k* + 2)(4*k* + 1) differences. Furthermore there are 8*k* + 4 elements of *G**F*(*p*)∖{0}, and each occurs as a difference *λ*<sub>1</sub> + *λ*<sub>2</sub> times. So,
    (2(4*k* + 2)(4*k* + 1)=(*λ*<sub>1</sub> + *λ*<sub>2</sub>)(8*k* + 4)
    ∴*λ*<sub>1</sub> + *λ*<sub>2</sub> = 4*k* + 1
     Adjoining 0 to *N* creates each member of *G**F*(*p*)∖{0} once again, as either 0 − *n* or *n* − 0.
    Adjoining ∞ to *R*, makes |*R*|=4*k* + 2 pairs involving ∞. Therefore, {∞} ∪ *R* and {0}∪*N* and their translates have between them each pair from {∞{ ∪ *G**F*(*p*) occurring 4*k* + 2 times. Hence the block design is balanced.

*Example 5.5.1*
Let *P* be the *C**B**H**R*(2*n* − 1) obtained from the *S**S**B**S* in Lemma 3.2 when *p* = 13
(1, 11),(3, 7),(4, 2),(9, 8),(10, 5),(12, 6)
 By the ***transpose*** *X*<sup>*T*</sup> of a starter *X* we mean those pairs in the first column of the square generated by *X*.
In this case, for example, (1, 11) goes in cell (0,12) therefore will be a pair in the first column (1 + *i*, 11 + *i*) in position (0 + *i*, 12 + *i*), such that 12 + *i* = 0 mod 13,

(2,12) goes in (1,0) hence belongs to the transpose of this starter

In general a starter-pair (*a*, *b*) goes in (0, *a* + *b*), so the corresponding transpose-pair will be (*a* − *a* − *b*, *b* − *a* − *b*)=(−*b*, −*a*). So the transpose of the above starter is:
(2, 12),(6, 10),(11, 9),(5, 4),(8, 3),(7, 1)
 If we now apply the Schellenberg construction as suggested in \[13\] we obtain *P* ⊙ *Q*:

<span>-0.45cm</span><span>-0.45cm</span>

$P Q = $

|  0,0 |  2,12 |  10,5 |  6,10 |  9,8 | 12,6 |  4,2  |  11,9 |  7,1  |  5,4 |  3,7  |  8,3  |  1,11 |
|:----:|:-----:|:-----:|:-----:|:----:|:----:|:-----:|:-----:|:-----:|:----:|:-----:|:-----:|:-----:|
| 2,12 |  1,1  |  3,0  |  11,6 | 7,11 | 10,9 |  0,7  |  5,3  | 12,10 |  8,2 |  6,5  |  4,8  |  9,4  |
| 10,5 |  3,0  |  2,2  |  4,1  | 12,7 | 8,12 | 11,10 |  1,8  |  6,4  | 0,11 |  9,3  |  7,6  |  5,9  |
| 6,10 |  11,6 |  4,1  |  3,3  |  5,2 |  0,8 |  9,0  | 12,11 |  2,9  |  7,5 |  1,12 |  10,4 |  8,7  |
|  9,8 |  7,11 |  12,7 |  5,2  |  4,4 |  6,3 |  1,9  |  10,1 |  0,12 | 3,10 |  8,6  |  2,0  |  11,5 |
| 12,6 |  10,9 |  8,12 |  0,8  |  6,3 |  5,5 |  7,4  |  2,10 |  11,2 |  1,0 |  4,11 |  9,7  |  3,1  |
|  4,2 |  0,7  | 11,10 |  9,0  |  1,9 |  7,4 |  6,6  |  8,5  |  3,11 | 12,3 |  2,1  |  5,12 |  10,8 |
| 11,9 |  5,3  |  1,8  | 12,11 | 10,1 | 2,10 |  8,5  |  7,7  |  9,6  | 4,12 |  0,4  |  3,2  |  6,0  |
|  7,1 | 12,10 |  6,4  |  2,9  | 0,12 | 11,2 |  3,11 |  9,6  |  8,8  | 10,7 |  5,0  |  1,5  |  4,3  |
|  5,4 |  8,2  |  0,11 |  7,5  | 3,10 |  1,0 |  12,3 |  4,12 |  10,7 |  9,9 |  11,8 |  6,1  |  2,6  |
|  3,7 |  6,5  |  9,3  |  1,12 |  8,6 | 4,11 |  2,1  |  0,4  |  5,0  | 11,8 | 10,10 |  12,9 |  7,2  |
|  8,3 |  4,8  |  7,6  |  10,4 |  2,0 |  9,7 |  5,12 |  3,2  |  1,5  |  6,1 |  12,9 | 11,11 |  0,10 |
| 1,11 |  9,4  |  5,9  |  8,7  | 11,5 |  3,1 |  10,8 |  6,0  |  4,3  |  2,6 |  7,2  |  0,10 | 12,12 |

**Figure 38**

Although this is the join of two Latin squares, the repetition of ordered pairs means that they are not orthogonal. An immediate solution might be to reverse the order of half the repeated pairs, but this approach ruins the join of Latin squares property.
Anderson, has developed a theorem to overcome this property. We present a slight adaptation of this theorem:

#### Theorem 5.5.2

\[2\] Let *p* = 8*k* + 5 be a prime, *p* &gt; 5. Then a *B**R**S* of side 2*p* + 1 exists.
*Proof*
Suppose we take *P* ⊙ *Q*, and label elements of the pairs from *P* with subscript 1 and all those from *Q* with subscript 2. Then remove the diagonal pairs (*a*, *a*), and call this new array *A*.
*A* contains all the unordered pairs {*a*<sub>1</sub>, *b*<sub>1</sub>},{*a*<sub>2</sub>, *b*<sub>2</sub>} exactly once.
The first row of *A* contains the ordered pairs,

(*x*<sub>1</sub><sup>4*i*</sup>, −*x*<sub>1</sub><sup>4*i* + 1</sup>),(*x*<sub>1</sub><sup>4*i* + 2</sup>, −*x*<sub>1</sub><sup>4*i* + 1</sup>) due to *P*, and
(*x*<sub>2</sub><sup>4*i* + 1</sup>, −*x*<sub>2</sub><sup>4*i*</sup>),(*x*<sub>2</sub><sup>4*i* + 1</sup>, −*x*<sub>2</sub><sup>4*i* + 2</sup>) due to *Q*
So all the squares subscript 1 appear as left hand members of pairs as do all the non-squares subscript 2. Also, all the non-squares appear with subscript 1 in the right hand positions and all the squares with subscript 2.
If we denote the set of squares with subscript 1 by *R*<sub>1</sub>, and with subscript 2 by *R*<sub>2</sub>. And similarly denote the sets of non-squares as *N*<sub>1</sub> and *N*<sub>2</sub>. Then in *A*,

*R*<sub>1</sub> ∪ *N*<sub>2</sub> occupies the left hand positions
while *N*<sub>1</sub> ∪ *R*<sub>2</sub> occupies the right
Now define *B* as the array of side *p* whose first row contains the pairs:
(*x*<sub>2</sub><sup>4*i*</sup>, −*x*<sub>1</sub><sup>4*i* + 1</sup>),(*x*<sub>1</sub><sup>4*i* + 2</sup>, *x*<sub>2</sub><sup>4*i* + 1</sup>),(−*x*<sub>2</sub><sup>4*i*</sup>, *x*<sub>1</sub><sup>4*i* + 1</sup>),(−*x*<sub>1</sub><sup>4*i* + 2</sup>, −*x*<sub>2</sub><sup>4*i* + 1</sup>)
 So in *B* the left hand positions are occupied by *R*<sub>2</sub> ∪ *R*<sub>1</sub>, while the right are occupied by *N*<sub>1</sub> ∪ *N*<sub>2</sub>.
In order that all unordered pairs {*a*<sub>1</sub>, *b*<sub>2</sub>} occur once in *B* requires that in the first row all the members of *G**F*(*p*) occur once as a difference in one of two ways:

Either as *a*<sub>1</sub> − *b*<sub>2</sub> which are called (1, 2) ***mixed differences***
Or as *b*<sub>2</sub> − *a*<sub>1</sub>, called (2,1) mixed differences.
Consider (2, 1) mixed differences in the first row, they are:
*x*<sup>4*i*</sup> + *x*<sup>4*i* + 1</sup> = *x*<sup>4*i*</sup>(1 + *x*)
−*x*<sup>4*i*</sup> − *x*<sup>4*i* + 1</sup> = −*x*<sup>4*i*</sup>(1 + *x*)
*x*<sup>4*i* + 1</sup> − *x*<sup>4*i* + 2</sup> = *x*<sup>4*i* + 1</sup>(1 − *x*)
−*x*<sup>4*i* + 1</sup> + *x*<sup>4*i* + 2</sup> = −*x*<sup>4*i* + 1</sup>(1 − *x*)
i.e. ±*x*<sup>4*i*</sup>(1 + *x*), ± *x*<sup>4*i* + 1</sup>(1 − *x*)
Again, these are all of *G**F*(*p*) provided that *x*<sup>2</sup> − 1 is a square.
Now arrange *A* and *B* in the following familiar manner to construct an array of side 2*p* + 1:

| *A* | *ϕ* |       *θ*<sup>*T*</sup>      |
|:---:|:---:|:----------------------------:|
| *ϕ* | *B* |       *θ*<sup>*T*</sup>      |
| *θ* | *θ* | ∞<sub>1</sub>, ∞<sub>2</sub> |

Next place the missing pairs in a manner similar to the original construction of Schellenberg. Take a pair (*a*<sub>1</sub>, *b*<sub>2</sub> from the first row of *B* in position (0<sub>2</sub>, *h*<sub>2</sub>) and consider the cells in transversal *T*<sub>1</sub> of *B*, where
$$T\_1 = \\left \\{((0+g)\_2,(h+g)\_2) \\hspace{0.2cm} \\middle| \\hspace{0.2cm} g \\in Z\_p \\right \\}$$
 If cell (*i*<sub>2</sub>, *j*<sub>2</sub>) in *T*<sub>1</sub> contains (*n*<sub>1</sub>, *k*<sub>2</sub>),

-   put (*n*<sub>1</sub>, *k*<sub>2</sub>) in cell (*i*<sub>2</sub>, ∞)

-   also put (∞<sub>1</sub>, *k*<sub>2</sub>) in (*k*<sub>1</sub>, *j*<sub>2</sub>) and (∞<sub>2</sub>, *n*<sub>1</sub>) in (*n*<sub>1</sub>, *j*<sub>2</sub>)

Now consider the transversal *T*<sub>2</sub> of *B*, where (*u*<sub>1</sub>, *v*<sub>2</sub>) is a pair in (0<sub>2</sub>, *l*<sub>2</sub>) and,
$$T\_2 = \\left \\{((0+g)\_2,(l+g)\_2) \\hspace{0.2cm} \\middle| \\hspace{0.2cm} g \\in Z\_p \\right \\}$$
 If cell (*i*<sub>2</sub>, *j*<sub>2</sub>) in *T*<sub>2</sub> contains (*h*<sub>1</sub>, *m*<sub>2</sub>),

-   put (*h*<sub>1</sub>, *m*<sub>2</sub>) in cell (∞,*j*<sub>2</sub>)

-   also put (∞<sub>2</sub>, *m*<sub>2</sub>) in (0<sub>2</sub>, *m*<sub>1</sub>) and (*h*<sub>1</sub>, ∞<sub>1</sub>) in (0<sub>2</sub>, *h*<sub>1</sub>)

Finally put (*i*<sub>1</sub>, *i*<sub>2</sub>) in (*i*<sub>2</sub>, *i*<sub>2</sub>) for 0 ≤ *i* ≤ *p* − 1, and put (∞<sub>1</sub>, ∞<sub>2</sub>) in cell (∞,∞).
*Example*
Continuing from before,
<span>-1.5cm</span><span>-1.5cm</span>

*A*= $\\begin{array}{|c|c|c|c|c|c|c|c|c|c|c|c|c|c|} \\hline  & 0\_1 & 1\_1 & 2\_1 & 3\_1 & 4\_1 & 5\_1 & 6\_1 & 7\_1 & 8\_1 & 9\_1 & 10\_1 & 11\_1 & 12\_1\\\\\\hline 0\_1 & & 2\_2 12\_2 & 10\_1 5\_1 & 6\_2 10\_2 & 9\_1 8\_1 & 12\_1 6\_1 & 4\_1 2\_1 & 11\_2 9\_2 & 7\_2 1\_2 & 5\_2 4\_2 & 3\_1 7\_1 & 8\_2 3\_2 & 1\_1 11\_1\\\\\\hline 1\_1 & 2\_1 12\_1 & & 3\_2 0\_2 & 11\_1 6\_1 & 7\_2 11\_2 & 10\_1 9\_1 & 0\_1 7\_1 & 5\_1 3\_1 & 12\_2 10\_2 & 8\_2 2\_2 & 6\_2 5\_2 & 4\_1 8\_1 & 9\_2 4\_2\\\\\\hline 2\_1 & 10\_2 5\_2 & 3\_1 0\_1 & & 4\_2 1\_2 & 12\_1 7\_1 & 8\_2 12\_2 & 11\_1 10\_1 & 1\_1 8\_1 & 6\_1 4\_1 & 0\_2 11\_2 & 9\_2 3\_2 & 7\_2 6\_2 & 5\_1 9\_1\\\\\\hline 3\_1 & 6\_1 10\_1 & 11\_2 6\_2 & 4\_1 1\_1 & & 5\_2 2\_2 & 0\_1 8\_1 & 9\_2 0\_2 & 12\_1 11\_1 & 2\_1 9\_1 & 7\_1 5\_1 & 1\_1 12\_2 & 10\_2 4\_2 & 8\_2 7\_2\\\\\\hline 4\_1 & 9\_2 8\_2 & 7\_1 11\_1 & 12\_2 7\_2 & 5\_1 2\_1 & & 6\_2 3\_2 & 1\_1 9\_1 & 10\_2 1\_2 & 0\_1 12\_1 & 3\_1 10\_1 & 8\_1 6\_1 & 2\_2 0\_2 & 11\_2 5\_2\\\\\\hline 5\_1 & 12\_2 6\_2 & 10\_2 9\_2 & 8\_1 12\_1 & 0\_2 8\_2 & 6\_1 3\_1 & & 7\_1 4\_1 & 2\_1 10\_1 & 11\_2 2\_2 & 1\_1 0\_1 & 4\_1 11\_1 & 9\_1 7\_1 & 3\_2 1\_2\\\\\\hline 6\_1 & 4\_2 2\_2 & 0\_2 7\_2 & 11\_2 10\_2 & 9\_1 0\_1 & 1\_2 9\_2 & 7\_1 4\_1 & & 8\_2 5\_2 & 3\_1 11\_1 & 12\_2 3\_2 & 2\_1 1\_1 & 5\_1 12\_1 & 10\_1 8\_1\\\\\\hline 7\_1 & 11\_1 9\_1 & 5\_2 3\_2 & 1\_2 8\_2 & 12\_2 11\_2 & 10\_1 1\_1 & 2\_2 10\_2 & 8\_1 5\_1 & & 9\_2 6\_2 & 4\_1 12\_1 & 0\_2 4\_2 & 3\_1 2\_1 & 6\_1 0\_1\\\\\\hline 8\_1 & 7\_1 1\_1 & 12\_1 10\_1 & 6\_2 4\_2 & 2\_2 9\_2 & 0\_1 12\_1 & 11\_2 2\_2 & 3\_1 11\_1 & 9\_1 6\_1 & & 10\_2 7\_2 & 5\_1 0\_1 & 1\_2 5\_2 & 4\_1 3\_1\\\\\\hline 9\_1 & 5\_1 4\_1 & 8\_1 2\_1 & 0\_1 11\_1 & 7\_2 5\_2 & 3\_2 10\_2 & 1\_2 0\_2 & 12\_1 3\_1 & 4\_2 12\_2 & 10\_1 7\_1 & & 11\_2 8\_2 & 6\_1 1\_1 & 2\_2 6\_2\\\\\\hline 10\_1 & 3\_2 7\_2 & 6\_1 5\_1 & 9\_1 3\_1 & 1\_1 12\_1 & 8\_2 6\_2 & 4\_2 11\_2 & 2\_2 1\_2 & 0\_1 4\_1 & 5\_2 0\_2 & 11\_1 8\_1 & & 12\_2 9\_2 & 7\_1 2\_1\\\\\\hline 11\_1 & 8\_1 3\_1 & 4\_2 8\_2 & 7\_1 6\_1 & 10\_1 4\_1 & 2\_1 0\_1 & 9\_2 7\_2 & 5\_2 12\_2 & 3\_2 2\_2 & 1\_1 5\_1 & 6\_2 1\_2 & 12\_1 9\_1 & & 0\_2 10\_2\\\\\\hline 12\_1 & 1\_2 11\_2 & 9\_1 4\_1 & 5\_2 9\_2 & 8\_1 7\_1 & 11\_1 5\_1 & 3\_1 1\_1 & 10\_2 8\_2 & 6\_2 0\_2 & 4\_2 3\_2 & 2\_1 6\_1 & 7\_2 2\_2 & 0\_1 10\_1 & \\\\\\hline \\end{array}$

**Figure 39**

<span>-1.5cm</span><span>-1.5cm</span>

*B*= $\\begin{array}{|c|c|c|c|c|c|c|c|c|c|c|c|c|c|} \\hline  & 0\_2 & 1\_2 & 2\_2 & 3\_2 & 4\_2 & 5\_2 & 6\_2 & 7\_2 & 8\_2 & 9\_2 & 10\_2& 11\_ 2& 12\_2\\\\\\hline 0\_2 & & 12\_2 2\_1 & 10\_1 5\_2 & 10\_2 6\_1 & 9\_2 8\_1 & 12\_1 6\_2 & 4\_1 2\_2 & 9\_1 11\_2 & 1\_1 7\_2 & 4\_2 5\_1 & 3\_2 7\_1 & 3\_1 8\_2 & 1\_2 11\_1\\\\\\hline 1\_2 & 2\_2 12\_1 & & 0\_2 3\_1 & 11\_1 6\_2 & 11\_2 7\_1 & 10\_2 9\_1 & 0\_1 7\_2 & 5\_1 3\_2 & 10\_1 12\_2 & 2\_1 8\_2 & 5\_2 6\_1 & 4\_2 8\_1 & 4\_1 9\_2 \\\\\\hline 2\_2 & 5\_1 10\_2 & 3\_2 0\_1 & & 1\_2 4\_1 & 12\_1 7\_2 & 12\_2 8\_1 & 11\_2 10\_1 & 1\_1 8\_2 & 6\_1 4\_2 & 11\_1 0\_2 & 3\_1 9\_2 & 6\_2 7\_1 & 5\_2 9\_1\\\\\\hline 3\_2 & 6\_2 10\_1 & 6\_1 11\_2 & 4\_2 1\_1 & & 2\_2 5\_1 & 0\_1 8\_2 & 0\_2 9\_1 & 12\_2 11\_1 & 2\_1 9\_2 & 7\_1 5\_2 & 12\_1 1\_2& 4\_1 10\_2 & 7\_2 8\_1 \\\\\\hline 4\_2 & 8\_2 9\_1 & 7\_2 11\_1 & 7\_1 12\_2 & 5\_2 2\_1 & & 3\_2 6\_1 & 1\_1 9\_2 & 1\_2 10\_1 & 0\_2 12\_1 & 3\_1 10\_2 & 8\_1 6\_2 & 0\_1 2\_2 & 5\_1 11\_2 \\\\\\hline 5\_2 & 6\_1 12\_2 & 9\_2 10\_1 & 8\_2 12\_1 & 8\_1 0\_2 & 6\_2 3\_1 & & 4\_2 7\_1 & 2\_1 10\_2 & 2\_2 11\_1 & 1\_2 0\_1 & 4\_1 11\_2 & 9\_1 7\_2 & 1\_1 3\_2 \\\\\\hline 6\_2 & 2\_1 4\_2 & 7\_1 0\_2 & 10\_2 11\_1 & 9\_2 0\_1 & 9\_1 1\_2 & 7\_2 4\_1 & & 5\_2 8\_1 & 3\_1 11\_2 & 3\_2 12\_1 & 2\_2 1\_1 & 5\_1 12\_2 & 10\_1 8\_2\\\\\\hline 7\_2 & 11\_1 9\_2 & 3\_1 5\_2 & 8\_1 1\_2 & 11\_2 12\_1 & 10\_2 1\_1 & 10\_1 2\_2 & 8\_2 5\_1 & & 6\_2 9\_1 & 4\_1 12\_2 & 4\_2 0\_1 & 3\_2 2\_1 & 6\_1 0\_1\\\\\\hline 8\_2 & 7\_1 1\_2 & 12\_1 10\_2 & 4\_1 6\_2 & 9\_1 2\_2 &12\_2 0\_1 & 11\_2 2\_1 & 11\_1 3\_2 & 9\_2 6\_1 & & 7\_2 10\_1 & 5\_1 0\_2 & 5\_2 1\_1 & 4\_2 3\_1\\\\\\hline 9\_2 & 5\_2 4\_1 & 8\_1 2\_2 & 0\_1 11\_2 & 5\_1 7\_2 & 10\_1 3\_2 & 0\_2 1\_1 & 12\_2 3\_1 & 12\_1 4\_2 & 10\_2 7\_1 & & 8\_2 11\_1 & 6\_1 1\_2 & 6\_2 2\_1\\\\\\hline 10\_2 & 7\_2 3\_1 & 6\_2 5\_1 & 9\_1 3\_2 & 1\_1 12\_2 & 6\_1 8\_2 & 11\_1 4\_2 & 1\_2 2\_1 & 0\_2 4\_1 & 0\_1 5\_2 & 11\_2 8\_1 & & 9\_2 12\_1 & 7\_1 2\_2\\\\\\hline 11\_2 & 8\_1 3\_2 & 8\_2 4\_1 & 7\_2 6\_1 & 10\_1 4\_2 & 2\_1 0\_2 & 7\_1 9\_2 & 12\_1 5\_2 & 2\_2 3\_1 & 1\_2 5\_1 & 1\_1 6\_2 & 12\_2 9\_1 & & 10\_2 0\_1\\\\\\hline 12\_2 & 11\_2 1\_1 & 9\_1 4\_2 & 9\_2 5\_1 & 8\_2 7\_1 & 11\_1 5\_2 & 3\_1 1\_2 & 8\_1 10\_2 & 0\_1 6\_2 & 3\_2 4\_1 & 2\_2 6\_1 & 2\_1 7\_2 & 0\_2 10\_1 & \\\\\\hline \\end{array}$

**Figure 40**

Now, assemble the large array and apply the construction using the following transversals,
$$T\_1 = \\{((0+g)\_2,(5+g)\_2)\\hspace{0.2cm}|\\hspace{0.2cm}g \\in Z\_{13}\\}$$
$$T\_2 = \\{((0+g)\_2,(11+g)\_2)\\hspace{0.2cm}|\\hspace{0.2cm}g \\in Z\_{13}\\}$$
 The obtained array is the *B**R**S*(28) in Figure 41.
The finished array (Figure 41) is an *O**R**S* because it contains one ordered pair corresponding to each unordered pair from the set {∞<sub>1</sub>, ∞<sub>2</sub>, 0<sub>1</sub>, ..., *p* − 1<sub>1</sub>, 0<sub>2</sub>, ..., *p* − 1<sub>2</sub>}, with each member of the same set occurring exactly once in each row and column. To prove that this *O**R**S* is a *B**R**S* we need to show that the block design obtained from the rows in the usual way is balanced.
Consider the blocks obtained from the first *p* rows. We have shown already that the first row of *A* conssted of two blocks, left and right where
$\\hspace{1cm}$ Left block: *R*<sub>1</sub> ∪ *N*<sub>2</sub>
$\\hspace{1cm}$ Right block: *N*<sub>1</sub> ∪ *R*<sub>2</sub>
The last stage of the construction put the pairs {∞<sub>2</sub>, 0<sub>1</sub>} and {∞<sub>1</sub>, 0<sub>2</sub>} in row 0<sub>1</sub> of the finished array. So the blocks obtained from the first *p* rows are:
*R*<sub>1</sub> ∪ *N*<sub>2</sub> ∪ {∞<sub>2</sub>, ∞<sub>1</sub>}
*N*<sub>1</sub> ∪ *R*<sub>2</sub> ∪ {0<sub>1</sub>, 0<sub>2</sub>}
 and their translates.
By similar reasoning the blocks obtained from the next *p* rows are:
*R*<sub>2</sub> ∪ *R*<sub>1</sub> ∪ {0<sub>1</sub>, ∞<sub>2</sub>}
*N*<sub>1</sub> ∪ *N*<sub>2</sub> ∪ {0<sub>2</sub>, ∞<sub>1</sub>}
 and their translates. Finally the row labelled ∞ contributes a further two blocks to the design: $\\hspace{1cm} \\{0\_1,\\infty \_1\\} \\cup R\_1 \\cup N\_1$ obtained from the left hand members of pairs, and
$\\hspace{1cm} \\{0\_2,\\infty \_2\\} \\cup R\_2 \\cup N\_2$ obtained from the right hand members.
Fortunately, Schellenberg has shown that these blocks do indeed form a *B**I**B**D* with parameters,
(2(*p* + 1<sub>,</sub>*p* + 1, *p*).
To show this we consider another result due to Bose. He showed that the blocks
{∞,*x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>}{0, *x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>} form a difference system in *G**F*(*q*) with *λ* = (*q* − 1)/2. This result implies that the blocks {∞,*x*<sup>1</sup>, *x*<sup>3</sup>, ..., *x*<sup>*q* − 2</sup>}{0, *x*<sup>1</sup>, *x*<sup>3</sup>, ..., *x*<sup>*q* − 2</sup>} also form a difference system with the same concurrence number.

#### Lemma 5.5.2

\[4\] If *q* = *p*<sup>*n*</sup> ≡ 1(mod 4) is a prime power, then if we write down the non-zero elements of *G**F*(*q*) which are squares:
*x*<sup>0</sup>, *x*<sup>2</sup>, *x*<sup>4</sup>, ..., *x*<sup>*q* − 3</sup>
 Every non-square element of *G**F*(*q*) occurs exactly (*q* − 1)/4 times as a difference between these elements and every square occurs (*q* − 5)/4 times.
*Proof*
We can write the differences in the following way: $$

|                               |                                      |         |                                                  |
|:-----------------------------:|:------------------------------------:|:-------:|:------------------------------------------------:|
|     (*x*<sup>2</sup> − 1)     | *x*<sup>2</sup>(*x*<sup>2</sup> − 1) | $ ... $ |    *x*<sup>*q* − 3</sup>(*x*<sup>2</sup> − 1)    |
|     (*x*<sup>4</sup> − 1)     | *x*<sup>2</sup>(*x*<sup>4</sup> − 1) | $ ... $ |    *x*<sup>*q* − 3</sup>(*x*<sup>4</sup> − 1)    |
|                               |                                      | $ ... $ |                                                  |
| $(x^{q-3}-1)\\hspace{0.25cm}$ |  $\\hspace{0.25cm}x^{2}(x^{q-3}-1)$  | $ ... $ | *x*<sup>*q* − 3</sup>(*x*<sup>*q* − 3</sup> − 1) |

$$ Where the first column has been obtained by substracting $x^0$ from
every other square. The second column by taking $x^2$ from every other
square, the third by taking $x^4$ and so on.\\
\\
Because the differences in every column except the first have an even
power of $x$ multiplied by some member of the first column it is clear
that the quadratic nature of these terms is determined by whether or not
the elements in the first column are square or not.\\
\\
Therefore to complete the proof we need to show that among the $(q-3)/2$
elements, $$
x<sup>2-1,x</sup>4-1,...,x<sup>{q-3}-1
$$ every square occurs $(q-5)/4$
times and every non-square $(q-1)/4$ times. We can further simplify the
problem if we write,
$$
x</sup>{2i}-1=(x<sup>i+1)(x</sup>i-1)=(x<sup>i-1)</sup>2
$$ Then $x^{2i}-1$
is a square or non-square depending on whether:
$$
z\_i =
*i**s**a**s**q**u**a**r**e**o**r**n**o**t*.*S**o**i**t**r**e**m**a**i**n**s**o**n**l**y**t**o**c**o**u**n**t**t**h**e**o**c**c**u**r**r**e**n**c**e**s**o**f**s**q**u**a**r**e**s*/*n**o**n* − *s**q**u**a**r**e**s**i**n**t**h**e**s**e**t*:
Z={z\_1,z\_2,...,z\_{(q-3)/2}}
*S**u**p**p**o**s**e**w**e**c**o**n**s**i**d**e**r**i**n**s**t**e**a**d**t**h**e**s**e**t*,
A = {z\_1,z\_2,...,z\_{q-2}}
$$ which clearly has $q-2$ members. We can
show that each member is a unique member of $GF(q)$, because if two
different elements $z\_i$ and $z\_j$ were the same we would have:
$$
 ( q)
(x<sup>j-1)(x</sup>i+1) (x<sup>j+1)(x</sup>i-1)( q)
x<sup>jx</sup>i+x<sup>j-x</sup>i-1 x<sup>jx</sup>i - x^j + x^i -1( q)
x^j x^i ( q)
$$ but
$1 \\leq i, j \\leq q-2$, therefore the above is only satisfied if
$x^j = x^i, \\therefore i=j$, which contradicts the assumption that the
two elements were different.\\
Further, if $z\_i \\equiv -1\\hspace{0.1cm}(\\mathrm{mod}\\hspace{0.1cm} q)$
then $x^i+1 = -x^i+1$, which implies $x^i=0$. So $-1 \\notin A$. Recall
that when $q \\equiv 1\\hspace{0.1cm}(\\mathrm{mod}\\hspace{0.1cm} 4)$, $-1$
is a square.\\
Also, if $z\_i \\equiv -1\\hspace{0.1cm}(\\mathrm{mod}\\hspace{0.1cm} q)$
then $x^i+1=x^i-1$, so $1 \\notin A$. 1 is a square.\\
Finally, $x^{q-1/2}=-1$, therefore $z\_{q-1/2}=0$.\\
Clearly, then $A=GF(q) \\backslash \\{1,-1\\}$, and
$A \\backslash \\{z\_{q-1/2}\\}
= GF(q) \\backslash \\{0,1,-1\\}$, so $A \\backslash \\{z\_{q-1/2}\\}$ contains
$(q-1)/2$ non-squares and $(q-5)/2$ squares.
$$
A {z\_{(q-1)/2}}={z\_1,z\_2,...,z\_{(q-3)/2},z\_{(q+1)/2},z\_{(q+3)/2},...,z\_{q-2}}
*B**u**t*,
z\_{{(q+1)/2}+k} = = = k = 1,2,...,(q-3)/2$$ So *z*<sub>{(*q* + 1)/2}+*k*</sub> and *z*<sub>*k*</sub> \[*k* = 1, 2, ..., (*q* − 3)/2\] are both squares or both non-squares, hence *Z* = {*z*<sub>1</sub>, *z*<sub>2</sub>, ..., *z*<sub>(*q* − 3)/2</sub>} contains exactly (*q* − 1)/4 non-squares and (*q* − 5)/4 squares. So the lemma is proven.

#### Corollary 5.5.2

If *q* = *p*<sup>*n*</sup> ≡ 1(mod 4) is a prime power, then if we write down the non-zero elements of *G**F*(*q*) which are non-squares:
*x*<sup>1</sup>, *x*<sup>3</sup>, *x*<sup>5</sup>, ..., *x*<sup>*q* − 2</sup>
 Every square element of *G**F*(*q*) occurs exactly (*q* − 1)/4 times as a difference between these elements and every non-square occurs (*q* − 5)/4 times.
*Proof*
As for the previous theorem except that each difference is multiplied by *x*, so squares become non-squares and non-squares, squares.

#### Theorem 5.5.3

\[4\] The blocks
{∞,*x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>}{0, *x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>}
 along with their translates, form a *B**I**B**D* with *λ* = (*q* − 1)/2 in *G**F*(*q*), when *q* = *p*<sup>*n*</sup> ≡ 1(mod 4).
*Proof*
From the Lemma we have shown that in the set
{*x*<sup>0</sup>, *x*<sup>2</sup>, *x*<sup>4</sup>, ..., *x*<sup>*q* − 3</sup>}
 each square occurs as a difference (*q* − 5)/4 times, and each non-square (*q* − 1)/4 times. The right hand block also contributes the differences
*x*<sup>0</sup> − 0, 0 − *x*<sup>0</sup>, 1 − *x*<sup>2</sup>, *x*<sup>2</sup> − 1, ..., *x*<sup>*q* − 3</sup> − 0, 0 − *x*<sup>*q* − 3</sup>
±*x*<sup>0</sup>, ±*x*<sup>2</sup>, ..., ±*x*<sup>*q* − 3</sup>
 And because −1 is a square, each square of *G**F*(*q*) occurs a further twice due to these differences.

|             | {∞,*x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>} | {0, *x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup> |    Total    |
|-------------|:----------------------------------------------------------------:|:----------------------------------------------------------------:|:-----------:|
| Squares     |                            (*q* − 5)/4                           |                          {(*q* − 5)/4}+2                         | (*q* − 1)/2 |
| Non-squares |                            (*q* − 1)/4                           |                            (*q* − 1)/4                           | (*q* − 1)/2 |

**Table 10**

Adjoining ∞ to a block of size (*q* − 1)/2 creates (*q* − 1)/2 pairs involving ∞. Therefore in {∞,*x*<sup>0</sup>, *x*<sup>2</sup>, ..., *x*<sup>*q* − 3</sup>} and the translates obtained from this block ∞ makes a pair with each member of *G**F*(*q*), (*q* − 1)/2 times.
Therefore the block design obtained from these two blocks is balanced, and the concurrence number is *λ* = (*q* − 1)/2.
Although we don’t need the following result, it now follows straightforwardly from Corollary 5.4.2.

#### Corollory 5.5.3

\[4\] The blocks,
{∞,*x*<sup>1</sup>, *x*<sup>3</sup>, ..., *x*<sup>*q* − 2</sup>}{0, *x*<sup>1</sup>, *x*<sup>3</sup>, ..., *x*<sup>*q* − 2</sup>}
 along with their translates, form a *B**I**B**D* with *λ* = (*q* − 1)/2 in *G**F*(*q*), when *q* = *p*<sup>*n*</sup> ≡ 1(mod 4).
Now returning to the Anderson construction:
Let:
*S* = *R*<sub>1</sub> ∪ *N*<sub>2</sub> ∪ {∞<sub>2</sub>, ∞<sub>1</sub>}
*T* = *N*<sub>1</sub> ∪ *R*<sub>2</sub> ∪ {0<sub>1</sub>, 0<sub>2</sub>}
*U* = *N*<sub>1</sub> ∪ *N*<sub>2</sub> ∪ {0<sub>2</sub>, ∞<sub>1</sub>}
*V* = *R*<sub>2</sub> ∪ *R*<sub>1</sub> ∪ {0<sub>1</sub>, ∞<sub>2</sub>}
 Now consider the pairs {*a*<sub>1</sub>, *b*<sub>1</sub>} such that *a*, *b* ∈ *G**F*(*q*)∪{∞}. We know, due to the Bose result, that the blocks
{∞<sub>1</sub>}∪*R*<sub>1</sub> and 0<sub>1</sub>}∪*R*<sub>1</sub> along with their translates contain each pair {*a*<sub>1</sub>, *b*<sub>1</sub>}, (*q* − 1)/2 times,
also
{∞<sub>1</sub>}∪*N*<sub>1</sub> and 0<sub>1</sub>}∪*N*<sub>1</sub> and translates contain each pair {*a*<sub>1</sub>, *b*<sub>1</sub>}, (*q* − 1)/2 times.
But,
{∞<sub>1</sub>}∪*R*<sub>1</sub> ⊂ *R*<sub>1</sub> ∪ *N*<sub>2</sub> ∪ {∞<sub>1</sub>, ∞<sub>2</sub>}
{∞<sub>1</sub>}∪*N*<sub>1</sub> ⊂ *N*<sub>1</sub> ∪ *R*<sub>2</sub> ∪ {0<sub>1</sub>, 0<sub>2</sub>}
 Therefore *S* and *T*, along with their translates, contain each pair {*a*<sub>1</sub>, *b*<sub>1</sub>},2 ⋅ (*q* − 1)/2 = *q* − 1, times. Finally each pair {*a*<sub>1</sub>, *b*<sub>1</sub>} occurs once more in the set {∞<sub>1</sub>, 0<sub>1</sub>}∪*R*<sub>1</sub> ∪ *N*<sub>1</sub>. So in the entire block design each pair {*a*<sub>1</sub>, *b*<sub>1</sub>} occurs *q* times.
The same reasoning can be applied to show that the pairs {*a*<sub>2</sub>, *b*<sub>2</sub>} for *a*, *b* ∈ *G**F*(*q*)∪{∞} also occur *q* times in the block design.
It remains to show that the mixed pairs of the form {*a*<sub>1</sub>, *b*<sub>2</sub>}, where *a*, *b* ∈ *G**F*(*q*)∪{∞}, also occur *q* times in the block design. Again we consider (1,2) mixed differences.
For a pair {*a*<sub>1</sub>, *a*<sub>2</sub>} to occur in the block design requires a mixed difference of 0 in either *S*, *T*, *U* or *V*.
In *T*, 0<sub>1</sub> − 0<sub>2</sub> = 0, gives one occurrence, while in *U*
$ .
} $ gives (*q* − 1)/2 occurrences of 0, and similarly *V*,
$ .
} $ gives another (*q* − 1)/2 occurrences of 0 as a mixed difference.
Therefore, 0 occurs as mixed difference in *S*, *T*, *U* and *V* (2 ⋅ (*q* − 1)/2)+1 = *q* times, therefore each pair of the form {*a*<sub>1</sub>, *a*<sub>2</sub>}, occurs *q* times in the block design.
Next, consider pairs of the form {∞<sub>1</sub>, *b*<sub>2</sub>}. In *S* and *U*, ∞<sub>1</sub> makes a pair with each of the (*q* − 1)/2 members of *N*<sub>2</sub>. Therefore in the blocks consisting of *S*, *U* and their translates, ∞<sub>1</sub> makes a pair with each element *b*<sub>2</sub> \[for all *b* ∈ *G**F*(*q*)\] 2 ⋅ (*q* − 1)/2 = *q* − 1 times. Also in *U*, ∞<sub>1</sub> is paired with 0<sub>2</sub>, so ∞<sub>1</sub> makes a pair with each *b*<sub>2</sub> once more. So there are *q* pairs {∞<sub>1</sub>, *b*<sub>2</sub>} for each element *b*<sub>2</sub> in the block design.
By identical reasoning we can say that ∞<sub>2</sub> makes a pair with each *b*<sub>1</sub>, for all *b* ∈ *G**F*(*q*), (*q* − 1)/2 times in *S* and its translates. Also {∞<sub>2</sub>, *b*<sub>1</sub>} \[for all *b* ∈ *G**F*(*q*)\] occurs (*q* + 1)/2 times due to *V* and its translates.
Therefore the pairs {∞<sub>2</sub>, *b*<sub>1</sub>} each occur *q* times in the block design, for all *b* ∈ *G**F*(*q*).
Next we confirm that all the pairs {*a*<sub>1</sub>, *b*<sub>2</sub>} *a*, *b* ∈ *G**F*(*q*) each occur *q* times in the block design. In order to do this we need to show that the non-zero members of *G**F*(*q*) each occur *q* times as a mixed difference *a*<sub>1</sub> − *b*<sub>2</sub>.
We have shown that for *q* ≡ 1(mod 4)

1.  every square, non-square occurs as a difference of two squares of *G**F*(*q*), *s* − 1, *s* times respectively. *s* = (*q* − 1)/4.

2.  every square, non-square occurs as a difference of non-two squares of *G**F*(*q*), *s*, *s* − 1 times respectively.

Consider first the mixed differences *a*<sub>1</sub> − *b*<sub>2</sub> = *c*, where *c* is a square.
*U* contains *N*<sub>1</sub> ∪ *N*<sub>2</sub>, so according to *B* every square occurs as a (1,2) difference (*q* − 1)/4 times in *U*. Also according to *B* each non-square occurs as a (1,2) difference between members of *U*, (*q* − 5)/4 times. Finally, *U* contains the element 0<sub>2</sub>, so each non-square is generated once more. *x*<sub>1</sub><sup>1</sup> − 0<sub>2</sub> = *x*<sub>1</sub><sup>1</sup>, *x*<sub>1</sub><sup>3</sup> − 0<sub>2</sub> = *x*<sub>1</sub><sup>3</sup>, ..., *x*<sub>1</sub><sup>*q* − 2</sup> − 0<sub>2</sub> = *x*<sub>1</sub><sup>*q* − 2</sup>.
Similarly, in *V* each non-square occurs as a mixed difference (*q* − 1)/4 times while each square occurs as a difference (*q* − 5)/4<sub>1</sub> times.
Next, consider blocks *S* and *T*. In *T* each square/non-square exists as a mixed difference once, in the following way: $$

<table style="width:49%;">
<colgroup>
<col width="19%" />
<col width="12%" />
<col width="16%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span class="math inline"><em>x</em><sub>1</sub><sup>1</sup></span> <span class="math inline"><em>x</em><sub>1</sub><sup>3</sup></span></td>
<td align="left"><span class="math inline">−0<sub>2</sub></span> <span class="math inline">−0<sub>2</sub></span></td>
<td align="left"><span class="math inline">=<em>x</em><sup>1</sup></span> <span class="math inline">=<em>x</em><sup>3</sup></span></td>
</tr>
<tr class="even">
<td align="left"><span class="math inline"><em>x</em><sub>1</sub><sup><em>q</em> − 2</sup></span></td>
<td align="left"><span class="math inline">−0<sub>2</sub></span></td>
<td align="left"><span class="math inline">=<em>x</em><sup><em>q</em> − 2</sup></span></td>
</tr>
</tbody>
</table>

<table style="width:49%;">
<colgroup>
<col width="19%" />
<col width="12%" />
<col width="16%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span class="math inline"><em>x</em><sub>2</sub><sup>0</sup></span> <span class="math inline"><em>x</em><sub>2</sub><sup>2</sup></span></td>
<td align="left"><span class="math inline">−0<sub>1</sub></span> <span class="math inline">−0<sub>1</sub></span></td>
<td align="left"><span class="math inline">=<em>x</em><sup>0</sup></span> <span class="math inline">=<em>x</em><sup>2</sup></span></td>
</tr>
<tr class="even">
<td align="left"><span class="math inline"><em>x</em><sub>2</sub><sup><em>q</em> − 3</sup></span></td>
<td align="left"><span class="math inline">−0<sub>1</sub></span></td>
<td align="left"><span class="math inline">=<em>x</em><sup><em>q</em> − 3</sup></span></td>
</tr>
</tbody>
</table>

The remaining mixed differences in *S* and *T* all involve differences between one square and one non-square (and vice versa). Now, for any *c* ∈ *G**F*(*q*), *a* − *b* = *c* has *q* solutions. Two of these,
*a* = 0 − ( − *a*)
*a* = *a* − 0
 involve zero, and can be rejected because we have already considered all differences involving 0 in these blocks. Further, from *A* and *B*, we know there are (*q* − 5)/4 + (*q* − 1)/4 = (*q* − 3)/2 solutions which involve either both squares or both non-squares, and so there remain
(*q* − 2)−\[(*q* − 3)/2\]=(*q* − 1)/2
 solutions which involve elements of opposite quadratic character. Hence we can say that each square, non-square occurs as a difference in *S* and *T* in (*q* − 1)/2 + 1 ways.

<span>|c|c|c|</span> &
& c=square & c = nonsquare
S & &
T & &
U & & +1
V & +1 &
& q & q
Which confirms that each pair {*a*<sub>1</sub>, *b*<sub>2</sub>} for *a*, *b* ∈ *G**F*(*a*)∪{∞} appears in *q* blocks of the block design.
So every pair {*a*, *b*}, *a*, *b* ∈ *G**F*(*q*)<sub>1</sub> ∪ *G**F*(*q*)<sub>2</sub> ∪ {∞<sub>1</sub>, ∞<sub>2</sub>},*a* ≠ *b* appears in *q* blocks of the block design. Hence that design is a *B**I**B**D*, with parameters (2(*q* + 1),*q* + 1, *q*).
So theorem 5.5.2 is established.

Closing Remarks
===============

The results we have established in the previous chapter regarding the existence of balanced Room squares represent by no means the complete story. Du and Hwang \[10\] have established the existence of *S**S**B**S* for all prime powers
*q* = 2<sup>*α*</sup>*t* + 1, *α* ≥ 2, *t* ≥ 3, *t*
 odd. Further, Anderson has shown that consequently the construction due originally to Hwang, Kang and Yu but corrected in \[2\], allows us to state the existence of the corresponding *B**R**S*(2*q* + 2) in one particular case.

By far the most significant remaining result which has not been included in the previous chapter is due to B.A. Anderson who proved that *B**R**S*(2<sup>*n*</sup>) exist for all odd *n* ≥ 3. His construction was based upon the theory of finite geometry, an area which has also contributed constructions for Room squares (the non-balanced kind). Other similar geometrical constructions have been used to establish the existence of *B**R**S*(2<sup>*n*</sup>), for 4 ≤ *n* ≤ 18, *n* even. The two smallest values of *n* ≡ 0(mod 4) for which the existence of a *B**R**S*(*n*) remains in doubt are 36 and 92. The first of these, along with many others, would be established by the doubling construction if a *S**S**B**S* could be found in *Z*<sub>17</sub>. This remains one of the most significant open problems for *B**R**S*, namely to establish the existence of *S**S**B**S* in *Z*<sub>*n*</sub> when *n* is a Fermat prime.

The link between graph theory and Room squares that was touched upon in the second chapter has opened many avenues of research. Possibly the most interesting of which is the existence of perfect Room squares. A one-factorisation of *K*<sub>*n*</sub> is said to be perfect if the union of two of its one-factors is a hamiltonian cycle of *K*<sub>*n*</sub>. A perfect Room square is one of side *n* in which both row and column factorisations of *K*<sub>*n* + 1</sub> are perfect. Very little seems to be known about perfect one-factorisations. Individual examples of perfect Room squares of side 11 have been constructed but no infinite classes have yet been found.

[1] The Room squre of side1 is just the single array element containing the pair {0, 1}.

[2] This is cycle notation, and stands for the permutation 4 → 5, 5 → 4.

[3] In over ten-million attempts, they claim

[4] Both Howell and Whitfield had previously found starters and adders, but the precise method used here due to Stanton & Mullin

[5] The starter in then first Lemma has pairs whose elements always sum to 2*n* − 1, while the second Lemma, because *a*<sup>*n* − 1</sup> = −1, has pairs which can be written in the form (*a*<sup>*x*</sup>, −*a*<sup>*x*</sup>).

[6] In 1880 F.Landry showed *F*<sub>6</sub> = 2<sup>64</sup> + 1 = 274177 × 67280421310721. In 1975 Brillhart and Morrison showed *F*<sub>7</sub> = 2<sup>128</sup> + 1 = 59649589127497217 × 5704689200685129054721. In 1981, Brent and Pollard found that
2<sup>256</sup> + 1 = 1238926361552897 × 93461639715357977769163558199606896584051237541638188580280321

[7] Wallis presented a Room square of side 257 a conference in 1973, completing his proof (different from the one presented here) of the existence of Room squares.

[8] This is a theorem, not proven here

[9] We could have used the same permutation in each case, but the general theorem (as will be introduced) insists they are different, as higher order multiplications require different permutations. Quintuplication, for example, needs at least two.

[10] This definition is extracted in its entirety from \[8\]

[11] Where the blocks are derived in the same way as for a BRS

[12] The *t* = 1 case was proven by Stanton and Sprott (1964) and Parker (1963) prior to Schellenberg.

[13] because *q* ≡ 3(mod 4)

[14] *A*(*X*)∩*A*(*Y*)≠⌀ implies, as (1 + *x*)≠0, that −*x*<sup>2*i*</sup> = −*x*<sup>2*i* − 1</sup> for some *i*, i.e. 1 = *x*<sup>−1</sup>, ∴*A*(*X*)∩*A*(*Y*)=⌀
