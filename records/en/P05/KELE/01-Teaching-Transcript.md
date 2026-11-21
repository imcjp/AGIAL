# P05 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | KELE |
| Participant ID | P05 |

## Round 1

### Student

Teacher, I want to confirm the rules: with two rows, putting 1 and 3 below gives 2 above, using 1, 2, 3 exactly once each. That meets the requirements, right? But I do not know where to start judging existence for 2018 rows. Could you give me a smaller example to try myself and help me identify what to observe?

### Teacher

Yes, your two-row arrangement meets the requirements: the upper cell is |1−3|=2, and the three cells use 1, 2, 3 exactly once each.

Next try three rows: these have 6 cells. Use **1 to 6 exactly once each**, with every upper cell equal to the absolute difference of its two adjacent lower cells.

As you try, notice the relationship between each upper cell and the larger number below it. Can you construct a suitable three-row number triangle?

## Round 2

### Student

I first tried bottom row 1, 6, 3, then 5, 3 above and 2 at the top, but 3 repeated. Changing the bottom to 1, 6, 4 gives 5, 2 above and 3 at the top, using all of 1 to 6. That should work, right? I noticed an upper cell is always less than the larger lower number because a positive number is subtracted. Thus 6 cannot be in the upper two rows and must be at the bottom. How can this observation apply to 2018 rows?

### Teacher

Yes, your three-row arrangement fully meets the requirements:

```text
    3
   5 2
  1 6 4
```

Your observation is also correct: both lower numbers are positive, so the upper cell is less than the larger of them. Regardless of the number of rows, the triangle’s largest number must therefore be in the bottom row. For 2018 rows, this gives a direction to pursue.

Consider upper cell 5 and the 1, 6 beneath it in your triangle: how would you rewrite “5 is the difference of 6 and 1” to **express the larger number 6 using addition**?

## Round 3

### Student

We can write 6=5+1. Thus the larger lower number equals the upper cell plus the smaller lower number. I can rewrite that, but still do not see how it judges whether a large triangle is impossible or can be constructed. Should we start at the top and keep choosing the larger lower number? If so, could you give me a small next step to try writing the relationship? Rewriting only one number each time leaves me unsure where these steps ultimately connect.

### Teacher

Yes, your proposed route is exactly to start at the top and always choose the larger lower number. The goal is to write **some bottom-row number** as a sum of several numbers along the way and examine the constraints on that sum.

Try your three-row triangle:

```text
    3
   5 2
  1 6 4
```

Following larger numbers gives **3 → 5 → 6**. The first step gives 5=3+2, and you already wrote the second as 6=5+1.

Connecting them, can you write bottom number 6 as the top cell plus the other two numbers along the way?

## Round 4

### Student

Substitution gives 6=3+2+1. Likewise, 2018 rows would give a bottom number equal to a sum of 2018 numbers: the top plus the smaller neighboring number at each step, right? These cells are distinct, so the minimum must be 1+2+…+2018. I calculate the sum as 2018×2019÷2=2037171, exactly the problem’s maximum. This only gives equality, apparently no contradiction. Have I missed a condition?

### Teacher

Your generalization and calculation are correct, and you perceptively noticed that **we have equality, not yet a contradiction**.

However, equality strongly constrains those 2018 summands. The path endpoint is a number in the triangle, hence at most 2037171; you calculated that, as a sum of 2018 distinct positive integers, it is also at least 2037171.

When these 2018 distinct positive integers have exactly the minimum sum, which 2018 numbers can they be?

## Round 5

### Student

Only 1 to 2018. Sorting the summands, the first is at least 1, the second at least 2, and likewise afterward; if any exceeded its corresponding index, the total would exceed the minimum. Thus the top and smaller neighboring numbers along the way do not exceed 2018, and the endpoint can only be 2037171. But the three-row example also achieves equality and can be constructed, so I still do not know why 2018 rows fail. Should we look next at the path numbers or the remaining unused cells? Could you give me a specific place to compare?

### Teacher

Your reasoning is correct: equality itself is not a contradiction, but shows that **all of 1 to 2018 are already occupied by the top and the smaller child cells along the way**. Next examine the remaining cells and seek a sufficiently large region containing none of these small numbers.

Specifically, consider **the final child pair** before the path reaches the bottom. There are bottom cells on either side, and each side supports a small triangle above it. Since the path and the other child along the way lead toward this final pair, those two side triangles avoid the cells just used as summands.

There are 2018 bottom cells. Excluding the final pair leaves 2016 on both sides altogether. **How many bottom cells must the larger side have at least?**

## Round 6

### Student

At least 1008, because 2016÷2=1008. But I still cannot visualize the side triangles: if the path turns left and right, why cannot an earlier smaller child beside it lie in this triangle? I cannot just memorize that claim. Could you use a six-row schematic with indexed cells to show the final pair and which region must avoid the summands? This section is harder than the algebra, so I want to see the positions first.

### Teacher

