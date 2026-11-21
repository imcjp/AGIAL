# P01 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P01 |

## Round 1

### Student

Teacher, I want to try a small one first. With two rows, putting 1 and 3 below gives 2 above, so 1, 2, 3 are all used, right? I still do not know how to judge 2018 rows. Could I try three rows first?

### Teacher

Yes, exactly: with 1, 3 on the bottom, the upper row is \(|3-1|=2\), so 1, 2, 3 are each used exactly once, making two rows possible.

You can try three rows first. Three rows require entering 1 to 6, each once, with each upper cell equal to the absolute difference between the adjacent cells below. First try any bottom-row arrangement, then calculate upward.

## Round 2

### Student

I tried 1, 6, 4 below, giving 5, 2 in the middle and 3 at the top, all without repetitions! So three rows work too. But that only tells us about three rows, right? We cannot keep trying random arrangements for 2018 rows. Could you give me a little hint about what to look at next? Just one thing first.

### Teacher

Yes, your three-row construction is correct, and you rightly recognize that feasibility with few rows does not directly establish feasibility with 2018 rows.

Here is just one key observation for the next step:

Starting at the top cell, move in every row to the larger of the two cells below. Since "upper cell = difference between the two lower cells," the larger lower cell equals "upper cell + the other lower cell." Thus, following this path to the bottom, the endpoint can be expressed as "the sum of one number selected from each row."

First consider: what properties do these selected numbers share?

## Round 3

### Student

Using my triangle, I go from 3 to 5, then to 6. Since 5 equals 3 plus 2 and 6 equals 5 plus 1, 6 equals 3 plus 2 plus 1. By selected numbers, do you mean 3, 2, 1? They are all different because no number can repeat in the whole triangle. At first I thought we were adding the 3, 5, 6 on the path. I can follow this breakdown, but how does their being different let us judge 2018 rows?

### Teacher

Yes, you understand accurately: the selected numbers are 3, 2, 1, rather than adding the path numbers 3, 5, 6. The path numbers are formed by successive accumulation, with the endpoint ultimately \(6=3+2+1\).

For 2018 rows, the key is to compare lower and upper bounds:

- There are 2018 selected numbers, all distinct positive integers, so their sum is at least  
  \(1+2+\cdots+2018=2037171\);
- But the endpoint is itself a number in the triangle and cannot exceed \(2037171\).

Thus both sides must be exactly equal. This means the 2018 selected numbers must be precisely \(1,2,\ldots,2018\), and the endpoint must be \(2037171\).

Next consider: since these small numbers are already "occupied" by this path, what numbers can the other regions of the triangle contain?

## Round 4

### Student

Only numbers greater than 2018 can go elsewhere, right? But there were still 4, 5 beside the path in my three-row triangle, without a problem. I still cannot see where the large triangle would conflict. Also, why must the sum of 2018 distinct numbers be larger whenever they are not 1 to 2018? Could you explain with fewer numbers, then guide me to the conflict?

### Teacher

Let us first examine the "minimum sum."

If we select 3 distinct positive integers:

- The smallest possible selection is \(1,2,3\), with sum \(6\);
- A different selection, such as \(1,2,4\), gives \(7>6\);
- Selecting \(1,3,4\) gives \(8>6\).

Thus, only selecting exactly \(1,2,3\) can achieve the minimum. The same reasoning applies to 2018 numbers: only \(1,2,\ldots,2018\) gives the minimum sum.

With three rows, having 4, 5 beside the path is fine because the remaining region is too small to create a numerical contradiction. With 2018 rows, a complete side triangle with at least 1008 rows must lie beside the path that selected the small numbers. It cannot contain the already selected \(1\) to \(2018\), so every number in it is at least 2019.

Following another "larger lower cell" path inside this side triangle, its endpoint is at least

\[
2019+2020+\cdots+3026
=2542680.
\]

But no number in the whole triangle exceeds

\[
1+2+\cdots+2018=2037171.
\]

Thus, the same triangle must contain a number at least 2542680 that simultaneously cannot exceed 2037171. That is the conflict.

## Round 5

### Student

I understand the minimum sum somewhat now: ordering three numbers from smallest upward, the second is at least 2 and the third at least 3; replacing one with a larger number increases the sum. I also know the incompatible sizes of the last two numbers mean a conflict. But I could not follow the claim in the middle that "a complete side triangle with 1008 rows must exist": the path can turn left and right, so how can such a large region remain beside it? And the small summands are themselves beside the path; could they enter this triangle? Could you first draw a small five- or six-row diagram and point it out?

### Teacher

