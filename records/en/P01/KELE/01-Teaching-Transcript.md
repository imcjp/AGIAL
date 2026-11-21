# P01 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P01 |

## Round 1

### Student

Teacher, I want to try two rows first: putting 1 and 3 below gives 2 above, with none of the three numbers repeated. Does that follow the rules? There are too many rows in 2018, and I still do not know where to start judging it. Could I try a smaller triangle first, then look at it together?

### Teacher

Your two-row example follows the rules: the difference between 1 and 3 below is 2, and 1, 2, 3 are each used once.

Let us try three rows next: can you use **each of 1 to 6 once** to arrange a number triangle following the same rule? Try arranging it first and write out your thinking.

## Round 2

### Student

I first arranged 1, 6, 2 below, calculated 5, 4 in the middle, and got 1 at the top. The differences are all correct, but 1 repeats and 3 is missing. Then I replaced the bottom 2 with 3, giving 5, 3 in the middle and 2 at the top, repeating 3 again. Changing them one at a time is confusing. Could you show me how to keep track of what I have tried? Please do not tell me an arrangement yet; I want to try again.

### Teacher

Your differences were correct both times, and you identified the repetitions. The second attempt also omitted 4. To meet the rules, each upper cell must equal the absolute difference between adjacent cells below, and every number from 1 to 6 must appear once.

You can record each attempt in a table, adding a row each time you change the bottom row:

| Bottom row (left to right) | Middle row | Top row | Repeated number | Unused number |
|---|---|---|---|---|
| 1, 6, 2 | 5, 4 | 1 | 1 | 3 |
| 1, 6, 3 | 5, 3 | 2 | 3 | 4 |

Next choose a bottom row you have not tried, calculate the two rows above, and record it. Which set would you like to try?

## Round 3

### Student

Next I tried 1, 6, 4, giving 5, 2 in the middle and 3 at the top. This time the six numbers are 1, 6, 4, 5, 2, 3, without repetitions or omissions! The table lets me continue from my previous attempt instead of changing things randomly. But arranging three rows does not show that 2018 rows will work too, does it? We cannot keep trying forever with such a large triangle. What should we look at next?

### Teacher

Yes, your three-row triangle meets all the conditions: every difference is correct and each number from 1 to 6 appears once. Your judgment is also correct: constructing three rows establishes only three-row feasibility and does not directly imply feasibility for 2018 rows.

Next we can start with "the relationship every small part must satisfy" and see whether it constrains the whole triangle.

In your triangle, the top is 3, with 5 and 2 below. **What happens if you add the upper number to the smaller lower number?**

## Round 4

### Student

3 plus 2 equals 5, exactly the larger number below. I also checked the bottom: 5 plus 1 equals 6, and 2 plus 4 also equals 6. It is just adding back what was subtracted. But if all these small parts work that way, how does that affect the whole triangle? I still have not connected this step.

### Teacher

Yes, we add back the subtracted number. We can connect two consecutive steps:

Starting from the top 3 and always moving to the larger number below gives the path **3 → 5 → 6**. You have already written:

- First step: 5 = 3 + 2
- Second step: 6 = 5 + 1

Substituting the first equation into the second gives **6 = 3 + 2 + 1**. Applying the local relationship row by row along the path thus connects the top, the smaller numbers encountered twice, and the bottom 6.

If the triangle had more rows and you still started at the top and always moved to the larger number below, how do you think the eventual bottom number could be expressed?

## Round 5

### Student

Would it be the top number plus the smaller number beside the path at each step? For example, if we went down one more row and the smaller number beside it were 4, we would add another 4 after 3 plus 2 plus 1 and reach 10. I can follow writing it row by row like that. Would 2018 rows mean adding lots of numbers? But I do not know what those smaller numbers would be, so how do we calculate next?

### Teacher

Yes, your generalization is correct: from the top to row 2018 takes 2017 steps, so the number reached at the bottom equals the top cell plus the smaller sibling at each of those 2017 steps, a **sum of 2018 numbers** in total.

Even without knowing the specific numbers, we can first consider their shared restrictions: the original problem requires positive integers throughout, with every number appearing only once.

**Why must these 2018 summands be distinct positive integers?**

## Round 6

### Student

The top cell is in the first row, and each downward step takes the smaller sibling from a new row, so we never select the same cell. The problem also says no cell numbers can repeat and they start from 1, so all the summands are distinct positive integers. To make their sum as small as possible, should we choose 1, 2, 3 all the way to 2018? But the sequence is too long for me to calculate at once.

### Teacher

Yes, you have found the smallest possible sum. Pair the first and last terms to calculate:

\[
1+2018=2019,\quad 2+2017=2019,\quad \ldots
\]

There are 1009 pairs, so

\[
1+2+\cdots+2018=2019\times1009=2\,037\,171.
\]

Thus the bottom number reached along the path is **at least** 2,037,171. The largest number allowed in the original problem is also exactly 2,037,171, so this bottom number must equal it.

