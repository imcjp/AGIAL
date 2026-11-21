# P01 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P01 |

## Round 1

### Student

Teacher, I want to try a small triangle first. With two rows, if I put 1 and 3 below and 2 above, I have used 1, 2, and 3 exactly once. Does that follow the rules? I do not know where to start with 2018 rows. Could you first give me a smaller example to try myself? Please do not tell me the answer yet.

### Teacher

It follows the rules: the lower row contains 1 and 3, the upper row contains the absolute value of their difference, \( |1-3|=2 \), and the three cells use 1, 2, and 3 exactly once each.

You can try a **three-row triangle**: use each number from 1 to 6 once to fill the cells below, so that each upper cell equals the absolute difference between the two adjacent cells directly below it.

```text
        [ ]
      [ ] [ ]
    [ ] [ ] [ ]
```

You can choose the bottom-row numbers yourself first, then check whether the whole triangle meets the requirements. I will not tell you the answer yet.

## Round 2

### Student

I first chose 1, 6, 3 for the bottom, which gives 5, 3 in the middle and 2 at the top. I calculated all the differences, but 3 appears twice and 4 is missing, so it does not work. Then I tried 1, 6, 2, giving 5, 4 in the middle and 1 at the top, another repetition. Changing them one by one feels a bit confusing. Could you give me a hint about choosing the bottom row so repetitions are less likely?

### Teacher

You checked accurately: the differences in both candidates are correct, but both contain repeated numbers.

You can first focus on the **bottom and middle rows**. After choosing three bottom-row numbers, calculate the two adjacent differences and first check these differences:

- Are they different from each other?
- Are both absent from the bottom row?

If both checks pass, calculate the top cell and check the remaining number. This saves you from drawing the entire triangle every time.

Try choosing another bottom row this way and send me your working.

## Round 3

### Student

I tried 6, 1, 4 on the bottom, giving 5, 3 in the middle. These five numbers are all different, leaving only 2; 5 minus 3 at the top is exactly 2, so this time it worked! Checking five numbers first really is clearer. But being able to arrange a small triangle does not tell us whether we can arrange 2018 rows, does it? Surely we cannot keep trying all the way up to that size?

### Teacher

Your three-row triangle meets every requirement! You found a valid example, proving that **three rows can be arranged**; it does not yet tell us whether 2018 rows can be arranged.

Indeed, we need not keep trying up to that size. We can first look in your triangle for a **relationship that holds regardless of the number of rows**:

```text
      2
    5   3
  6   1   4
```

Starting at the top cell, move downward each time to the larger of the two adjacent cells, obtaining the path \(2\to5\to6\). At each step, the upper number is the difference between the two lower numbers, so we can also write this in reverse:

\[
5=2+3,\qquad 6=5+1.
\]

Combining these gives \(6=2+3+1\).

If a triangle had more rows and we kept moving this way to the bottom, could you describe **which numbers would sum to the number at the bottom endpoint**? You can describe it in words first; there is no need to write a formula for 2018 rows straight away.

## Round 4

### Student

Do we start with the top number and, at every downward step, add the number beside it that we did not move to? Here we first add 3 to 2 to get 5, then add 1 to get 6. With more rows we would keep adding like that. I do not quite understand how this relates to whether we can arrange 2018 rows. Could the number at the bottom not just be large enough to accommodate the sum?

### Teacher

Yes, you described it accurately: starting from the top cell, every downward move to the larger cell adds the number in the other cell of the same pair.

The key is that although the bottom number can become larger, **the original problem specifies its upper bound**: 2018 rows contain

\[
1+2+\cdots+2018=2037171
\]

cells, and only the numbers 1 to 2037171 may be used, so no cell can exceed 2037171.

Suppose such a triangle exists. Following your path to the bottom, the endpoint equals **the top cell plus the sibling cell not chosen at each step**, giving 2018 summands in total. These summands occupy different rows, and no number repeats anywhere in the triangle, so they are 2018 distinct positive integers. Their sum is at least

\[
1+2+\cdots+2018=2037171.
\]

Thus, the endpoint is at least 2037171 and cannot exceed 2037171, so it must equal it exactly; the summands must therefore be precisely 1 to 2018.

This connects the path to the large triangle: it tightly constrains the endpoint and the positions of a set of small numbers. **This step has not yet produced a contradiction**, so it alone cannot determine whether the whole triangle can be arranged; next we need to consider what these constraints imply for the rest of the triangle.

## Round 5

### Student