Yes. First consider a schematic with 6 rows. Suppose the path finally reaches cells 3, 4 of the penultimate row:

```text
                 ·
              ·     ·
           ·     ·     ·
        ·     ·     ·     ·
     ·     ·    [3] [4]    ·
  ·     ·     ·     ·     ·     ·
```

Think of the region traversed by the path as a "strip" that moves left and right. It must ultimately lead to the adjacent cells `[3], [4]`, so:

```text
Left region       Path strip       Right region
   △                  ▽                  △
   △                  ▽                  △
```

With 6 rows, there are \(p-1\) cells to the left of the final pair of child cells and \(6-p-1\) to the right. Their sum is \(6-2=4\), so at least one side has height no smaller than 2 rows, forming a complete side triangle.

As for whether "small numbers beside the path might enter it," the key is that, although the horizontal range covered expands with each upward row, it remains within the strip leading to the final pair. The other child of each path cell also remains in this strip; the complete triangles on both sides lie outside it and therefore contain none of the selected numbers.

With 6 rows, the side triangle has only 2 rows, insufficient for a numerical contradiction; with 2018 rows, the same geometric relationship leaves at least 1008 rows, pushing the larger numerical lower bound above the whole-triangle maximum.

## Round 6

### Student

I still find this diagram hard to locate things in. A six-row triangle has only five cells in its penultimate row. Are the labeled 3, 4 cells 3, 4 of row five? I want to check for myself: if the path keeps going left and turns right only on the last step, are the small numbers selected beside the earlier path all still in this strip? Could you label this path and the other small cell at each step, then circle the remaining two-row triangle? Looking only at △ and ▽ does not tell me which cells they correspond to.

### Teacher

You are right; my earlier diagram was not sufficiently accurate. A 6-row triangle has 1, 2, 3, 4, 5, 6 cells in successive rows. Here is a path that "keeps going left, then turns right at the end":

```text
Row 1                         P

Row 2                      P     A

Row 3                   P     A     ·

Row 4                P     A     ·     ·

Row 5             A     P     A     R     R

Row 6          ·     A     P     A     R     R     R
```

The labels mean:

- `P`: a path cell;
- `A`: the "other child" selected at each path step;
- `R`: the complete side triangle remaining on the right;
- `·`: other cells.

Look specifically at the last few steps:

```text
Row 4, cell 1: P
        ↙       ↘
Row 5, cell 1: A   Row 5, cell 2: P
                  ↙       ↘
Row 6, cell 2: P   Row 6, cell 3: A
```

Thus the final pair consists of cells 2, 3 of row 6; the cells to their right form:

```text
Row 5:             R     R
Row 6:          R     R     R
```

This is a complete 2-row side triangle.

Although the path turns right at the end, the preceding `P` cells and their corresponding `A` cells all remain within the strip leading to the final pair; the right `R` triangle starts at cell 4 of row 5, separately from them. Thus the small numbers being accumulated cannot enter the `R` region.

## Round 7

### Student

I counted seven cells in row 6, one too many. Row 5 in the upper diagram has two A cells, but when the path comes from cell 1 of row 4, should there not be only the pair in cells 1, 2? The P positions in the smaller diagram below also differ from the larger one. Now I am even more confused. Could you keep just one correct six-row diagram, check the number of cells in each row first, and circle a triangle with one cell above and two below? There is no need to repeat the large-number calculations; I know we need to compare their sizes.

### Teacher

You are right; the earlier diagram contained errors. Here is just one correct six-row diagram, with 1, 2, 3, 4, 5, 6 cells in successive rows:

```text
Row 1                         P

Row 2                      P     A

Row 3                   P     A     ·

Row 4                P     A     ·     ·

Row 5             A     P     A     ·     ·

Row 6          ·     P     A     ·     ·     ·
```

Here:

- `P` is the path;
- `A` is the other child beside the path at each step;
- `·` is an as-yet unlabeled cell.

The final cells can be viewed separately as a correct local triangle:

```text
                 P
              ↙     ↘
             P       A
```

This triangle means that the upper cell equals the difference between the two lower cells; if the `P` on the right among the lower cells is larger, it equals the upper cell plus the other cell `A`. The confusing earlier diagrams were my fault; this diagram has the correct number of rows and cells per row.

### Student

Let us stop here today. I can calculate small triangles using the differences between adjacent numbers, and I understand that distinct positive integers have a minimum sum. But row 5 in this diagram still has two A cells, and the remaining large triangle has not been circled, so I still cannot explain myself why 2018 rows must be impossible. Repeatedly checking the diagrams has made me a bit confused. I will stop for now.

### Teacher

This teaching session has been confirmed as ended.
