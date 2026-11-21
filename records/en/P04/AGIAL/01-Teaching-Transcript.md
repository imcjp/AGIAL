# P04 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | AGIAL |
| Participant ID | P04 |

## Round 1

### Student

Teacher, I want to confirm the rules first. With two rows, if I put 1 and 3 below, I get 2 above, using 1, 2, and 3 exactly once. Does that count? For three rows I tried 1, 6, 4 below, getting 5, 2 in the middle and 3 above. That also seems to use 1 to 6 exactly once. But I do not know how to judge the 2018-row case. I cannot just keep trying. Could you check these two examples first, then give me a direction I can try myself?

### Teacher

Both your examples follow the rules:

- **Two rows**: the bottom row is 1, 3, with \(|1-3|=2\) above, using 1, 2, 3 exactly once each.
- **Three rows**: the bottom row is 1, 6, 4, the middle row is \(|1-6|=5\), \(|6-4|=2\), and the top row is \(|5-2|=3\), using 1 to 6 exactly once each.

These examples show that two and three rows are possible, but do not directly settle 2018 rows. Here is a direction that does not require placing the numbers one by one:

Start at the top cell, and at each step move down to **the larger** of the two adjacent cells. Think about the difference rule: can that larger number be written as “the number above + the other, smaller number”?

First follow this path in your own three-row example and connect the equations at each step. See which numbers along the way sum to the number reached in the bottom row. Then consider what conditions these summands share if the triangle has 2018 rows.

## Round 2

### Student

I go from 3 to 5, then to 6. Since 5=3+2 and 6=5+1, we get 6=3+2+1. This lets me focus on the path without worrying about the whole arrangement. I can follow that. For 2018 rows, is it the top number plus the smaller number beside each step, giving 2018 summands in total? They are all in different cells, so they cannot repeat, and the minimum is the sum from 1 to 2018. But I am still unsure: when the path turns left and right, could a small number beside it be counted again later? Could we clarify that first?

### Teacher

Yes, your count is correct: the top cell is one summand, and the 2017 downward steps each collect one number beside the path, making **2018 summands** in total. They are distinct positive integers, so their sum is at least \(1+2+\cdots+2018\).

Turning does not cause a number beside the path to be counted again. The key is the **row**: each downward step reaches a new row and collects one sibling cell in that row. Whether the next step goes left or right, it reaches the next row down and cannot return to a previously collected cell.

In your three-row example, the first step collects 2 in the second row, and the second step collects 1 in the third row. Even if the path turns, they belong to different rows and different cells. Together with the top cell, 3, the three summands come from three different rows.

We should distinguish two things: **the numbers visited on the path are successively accumulated partial sums; the collected summands are the top cell and the sibling cell at each step.** For example, 5 is the result of \(3+2\), and is not counted again as a new summand.

## Round 3

### Student

It is clear when I look by row: collect only one summand from each row, and 5 is just an intermediate sum, so it cannot be added again. Pairing the numbers from 1 to 2018 gives 2018×2019÷2=2037171, exactly the largest allowed number. Then the bottom number reached must be 2037171, and the collected summands must be exactly 1 to 2018, right? I originally thought a lower bound would establish impossibility, but it does not exceed the largest number; we are stuck at equality. Do we also need to use the fact that the intermediate sums on the path cannot repeat? Could you give me a small hint so I can try finding where equality causes a problem?

### Teacher

Yes, your equality conclusion holds: the bottom number reached must be 2037171, and the 2018 collected summands are exactly 1 to 2018. You also correctly noticed that **we have only established equality, not yet a contradiction.**

Here is a small hint: do not rush to check whether the intermediate sums repeat. Look at the final two adjacent cells when the path reaches the bottom row, then see how many cells remain to their left and right.

What shapes can the cells above those remaining cells form? If one such region avoids all the small numbers collected along the path, what common magnitude condition would its numbers satisfy?

## Round 4

### Student

I cannot quite make the connection from this hint. I can imagine that the consecutive bottom cells remaining to the left and right of the final pair can form small triangles above them. If a region really contains none of the collected small numbers, all its numbers should exceed 2018, because all of 1 to 2018 have already been collected. But I cannot confirm why this triangle must avoid the small numbers beside the path. Can the path not turn left and right? Could you draw four or five rows showing the final two cells and that region? Please explain only how to find the region first, and let me try the magnitude relationships afterward.

### Teacher

