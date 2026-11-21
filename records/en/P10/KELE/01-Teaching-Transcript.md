# P10 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the integers from 1 to 2037171 each be used once to form an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P10 |

## Round 1

### Student

I want to check the rules first. With two rows, putting 1, 3 at the bottom gives 2 at the top, using exactly 1 to 3. But with three rows, putting 1, 6, 4 at the bottom gives 5, 2 above and 3 at the top, apparently also using exactly 1 to 6. Is this understanding correct? Successful small examples do not imply success for 2018 rows. I do not currently know whether to look for a construction or a restriction establishing impossibility. Could you first give me a starting point I can check myself, without giving the complete proof directly yet?

### Teacher

Yes, both your examples are correct:

- Two rows: \([2]/[1,3]\), with top cell \(|1-3|=2\).
- Three rows: \([3]/[5,2]/[1,6,4]\), because \(|1-6|=5,\ |6-4|=2,\ |5-2|=3\).

Your judgment is also crucial: small-scale feasibility does not imply feasibility for 2018 rows. First consider a starting subproblem:

Start at the top cell and move down through the “larger child cell” in every row. Can you observe and write a relation between the bottom number reached and the numbers not selected in each row along the path?

## Round 2

### Student

In the three-row example the path is 3→5→6, and the unselected numbers are 2 and 1, so 6=3+2+1. Since the parent equals the larger child minus the smaller child, at each downward step the larger child equals the parent plus the unselected smaller child. Substituting repeatedly, the bottom number should equal the top cell plus the unselected numbers in each row. This hint helped me write a concrete relation. But “unselected numbers” should refer only to the child cell beside the path, rather than all the other cells in the row, right? If this gives 2018 distinct positive integers for 2018 rows, their sum is at least 1+…+2018=2037171, while the bottom number cannot exceed 2037171, so apparently equality must hold. I do not yet know whether this equality condition suffices to rule out existence. Where could I check next?

### Teacher

Correct: “unselected numbers” refers only to the child cell beside the path at each step, rather than every cell in the row.

You have obtained two inequalities:

\[
\text{bottom number}\ge 1+2+\cdots+2018,\qquad \text{bottom number}\le 2037171.
\]

Now check what equality means: if the two sides are indeed equal, exactly which set of numbers must these 2018 cells beside the path contain? Also, which number in the whole triangle must the bottom cell of the path contain?

## Round 3

### Student

For equality, the top cell and the 2017 child cells beside the path together must be exactly 1 to 2018; the bottom number must be 2037171. I want to correct the wording: not all 2018 are beside the path; the top cell counts as one, or we would overcount by one. The reason is that, putting these 2018 distinct positive integers in increasing order, the kth is at least k; if any exceeds k, the total exceeds the minimum. But the three-row example also has 1, 2, 3 as the top and sibling cells, with 6 at the bottom, without a contradiction. Thus I currently have only a necessary condition and cannot conclude impossibility. Do we also need to use that the intermediate path numbers cannot repeat 1 to 2018? I cannot yet connect this part; please give one hint focused on this gap.

### Teacher

Correct: your present conclusion is still only a necessary condition, as the three-row example illustrates.

Next, check “spatial positions”:

Suppose the last pair of bottom-row cells occupies columns \(p,p+1\), and the path occupies column \(q\) in row \(r-1\), eventually reaching column \(p\). Since the column number changes by at most 1 with each downward row, can you specify the range of \(q\), and then determine which columns the sibling cell beside this path might occupy in row \(r\)?

## Round 4

### Student

I will assume the bottom endpoint really is in column p. From row r−1 to row 2018 there are 2019−r steps, each leaving the column unchanged or increasing it by 1, so p−(2019−r)≤q≤p, also combined with 1≤q≤r−1. The sibling cell in row r is in column q or q+1, giving a coarse range from max(1,p−2019+r) to min(r,p+1). But two points are unclear: when the last pair occupies columns p, p+1, the larger child could also be in p+1, so do we need cases? Also, I do not see how this positional range helps rule out the placement of 1 to 2018. Introducing r, p, q all at once is a little hard to follow. Could you first use four rows and a specified endpoint to draw or list one particular sibling cell's position, then let me generalize?

### Teacher

Yes, let us replace the abstract symbols with a four-row example:

\[
\begin{array}{c}
4\\
2\quad 6\\
5\quad 7\quad 1\\
8\quad 3\quad 10\quad 9
\end{array}
\]

Take the “larger-child” path:

\[
4\to6\to7\to10.
\]

The sibling cells are \(2,1,3\), respectively, so

\[
10=4+2+1+3.
\]

If the last pair of cells occupies columns \(3,4\), the path ends at \(10\) in column \(3\), while sibling cell \(3\) occupies column \(2\). The remaining left subtriangle then consists only of the column \(1\) region.

First indicate on this four-row diagram: could cells in the left subtriangle be any of the path cells \(4,6,7,10\) or sibling cells \(2,1,3\)?

## Round 5

### Student

I checked the diagram term by term, and it works; 4→6→7→10 and sibling cells 2, 1, 3 are also correct. But the children of 7 are 3 in column 2 and 10 in column 3, so the last pair should be columns 2, 3, rather than 3, 4. If the remaining left cells you mean are 5 in row 3 and 8 in row 4, they are indeed outside this path and its sibling cells. But if the “column 1 region” includes the top 4 and the 2 in row 2, that does not hold. I can identify the uncovered cells as 5, 8, 9 in this diagram, but the exact boundary of the “left subtriangle” is unclear. A concrete diagram helps, but the changing positional definition makes subsequent reasoning harder to assess. Please first specify which cells we are taking and how they yield a restriction usable for 2018 rows.

