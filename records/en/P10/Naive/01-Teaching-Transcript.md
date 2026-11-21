# P10 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the integers from 1 to 2037171 each be used once to form an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P10 |

## Round 1

### Student

I want to check the rules with small examples first. With two rows, a bottom row of 1, 3 gives 2 at the top, using 1 to 3 exactly once, so two rows are possible. For three rows I tried 1, 5, 6 at the bottom, giving 4, 1 above, which already repeats 1. I know one failed attempt cannot prove nonexistence, but 2018 rows clearly cannot be tackled by trying arrangements one by one. Could you confirm this understanding, then suggest a necessary condition I can check myself? Please do not give the complete proof directly yet.

### Teacher

Your understanding is correct:

- With two rows and \(1,3\) at the bottom, the top is \(|3-1|=2\), using exactly \(1,2,3\), so this is possible.
- With three rows, the bottom row \(1,5,6\) produces \(4,1\) above it, which does repeat a number. But this shows only that this arrangement fails, not that three rows have no solution.
- We cannot tackle 2018 rows by trying arrangements one by one; we need a necessary condition that holds for every arrangement.

Here is a direction to check:

Start at the top and move down to the “larger child cell” at each row. Along this path, the bottom number can be written as a sum of distinct positive integers on the path.

Consider: with \(n\) rows in total, what is the minimum possible sum? What is the maximum number permitted anywhere in the triangle? When these two bounds are exactly equal, which numbers does that force the path to use?

## Round 2

### Student

I tried writing one step: if the parent is a and the children are b<c, then a=c-b, so the increase when we move to c is b, not a. Continuing, the bottom number should equal the top cell plus the smaller child cell not visited at each step. These n cells are distinct, so the sum is at least 1+…+n=n(n+1)/2, which is also exactly the permitted maximum. Thus these summands can only be 1 to n, and the bottom cell must be the maximum. Is that right? Your direction got me started, but “numbers on the path” initially made me think we were directly adding the cells visited. Now I am stuck after equality: the small summands are scattered across different rows, so how does this rule out 2018 rows? Could you give me a small hint for the next step so I can keep trying?

### Teacher

Yes, your understanding is now accurate, and you have resolved the ambiguity about “directly summing along the path”:

- The cells visited form a larger-child path.
- The increase at each step is the smaller child cell not visited.
- Thus the bottom number is the sum of “the top cell + the unselected child cell at each step,” giving \(n\) distinct positive integers.
- Their sum is at least \(1+\cdots+n=N\), and cannot exceed the whole triangle's maximum \(N\), so equality must hold. Thus the summands are exactly \(1,\ldots,n\), and the bottom number is \(N\).

A hint for the next step:

Focus on the “last pair of bottom-row child cells” reached by this path. There is a side triangle to its left and another to its right. Try to prove:

1. At least one side triangle has approximately \((n-2)/2\) rows.
2. None of the small numbers \(1,\ldots,n\) from earlier lies in this side triangle.
3. Thus every number in the side triangle exceeds \(n\).

Then repeat the same “summing through larger child cells” idea within this side triangle. For \(n=2018\), see whether the resulting lower bound can still be at most \(N=2037171\).

## Round 3

### Student

There are two points in this hint I cannot yet connect. If the bottom pair occupies positions j and j+1, the remaining bottom cells on the two sides number j-1 and n-j-1, totaling n-2. Thus the larger side has at least 1008 rows; I can calculate that. But why are all the earlier unselected child cells outside this side triangle? The path can turn left and right, and I cannot guarantee it just from visual intuition. Also, even accepting that every number exceeds 2018, summing over 1008 rows gives at least 2019+…+3026, which I calculate as 2542680, greater than 2037171: indeed a contradiction. The numerical part is clear; the key gap is the spatial argument in step 2. Could you use a five- or six-row example with rows and columns labeled to specify the side-triangle cells and explain why the small summands beside the path cannot enter? Please expand this part a little; there is no need to repeat the other sums.

### Teacher

The key is to locate cells using their bottom-row descendant intervals, rather than relying on “how the path appears to turn.”

Suppose there are \(n\) rows and the path reaches column \(p\) in the penultimate row. Consider the path cell in row \(r\), whose column we denote by \(q\).