We can go a step further: 2018 distinct positive integers achieve this minimum sum only if they consist precisely of \(1,2,\ldots,2018\). Therefore all these small numbers already occupy the cells from which we collected the summands.

This has not yet proved that the whole triangle does not exist. Consider: **since 1 to 2018 have all been used in these cells, what must be true of the numbers in the other cells?**

## Round 7

### Student

The other cells must all be greater than 2018, or they would repeat. I can understand pairing the first and last terms to make equal sums. But I am a bit confused: the cells we visited and the cells we collected to add do not seem to be the same group. With three rows we visited 3, 5, 6 but collected 3, 2, 1. Could you use that small triangle to point out the "other cells," then tell me where to look next?

### Teacher

Yes, you distinguish them accurately: **visited cells** and **cells collected for addition** are two different groups.

Using your three-row triangle:

```text
       3
     5   2
   1   6   4
```

Following the larger numbers gives **3 → 5 → 6**; the collected summands are the top **3** and the smaller siblings **2, 1** at each step. Relative to these summands, the "other cells" are **5, 6, 4**, all greater than 3. Notice that the path cells 5 and 6 are also "other cells."

For a hypothetically existing 2018-row triangle, the same reasoning shows that all cells except those containing the 2018 collected summands are greater than 2018.

Next look at **the regions to the left and right of the final pair of child cells when the path reaches the bottom**. If we can find a sufficiently large complete small triangle beside them and confirm that it contains none of the collected cells, all its numbers will exceed 2018; we can apply row-by-row accumulation again inside it.

First identify in the bottom row of your three-row triangle: which two numbers form the final pair, and which number remains on either side?

## Round 8

### Student

The last step was from 5 to 6, so the child pair is 1 and 6. Nothing is left to their left, and 4 remains to their right. Drawing it makes the distinction clear. But there is only one 4 here; how can we find a complete small triangle in the large one? Could you draw a slightly larger cell diagram and circle the collected cells separately from the small triangle beside them? Just talking about left and right regions does not let me imagine which cells above are included.

### Teacher

Yes, the final pair in the three-row example is **1, 6**, leaving only the single cell 4 on the right, so the small right triangle has one row.

Here is a **six-row positional schematic**. It contains no numbers and simply assumes that the final pair reached occupies bottom cells 3, 4:

```text
                 ●
              ○  ×
           ○  ×  ●
        ○  ○  ●  ×
     ○  ○  ×  ●  [□]
  [□] [□]  ×  ●  [□] [□]
```

- `●`: the path through larger child cells.
- `×`: the other child collected at each step; the top `●` also counts among the summands.
- `[□]`: the complete small triangles on the two sides; `○` marks the other cells.

Look at the `[□]` cells on the right: the upper cell has the two adjacent `[□]` cells below as its children, making a complete **two-row small triangle**. The two bottom `[□]` cells on the left also form a two-row small triangle.

Why do these side triangles avoid the collected cells? On the right, for example, expanding downward from any of its cells reaches only cells **to the right** of the final pair. Since each path step must continue toward that pair, the path cells and the other children collected beside them lie within the strip leading to the pair. The same holds on the left.

In the hypothetical 2018-row triangle, the bottom-row cell counts on both sides sum to **2016**. The larger side contains at least **1008 cells**, forming a side triangle of at least 1008 rows; it contains no collected cells, so all its numbers exceed 2018.

Now consider: starting at the top of this small triangle of at least 1008 rows and always moving to the larger child, which positive integers must at minimum sum to the number reached at its bottom?

## Round 9

### Student

If everything inside really is greater than 2018, the smallest selection starts at 2019, 2020 and continues upward, selecting 1008 numbers in total. But why is there no path ● in row two of the diagram? There is also no box above the two boxes on the left; were labels omitted? Also, I cannot see why the other collected child is in the strip: might it extend into the small side triangle? Could you clarify this part first?

### Teacher

You are right; the previous diagram omitted two labels: the path marker in row two and the top cell of the small left triangle. Thank you for pointing them out. Your lower bound is also correct: once we confirm that all numbers in the side triangle exceed 2018, the sum of 1008 distinct summands is at least the sum of the 1008 integers starting at 2019.

Here is the corrected six-row **positional schematic**. Cells are ordered from left to right in each row; the chosen path is merely an example, and the diagram represents no actual numbers.

```text
                   A
                P     C
             ·     P     C
          ·     ·     P     C
       [L]    ·     C     P    [R]
    [L]   [L]    C     P    [R]   [R]
```

`A` is the top cell and also a collected summand; `P` marks path cells; `C` marks the other child collected at each step. `[L]` and `[R]` outline the complete small triangles on the left and right. The final pair is bottom cells 3, 4, namely `C, P`.

**Why cannot the collected sibling cells extend into the side triangles?** We can look backward from the bottom:

- The final bottom pair occupies cells 3, 4; the bases of the side triangles occupy only cells 1, 2 and 5, 6, respectively.
- Looking upward, path cells must be able to follow adjacent children to the cell above the final pair. The sibling collected at each step is precisely **the other adjacent child** of this path cell, and is therefore also restricted to the region leading to the final pair.
- More precisely, suppose the final pair occupies bottom cells \(p,p+1\). In row \(r\), if the preceding path cell is in column \(q\), its ability to reach column \(p\) of the penultimate row requires \(q\le p\le q+6-r\). The collected sibling occupies column \(q\) or \(q+1\), and thus lies between columns \(p-(6-r)\) and \(p+1\). The left side triangle lies to the left of this interval and the right side triangle to its right, so neither intersects it. This argument applies to any number of rows by replacing 6 with the total row count.

For 2018 rows, 2016 bottom cells remain outside the final pair, so the larger side contains at least 1008 cells and thus a side triangle of at least 1008 rows. It avoids every collected cell, so every number inside exceeds 2018. Descending through larger child cells within it again gives an endpoint at least

\[
2019+2020+\cdots+3026
=\frac{1008(2019+3026)}2
=2\,542\,680.
\]

But the whole-triangle maximum is **2,037,171**, a contradiction, so the original 2018-row triangle does not exist.

You have independently discovered path accumulation, distinctness of summands, and the minimum sum in the side triangle; the separation of the side triangle from the collected cells and the final contradiction are the arguments we have just added. The earlier incorrect diagram really was insufficient to support that step.

## Round 10

### Student

The final sum is larger than the permitted maximum, so it cannot be arranged; I understand that. But the p, q, r passage is too long for me to follow. Also, in the new diagram P is on the left in row two and in the middle in row three, so should the collected C in row three not be on the left? From the left cell of row two, we can only touch the left and middle cells of row three, right? Could you draw only these two rows to confirm? You also helped me connect path accumulation using 3, 5, 6; I still cannot explain the complete proof myself.

### Teacher

Yes, your observation is accurate: **C in row three should be on the left**. I mislabeled the second diagram too. Sorry.

For these two rows alone, the correct positions are:

```text
Row two:       P       ·
              / \
Row three:   C   P       ·
```

The left `P` in row two is adjacent only to the **left and middle cells** in row three. If the path goes to the middle `P`, the other collected child is the left `C`; the right cell is not adjacent to this `P`. Placing `C` in the right cell earlier was incorrect.

I have also noted your account of your progress: you understand the final numerical contradiction, but connected path accumulation with help from my example, and still need to examine the spatial separation slowly. We cannot yet say that you can independently present the complete proof.

## Round 11

### Student

I can see these two rows clearly. If we instead chose the left cell, C would go in the middle, and the right cell still could not be touched. Looking at one small part is easier than that series of letters. But after two incorrect diagrams, I am no longer sure the large triangle really avoids C. Could you redraw the six-row diagram correctly and let me check it row by row myself? Please do not discuss the final addition again yet; I want to understand this diagram first.

### Teacher

You are right; after two incorrect diagrams, it deserves another row-by-row check. This diagram represents only **cell positions**, without numbers. The path still goes from the left cell of row two to the middle cell of row three, and the final pair occupies bottom cells 3, 4.

```text
Row 1                 A
Row 2              P     C
Row 3           C     P     ·
Row 4        ·     C     P     ·
Row 5     [L]   ·     P     C    [R]
Row 6  [L]   [L]   C     P    [R]   [R]
```

- `A`: the top cell, also a collected cell.
- `P`: a cell visited by the path.
- `C`: the other child below the path cell at each step, namely a collected cell.
- `[L]`, `[R]`: the small triangles on the left and right.
- `·`: other cells.

To help you check row by row, the **two cells in the next row** encountered from each path cell are listed separately below. Columns are counted from left to right:

| Starting row and cell | Adjacent cells in next row | Path goes to | Collected |
|---|---|---|---|
| Row 1, cell 1 | Row 2, cells 1, 2 | Cell 1 `P` | Cell 2 `C` |
| Row 2, cell 1 | Row 3, cells 1, 2 | Cell 2 `P` | Cell 1 `C` |
| Row 3, cell 2 | Row 4, cells 2, 3 | Cell 3 `P` | Cell 2 `C` |
| Row 4, cell 3 | Row 5, cells 3, 4 | Cell 3 `P` | Cell 4 `C` |
| Row 5, cell 3 | Row 6, cells 3, 4 | Cell 4 `P` | Cell 3 `C` |

Here neither the left `[L]` nor the right `[R]` cells overlap `A` or `C`; each side has a small two-row triangle. This lets us check the positional relationship for **this particular path**. Establishing separation for arbitrary paths still requires a general argument; you have not independently mastered that step, so we will not treat it as a proof you have completed.

### Student

I checked using the column numbers: below cell 3 of row four are cells 3, 4 of row five, so P is in 3 and C in 4; the next step goes from cell 3 to cell 4 of row six, so C is in cell 3. This time the small triangles on both sides avoid C. With this diagram and table, I can check it myself. I want to stop here today. I can follow the small triangle and the addition along the path, but I still do not understand why another path must also avoid the small side triangles, so I still cannot prove myself that 2018 rows cannot be arranged.

### Teacher

This teaching session has been confirmed as ended.