Certainly. First use a **five-row position diagram**, without filling the cells with numbers. Suppose the path ends at bottom cell 3, and the final adjacent pair is bottom cells 3 and 4:

```text
Row 1          ·
Row 2        ·   ·
Row 3      L   ·   ·
Row 4    L   L   ·   ·
Row 5  L   L   P   C   R
       1   2   3   4   5
```

The bottom **P and C** mark the final pair: P is the larger cell chosen by the path, and C is the cell beside it. Cells 1 and 2 remain on the left, and cell 5 remains on the right.

The two bottom cells on the left, together with the cell immediately above them, form the two-row small triangle marked **L**. On the right, just one bottom cell remains, forming a one-row **R**. For every non-bottom cell in a small triangle, both adjacent cells immediately below it also belong to that triangle.

As for turns in the path, merely drawing L and R does not yet justify saying that they avoid all sibling cells. First notice a positional relationship: to reach the common parent of the final pair, namely cell 3 in row 4, earlier positions of the path must remain within the range from which it can be reached downward. Each step can go only to the adjacent cell below-left or below-right. The sibling cells also lie immediately beside the path, so they cannot be arbitrarily far out to either side.

This diagram first helps locate the two regions. To establish rigorously that sibling cells stay outside them for **any turning path**, we still need to compare positions in each row.

## Round 5

### Student

I understand the explanation below the diagram, but the L in row 3 does not seem to belong to the two-row triangle formed by the two bottom cells on the left. Two rows should include only cell 1 in row 4 and bottom cells 1 and 2. Looking backward, to reach cell 3 in row 4, the path can only be in cell 2 or 3 in row 3. The sibling cell for that step can only be in cell 2 or 4 in row 4, neither of which is cell 1 in row 4. When moving from row 2 to row 3, the sibling cell can be in cell 1, but that cell does not belong to this two-row triangle anyway. Is this check correct? I want to align the diagram and ranges before continuing, otherwise I may count the extra cells too.

### Teacher

You are right. My previous diagram included an extra **L** in row 3. The left triangle formed by bottom cells 1 and 2 has two rows, containing only cell 1 in row 4 and bottom cells 1 and 2. The corrected diagram is:

```text
Row 1          ·
Row 2        ·   ·
Row 3      ·   ·   ·
Row 4    L   ·   ·   ·
Row 5  L   L   P   C   R
       1   2   3   4   5
```

Your backward check is correct too. To reach cell 3 in row 4, the path can only occupy cell 2 or 3 in row 3. Thus, in row 4, the sibling cell paired with the path cell can only be in cell 2 or 4, neither of which is cell 1 of the left triangle.

In row 3, the sibling cell can indeed occupy cell 1, but the left triangle has **no cells** in this row, so it still does not enter the left region.

The final bottom pair P, C occupies cells 3 and 4, both outside cells 1 and 2 on the left. The top cell and higher rows likewise do not belong to this two-row triangle. You have now checked the positional ranges row by row for the left region in the diagram.

## Round 6

### Student

The correction makes it clear, and the positions I checked now match. But this is only one path in five rows, and I still cannot write ranges that hold for 2018 rows. Also, even if a region has only numbers greater than 2018, the difference of two large numbers might still exceed 2018, such as 5000 and 2500, so that statement alone gives no contradiction. I now need help in two steps: first use column indices to explain why arbitrary paths avoid both side triangles; once I understand that, let me try what magnitude constraints can still be used there. If you write the whole proof at once, I might manage to read it but fail to connect it myself.

### Teacher

Your judgment is correct: the difference of two numbers greater than 2018 may still exceed 2018, so further magnitude constraints are needed. First we will address only positions.

Suppose the triangle has \(n\) rows and the final bottom pair occupies columns \(p\), \(p+1\). The left triangle has bottom cells 1 through \(p-1\) as its base; the right triangle has cells \(p+2\) through \(n\) as its base.

Consider any row \(r\), and let \(k=n-r\), meaning there are \(k\) steps from this row to the bottom.

**First consider the path cell and its sibling cell.** Their common parent is in row \(r-1\), say in column \(q\). Starting from this parent, the path needs \(k\) more steps to reach cell \(p\) in row \(n-1\), the common parent of the final bottom pair.

Each step leaves the column index unchanged or increases it by 1, so necessarily

\[
q\le p\le q+k,\qquad\text{that is,}\qquad p-k\le q\le p.
\]

The path cell and sibling cell in row \(r\) are this parent’s two children, in columns \(q\) and \(q+1\). Both therefore lie within

