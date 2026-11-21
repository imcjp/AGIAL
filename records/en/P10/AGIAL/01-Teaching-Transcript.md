# P10 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the integers from 1 to 2037171 each be used once to form an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P10 |

## Round 1

### Student

I want to check the rules first. With two rows, if I put 1 and 3 in the bottom row and 2 at the top, using 1 to 3 exactly once, that counts as a valid small triangle, right? But a successful small example does not seem to support existence for 2018 rows. I have studied research methods and tend to distinguish examples from general evidence first. To establish nonexistence in this kind of problem, do we need a restriction that no arrangement can avoid? Could you give me a suitable starting point so I can work out a small step myself?

### Teacher

Yes, your two-row triangle is valid: the top cell satisfies \(2=|3-1|\), and the three cells use \(1,2,3\) exactly once each.

Your judgment is also correct: this example proves that a two-row arrangement is possible, but does not directly establish that a 2018-row arrangement is possible. To prove nonexistence for 2018 rows, we can look for **conditions that every arrangement satisfying the rules must meet**, and then see whether those conditions lead to a contradiction.

One starting point is your small triangle:

```text
    2
  1   3
```

Starting at the top cell, move down to the larger of the two adjacent child cells. Try expressing the number you selected in terms of the top number and the other child number. Why does this relation hold for any three adjacent cells satisfying the rules?

## Round 2

### Student

Let the upper number be a, the larger number below it be b, and the other one be c. Then a=b-c, so b=a+c. In the small example, this is 3=2+1; swapping left and right below makes no difference. Along a path that always selects the larger child cell, the numbers keep increasing because the c added each time is positive. I tried adding these relations together: the bottom cell equals the top cell plus the unselected child cells along the path. Is that right? But increasing 2017 times alone does not seem enough to exceed 2037171. I still do not see how to use the condition that no number is repeated.

### Teacher

Your understanding is correct. Swapping left and right does not affect the relation. Whenever you select the larger child cell, you have “new path number = previous path number + the other child number.” Combining these equations gives the bottom cell as the top cell plus the unselected child cell in each row along the path.

You also noticed a key point: knowing only that the numbers increase is insufficient to show directly that the bottom cell exceeds the permitted maximum.

Here is how to use “no repetitions”: in a triangle with 2018 rows, your sum includes the top cell and one unselected child cell in each subsequent row. These come from different rows, so they are different cells. By the problem's condition, the numbers in these cells are also distinct.

You can try the next small step yourself: **How many distinct positive integers are being added in total? What is the smallest possible sum?** Then compare that lower bound with the largest permitted bottom-cell value.

## Round 3

### Student

There is 1 top cell plus 2017 unselected child cells, giving 2018 distinct positive integers. In increasing order, the kth is at least k, so their sum is at least 2018×2019÷2=2037171. I get exactly the permitted maximum, so this does not seem to be a contradiction yet. If equality holds, these 2018 summands must be exactly 1 to 2018, and the bottom cell of the path must be 2037171. This equality condition is much stronger than increasing alone. Your hint helped me turn distinctness into a quantitative restriction. But I do not yet know how to rule out equality. Saying this lower bound alone proves nonexistence would leave a gap in the evidence, wouldn't it?

### Teacher

Correct: **there is no contradiction yet**. Your calculation shows that if such a triangle exists, its bottom cell is both at least 2037171 and at most 2037171, so equality must hold. Both equality conditions you derived are correct.

Next, we can use the fact that “this path has collected all the small numbers” to see whether some region of the triangle is forced to contain only large numbers.

First consider positions alone: look at the two adjacent bottom-row cells involved in the last step of the path. The bottom-row cells to their left can form the base of a smaller triangle, and so can those to their right.

How many cells do these two side bases contain altogether? Therefore, how many rows must the larger side have at minimum? For now, you need not determine the numbers in the side triangles.

## Round 4

### Student

Removing those two adjacent bottom-row cells leaves 2016 cells in total on the left and right. The larger side therefore has at least 1008 cells, corresponding to a small triangle with at least 1008 rows. I can follow this; separating positions from values makes it easier to handle. But before saying this side triangle contains none of 1 to 2018, I want to check something: could an earlier unselected child cell fall inside it? The path turns left and right, so I cannot yet guarantee from a picture alone that they are all outside. Could you explain this positional condition with a small diagram or column relations?