The bottom-row descendant range of the cell in row \(r\), column \(q\), is:

\[
[q,\ q+n-r].
\]

Since it can eventually reach column \(p\) in the penultimate row, we must have:

\[
q\le p\le q+n-r.
\]

Thus:

\[
p-(n-r)\le q\le p.
\]

The smaller child cell not selected at this step can only occupy column \(q\) or \(q+1\), so it must lie within the horizontal range:

\[
[p-(n-r),\ p+1].
\]

Meanwhile, cells in row \(r\) of the left side triangle must have bottom-row descendants entirely to the left of column \(p\), so they satisfy:

\[
j+n-r\le p-1,
\]

that is:

\[
j\le p-(n-r)-1.
\]

This is one cell further left than the leftmost possible position of a small path summand. The right side triangle begins at column \(p+2\), also separate from \([p-(n-r),p+1]\). Therefore, small summands cannot enter either side triangle.

Take a simplified six-row example. If the selected penultimate-row cell is in column \(p=3\):

- In row \(r=2\), the small summand may occupy columns \(1\) to \(4\).
- In row \(r=3\), it may occupy columns \(2\) to \(4\).
- In row \(r=4\), it may occupy columns \(3\) to \(4\).
- The closer to the bottom, the narrower the range.

The left side triangle always lies strictly to the left of these ranges, and the right side triangle strictly to their right. The path can turn left or right, but its “bottom-row descendant interval” constrains the small summand's position at each step, so spatial separation still holds.

## Round 4

### Student

The bottom-row descendant interval helps, but your six-row example seems inconsistent with the formula: when n=6, p=3, r=4, p-(n-r)=1, not 3. Row 2 also has only two cells, so it cannot actually extend to column 4. Also, you first define r as the row of the path parent, so the small child cell is actually in row r+1, but later compare it with the side triangle in row r. I am concerned about an off-by-one row error. Could we consistently use s for the actual row of the small summand, then rewrite its column lower bound? My attempt is: the preceding-row path cell in column q must reach row n-1, column p, in the remaining n-s steps, so q≥p-(n-s), and the small summand's column is at least q. In row s, the left side triangle has j≤p-(n-s)-1, so they just avoid each other. The small summand's column is at most p+1 on the right, and the side triangle's column is at least p+2. Does this fix the row-index issue? If so, I think I can organize the proof myself.

### Teacher

Yes, you have made the row indices consistent. My earlier six-row example did contain a row-and-column calculation error. Thank you for pointing it out.

Use the following consistent notation:

- The small summand is actually in row \(s\).
- Its parent is in row \(s-1\), column \(q\).
- The path requires another \(n-s\) downward steps to reach column \(p\) in the penultimate row.

Therefore:

\[
q\le p\le q+(n-s),
\]

so:

\[
q\ge p-(n-s).
\]

The small summand occupies column \(q\) or \(q+1\), so its column is at least

\[
p-(n-s).
\]

The rightmost column of the left side triangle in row \(s\) is strictly less than this position, namely:

\[
j\le p-(n-s)-1.
\]

The small summand's column on the right is at most \(p+1\), while the right side triangle starts at column \(p+2\). Thus both sides avoid the small-summand region.

Your row-index correction and spatial-separation reasoning are therefore correct, and you can now use them to organize a formal proof.

### Student

I will stop here today. I can now explain the basis for nonexistence: the larger-child path makes the bottom number a sum of n distinct positive integers, and the bounds force the top cell and the small summands to use exactly 1 to n. The two side triangles outside the last pair of child cells have bottom widths totaling n-2, so at least one has 1008 rows. The column ranges with consistent row indices show that it avoids every small summand, and the top cell is also outside, so all its numbers exceed 2018. Repeating the summation inside gives a bottom number at least 2019+…+3026=2542680, exceeding the whole triangle's maximum 2037171, a contradiction. I can follow these relations to finish this problem, but would not yet claim I could discover such a proof independently. The stepwise hints and the decision to expand only the positional argument helped me. The earlier example's errors required extra checking; after correction, the key gap was bridged. I will end learning here and answer any subsequent experience questions for this session.

### Teacher

This teaching session has been confirmed as ended.
