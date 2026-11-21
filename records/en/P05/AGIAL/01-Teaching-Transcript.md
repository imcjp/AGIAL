# P05 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | AGIAL |
| Participant ID | P05 |

## Round 1

### Student

Teacher, I want to confirm the rules first. With two rows, placing 1, 3 below gives 2 above and uses exactly 1 to 3, right? For three rows I tried 1, 6, 4 below, giving 5, 2 in the middle and 3 at the top, which also seems to use all of 1 to 6. But we cannot keep trying like that for 2018 rows, can we? I still do not know what kind of pattern to seek to judge existence. Could you guide me from these small examples?

### Teacher

Yes, both your examples follow the rules:

```text
    2              3
  1   3          5   2
               1   6   4
```

With two rows, \(|1-3|=2\), using exactly 1 to 3. With three, \(|1-6|=5\), \(|6-4|=2\), \(|5-2|=3\), also using exactly 1 to 6.

You are right that trial constructions one by one make the 2018-row case difficult to judge. Small examples help us **discover patterns**, but even many unsuccessful attempts cannot prove that every arrangement fails.

First trace a path in your three-row example: start at the top cell and always move down to **the larger** of the two adjacent child cells, obtaining

\[
3 \rightarrow 5 \rightarrow 6.
\]

At the first step, 5 differs from its neighbor 2 by 3, so \(5=3+2\). At the second, 6 differs from its neighbor 1 by 5, so \(6=5+1\). Together:

\[
6=3+2+1.
\]

Here 3 is the top cell; 2 and 1 are the sibling cells not selected at each step. The 5 is an intermediate partial sum.

Consider a triangle with \(n\) rows. If we still start at the top and always follow the larger child, can the bottom-endpoint number be written as a sum of several numbers? How many summands are there, and why are they distinct?

## Round 2

### Student

Following that idea: each row down, the larger child equals the number above plus the other child, so the bottom endpoint is the top cell plus the sibling cell left behind at each step. There are n-1 steps and the top cell, making n summands. The sibling cells belong to different rows, and the top cell has a row of its own, so these are different cells. The problem also says all numbers are distinct, so the summands are distinct. Can we say the bottom endpoint is at least 1+2+…+n? But this sum is exactly the number of cells in the whole triangle, which is also the largest allowed number. It seems we only obtain that the bottom endpoint must be the largest number, without a contradiction. Is my reasoning correct? Should we next check what equality requires?

### Teacher

Your reasoning is correct, and you have noticed the key: we have only forced the bottom endpoint to attain the maximum; **there is no contradiction yet**.

Let the number of cells, also the largest allowed number, be \(N=n(n+1)/2\). The \(n\) summands you found are distinct positive integers, so their sum is at least

\[
1+2+\cdots+n=N.
\]

This sum equals the bottom-endpoint number, which cannot exceed \(N\). Equality must therefore hold: the bottom endpoint equals \(N\).

We should indeed check equality next. Arrange these \(n\) distinct positive integers in ascending order. The first is at least 1, the second at least 2, and so on, with the \(n\)th at least \(n\). Their sum already equals the smallest possible sum, so every term must attain its corresponding minimum. That is, **the top cell and sibling cells left behind at each step contain exactly \(1,2,\ldots,n\)**, although not necessarily in ascending order.

In your three-row example, the collected numbers are precisely 3, 2, 1, and the bottom endpoint is the maximum, 6.

This gives a strong global constraint: the path collects all the small numbers. Next, is there a region of the triangle that definitely avoids these collected cells? If so, what constraint would its numbers satisfy?

## Round 3

### Student

I can follow equality: if any sorted term exceeded the corresponding number from 1 to n, the sum would exceed N. I tried drawing four rows, but the path may go left or right, and I cannot identify a region it necessarily avoids. Could we take a small triangle on one side of the path? But sibling cells left behind in each row are there too, and I worry about including small numbers again. Could you use a specific path to explain how to select the region? Please address just that step first; I want to try its numerical constraints myself afterward.

### Teacher

Your concern is correct: we cannot simply take “one side of the path,” because sibling cells may also be there. First examine a specific path, then choose regions using **the position of its final step**.

The following shows only six-row positions, without implying that numbers have been successfully filled in. `P` marks path cells, `C` marks the sibling cells left behind at each step, and `L`, `R` mark the two selected regions:

```text
              P
            C   P
          ·   P   C
        ·   C   P   ·
      L   ·   P   C   R
    L   L   C   P   R   R
```

The final step uses the pair of bottom cells 3 and 4, selecting cell 4. We **exclude both cells of this pair**, then:

- Bottom cells 1 and 2 support the complete small triangle `L` on the left;
- Bottom cells 5 and 6 support the complete small triangle `R` on the right.

You can check row by row in this diagram that the top `P` and all sibling cells `C` lie in neither `L` nor `R`. The top cell of each two-row small triangle is also connected to the two cells beneath it in the same region.

This checks only this particular path. Why such a choice works for arbitrary paths needs a separate explanation. For now, use the equality conclusion already established to consider the constraints on the numbers in these two regions.

## Round 4

### Student

This diagram shows me that we need to exclude the final pair, not just the bottom-endpoint cell. L and R contain neither the top cell nor C, so all of 1 to 6 are already used outside them, and every number inside is at least 7. If a two-row small triangle has a above and the smaller number b below, the larger is a+b, at least 14. But 14 does not exceed 21, so this estimate cannot establish impossibility for six rows. For n rows, I guess every number in the region is at least n+1. Following larger children in the region increases the value by at least n+1 per step. Could we use the region’s height? I still cannot prove that an arbitrary turning path avoids both regions. Could you explain those positions, then let me calculate the 2018-row case?