### Teacher

You are right: I gave the column numbers incorrectly. The final relevant pair of bottom-row cells should be \(3,10\) in columns \(2,3\), rather than columns \(3,4\).

In this four-row example, we cannot loosely interpret the “left region” as the entire strip of column 1. We take only a complete subtriangle lying entirely outside the path strip. In this small example, we can first take the single bottom cell \(8\) or \(9\) as a one-row subtriangle; neither belongs to the set of sibling cells beside the path \(\{4,2,1,3\}\).

For 2018 rows, the same idea produces larger side triangles: they entirely avoid the path and sibling cells, so their numbers cannot be \(1,\ldots,2018\). Next consider: in a subtriangle with \(\ell\) rows whose cells all exceed 2018, what is the minimum bottom number reached by the larger-child path?

## Round 6

### Student

I can reuse the earlier addition relation: for ℓ rows, the top cell plus ℓ−1 sibling cells gives ℓ distinct integers, all greater than 2018. Thus the bottom number is at least 2019+2020+…+(2018+ℓ)=2018ℓ+ℓ(ℓ+1)/2. Even the coarser 2019ℓ already exceeds 2037171 when ℓ=1010. But I cannot treat this as a proof yet: you said 2018 rows produce larger side triangles, but how many rows are guaranteed at minimum? “Larger” may not reach the size needed for a contradiction. Could you give explicit coordinate ranges for the side triangles and explain why at least this size must remain however the path moves left and right? This positional guarantee is my main gap now; I can calculate the numerical lower bound myself.

### Teacher

This gap can be filled explicitly.

Suppose the last pair of bottom-row cells occupies columns \(p,p+1\). There are \(p-1\) bottom cells to their left and \(2018-p-1\) to their right, forming side triangles with heights

\[
p-1,\qquad 2017-p,
\]

respectively. The larger has at least

\[
\left\lceil\frac{2018-2}{2}\right\rceil=1008
\]

rows.

The key positional fact is that the path and its sibling cells always lie within the “strip” leading to columns \(p,p+1\). The left side triangle lies entirely to the strip's left, and the right side triangle entirely to its right, so they contain none of the numbers \(1,\ldots,2018\) on the path.

Thus at least one side triangle has \(1008\) rows and all its cells exceed \(2018\). Following its larger-child path gives a bottom number at least

\[
2019+2020+\cdots+3026
=2542680,
\]

but no cell in the whole triangle exceeds

\[
2037171.
\]

This produces a contradiction. Your numerical lower-bound approach was correct; the precise missing pieces were the two positional facts that “the side triangle has at least \(1008\) rows” and “it avoids \(1,\ldots,2018\).”

## Round 7

### Student

The row count and numerical values finally connect this time. I will add specific coordinates to check the “avoidance”: the parent in the last step is in row 2017, column p. The sibling cell in row r comes from a parent in row r−1, which still needs 2018−r steps to reach row 2017. Its column therefore ranges from at least p−2018+r to at most p, so the sibling cell's column lies between p−2018+r and p+1. On the left we can take row-r cells in columns 1 to p−2019+r; on the right, columns p+2 to r, omitting empty ranges. The base lengths of these regions are p−1 and 2017−p, and their child cells stay in the same region, so they really are complete subtriangles and avoid every sibling cell and the top cell. If this coordinate check is correct, I can explain: equality forces 1 to 2018 into the top and sibling cells; side-triangle numbers all exceed 2018; at least one has 1008 rows; hence its bottom number is ≥2542680>2037171, proving nonexistence. In the four-row example p=2, these two regions are exactly 8 and 9, matching the earlier diagram. There is no need to calculate larger examples now; please check whether my positional explanation misses any boundary.

### Teacher

Your coordinate check is correct, and the boundaries are handled properly:

- Left region: in row \(r\), the column satisfies
  \[
  1\le j\le p-2019+r.
  \]
- Right region:
  \[
  p+2\le j\le r.
  \]

Empty ranges are naturally ignored. The two regions form complete subtriangles of heights \(p-1\) and \(2017-p\), respectively, with the larger having at least \(1008\) rows.

The column of a sibling cell beside the path lies within

\[
p-2018+r\le j\le p+1,
\]

which intersects neither \(j\le p-2019+r\) on the left nor \(j\ge p+2\) on the right. The top cell also lies outside both side regions.

Thus your complete reasoning holds: equality forces the top and sibling cells to contain exactly \(1,\ldots,2018\); all numbers inside the side triangles exceed \(2018\); the larger side has at least \(1008\) rows, giving a bottom number at least \(2542680>2037171\), a contradiction. Therefore the 2018-row number triangle does not exist.

### Student

I will stop here today. I can now connect the reasons for nonexistence: first obtain the minimum-sum equality condition from the larger-child path, then find a complete subtriangle with at least 1008 rows in the unused region beside the path, and use a second path sum to exceed the maximum. The initial path hint and the final explicit row-count relation were most useful. The intervening column error and vague regions did cause an extra detour; I understood the reason for “avoidance” only after supplying coordinates myself. I can now explain this argument, but have not independently tested its general range of applicability at another scale, so I do not count that as mastered. I will end this learning session and answer any subsequent post-session evaluation questions as asked.

### Teacher

This teaching session has been confirmed as ended.
