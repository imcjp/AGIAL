# P08 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P08 |

## Round 1

### Student

I want to check the rules first: for two rows, putting 1, 3 at the bottom gives 2 at the top, using exactly 1 to 3, so this is a valid example, right? I have no conclusion yet for 2018 rows. Directly arranging the bottom row and taking differences upward seems hard to control for repeats; I want to find a quantity constraining the entire triangle myself. Could you give a small question without its answer to help me move from small examples to an existence argument?

### Teacher

Yes, it is valid: the absolute difference of bottom-row \(1,3\) is \(2\), using exactly \(1,2,3\).

A small question: in any \(n\)-row number triangle, start at the top and always move to the larger cell below. Can you express the endpoint as a sum of \(n\) numbers of what kind, and compare that sum with the total of all the numbers in the triangle?

## Round 2

### Student

Let the path values be a1 to an, and the unchosen smaller child at each step br. Then a(r+1)=ar+br, so an=a1+b1+…+b(n-1). These are n different cells from different rows, so an is at least 1+…+n=N. Since an≤N too, equality must hold. This hint was very effective, clearer than enumerating bottom rows. But I have only obtained that these n numbers are exactly 1 to n and the endpoint is N, without a direct contradiction; comparison with the total sum also seems insufficient. Should I next study overlap between adjacent paths? Please give a local direction first so I can continue deriving it.

### Teacher

Good, you have completed the “path equality” step. Next turn to spatial positions:

Suppose this path lands in one of the final pair of child cells in the penultimate row. Observe the subtriangles formed on the left and right of this pair: can you prove that none of the \(n\) small numbers \(1,\ldots,n\) obtained along the path lies inside either side triangle?

## Round 3

### Student

I am not sure about the side triangles' extent. If the penultimate-row path cell is (n−1,j), with children (n,j), (n,j+1), do you mean the two triangles formed upward from bottom intervals [1,j−1] and [j+2,n]? At present I can only prove that the larger-child values strictly increase along the path, which does not establish that all of 1 to n stay outside the side triangles; in particular, unchosen children lie on both sides of the path. Could you specify the regions using row-column coordinates and explain the key relationship needed to exclude small numbers? This spatial description jumps a little for me; please expand just this part first.

### Teacher

Yes, the side triangles are those two regions. More precisely:

- Denote cell \(j\) of row \(r\) by \((r,j)\);
- the selected penultimate-row cell occupies column \(p\), namely \((n-1,p)\);
- the left region satisfies \(j+n-r\le p-1\);
- the right region satisfies \(j\ge p+2\).

Now take a path cell in row \(r-1\), at column \(q\). To ultimately reach \((n-1,p)\), its bottom-row descendant range must cover column \(p\), so

\[
q\le p\le q+n-r.
\]

Thus the two children of the row-\(r-1\) path cell, the possible positions of the unchosen \(a_r\), can only have column indices in

\[
[p-(n-r),\,p+1].
\]

This interval is disjoint from both the left region's \(j\le p-(n-r)-1\) and the right region's \(j\ge p+2\). So every \(a_r\) avoids the side triangles; the top cell \(a_1\) is clearly outside them too.

Continue checking: how many rows must the larger of the two side triangles have at least?

## Round 4

### Student

The coordinates connected the reasoning: reachability of (n−1,p) restricts earlier path columns, placing unchosen children outside the side regions too; it is not merely increasing path values. The side triangles have p−1 and n−p−1 rows, totaling n−2. For n=2018, the larger has at least 1008 rows. All its numbers exceed 2018. Following the larger-child path inside it makes the endpoint a sum of 1008 distinct numbers (more if it is taller), at least 2019+2020+…+3026=2542680, exceeding 2037171, a contradiction. Thus the original triangle does not exist. Is my use of path summation in the subtriangle complete? Also, for general n, this estimate is only a necessary restriction, and small n giving no contradiction cannot directly be judged possible, right? Locating cells before giving numerical bounds is clear now; there is no need to enumerate the large triangle.

### Teacher

It is complete, and both judgments are correct:

- The side triangle's numbers do all exceed \(2018\), so following larger child cells again gives an endpoint at least
  \[
  2019+\cdots+3026=2542680.
  \]
- However, no cell's number exceeds \(N=2037171\), so the same endpoint is both “at least \(2542680\)” and “at most \(2037171\),” a contradiction.
- For general \(n\), this estimate is only a necessary condition; failure to obtain a contradiction never implies a construction exists.

Explain one more step: why must the side-triangle path's endpoint also not exceed the full triangle's maximum \(N\), directly conflicting with that lower bound?

### Student

Because the side triangle is part of the original triangle, its path endpoint remains an actual cell in the original. Every original cell takes a value from 1 to N, so of course it is ≤N. I am not treating the sum as an extra new cell. I already understood this bound in the previous round and do not need to check it again. What really helped was the larger-child path hint and the later coordinate ranges; afterward I could complete the side-triangle row count and summation contradiction myself. The distinction between necessary conditions and an existence construction is confirmed too. I will stop here today, thank you.

### Teacher

This teaching session has been confirmed as ended.
