# P03 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P03 |

## Round 1

### Student

Teacher, let me first confirm: with two rows, putting 1, 3 below gives 2 above, using all of 1 to 3; that meets the rules, right? But directly trying numbers for 2018 rows is far too much. I usually calculate problems quickly, but here I still cannot see where to begin judging existence or nonexistence. Could I first try a small example, then get a hint about what to observe? Please do not give the complete answer yet.

### Teacher

Yes, your two-row example meets the requirements: bottom 1, 3 and top |1−3|=2 use each of 1 to 3 exactly once.

Next try **three rows**: use each of 1 to 6 once and see whether you can arrange a valid number triangle. Where do you plan to start? After trying, also describe what you noticed.

## Round 2

### Student

I started at the bottom because that determines the numbers above. First I tried 1, 6, 2, giving middle 5, 4 and top 1, a repetition; changing to 1, 6, 3 gives middle 5, 3, another repetition. But bottom 6, 1, 4 gives middle 5, 3 and top 2, exactly 1 to 6. So three rows can also be arranged. I also noticed that 6 must be at the bottom because the difference of two positive numbers no greater than 6 cannot be 6. Is this observation useful for 2018 rows? Would continuing to try four rows merely be relying on luck?

### Teacher

Your three-row construction is correct, as is your observation about 6: above the bottom, it would have to be the difference between two smaller positive integers, which is impossible. The same reasoning applies to the maximum with 2018 rows.

Four rows can help explore patterns, but finding a four-row example alone still cannot establish whether 2018 rows exist. You have the clue of the maximum's position: **how could you use it next to find a restriction also useful for larger row counts?**

## Round 3

### Student

Calling the maximum M and its neighbor a, M−a appears above, so those two numbers sum to M. In the three-row example, 6 is beside 1 with 5 above. If M is in the bottom middle, both sides allow such pairings. But I still cannot see why these pairings would fail to fit, and M may be at the edge too. Your question tells me to seek restrictions but still does not make clear where to check. Could you use my three-row triangle to identify a quantity to compare next? Just one key hint, then I will try myself.

### Teacher

Your boundary case matters: when the maximum is at an edge, we indeed cannot rely on pairings on both sides.

You have found **6=1+5** in the three-row triangle. Can you find similar additive relationships in it and try connecting them? Try in your own way first and just write the equations you discover.

## Round 4

### Student

I wrote 6=1+5, 4=1+3, and 5=3+2. Substituting the third into the first gives 6=1+3+2; using 1+3=4 then gives 6=4+2. This connects the triangle's relationships. But it is still some numbers summing to others, and I do not know whether to compare total sums or find repetition. Could you specify what restriction these equations are meant to prove? Continually asking me to look again makes me feel I am guessing which kind of equation you want.

### Teacher

You are right; I did not clarify the exploration's goal, leaving you to guess what I wanted. Your equations and substitutions are correct.

We want to find **what restrictions a number triangle's number distribution must satisfy if it exists**, then see whether this helps judge 2018 rows.

You now have 6=1+3+2 and 6=4+2. Which seems likelier to help formulate a necessary condition for triangles with more rows? Explain your thinking first, without rushing to prove it.

## Round 5

### Student

I would choose 6=1+3+2 because the right side has three numbers, suggesting more rows might split into more positive terms, whose sum still cannot exceed the maximum. But that is only a guess; 6=4+2 is also right, and I cannot say why the former must be chosen. The goal is clearer now, but I still cannot connect the equations into a condition holding for all triangles. Please demonstrate a key connection directly, such as how to choose the positions of those three numbers and why another bottom order permits it too; then leave a small variation for me to check.

### Teacher

Your conjecture has a clear direction: focus on the number of positive terms on the right and their sum's relationship to the maximum.

First draw your three-row triangle:

```text
    2
   5  3
  6  1  4
```

You already have **6=2+3+1**. Looking at the positions, can you start at the top 2, follow the same selection rule downward through 5 to 6, then check how the unvisited adjacent cell at each step relates to the equation?

Once you find the rule, try reversing the bottom row's left-right order and see whether it still applies.

## Round 6

### Student

Putting the diagram and positions together makes it clear this time: always move to the larger lower number. From 2 to 5, the unchosen number is 3, so 5=2+3; from 5 to 6, it is 1, so 6=5+1=2+3+1. Reversing the bottom gives 4, 1, 6, with middle 3, 5; the path is still 2→5→6, now moving right, with the same equation. Because the upper cell is the difference, the larger number always equals the upper plus the smaller; the rule does not depend on left and right. For n rows, some bottom number should equal a sum of n positive numbers from different positions with no repeated numbers. Is their sum therefore at least 1 to n? For 2018 rows this minimum is exactly 2037171. Is that what we use next?

### Teacher

Yes, exactly! Your path rule and calculations are correct: the endpoint equals a sum of 2018 distinct positive integers and is therefore at least 2037171.

Combining this with the permitted number range, can you determine the bottom endpoint? What restriction does that impose on the 2018 summands?

## Round 7

### Student

The endpoint cannot exceed 2037171 and is at least that, so it must equal 2037171. The 2018 summands must be exactly 1 to 2018: ordering them by size, the kth is at least k, and any larger term makes the total exceed it. Thus the top and the unchosen smaller number in each row are no greater than 2018. But that is still no contradiction; the three-row example attains equality and can be arranged. For 2018 rows, must we examine further differences between unvisited cells? I have not connected that step; equality alone does not establish nonexistence.

### Teacher