1008 is correct. Your position question is necessary: **the path turns, so we must explain why the side regions avoid each step’s summand.**

First number each row of a six-row triangle from left to right. Suppose the path finally passes through cell 3 in row five, making the final pair **cells 3, 4** in row six:

```text
Row 1           1
Row 2          1 2
Row 3         1 2 3
Row 4        1 2 3 4
Row 5       1 2 [3] 4 5
Row 6      L L [3 4] R R
             ↑       ↑
         Two left cells  Two right cells
```

Brackets mark the final pair and the cell above it. Bottom cells 1, 2 on the left support a two-row small triangle: cells 1, 2 of row six and cell 1 of row five. Similarly, the right consists of cells 5, 6 of row six and cell 5 of row five.

The key is where a cell can reach downward. **Cell \(j\) in row \(r\)** can reach only cells \(j\) through \(j+5-r\) in row five: each downward row leaves the column index unchanged or increases it by one.

The path must reach cell 3 in row five. If it passes through cell \(j\) in row \(r\), necessarily

\[
j\le 3\le j+5-r.
\]

Its two children in the next row have columns \(j\), \(j+1\). Even when one is chosen and the other becomes a summand, both cells remain in the range leading to the final pair.

But every fifth-row descendant of a left-triangle cell lies left of cell 3, and every fifth-row descendant of a right-triangle cell lies right of cell 3. Thus these side cells can be neither path cells nor neighboring summand cells. The top also lies outside the small side triangles.

Return to the six-row diagram and consider cell 1 in row five. Its bottom children are cells 1, 2. Can it reach cell 3 or 4 of the final pair downward?

## Round 7

### Student

Cell 1 in row five can reach only cells 1, 2 of row six, not 3, 4. The diagram makes this clearer than “side region” alone. But checking it, I noticed cell 2 in row five also cannot reach cell 3 in row five, yet could be the other child of row four cell 2 and serve as a summand. So saying its fifth-row descendants lie left of 3 seems insufficient. I think we should examine bottom-row descendants: all bottom descendants of a side-triangle cell avoid 3, 4, whereas the other child of a path cell can reach at least one of 3, 4, thereby excluding it. Is that revised explanation correct? If so, every number in the 1008-row small triangle exceeds 2018. Do we next add downward along larger numbers again?

### Teacher

Yes, your correction is right. My earlier use of “fifth-row descendants lying on one side of cell 3” to exclude neighboring summands was insufficient. Your example of cell 2 in row five identifies the issue precisely.

Using **bottom-row descendants** works: a path cell can reach cell 3 in row five, so of its children, the chosen one can reach a cell in the final pair, and the other child can also reach at least one cell of that pair. Every bottom descendant of a side-triangle cell lies outside the final pair, so such cells cannot be these summands. The top also lies outside the side regions.

Thus, assuming the large triangle exists, the small side triangles avoid the already occupied 1 to 2018, and all their numbers exceed 2018.

Your next idea is correct too: take a **1008-row** small triangle on the larger side, start at its top, and again follow larger children downward. As before, the endpoint equals the top plus the smaller children along the way: this time a sum of 1008 distinct positive integers, all greater than 2018.

What is its minimum endpoint? Write it as a sum of consecutive integers and compare with the whole triangle’s maximum, 2037171.

## Round 8

### Student

For 1008 distinct integers greater than 2018, the minimum values are 2019 through 3026. Their sum is (2019+3026)×1008÷2=5045×504=2542680, greater than 2037171. Assuming the large triangle exists would thus make one bottom number exceed its maximum, a contradiction, so it does not exist. The two larger-number paths now connect. Constructing three rows myself and substituting helped earlier; I understood positions better only after the indexing and correction to bottom descendants. One variation to check: if only distinctness is required, without requiring 1 to 2037171, this proof cannot establish nonexistence, because the endpoint has no such upper bound and the first step cannot force exactly 1 to 2018 as summands, right?

### Teacher

Yes, your contradiction and judgment about the changed condition are correct.

In the original problem, the first larger-child path uses the equality between the minimum sum of distinct positive integers and the whole triangle’s maximum to force summands exactly 1 to 2018. Bottom-row descendants then show that side triangles avoid them, and the second descent gives a bottom number at least **2542680**, exceeding the allowed maximum **2037171**. Thus the original number triangle does not exist.

If distinct positive integers are still required but not specifically 1 to 2037171, both changes you identified hold: the first sum still has a lower bound, but lacks the original upper bound forcing equality; the final step also cannot use 2037171 as a global upper bound to create a contradiction. Therefore **the original proof cannot establish nonexistence for this variation**. Failure of the original proof alone also cannot establish that the variation necessarily exists.

### Student

I will stop here today. I can organize the original contradiction using two path sums and know that removing the numerical range only invalidates the original proof, without directly establishing existence for the variation. The indexed diagram and bottom-descendant checks supplied the positional reasoning, but with a differently drawn path I might still need a new diagram to check, so I cannot say I am proficient yet. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
