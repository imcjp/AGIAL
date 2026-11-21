# P08 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P08 |

## Round 1

### Student

Let me first check the rules: for two rows, putting 1, 3 at the bottom and 2 above uses exactly 1 to 3, so this is a valid small triangle. For 2018 rows, direct construction gives too many bottom-row choices; I want to find restrictions first. The largest number must be in the bottom row, because the difference of two positive numbers is smaller than the larger number. Can this observation further restrict the positions of the next-largest numbers? Please give me a direction suitable for continuing independently, rather than the entire proof.

### Teacher

Your two-row example is valid; the largest number can indeed only be in the bottom row.

Following your observation, ask: **If a number is not in the bottom row, at least one number below it is larger.** Starting at that cell, always move to the larger child cell until reaching the bottom row.

Try counting: if this cell is \(k\) rows above the bottom, how many numbers larger than it are needed along this path at least? Then use that condition to see which rows can contain the second-largest and third-largest numbers.

## Round 2

### Student

Being k rows above the bottom gives k strictly larger numbers, since the path increases at each step and passes through different cells. So the j-th largest number can only be in the bottom j rows; the second-largest in the bottom or penultimate row, and the third-largest in the bottom three. This hint helped me generalize a single-point observation into a row restriction. But it seems insufficient: concentrating large numbers near the bottom does not directly exceed capacity there, and paths from different starting points can merge, so their counts cannot simply be added. Could the size of the difference connect a “very large” number with the “small number” beside it? I want to know which counting relationship to test next.

### Teacher

Your generalization is correct, and the warning about paths merging is crucial: we cannot simply add path counts from different starting points.

First consider just **one** path from the top to the bottom, choosing the larger child cell at each step. For an upper cell on the path and its two children, call the larger child \(B\) and the smaller \(a\). Think about expressing \(B\) as the upper cell plus \(a\).

Then test two counting relationships:

1. After connecting these equations along the whole path, which cells' values sum to the bottom endpoint? How many terms are there?
2. Are these terms distinct? If so, what is their minimum sum, and what is the maximum bottom endpoint?

You need not consider multiple paths merging yet; see what restriction this one path alone provides.

## Round 3

### Student

Let the path values be x1,…,xn, and the other, smaller child at each step be a2,…,an. Then x(r+1)=xr+a(r+1), so xn=x1+a2+…+an. There are n terms, in different rows, so their cells and values must differ. Thus xn≥n(n+1)/2. But the maximum number in the problem is also n(n+1)/2, so this inequality alone gives no contradiction. Equality forces xn to be the maximum, and the summands to be exactly 1 to n. For n=2018, the top number and 2017 sibling values must be exactly 1 to 2018. I want to pursue equality: intermediate path values other than the top cannot use 1 to 2018, so the second-row path value x2 is at least 2019; but x2=x1+a2, with both terms ≤2018, is still possible. Should I compare the last two steps near the bottom, or choose another path to break this equality condition? The summation hint was very effective, but I need a local hint for handling equality. Please do not give the whole remaining proof yet.

### Teacher

Your equality analysis is correct, and the second-row observation is justified: \(x_2\) is not in a cell occupied by those \(n\) summands, so it cannot reuse \(1\) to \(n\).

Rather than changing paths or immediately comparing the final two steps numerically, look at **the bottom-row positions of the final pair of child cells**. Suppose they occupy columns \(p\), \(p+1\):

- How many bottom-row cells remain to their left and right, respectively? How many altogether?
- Each side's bottom-row cells support a complete small triangle. How many rows must the larger side have at least?

Then test a key positional relationship: could the top cell and the sibling cell collected at each step fall inside either small side triangle? You can first explore this with a small-row lattice diagram, but remember that a small diagram only helps discover a pattern.

## Round 4

### Student

The left and right sides leave p−1 and n−p−1 cells, totaling n−2=2016, so the larger side has at least 1008 rows. I checked positions with bottom-row descendant intervals: cell c of row r has descendant interval [c,c+n−r]. The penultimate path cell has interval [p,p+1], and each ancestor contains this interval. The intervals of an ancestor's two children remove only one left or right endpoint from its interval, so a sibling interval meets at least p or p+1 and cannot lie wholly in the left region [1,p−1] or right region [p+2,n]. Thus the side triangles contain none of those 2018 summands, and every number in them is at least 2019. Taking an increasing path in a 1008-row side triangle again makes its endpoint the sum of 1008 distinct numbers ≥2019, at least 2019+2020+…+3026=2542680, exceeding the overall maximum 2037171, a contradiction. This proves nonexistence. Please check my interval argument and numerical sum for gaps. If they are correct, I would like to test smaller n to find the limits of this argument and ensure it does not incorrectly exclude the two-row example.

### Teacher

Your proof is correct; neither the interval argument nor the sum has a gap.

The key interval point is this: the penultimate path cell's bottom-row descendants are \([p,p+1]\), and every path ancestor's descendant interval contains both positions. Moving from a cell to either child removes only the leftmost or rightmost position, so each child's interval meets at least \(p\) or \(p+1\). This holds for the sibling cell at every step. The top cell's descendants cover the entire bottom row, so it is outside the side triangles too.

Thus the side triangles avoid the cells already occupying \(1\) to \(2018\). Reusing path summation in a side triangle with at least \(1008\) rows gives

\[
2019+\cdots+3026
=\frac{1008(2019+3026)}2
=2\,542\,680>2\,037\,171,
\]

which does produce a contradiction.

For smaller row counts, let the larger side triangle have at least \(L=\lceil(n-2)/2\rceil\) rows. Your method gives the lower bound

\[
(n+1)+\cdots+(n+L)=\frac{L(2n+L+1)}2.
\]

When \(n=2\), \(L=0\), so no side triangle is available; this argument therefore **does not exclude** your two-row example. Consider a few more boundaries:

| Rows \(n\) | Maximum allowed value | Side-triangle lower bound | Result of direct comparison |
|---|---:|---:|---|
| 4 | 10 | 5 | Not excluded |
| 9 | 45 | 46 | Excluded |
| 10 | 55 | 50 | Not excluded |
| 14 | 105 | 105 | Not yet excluded using only “lower bound exceeds maximum” |
| 20 | 210 | 225 | Excluded |

“Not excluded” means only that this comparison has not produced a contradiction; it does not prove existence. For \(14\) rows, another detail is worth checking yourself: the first path's endpoint already occupies the unique maximum, while the side triangle's endpoint is a different cell. Could this strengthen its upper bound from “at most \(105\)”?

### Student

Yes, the side triangle's endpoint and the first path's endpoint occupy different cells, so it is at most N−1. For n=14, the lower bound is 105 and the upper bound 104, so it is impossible too. Generally, L(2n+L+1)/2≥n(n+1)/2 suffices to exclude it; failure to reach this still does not establish existence. The parity effect excluding n=9 but not yet n=10 reflects changes in the strength of this particular lower bound, not a conclusion that actual existence varies monotonically with row count. I can now connect the proof: summing a full-triangle path forces equality and occupation of 1 to n, descendant intervals isolate a side triangle, and repeating path summation yields a contradiction. Your two hints about a single path and side-triangle positions resolved my specific difficulties, and retaining local hints let me supply the proof myself. My goal is complete; I will stop here today.

### Teacher

This teaching session has been confirmed as ended.
