# P08 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P08 |

## Round 1

### Student

I want to check the rules first: for two rows, 1, 3 at the bottom and 2 above use 1 to 3 exactly once. For three rows, I tried bottom 1, 6, 4, middle 5, 2, and top 3; that seems valid too. But small examples existing does not establish existence for 2018 rows. I want to find restrictions myself first; the maximum must be in the bottom row because the difference of two positive integers is smaller than the larger. How can this observation advance the argument? Please give one local hint first for me to try.

### Teacher

Your observation is crucial: the maximum can only be in the bottom row, because an upper cell is the difference of two positive integers.

A local hint: start at the top, moving down each row through “the larger lower cell.” Let the other cell be \(a_r\), and use

\[
\text{upper cell}=\left|\text{difference of the two lower cells}\right|
\]

to express the larger lower cell as “upper cell \(+\ a_r\).” After reaching the bottom, which numbers sum to its value?

First consider two points:

1. What common properties do the \(a_r\) selected each row have?
2. Comparing this sum with the maximum \(N=\frac{n(n+1)}2\), what equality conditions are forced?

## Round 2

### Student

Following larger lower cells from top value t yields b=t+a₂+…+aₙ at the bottom. Here t and each a come from different rows, so they are n distinct positive integers, with sum at least 1+…+n=N. On the other hand, b≤N, so b=N and the summands are exactly 1 to n. I can connect this step, and it shows any such path must leave these small numbers beside it. But I still cannot see how equality excludes 2018 rows: the path can turn, and the small numbers beside it need not be ordered. Which adjacent cells' constraints should I check next? Please continue with only local clues.

### Teacher

Next, instead of tracking whether the path “always goes left or right,” consider the range of columns it can cover in each row.

Suppose the path finally reaches a pair of bottom-row cells in columns \(p,p+1\). Consider the complete subtriangles to the left and right of this pair, taking the larger by row count.

The local clue: if the path occupies column \(q\) in row \(r-1\), its eventual arrival at bottom-row columns \(p,p+1\) requires

\[
q\le p\le q+n-r.
\]

The other cell beside the path can only occupy column \(q\) or \(q+1\). Use this to prove that all \(a_r\) fall in a central “strip,” so the larger left or right subtriangle uses none of \(1,\ldots,n\).

Then repeat the accumulation observation of “following larger lower cells” inside that side triangle.

## Round 3

### Student

The column-range hint lets me avoid the issue of path turns. From p−(n−r)≤q≤p, a_r lies in columns [p−n+r,p+1]. Thus the left triangle supported by bottom-row 1 to p−1 has rightmost column p−n+r−1 in row r, while the right triangle starts at p+2; both avoid a_r, and the top cell is outside both too. Thus all values on both sides exceed n. Their row counts are p−1 and n−p−1, totaling n−2, so for n=2018 one side has m≥1008 rows. Following larger lower cells there gives an endpoint summing m distinct numbers greater than 2018, at least 2019+…+(2018+m). Taking m=1008 gives 2,542,680, exceeding the overall maximum 2,037,171. Thus it does not exist. Please check whether I missed conditions in the subtriangle boundaries or lower bound; if valid, I want to use small row counts to check why this does not incorrectly exclude the earlier three-row example.

### Teacher

Your treatment is valid and covers all key conditions:

- Path and sibling cells lie in the central strip;
- left and right subtriangles are completely disjoint from \(1,\ldots,n\);
- thus all numbers in a side triangle exceed \(n\);
- following larger lower cells inside it again gives an endpoint summing \(m\) distinct numbers greater than \(n\).

Thus for \(m\ge1008\), the lower bound is indeed

\[
2019+\cdots+3026
=\frac{1008(2019+3026)}2
=2,542,680>N=2,037,171,
\]

a contradiction.

Small row counts are not incorrectly excluded because the side triangles are not tall enough. For example:

- \(n=3\): both side heights are \(0\), so no side triangle is available;
- \(n=4\): the larger side triangle has height only \(1\), with lower bound \(5\), while the maximum is \(N=10\), giving no contradiction.

Thus this contradiction excludes only sufficiently large row counts; a four-row example is fully compatible too.

## Round 4

### Student

I can now independently connect the main proof, but the small-row explanation has a counting problem: the side heights sum to n−2, so for n=3 they cannot both be 0. My example is bottom 1, 6, 4, middle 5, 2, top 3, with larger-child path 3→5→6 and final pair 1, 6, so p=1. The right side leaves a height-1 triangle with value 4. Its lower bound is 4≤N=6, still no contradiction. For n=4, the larger side height can also be 2, giving 5+6=11>10, so that endpoint position cannot occur; only p=2 gives both heights 1 without contradiction. Distinguishing “all positions yield contradictions” from “some positions are excluded” is the difference between the 2018-row proof and small row counts, right? The small hints suit me well: the column range supplied the spatial constraint I lacked and left me room to derive the lower bound. The final small-example check still needs correction.

### Teacher

Yes, your correction is right; my earlier small-row explanation was not rigorous.

The two side heights are

\[
p-1,\qquad n-p-1,
\]

totaling \(n-2\), but varying with endpoint position \(p\).

- \(n=3,\ p=1\): heights \(0,1\), right-side lower bound \(4\le N=6\), no contradiction.
- \(n=4,\ p=1\): heights \(0,2\), lower bound \(5+6=11>N=10\), excluding that endpoint position.
- \(n=4,\ p=2\): heights \(1,1\), lower bound only \(5\), no contradiction; a four-row construction may still exist.

Your distinction is very precise: the proof only needs to show that every possible endpoint for 2018 rows leaves at least one side of height \(\ge1008\), so all positions yield contradictions. Small row counts may exclude only some positions, insufficient to conclude overall nonexistence.

### Student

I can now connect the contradiction: the first larger-child path forces all of 1 to n into sibling cells and the top; column ranges give a side triangle avoiding these small numbers; wherever the endpoint lies for 2018 rows, one side has height at least 1008, and its path-accumulation lower bound exceeds the maximum, so it does not exist. Small row counts only exclude some endpoints, so the overall conclusion cannot simply be transferred. Stepwise hints helped me complete the key connections, and checking corrected the final example's counting error. I will stop here for this session.

### Teacher

This teaching session has been confirmed as ended.