I checked using three rows: the smallest three distinct positive integers are 1, 2, 3, which sum to 6; changing them to 1, 2, 4 gives 7, exceeding the maximum of 6. My triangle adds 2, 3, 1, which fits exactly. That helps me understand why the 2018 summands must be the smallest numbers. But I cannot yet see what happens elsewhere in the whole triangle. Could you point out which cell to look at next in my three-row triangle, then let me try?

### Teacher

Your check is correct; the three-row triangle illustrates exactly this equality case.

Along your path \(2\to5\to6\), the top cell and the two sibling cells are \(2,3,1\). Now look at **the 4 at the far right of the bottom row**:

```text
      2
    5   3
  6   1  [4]
```

It is beside the final pair of cells on the path, \(6,1\), and was not included among those summands.

Using the facts that "1, 2, and 3 already occupy one cell each" and "no number can repeat in the whole triangle," can you explain why the number in this cell must be greater than 3?

## Round 6

### Student

Because 1, 2, 3 have already been used in other cells, we cannot use them again here, and we cannot put 0 there, so the smallest possible number is 4. With 2018 rows, does that mean all cells not occupied by those summands must be greater than 2018? But my 4 being greater than 3 did not cause a problem. Which two numbers should we compare next to find a problem?

### Teacher

Yes. Since those summands already use every number from 1 to 2018, other cells cannot reuse them and must therefore be greater than 2018. In your three-row example, 4 being greater than 3 is not itself a contradiction; the key is that in a large triangle we can find a sufficiently large region where many large numbers are added again.

We need to compare **a lower bound for a bottom cell in this region** with **the largest number permitted anywhere in the triangle, 2037171**.

After following the original path to the bottom, two side triangles are supported by the cells to the left and right of the final adjacent pair. It can be proved that all 2018 summands collected earlier lie outside these side triangles, so every number in the side triangles is greater than 2018. Their numbers of rows sum to 2016, so at least one has no fewer than 1008 rows.

Within that side triangle, follow the larger child cell downward again. This produces a bottom cell equal to the sum of at least 1008 distinct positive integers, all greater than 2018. It is therefore at least

\[
2019+2020+\cdots+3026=2542680.
\]

But this cell also belongs to the original triangle and cannot exceed 2037171. Now compare:

\[
2542680>2037171.
\]

This gives a contradiction, showing that a 2018-row triangle satisfying the original rules does not exist.

The step most in need of further clarification is why both side triangles avoid the summands collected earlier. I have used this spatial relationship above; if you wish, we can next use a small diagram to make it clear.

## Round 7

### Student

I understand the comparison between the two large numbers at the end, but the side-triangle part introduced so many things at once that I could not keep up. I still cannot say I understand why it does not exist. Please draw a small five- or six-row diagram showing the path, the collected summands, and the triangles on both sides. I want to count their rows myself and see why the collected numbers cannot enter them. Let us just clarify this part first.

### Teacher

Let us first look only at **cell positions**, without entering numbers or assuming that this six-row triangle can already be arranged according to the rules.

In the diagram, **P** denotes the path followed, **C** the sibling cell not chosen at each step, and **L, R** the triangles on the left and right, respectively:

```text
Row 1           P
Row 2         C   P
Row 3       ·   P   C
Row 4     ·   C   P   ·
Row 5   L   ·   P   C   R
Row 6 L   L   C   P   R   R
```

The path from top to bottom consists of the P in each row; each C is the other child cell adjacent to the path cell at that step, sharing the same path cell above as its parent. **The collected summands are the top P and all the C cells**; the other P cells are the results of successive additions.

The path ends at the middle P in row 6, paired with the C on its left. We leave this final pair in the middle and look at L on their left and R on their right.

First count for yourself: how many rows does each of the L and R triangles have? Does any C enter L or R? You can also check row by row along the path that each C is immediately beside the P in the same row.

## Round 8

### Student

This diagram is clearer. L has two rows and R also has two, making 4 altogether, exactly 6 minus 2. All the C cells are beside the path and do not enter L or R. I also want to check a variation: if P keeps going along the far left, would there be no triangle on the left and four rows on the right? But there are no C cells in that diagram, so it only explains this particular path; I still do not understand why other paths must also avoid C. Could you explain it in terms of walking?

### Teacher

Yes. If P stays along the far left, the final pair occupies columns 1, 2 of the bottom row: there is no left side triangle, while columns 3 to 6 on the right support a four-row triangle. The row counts on both sides still total \(6-2=4\).

