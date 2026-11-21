# P04 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | StratL |
| Participant ID | P04 |

## Round 1

### Student

Teacher, I want to try two rows first: put 1, 3 below and 2 above, using 1 to 3 once each. That should work, right? For three rows I tried 1, 5, 6 below, giving 4, 1 in the middle, repeating 1. I still do not know how to choose bottom numbers to determine whether 2018 rows exist. Can we start with this small example and see what to notice?

### Teacher

Your two-row example meets the conditions, and your three-row attempt identified the problem of repetition.

We can continue exploring small examples: how would you adjust the bottom numbers of the three-row triangle? Try once and explain how you chose them and what changed in the result.

## Round 2

### Student

I replaced the bottom 1 with 2, trying 2, 5, 6: the middle is 3, 1, and the top is 2, another repetition, this time of 2. I wanted to avoid the middle row repeating bottom numbers, but the top repeats one instead. One failed example seems to show only that this arrangement fails, not that all three-row arrangements fail. Could you give me a clue for choosing numbers? Changing them one at a time leaves me unsure where to try.

### Teacher

You are right: a failed arrangement excludes only that arrangement. You have also clarified your selection approach: first avoid repetition between middle and bottom rows, then check the top cell.

Repeatedly changing numbers can indeed be disorienting. Before changing again, could you review the two attempts and consider how to turn “checking an arrangement” into a more systematic search? Explain what you would fix or record first.

## Round 3

### Student

I could make a table recording bottom, middle, top, and repeated numbers. For instance, fix the last two as 5, 6 and try 1, 2, 3, 4 first: we already calculated the first two; 3, 5, 6 gives 2, 1, then 1 at the top; 4, 5, 6 gives 1, 1, then 0. All four fail. But this only checks cases ending in 5, 6; many other orders remain. Recording does reduce repeated calculations, but after asking for selection clues, I still only know to keep checking. Could you demonstrate a specific observation that narrows the possibilities? One small step followed by a chance to apply it would be easier for me to follow.

### Teacher

You calculated all four cases correctly and identified the table’s limitation: it covers only bottom rows ending in 5, 6.

I hear that you want a specific observation to narrow the possibilities. Use your existing table first: in these four arrangements, **5 and 6 are adjacent** in the bottom row. What do their corresponding middle cells share? Which arrangements could that common feature exclude at once?

## Round 4

### Student

The difference of 5 and 6 is always 1. If 1 already appears elsewhere below, repetition is certain, as in 1, 5, 6, without calculating the top. But 2, 5, 6 does not immediately fail for this reason and needs further calculation, so this alone cannot exclude all four. I tried something different: 1, 6, 4 gives 5, 2 in the middle and 3 at the top, exactly all of 1 to 6! Your hint showed me we can check a fixed pair first. Now three rows work, but I still do not know how this relates to 2018 rows. Is there a constraint usable in every row? Could you give a specific example first?

### Teacher

Your three-row triangle works:

```text
    3
   5 2
  1 6 4
```

Your analysis of adjacent 5, 6 is also accurate: it excludes some arrangements, but cannot exclude all arrangements by itself.

To find a constraint usable in every row, consider this successful example. Starting at the top 3 and moving down through adjacent cells, can you choose a path you consider worth studying? Write relationships among its numbers and see whether they could generalize to more rows.

## Round 5

### Student

I choose 3→5→6, always choosing the larger of the two below. This path increases because 3=5−2 and 5=6−1, so the larger lower number must exceed the upper. It seems we can always follow larger numbers with more rows too. But 3→2→4 is not increasing throughout, so we cannot choose arbitrarily. I can explain this observation, but it gives only a path of 2018 numbers, while the problem has over two million numbers, which should still fit. I do not see how to establish impossibility or constructibility. Could you demonstrate how this path yields a quantitative constraint next?

### Teacher

Your judgment is correct: knowing only that the path increases is insufficient to show impossibility for 2018 rows. You have already written two relationships: \(3=5-2\), \(5=6-1\).

Try using them first: can you write the bottom endpoint \(6\) as the top cell \(3\) plus some other numbers? Then examine where those numbers lie in the triangle.

## Round 6

### Student

5=3+2 and 6=5+1, so 6=3+2+1. The 3 is the top, 2 is unchosen at the first step, and 1 at the second, one in each row. I can connect that hint: every downward step adds the unchosen neighboring number. With 2018 rows there would be the top plus 2017 such numbers, in different rows and therefore distinct. The minimum is then 1+2+…+2018, exactly the total cell count 2037171? I calculate the sum as 2018×2019÷2. Then the bottom number must equal 2037171, and the summands must be exactly 1 to 2018? Equality still seems not to contradict anything. Have I missed something?

### Teacher

That step is correct. Assuming such a triangle exists, these 2018 summands are distinct positive integers whose sum is at least \(1+2+\cdots+2018=2037171\), while the path’s bottom endpoint is at most the entire triangle’s maximum \(2037171\). Equality must hold and the summands must be exactly \(1\) to \(2018\).

You also noticed the key: **equality itself has not produced a contradiction**, but constrains the positions of these small numbers.

How would you next use the fact that “all of \(1\) to \(2018\) already occur in the top and sibling cells” to examine numbers elsewhere in the triangle?

## Round 7

### Student