\[
\boxed{\text{columns }p-k\ \text{through}\ p+1}
\]

This does not assume a path without turns. It may move below-left or below-right arbitrarily; as long as it eventually reaches the specified parent, it must satisfy this range.

**Now consider the side triangles in the same row.** The bottom-row descendants of cell \(j\) in row \(r\) extend from column \(j\) through column \(j+k\):

- In the left triangle, all bottom-row descendants must lie in column \(p-1\) or farther left, so \(j+k\le p-1\), or \(j\le p-k-1\).
- In the right triangle, all bottom-row descendants must lie in column \(p+2\) or farther right, so \(j\ge p+2\).

Thus the left cells extend at most to \(p-k-1\), whereas path and sibling cells start no farther left than \(p-k\). The right cells start at \(p+2\), whereas path and sibling cells extend at most to \(p+1\). They are separated in every row. The top cell also lies outside both side triangles.

Therefore, however the path turns, **the top cell and the sibling cells collected at each step avoid both side triangles**. You already know that these collected numbers are exactly 1 to \(n\), so every number in the side triangles exceeds \(n\).

Let us stop here for now. Try following the larger child cell downward inside one of these complete small triangles: how can the earlier accumulation relationship be used again?

## Round 7

### Student

I substituted a small diagram: n=5, p=3, and in row 4, k=1. Path and sibling cells are in columns 2 to 4, the left region extends at most to column 1, and the right region starts at column 5. They really are separated. With the column indices written out this time, I can check why turns do not matter.
Continuing: the two sides have 2016 bottom cells altogether, so at least one has 1008 cells, giving a 1008-row triangle. Following the larger number there too, the bottom number reached is the sum of 1008 distinct numbers, each greater than 2018. Using only that each is at least 2019 gives 2019×1008=2035152, still 2019 less than 2037171, so no contradiction yet. But they cannot all equal 2019. Should I instead add 2019, 2020, all the way to 3026? That exceeds 2035152 by the sum from 1 to 1007, which certainly exceeds 2019. Can this lower bound rule it out?

### Teacher

Yes. You identified the key: these 1008 summands are not only all at least 2019, but also **distinct integers**. Arranged in ascending order, the first is at least 2019, the second at least 2020, and so on, with the 1008th at least 3026.

Therefore the bottom number reached by the path in the side triangle is at least

\[
2019+2020+\cdots+3026
=1008\times2019+(1+2+\cdots+1007)
=2\,542\,680.
\]

This exceeds the largest number allowed in the whole triangle, \(2\,037\,171\), a contradiction. Therefore a **2018-row anti-Pascal number triangle satisfying the original conditions does not exist**.

Your calculation \(2019\times1008=2\,035\,152\) is also correct. What makes the lower bound exceed the maximum is your further use of the distinctness of the summands.

## Round 8

### Student

I can connect that step now. We cannot stop after treating all 1008 terms as 2019; we must include the increases required by their distinctness. I want to check one boundary case: if the final pair is at the far left, one side is empty and the other has 2016 cells. We should still be able to take a complete 1008-row triangle from it and use the same accumulation, so that does not affect the argument, right? My own three-row example has not been ruled out because just 1 cell remains on the sides, so we cannot get such a large lower bound. Am I correctly distinguishing the small example from the 2018-row conclusion?

### Teacher

Yes, your distinction is clear.

If the final pair is at the far left of the bottom row, the left side is empty and the right has 2016 cells, forming a complete 2016-row triangle. Choose any 1008 consecutive cells along its base, together with the cells above supported by them, to obtain a complete 1008-row small triangle. It remains within the original side region, so the same accumulation and lower bound apply, and the conclusion is unaffected.

Your three-row example is also not ruled out. With three rows, the two side bases have just one cell altogether, so the available side triangle has only one row. Its lower bound does not exceed the maximum number 6 in the whole triangle and naturally does not produce the contradiction used in the 2018-row proof. Your specific arrangement already verifies that three rows are feasible.

### Student

I will stop here today. I can organize it around following the larger number twice: first force all of 1 to 2018 into the collected cells, then find a side triangle avoiding them; second, use distinct summands greater than 2018 to obtain a contradiction exceeding the maximum. For the arbitrary-path column indices, I still need to look at the record and explain it slowly. I cannot say I can write it independently yet. After separating the explanations and correcting the small diagram, I really could continue checking, and I also tried the edge case at the end. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