### Teacher

Your approach is correct: if we first prove that both side triangles avoid the top cell and all sibling cells, every number in them is at least \(n+1\), and we can use the height of one triangle to accumulate again.

First, one detail: the numbers in the side regions of the six-row diagram are distinct, so your \(a+b\) is actually at least \(7+8=15\). This still does not exceed 21, so this estimate alone cannot rule out six rows.

Now consider positions for an arbitrary turning path. Number each row from left to right, and suppose the final bottom pair faced by the path occupies columns \(p\), \(p+1\). The path cell in the penultimate row must then be in column \(p\). The left triangle is supported by bottom cells 1 through \(p-1\), and the right by cells \(p+2\) through the final cell.

Consider a pair in any row \(r\): the path cell and its sibling. Suppose their common parent is in column \(q\) of the preceding row. From this parent, the path needs \(n-r\) steps to reach column \(p\) of the penultimate row. Each step leaves the column index unchanged or increases it by 1. Thus, even with turns, necessarily

\[
p-(n-r)\le q\le p.
\]

The children occupy columns \(q\), \(q+1\), so both lie within the column range

\[
[p-(n-r),\,p+1]
\]

in row \(r\). The common parent constrains the positions of **both children**, including the sibling cell.

In the same row, the left triangle extends at most to column \(p-(n-r)-1\), and the right starts at column \(p+2\). They lie on opposite sides of that range, so neither path nor sibling cells enter the side regions. The top cell has bottom-row descendants covering the whole base, so it belongs to neither side region either.

Your numerical constraint therefore holds: the top cell and all sibling cells already contain all of \(1\) to \(n\), and every number in the whole triangle is distinct, so all numbers in the side triangles exceed \(n\).

Here is the 2018-row calculation for you: excluding the final pair, how many bottom cells remain on the two sides altogether? Consequently, how many rows must the larger side triangle have at least? Then follow its larger-child path and use the distinctness of the summands to see whether you can obtain a lower bound exceeding the maximum allowed in the whole triangle.

## Round 5

### Student

The side bases total 2016 cells, so the larger has at least 1008 cells, hence at least 1008 rows. Following larger children inside gives at least 1008 distinct summands, all greater than 2018, so their minimum values are 2019, 2020 through 3026. Their sum is (2019+3026)×1008÷2=2542680, exceeding 2037171, so the triangle does not exist. Initially I only calculated 1008×2019=2035152, still less than the maximum, and almost thought it was useless. Now I know we must strengthen it using distinctness. For positions, I can follow the column index staying unchanged or increasing by 1, but might get n-r wrong if I rewrite it myself. Is it enough to show that this pair’s common parent can still reach column p, thereby constraining both path and sibling cells? Also, if one side of the base is empty, can we still take the other side directly?

### Teacher

Yes, your 2018-row calculation and conclusion are correct. You also identified the key: merely using that each term is at least 2019 does not give a contradiction; distinctness of the 1008 summands raises the lower bound to \(2019+\cdots+3026=2542680\).

For the position proof, **the common parent indeed constrains both the path and sibling cells**. To obtain \(n-r\), count this way:

- The children are in row \(r\), and their common parent is in row \(r-1\).
- From row \(r-1\) to the penultimate row \(n-1\), the number of steps is \((n-1)-(r-1)=n-r\), reaching column \(p\).
- Thus the parent’s column \(q\) satisfies \(p-(n-r)\le q\le p\). The children’s columns are \(q\), \(q+1\), so both lie within \([p-(n-r),\,p+1]\).

The sibling cell need not itself be able to reach column \(p\). Sharing this constrained parent with the path cell suffices to constrain its position.

If one side of the base is empty, we can take the other side. It then has all \(n-2\) cells, supporting a complete \(n-2\)-row triangle. For 2018 rows this means 2016 rows, certainly no fewer than the required 1008.

## Round 6

### Student

Let me check against the six-row diagram: n=6, and the final pair is in columns 3 and 4. For children in row 4, the parent is in row 3, with 2 steps to row 5. Thus q is between 1 and 3, and both children are in columns 1 to 4. The side triangles have not appeared yet in that row. For row 5, is it 0 steps from the parent to row 5? I got confused again: the children are in row 5, the parent is in row 4, so it takes 1 step to row 5. Thus q is 2 to 3, and the children are in columns 2 to 4, exactly avoiding column 1 of L and column 5 of R. Subtracting row indices like this prevents mistaking a child for the parent. This specific check helps me; the general expression alone is easy to apply incorrectly. I can now explain the main nonexistence argument. One last check: this proof only works for 2018, and the six-row lower bound not exceeding 21 does not establish that six rows definitely exist, right?

### Teacher

Yes, your checks for rows 4 and 5 are both correct. Writing “the children are in row \(r\), and the parent is in row \(r-1\)” before counting the parent’s steps to row \(n-1\) does prevent confusion.

Your final judgment is also correct: **the six-row lower bound not exceeding 21 only means that this step has not produced a contradiction; it does not establish that six rows necessarily exist.** To prove existence, we need an arrangement satisfying all the rules; to prove nonexistence, we need reasoning that excludes every arrangement.

The approach is not restricted to 2018 rows: path accumulation and side-region analysis can be used for other row counts, but whether the resulting numerical bounds yield a contradiction must be checked for each count.

### Student

I will stop here today. I can connect the proof’s main argument: the first path forces the top and sibling cells to use all of 1 to 2018; excluding the final pair leaves a side region with at least 1008 rows containing only large numbers; accumulating distinct numbers there gives 2542680, exceeding the allowed maximum, so the triangle does not exist. I still need the diagram when writing the position proof, but counting the parent’s steps row by row resolved my sticking point. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