All other cells must exceed 2018. I thought that if two small numbers are adjacent in one row, their difference is also less than 2018, so the small number above would already have been used elsewhere. But the selected sibling cells are one per row, not in the same row, and I do not know how to find adjacent small numbers. In my three-row example, top 3 and siblings 2, 1 are also in different rows, and it works, so using up small numbers alone cannot give a contradiction. Could you draw local positions with another row and point out exactly which two cells to consider? I am mainly stuck on positions, not the sum of the summands.

### Teacher

You are right: we cannot currently assume two adjacent small numbers in one row, and the three-row example also shows that “using up small numbers” alone is not a contradiction.

We can explore with a **position schematic**. This is not a completed number triangle; `P` marks path cells, `a` the unchosen sibling at that step, and `·` other cells:

```text
        P
       a P
      · P a
     · a P ·
    · · a P ·
```

This is one possible path, moving from a `P` to a `P` in the next row at each step. Can you find connected `·` cells forming a complete small triangle? Do they overlap any cells marked `a`?

## Round 8

### Student

I found the leftmost dot in row four and the two leftmost dots in row five: they form a complete small triangle without a or P. Drawing makes the positions much clearer. But three numbers all exceeding 2018 could still satisfy the difference relationship, right? For example, 5000 and 8000 differ by 3000, and all exceed 2018. Also, this diagram is only one path. If the path always goes left, those three dots might not remain in the bottom-left corner. I can locate cells in the diagram now, but cannot turn that into reasoning for all paths. Which relationship in this small triangle should we use next?

### Teacher

You found it correctly. Your example also shows that all three numbers exceeding 2018 does not prevent the difference relationship. This alone therefore cannot yield a contradiction.

Set aside the “all paths” question temporarily and consider your two-row small triangle. It also follows the number-triangle rules. Can you repeat the path choice used in the larger triangle within this one, and see what sum expresses its bottom endpoint?

## Round 9

### Student

Choose the larger lower number again. Using my numbers gives 8000=3000+5000. Both summands exceed 2018, so the bottom endpoint is at least 2019+2020=4039. I can apply that. But 4039 is much less than 2037171 and still gives no conflict. Many rows avoiding P and a might produce a larger sum, but I cannot judge how many rows remain or where to start. Could you directly explain how to expand this two-row example next? I can follow calculations one small step at a time, but currently do not know where these steps are heading.

### Teacher

Your calculation is correct: the two-row lower bound 4039 is far from sufficient for a contradiction. We need a **complete triangle with enough rows that avoids those small numbers**, then accumulate using your method.

First return to the bottom row and examine the adjacent pair involved in the final path step. Can you count the cells remaining on its left and right? If the final step changes position, does the total remaining on both sides change?

## Round 10

### Student

The bottom row is ·, ·, a, P, ·, so 2 remain on the left and 1 on the right, 3 altogether. Moving the pair still leaves 5−2=3. With 2018 rows, 2016 remain, so at least one side has 1008. I can calculate that. But I am still unsure why the entire triangle supported by these 1008 cells avoids every a higher up. The path turns, so looking only at the bottom might not suffice. Could you explain that directly? If all numbers exceed 2018, summing 1008 terms gives even 2018×1008 close to the maximum, and adding the extra amounts from distinctness may exceed it.

### Teacher

Your count is correct: 2016 cells remain outside the final pair, so at least one side has 1008. Your concern is crucial too: the path can turn, so the bottom row alone does not show that sibling cells above avoid the side triangles.

First focus on one positional relationship: at any path step, of the current cell’s two children, one is the next path cell and the other the sibling \(a\).

Now consider: starting at that sibling and following adjacent cells downward, could it reach the path’s bottom endpoint? If so, what does that imply about its position?

## Round 11

### Student

Some can and some cannot, I think. In your diagram, a on the left of row two can reach P in cell two of row three, then P in cell three of row four and P in cell four of row five. But a in row five is already at the bottom, so clearly cannot move downward to the P beside it. I therefore cannot claim every a reaches the bottom endpoint. I asked why the complete side triangle has no a, but now have to consider another path, which is hard to connect. Could you simply mark the side-triangle boundary on this diagram and explain why it remains valid when the path changes? If the earlier reasoning was insufficient, please say so directly.

### Teacher

You are right: a bottom sibling cannot move farther down to the adjacent path endpoint. My previous question did not connect properly: **we should consider the final child pair rather than require every sibling to reach the bottom \(P\)**. Counting bottom cells alone also indeed leaves unexplained why the side triangles avoid sibling cells above.

First mark the left triangle as `L` in the original diagram:

```text
        P
       a P
      · P a
     L a P ·
    L L a P ·
        └─┘
       Final pair
```

Could you try moving down from each `L` and see which bottom cells it can reach? Then look downward from the `a` cells in each row: how do their positions relate to the final pair? This might help us compare the two regional boundaries.

### Student

Let us stop here today. With L marked, I can see they reach only the two leftmost bottom cells, not the final pair. But I still have not worked out the general relationship between each row’s a and that boundary. I can follow and explain the larger-number path, expressing the bottom endpoint as a sum, and the positions of the small numbers under equality. I still cannot provide complete reasoning about whether 2018 rows can exist. Several times I wanted you to explain the step where I was stuck directly, but afterward I still had to keep finding the next point myself. It felt somewhat roundabout, and I want to stop and organize it first.

### Teacher

This teaching session has been confirmed as ended.
