# P07 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P07 |

## Round 1

### Student

Teacher, I want to try a small one first: with two rows, putting 1 and 3 below gives 2 above, using 1 to 3 exactly once, right? 2018 rows is too large; I do not know where to start. Could you give me a three-row attempt to fill in first, without giving the entire answer?

### Teacher

Yes, **bottom 1, 3 and upper 2** follows the rules and uses 1, 2, 3 once each.

Now try three rows. Fill these with 1 to 6, each once:

```text
      □
    □   □
  □   □   □
```

One key question first: which three numbers do you want to place in the bottom row?

## Round 2

### Student

I first put larger values 4, 5, 6 below, giving middle 1, 1 and top 0, with repeats and an extra 0, so that failed. I changed to bottom 6, 1, 4, middle 5, 3, top 2, using all of 1 to 6 this time. I can check this trial result, but cannot keep randomly trying for 2018 rows, right? Is there a pattern to rule out some arrangements first? Just a concrete direction to observe would help.

### Teacher

You have found a valid three-row construction:

```text
      2
    5   3
  6   1   4
```

Now observe a “larger-child path”: from top 2 to the larger middle 5, then to the larger bottom 6.

Notice:

- \(5=2+3\)
- \(6=5+1=2+3+1\)

This suggests a pattern ruling out many arrangements: following larger children all the way downward turns the endpoint into “a sum of several distinct numbers along the path.”

Can you identify exactly which numbers are summed in this three-row example?

## Round 3

### Student

It adds top 2, sibling 3, and bottom 1, totaling 6. It does not add the whole path 2, 5, 6; 5 already contains 2 and 3. Since the upper number is a difference, the larger lower number equals the upper plus the other; I understand that step. For 2018 rows, would it sum 2018 different numbers? With minimum 1 through 2018? But that sum seems exactly the total number of cells, 2037171, not exceeding the maximum. Can it still rule anything out?

### Teacher

Your calculation is correct: the minimum sum

\[
1+2+\cdots+2018=2037171
\]

equals exactly the maximum allowed in the whole triangle, so this is “equality,” rather than a direct contradiction.

Equality means two things:

1. The 2018 summands along this path must be exactly \(1,2,\ldots,2018\);
2. the endpoint must be exactly the maximum \(2037171\).

Next consider: with \(1\) to \(2018\) all “occupied” by this path, can regions beside it, especially far from it, still contain these small numbers? If not, how large must their values be at least?

## Round 4

### Student

Unoccupied cells are at least 2019, because those 2018 small numbers cannot be reused. But I am afraid of confusing “occupied by the path”: small numbers are the top and the unchosen sibling at each step, rather than all visited cells, right? In three rows, small values are 2, 3, 1, but the path is 2, 5, 6. Also, I cannot see exactly which region is “far from the path.” Could you draw a small diagram marking cells necessarily greater than 2018, then advance only one step?

### Teacher

Your distinction is precise:

- “Visited path”: \(2\to5\to6\)
- “Summed sibling cells”: \(2,3,1\)

Drawing the three-row example:

```text
          2 ← Path start and summand
        ↙   ↘
      5       3 ← Sibling cell, summand
    ↙   ↘
  6       1       4
  ↑       ↑
Path continues  Sibling cell
```

For 2018 rows, after fixing the final pair of children, the path and these sibling cells form a “strip”; complete small triangles outside it on the left or right are the “regions far from the path.”

First observe just one question: can a cell outside this strip be any number from \(1\) to \(2018\)?

## Round 5

### Student

No; the small numbers are already used in summand cells. The diagram's 4 is outside the strip, so it exceeds 3; I can see that now. But I answered that question just before and want to try moving forward: if a complete small triangle lies outside, following larger children again with every term at least 2019 might make the bottom too large? I do not know what height is guaranteed, and the path turns sideways. Could you specify its height and why we can always find it?

### Teacher

At least \(1008\) rows are guaranteed.

Suppose the path finally reaches column \(p\) of the penultimate row, so the final pair below occupies columns \(p,p+1\). The complete small triangles remaining on either side have heights:

- Left: \(p-1\) rows;
- right: \(2018-p-1=2016-p\) rows.

The path may turn, but side sizes depend only on its final pair. The larger side is at least

\[
\left\lceil\frac{(p-1)+(2016-p)}2\right\rceil
=\left\lceil\frac{2015}{2}\right\rceil
=1008.
\]

Thus a small triangle outside the strip with at least \(1008\) rows must exist. Next estimate: accumulating \(1008\) numbers along a larger-child path inside it, each at least \(2019\), how large is the endpoint at least?

## Round 6

### Student

For 1008 times 2019, I split it into 1000 times 2019 plus 8 times 2019, getting 2035152, which is 2019 below 2037171, so no contradiction yet. But these 1008 numbers cannot repeat either, so the minimum should add 2019, 2020 onward, making it much larger? Also, I did not follow why complete side triangles depend only on the final position: the path could have turned that way earlier, so how do we know no small sibling cells lie inside? Could you check that guarantee with a five-row diagram where the path turns once?

### Teacher

Yes, “no repeats” is crucial: these \(1008\) numbers must be distinct and at least \(2019\), so the minimum sum is not \(1008\times2019\), but

\[
2019+2020+\cdots+3026
=\frac{1008(2019+3026)}2
=2542680.
\]

This exceeds the overall maximum \(2037171\), a contradiction.

For turns, consider “five rows, turning right once”:

```text
          ●
        ●   ○
      ○   ●   ○
    ○   ●   ●   ○
  ○   ○   ○   ○   ○
```