Yes, your equality argument holds, and your judgment is rigorous: **equality itself is no contradiction**, as the three-row triangle demonstrates.

Examining the other cells is a direction worth trying. Since 1 to 2018 occupy precisely the positions you identified, what restriction do all other numbers share? How could you use it to continue seeking a contradiction?

## Round 8

### Student

All other cells exceed 2018. But two large numbers can have a small difference, such as 2020 and 2019 differing by 1, so we cannot just say subtracting large numbers stays large. I want to find two already-forced numbers no greater than 2018 adjacent below, making the upper number less than 2018 and repeating an exhausted small number; but there is only one such small cell per row, not necessarily adjacent. Could you tell me whether to look at path turns or some bottom rows? Locating positions with the earlier diagram helped, and I hope this step's positions can be specified too.

### Teacher

Your counterexample is persuasive: the difference of two large numbers need not be large, and the existence of adjacent small cells still needs proof.

You previously obtained a lower bound through addition along a path. Knowing now that all other cells exceed 2018, could you reuse such a path within some region to turn "large numbers" into a sum? First consider what kind of region is needed to keep all required path cells inside it.

## Round 9

### Student

It should be an entire small triangular number triangle, rather than scattered large numbers. If a k-row small triangle has all numbers greater than 2018, the same path makes its endpoint a sum of k distinct numbers greater than 2018, at least 2019+2020+…+(2018+k). But how can we guarantee such a large region? Might the original path and its small sibling cells block it? I still do not know. Could you draw a small schematic demonstrating how to take a complete small triangle avoiding the small cells? Merely asking what region I need still does not let me find it.

### Teacher

Your lower-bound derivation is correct. The difficulty is precisely that a bottom segment of large numbers alone does not guarantee the small triangle above also avoids all small numbers.

First draw a six-row **positional schematic**. Suppose the original path's final child pair is in the bottom middle, marked `×`; all other symbols currently indicate positions only:

```text
          ·
         · ·
        · · ·
       · · · ·
      · · · · ·
     · · × × · ·
```

Can you find complete small triangles supported above the two left bottom `·` cells and the two right ones? Then consider what restrictions apply to the path positions in upper rows if it must reach the middle `× ×`. First try drawing several paths.

## Round 10

### Student

The left bottom cells 1, 2 and cell 1 of row five form two rows; the right cells 5, 6 and cell 5 of row five also form two. The original path must occupy cell 3 in row five to face bottom cells 3, 4, so it avoids these triangles. I still need to check whether the unchosen small sibling can enter: the other sibling of the path in row five can only be cell 2 or 4, not 1 or 5. So both small triangles here really contain no small numbers. Generalizing, removing those two × cells from the bottom leaves 2016 cells on both sides, with at least 1008 on one. Can we then take a 1008-row triangle containing only large numbers? I want to use 1008×2019 as a lower bound, but it is only 2035152, slightly short; the extra increment from distinctness of those large numbers would exceed 2037171. Is that connected correctly?

### Teacher

This looks promising: the two side bases contain 2016 cells total, so the larger has at least 1008. Your multiplication and the idea of raising the lower bound using distinctness are also correct.

One positional detail still needs complete proof: in six rows you checked the row-five sibling; for 2018 rows, how can you ensure **every row's** sibling stays outside the small side triangles? Reuse the condition of "reaching the final pair" and consider the possible upper positions.

Once that is complete, calculate your increment \(0+1+\cdots+1007\) to find exactly how much the lower bound exceeds the permitted maximum.

## Round 11

### Student

I number cells left to right. If the final pair occupies cells j, j+1, the penultimate path cell is in column j. Each downward step keeps the column unchanged or adds 1, so going backward upward keeps it unchanged or subtracts 1. The sibling in row r can be no further left than j−(2018−r) and no further right than j+1. The rightmost left-triangle cell in row r is j−1−(2018−r), even further left than that bound; the right triangle starts at j+2 in every row. Thus no row's sibling enters, and the top is outside both side triangles too. The small triangle therefore contains only large numbers. The increment is 1007×1008÷2=507528; adding 2035152 gives 2542680, exceeding 2037171 by 505509. So assuming a triangle exists gives a contradiction: 2018 rows do not exist. I feel this numbered explanation works. Please check whether I missed a boundary case; if the final pair is at an edge, one side is empty and the other larger, so it should still apply, right?

### Teacher

I checked: your column bounds and calculations are correct, **including the boundary cases**. With the final pair at an edge, one side is empty and the other has 2016 cells, still allowing a side triangle of at least 1008 rows. You proved all small numbers lie outside it, so descending through larger children inside it gives a lower bound exceeding the whole-triangle maximum, establishing the contradiction.

Here row \(r\) for sibling cells satisfies \(2\le r\le2018\); the top is checked separately and, as you said, lies outside both side triangles. This makes the positional argument's boundaries explicit.

Looking back, summarize in a few sentences: **what conditions does equality on the first path create for the second path?** How has the approach changed from initially trying small arrangements directly?

### Student

The first equality locks all of 1 to 2018 into the top and each row's sibling, making every number in a side triangle avoiding those positions greater than 2018. On the second path, each summand starts larger and is also distinct, so the endpoint exceeds the upper bound. Initially, trial arrangements only showed that a particular small triangle exists; now we assume the large one exists and find restrictions it must satisfy but cannot. The two- and three-row examples helped me understand the rule but cannot replace this proof. I was stuck on positions in the middle and connected it only after diagrams and column numbers. Now I can explain why reflection and edge cases also hold. I will stop here for this problem today.

### Teacher

This teaching session has been confirmed as ended.
