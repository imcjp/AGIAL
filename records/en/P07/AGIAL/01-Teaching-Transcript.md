# P07 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P07 |

## Round 1

### Student

I would like to build a small triangle first to check the rules. For two rows using 1, 2, and 3, putting 1 and 3 at the bottom and 2 above uses each exactly once, right? For 2018 rows, I do not know where to start; just trying arrangements seems endless. Could you give me a small-scale direction to try, so I can work through it myself?

### Teacher

Yes, your two-row triangle follows the rules: the upper number is \(2=|1-3|\), and \(1,2,3\) are each used once.

You can next try a three-row triangle. There are six cells in three rows, and **1 to 6 must each be used once**. First choose three numbers for the bottom row, then work upward row by row using the absolute differences of adjacent numbers:

```text
        [ ]
      [ ] [ ]
    [ ] [ ] [ ]
```

For example, you could first try **1, 2, 3** from left to right in the bottom row, calculate the three cells above them, and check whether “1 to 6 each used once” is satisfied. If not, try another bottom row.

After calculating, you can also start at the top cell and move down each time to the larger of the two adjacent cells. Look at the relationship between the numbers along the way and the unchosen numbers beside them. Try it first and tell me what you find.

## Round 2

### Student

With 1, 2, 3 at the bottom, the middle is 1, 1 and the top is 0. There are repeats and even a 0, so that does not work. I changed it to 1, 6, 4, giving 5, 2 in the middle and 3 at the top. This time all of 1 to 6 appear. From 3, I choose 5 going down, then 6; the unchosen numbers are 2 and 1. It seems that 3+2=5 and 5+1=6. I can follow the calculations, but why choose the larger one? How can a path like this tell us whether 2018 rows are possible? Could you explain this part first without introducing too much at once?

### Teacher

Your calculations are correct. The three-row triangle is:

```text
       3
     5   2
   1   6   4
```

Choosing the larger child cell turns a “difference” into a “sum” that is convenient to accumulate. For example, \(3=|5-2|\), and since \(5\) is larger, we can write \(5=3+2\). Similarly, the next step gives \(6=5+1\). Combining them:

\[
6=3+2+1.
\]

Here **5 is an intermediate result**; the final sum consists of the top cell 3 and the unchosen sibling cells 2, 1 at each step.

This method also applies to the hypothetical 2018-row triangle: starting at the top cell and choosing the larger child cell each time, the number reached in the bottom row equals the sum of the top cell and the 2017 sibling cells along the way. Since these summands occupy different cells, the problem requires them to be distinct positive integers.

This suggests a comparison: **What is the minimum sum of these 2018 distinct positive integers? And what is the largest possible number in the bottom row?** Comparing these two numbers first will show what restriction this path imposes on the entire triangle.

## Round 3

### Student

Separating them like that helps me see that 5 should not be added again. For 2018 distinct positive integers, the minimum should be 1 through 2018 added together. I paired 1 with 2018; each pair totals 2019, with 1009 pairs, giving 2037171. The bottom number can also be at most 2037171. They are exactly equal, so it seems we cannot say it is impossible yet? Does the path have to end at the largest number, with the sibling cells using only the smallest numbers? I have not worked out where this leads to a problem. Could you let me try another concrete variation?

### Teacher

Yes, your judgment is correct: the two bounds are exactly equal, so **we cannot directly conclude impossibility at this point**.

Equality does impose restrictions: the path ends at the largest number, 2037171; the top cell and the unchosen sibling cells together must be exactly 1 to 2018. Remember to **include the top cell in this set**.

Here is a concrete variation: keep the difference rule and the range of values, but allow repeated numbers and allow some numbers to be absent. Look at this three-row triangle:

```text
       1
     1   2
   3   2   4
```

First check whether it satisfies these new conditions, then follow the larger child cells from the top to the bottom. Collect the top cell and the unchosen sibling cell at each step: must they still be distinct? This can help you identify which condition the equality argument depended on.

## Round 4

### Student

All the differences in the new triangle are correct: 3 and 2 differ by 1, 2 and 4 by 2, and 1 and 2 by 1. The downward path is 1, 2, 4, and the summands are 1, 1, 2. They repeat, so we can no longer use the step that three distinct numbers total at least 1+2+3. The original condition of no repeats really is needed. I understand this variation now, but still cannot connect what comes after equality in the original problem. Could we return to it and could you tell me where to look next? Just one concrete direction for me to try.

### Teacher

Your analysis is correct: when repeats are allowed, the collected summands can repeat, so we cannot directly reuse the lower bound for “distinct positive integers.”

Returning to the original problem, next look at the **two adjacent bottom-row cells** at the final step of the path. Treat the bottom-row cells to their left as one group and those to their right as another.

Given that the bottom row has 2018 cells, can you calculate how many cells remain in these two groups altogether, and how many cells the larger group must contain at least?

## Round 5

### Student

Removing those two adjacent cells leaves 2016 cells. The two groups total 2016, so the larger must have at least 1008; if they are equal, each has 1008. But these cells are outside the summands we just collected, and I do not know what restrictions we can place on their values. Should we next calculate differences upward from these 1008 cells? A smaller diagram marking the bottom row would help; I am afraid of confusing the sibling cells along the path with these cells.