### Teacher

Your concern is crucial: because the path can turn, we need to check **every row**, rather than rely on intuition from a diagram. Your calculation of 1008 rows is also correct.

Column numbers let us account for any turns. Suppose the last pair of bottom-row child cells occupies columns \(p\) and \(p+1\). Their parent, the path cell in the penultimate row, must then be in column \(p\).

Now consider any row \(r\). Suppose the common parent of its path cell and unselected child cell occupies column \(q\) in the preceding row:

- From this parent, reaching column \(p\) in the penultimate row along the path takes another \(n-r\) steps. At each downward step, the column number either stays the same or increases by 1, so
  \[
  p-(n-r)\le q\le p.
  \]
- Its two child cells occupy columns \(q\) and \(q+1\). Thus, whichever is selected, **both the path cell and the unselected child cell lie in**
  \[
  [\,p-(n-r),\ p+1\,].
  \]

Now consider the two side triangles in the same row. The descendants in the bottom row of cell \(j\) in row \(r\) range from column \(j\) to column \(j+n-r\). Therefore:

- Cells of the left side triangle extend rightward only as far as column \(p-(n-r)-1\).
- Cells of the right side triangle begin no further left than column \(p+2\).

Both ranges avoid the interval above, so the unselected child cell in every row lies outside the side triangles. The top cell also lies outside them. Thus, all the numbers from \(1\) to \(2018\) you collected earlier lie outside the two side triangles. Since numbers cannot repeat anywhere in the whole triangle, every number in the side triangles is greater than \(2018\).

## Round 5

### Student

The column explanation addresses my concern about turns. Let me try n=6 with the last pair in columns 3 and 4: in row 5, the path and unselected cells lie within columns 2 to 4; the left side triangle extends only as far as column 1 in this row, and the right side begins at column 5. They do avoid each other. Every number in a side triangle is at least 2019. I want to follow the larger-child path again within the side triangle with at least 1008 rows, giving 1008 distinct summands again. Using only that each is at least 2019 gives 1008×2019=2035152, which still does not exceed 2037171. But since they are distinct, the smallest sum should be 2019+2020+…+3026=2542680, exceeding the maximum. Is it valid to reuse the same relation inside the side triangle this way? The side triangle does not need to use exactly a consecutive sequence of integers; it seems enough that they are distinct and all greater than 2018.

### Teacher

It is valid, and both your judgment and your calculation are correct. The side triangle need not use exactly a consecutive sequence of integers. The second sum only requires that the adjacent absolute-difference rule still holds within the side triangle, and that the numbers collected are distinct and all greater than 2018.

The side triangle is a **complete subtriangle**: both children of every cell above its bottom row are also inside it, so we can again move down through the larger child cells. If the larger side triangle has more than 1008 rows, we can first take a complete 1008-row subtriangle within it. Along this path, the bottom cell equals the top cell plus the 1007 unselected child cells along the way, giving 1008 summands in total.

These summands are distinct and each is greater than 2018, so their sum is at least what you calculated:

\[
2019+2020+\cdots+3026=2542680.
\]

But this bottom cell is still a cell of the original triangle, so its value cannot exceed 2037171. The lower bound exceeds the upper bound, a contradiction. Thus the initial assumption that “a 2018-row triangle exists” is false.

You made the distinction accurately: the consecutive integers \(2019,\ldots,3026\) provide a **lower bound** for the sum of distinct large numbers; the side triangle need not actually contain exactly these numbers.

### Student

I will stop here today. I can now distinguish the two sums: the first lower bound only reaches the maximum, forcing all the small numbers into the collected cells; the column relations ensure the side triangles avoid those cells; only the second sum gives a contradiction by strictly exceeding the maximum. Thus a 2018-row triangle does not exist. The explanation of a complete subtriangle also supplies the condition needed to reuse the relation. I am still not proficient at this kind of geometric positional proof, but I have checked it with a small example and do not need to go further. Separating positions from values and letting me calculate the lower bounds myself helped me.

### Teacher

This teaching session has been confirmed as ended.