For any path, we can explain why C cannot enter the side triangles by asking **whether there are still enough steps to reach the endpoint**.

Suppose the final pair occupies columns \(p\), \(p+1\) of the bottom row. Then the path cell in the penultimate row must be in column \(p\). Now look back at a pair P, C in any row:

1. They have the same path parent cell. Suppose that parent is in column \(q\), with \(k\) steps remaining to the penultimate row.
2. At each step the column number either stays unchanged or increases by 1. Since it must eventually reach column \(p\), we must have \(q\le p\le q+k\).
3. The pair P, C consists of the parent's two children, in columns \(q\) and \(q+1\). Thus both lie between columns \(p-k\) and \(p+1\).

Now consider the side triangles in the same row. For cells in the left triangle, every bottom-row cell reachable by downward moves must lie in column \(p-1\) or further left; this restricts them to at most column \(p-k-1\) in that row. Cells in the right triangle start at column \(p+2\).

Thus the positions within the same row are:

```text
Left side triangle     Possible positions of P, C     Right side triangle
… up to p−k−1      |       p−k to p+1           |      p+2 onward …
```

However the path turns, P and C remain between the two side triangles. What constrains C here is **the parent it shares with P**; C itself need not be able to follow the chosen path to the endpoint. The top cell is also outside the side triangles, so the collected top cell and all C cells avoid both sides.

You can check this against the path that stays on the left: here \(p=1\), P and C occupy columns 1, 2 in each row, while the right side triangle starts at column 3.

## Round 9

### Student

I can check the path along the left: P is in the first column, C in the second, and the right triangle starts at the third, so they do not touch. I also understand that a parent can only move to the two cells below it each time; if it is too far away, it cannot reach the final pair in time. But seeing p, q, k together confuses me again, and I still cannot work out p minus k minus 1 myself. Could you use row four of the six-row diagram, without letters? I want to look only at this row and try to decide why C cannot be placed where L is.

### Teacher

Yes, let us look only at **row four** of the six-row diagram:

```text
Row 4     ·   C   P   ·
Row 5   L   ·   P   C   R
Row 6 L   L   C   P   R   R
```

The final pair occupies **columns 3, 4 in row six**, so the path cell in row five must be in **column 3**.

There is only one downward step from row four to row five: it can go only to the left or right child directly below. Look at C and P in row four: they share a path parent in row three.

If C in row four were at the far left, in column 1, which column would its paired P occupy? Could that P reach column 3 of row five in one more step?

Also, the left L triangle in the diagram extends only as high as row five; **there is no L cell in row four in the first place**. First try deciding whether C can occupy the far-left cell in row four, then consider how this relates to L on the left of row five.

## Round 10

### Student

If C in row four is in column 1, then P is in column 2, right? If P takes one step down to the right, would it not reach column 3 of row five? So it seems possible. I also see there is no L in row four, so my earlier question about putting it at L was not quite right. Could we instead look at the actual L in column 1 of row five? If C goes there, the paired P is in column 2, and it seems it can also reach column 3 of row six in the next step. Am I missing a restriction from some row?

### Teacher

You have not missed anything; I stated the condition incorrectly in my previous message. With C in column 1 and P in column 2 of row four, P can indeed move down to the right to column 3 of row five. Thank you for pointing that out.

Now consider your proposed situation in row five. The key is: **reaching column 3 of row six is not enough; the final pair must occupy columns 3, 4.**

If column 1 of row five is C, its paired P is in column 2. The two children below this P occupy **columns 2, 3 of row six**; whichever is chosen, the final pair is columns 2, 3, rather than the fixed pair in columns 3, 4.

For the final pair to be columns 3, 4, P in row five must be in column 3. C in row five must share a path parent in row four with this P, so C can only occupy column 2 or column 4, not the L in column 1.

Your proposed path really can reach column 3 of row six; what it changes is **the position of the final pair**.

### Student

I know what I missed: reaching column 3 alone could mean coming from the parent in column 2, which makes the pair 2, 3; to keep the pair 3, 4, P in the row above must occupy column 3, and C beside it can only be in 2 or 4, so it cannot touch L in column 1. I can check this small diagram now. Trying small triangles myself, checking in stages, and drawing diagrams help me, but I cannot keep up when several letters appear together. I still cannot explain the entire 2018-row proof myself, but I understand why we need to find a region containing only large numbers, add them, and compare their sum with the maximum. I will stop here for today.

### Teacher

This teaching session has been confirmed as ended.