### Teacher

Yes, the larger group contains at least 1008 cells. Looking upward from this bottom-row group, the cells above adjacent cells also form a small triangle. However, your concern about confusion is crucial: **the grouping of bottom-row cells alone does not establish that the entire small triangle avoids the sibling cells along the path**. We still need to check their positions.

Here is a six-row position diagram. `P` is the selected path, `C` is the unchosen sibling cell at each step, and `L` and `R` are the small triangles on either side of the final bottom-row pair:

```text
Row 1           P
Row 2         C   P
Row 3       ·   P   C
Row 4     ·   C   P   ·
Row 5   L   ·   P   C   R
Row 6 L   L   C   P   R   R
```

The final bottom-row pair is `C, P`. The two cells to its left support the small `L` triangle, and the two to its right support the small `R` triangle. First check the diagram: is every `C` outside `L` and `R`?

If so, combine this with your existing conclusion that **the top cell and all the `C` cells occupy exactly the smallest set of numbers**. What restriction does that impose on the values in the small side triangles? This diagram only shows the positions for one particular path; we will then need to consider whether the same holds for every path.

## Round 6

### Student

All the C cells in the diagram are outside L and R; the picture really clears up the confusion. So the two small triangles cannot use 1 to 2018 again, and every number in them is at least 2019. But I have only checked this diagram. If the path keeps moving to one side, could a C enter a side triangle? I tried to think about it: the path can only move one position per row, so it seems it cannot suddenly go in and return to that final bottom-row pair, but I cannot explain it clearly. Could you use a path that keeps going left to explain why they always stay outside? Also, once all the numbers are at least 2019, are we comparing whether the differences inside the small triangle can still be that large?

### Teacher

Your intuition is right: each time the path goes down a row, the column number can only stay the same or increase by 1. Thus the location of the final bottom-row pair constrains positions in every earlier row.

First consider **always going left**, as you suggested. Choosing the lower-left cell all the way from the top keeps the path in column 1; the unchosen sibling `C` is in column 2 of each row. The final pair occupies columns 1, 2 in the bottom row. There is no side triangle on the left, and the right side triangle starts at column 3 of the bottom row. Its left boundary remains in column 3 as it narrows upward, so all the `C` cells lie to its left.

The same positional relationship explains an arbitrary path. Suppose the final pair occupies columns \(p\), \(p+1\) of the bottom row; consider a row \(k\) rows above it:

- The path cell and its sibling `C` in this row both lie between columns \(p-k\) and \(p+1\). Their common parent must still follow the path to column \(p\) of the penultimate row, and it can move right by at most one column per row.
- The left small triangle extends rightward only to column \(p-k-1\) in this row; the right small triangle starts at column \(p+2\).

Thus both side triangles avoid the path cells and `C`. The top cell is outside them as well. Since all numbers are distinct in the original problem, and the top cell and all the `C` cells already use every number from 1 to 2018, every number in the side triangles is at least 2019.

As for the next comparison: **follow another path that always chooses the larger child cell inside the side triangle with at least 1008 rows**. Its bottom endpoint again equals the top cell plus the sibling cells along the way. This time, all these summands are at least 2019 and distinct. Try calculating: if we take a 1008-row small triangle within it, what is the minimum sum of those 1008 summands? Then compare it with the largest number allowed in the original triangle.

## Round 7

### Student

I can match the always-left example: C is in column 2, and the right triangle starts in column 3. For the general column argument, I still need to look at your formulas and cannot rewrite it myself yet. I can calculate the second path: 1008 distinct numbers all at least 2019 have minimum sum 2019 through 3026. Each pair totals 5045, and there are 504 pairs, totaling 2542680, which exceeds 2037171. So, assuming the original triangle exists, this side path produces a bottom endpoint outside the allowed range, a contradiction; the original triangle does not exist. Is that the right chain of reasoning? One more small question: if the side triangle has more than 1008 rows, can we take its first 1008 rows from the top, since all these cells still have values at least 2019?

### Teacher

Your whole argument is correct: assuming the original triangle exists, we can find a complete small triangle with at least 1008 rows on one side; following the larger child cells downward again yields a bottom endpoint at least 2542680, exceeding the maximum allowed value of 2037171 and producing a contradiction.

Your proposed truncation also works: **take the first 1008 rows from the top of the side triangle**. They still form a complete 1008-row number triangle, retaining every relation between an upper cell and the two adjacent cells below it. The selected cells still belong to the original side triangle, so their values are all at least 2019 and distinct.

You can now connect the steps leading to the numerical contradiction. The column argument explaining why an arbitrary path avoids the side regions still needs more practice; it justifies the claim that “all numbers in the side triangle exceed 2018.”

### Student

I will stop here today. I can check the rules with a small triangle and follow the two paths to calculate the numerical contradiction. For the part about an arbitrary path avoiding the side regions, I still need the column explanation in front of me and cannot claim I can prove it independently. Diagrams and one direction at a time are easier to follow, and the example allowing repeats helped me see why the distinctness condition cannot be left out.

### Teacher

This teaching session has been confirmed as ended.