Black dots mark the path or neighboring summands; white dots mark side regions. Although the path turns, all bottom positions reachable from a cell form a continuous interval. Thus the complete triangles to the left and right of the final pair are outside this interval and do not meet sibling cells.

First check this diagram: if the path ends at the middle two positions of the penultimate row, how many complete small-triangle rows are on each side?

## Round 7

### Student

I can use the addition: 2542680 exceeds the maximum, giving a contradiction if that region really exists. But I still cannot check the diagram. When going from the top to the left black dot, should the right summand not also be black? Row three also seems to have only one black dot. Does the path finally occupy row four cell 2 or cell 3? Could you list the path's cell index in each row, then list one complete small triangle's positions? I cannot say I understand the guarantee yet.

### Teacher

You are right: the previous diagram was not labeled rigorously and cannot serve for checking. Here is a clearer five-row example.

Let the “larger-child path” choose:

\[
(1,1)\to(2,1)\to(3,2)\to(4,2)\to(5,3).
\]

The cell indices in each row are:

```text
Row 1: cell 1
Row 2: cell 1
Row 3: cell 2
Row 4: cell 2
Row 5: cell 3
```

The sibling cells at each step are:

- Row 1: the path start;
- row 2 sibling: row 2 cell 2;
- row 3 sibling: row 3 cell 1;
- row 4 sibling: row 4 cell 3;
- row 5 sibling: row 5 cell 2.

Thus summand positions are:

\[
(1,1),(2,2),(3,1),(4,3),(5,2),
\]

rather than all visited cells.

The path finally passes through cell 2 of the penultimate row and lands at cell 3 of the bottom, so the final pair is penultimate-row cells 2, 3. Its complete left region is:

\[
\{(4,1)\},
\]

and complete right region:

\[
\{(4,4)\}.
\]

Neither position is in the listed summands. In larger triangles, the same “left and right of the final pair” expands into complete small triangles; earlier turns never enter these regions because the path and siblings stay in the continuous strip leading to the final pair.

## Round 8

### Student

Coordinates are clearer, and I can match the sibling cells. But the final step from (4,2) has children (5,2), (5,3); calling them penultimate-row cells 2, 3 confuses me again. Also, for five rows with p=2, the left has p-1=1 row and the right 5-p-1=2 rows, but you list only (4,4) on the right. Should (5,4), (5,5) below it count too? On the left, (4,1) has (5,2) below, which is already a sibling, so we cannot count all of them outside the strip? Could you check how many rows each side really has first, before simply saying it works for the large triangle too?

### Teacher

You are right; the previous wording confused which row contains the “final pair of children.” Clearly:

- The final pair is in the bottom row;
- in five rows, take bottom cells \(2,3\), namely \(p=2\);
- the path can be
  \[
  (1,1)\to(2,1)\to(3,2)\to(4,2)\to(5,3).
  \]

Thus the side regions are indeed:

Left: \(p-1=1\) row, containing only

\[
(5,1).
\]

Right: \(n-p-1=2\) rows, containing

\[
(4,4),\quad (5,4),(5,5).
\]

Meanwhile, \((5,2)\) is the final step's sibling, belonging to the strip and excluded from the right side triangle. Full positions are:

```text
Row 1:              (1,1)
Row 2:          (2,1)   (2,2)
Row 3:      (3,1)   (3,2)   (3,3)
Row 4:  (4,1)   (4,2)   (4,3)   (4,4)
Row 5:(5,1) (5,2) (5,3) (5,4) (5,5)
                                  ↑
                         Right side triangle
```

The side heights are therefore 1 and 2 rows, exactly matching

\[
p-1=1,\qquad n-p-1=2.
\]

Your key observation is that the strip between bottom cells \(2,3\) includes the path and sibling cells, while the right triangle begins at row \(4\), cell \(4\).

## Round 9

### Student

I can check the five-row positions now: one cell on the left, and three cells forming two rows on the right. But I want to try another path: (1,1) to (2,2) to (3,2) to (4,2) to (5,3), reaching the same bottom pair. Its first sibling is (2,1) and third sibling (4,3), both outside your listed regions. My change still works, but checking once cannot guarantee all turns. Could you explain why sibling cells are always avoided in terms of how column indices change? This is my final remaining difficulty.

### Teacher

Yes. Suppose the path's column in row \(r-1\) is \(q\), and it must ultimately reach the final pair between bottom cells \(p,p+1\).

From row \(r-1\) to the final pair, the path can move right by at most 1 column per downward row, so:

\[
q\le p\le q+(n-r).
\]

The sibling column at this step can only be \(q\) or \(q+1\). The inequality gives:

\[
p-(n-r)\le q\le p,
\]

so the sibling must lie in

\[
[p-(n-r),\;p+1]
\]

this strip of columns.

Left-side cells satisfy:

\[
j+n-r\le p-1,
\]

placing them wholly to the left of the strip. Right-side cells satisfy:

\[
j\ge p+2,
\]

wholly to its right.

Thus regardless of sideways turns, all sibling cells remain in the central strip and never enter either small side triangle. This is the column proof that “sibling cells are always avoided.”

### Student

I will stop here today. Each downward row keeps the column unchanged or increases it by 1, so positions too far from the endpoint cannot be sibling cells; this is clearer than just saying “strip.” I can check the five-row example and connect the contradiction: small numbers are all used, and distinct large numbers in another region sum beyond the maximum. I still cannot write the full column formulas from scratch, so this does not count as an independent proof. Coordinates helped; the repeated earlier changes to diagrams and row numbers were confusing. I will stop here.

### Teacher

This teaching session has been confirmed as ended.
