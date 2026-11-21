# P02 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P02 |

## Round 1

### Student

Teacher, this triangle is too large. I want to try two lower numbers first. For example, putting 2 and 5 below means putting 3 above because 5 minus 2 is 3, right? But that leaves 1 and 4 unused, so is it still invalid? Please explain one thing at a time first and give me a very small triangle to try.

### Teacher

Yes, the upper cell for 2 and 5 is 3; but if the problem requires using 1 to 4, it is still incomplete.

Try a small two-row triangle first: use 1, 2, 3 once each, making the upper cell equal the absolute difference of the two below. How would you arrange it?

## Round 2

### Student

I put 1 and 3 below and 2 above, since 3 minus 1 equals 2. All three numbers are used without repetitions. I can arrange a small one like this. But if two rows work, do 2018 rows also work? I do not know how to see that from this small one. Could you guide me through the next small step?

### Teacher

You understand the "two-row relationship" now. The next small step is to apply it twice consecutively.

Try this three-row triangle:

```text
      3
    2   5
  4   6   1
```

Do not look at the answer yet: with 6 in the bottom middle, why must the left and right numbers be 4 and 1, respectively?

## Round 3

### Student

Calculating from the diagram, 6 minus 4 is 2, 6 minus 1 is 5, and 5 minus 2 is 3. All of 1 to 6 are there too. I can check it, but 4 and 1 are already written in the diagram, so I have not thought of them myself. By "must," do you mean because 2 and 5 are already above them? Could you leave a blank for me to fill and explain how this relates to 2018 rows?

### Teacher

Yes, precisely because the middle row contains 2 and 5: they are calculated from the adjacent bottom pairs, respectively.

Here is a blank for you:

```text
      3
    2   5
  □   6   1
```

Look only at the left group: to make `6 − □ = 2`, what goes in the blank? This is the same local rule for "working backward from an upper number to lower numbers" in the large triangle.

## Round 4

### Student

4, because 6 minus 4 is 2. I can do this step; looking at just one group is clearer. But I still do not know whether the large triangle can be arranged: even filling one blank correctly, might other places repeat? Could you first tell me what to check so we do not keep trying one by one? Please do not give me lots of formulas at once.

### Teacher

First check one overall issue: whether any numbers repeat or are missing. The small triangle uses exactly 1 to 6 once each; the large triangle must likewise contain "as many distinct numbers as there are cells."

For the next small step, look only at a path from top to bottom: always choose the larger lower cell and observe whether the endpoint can be expressed as a sum of the "other cell" numbers along the path. First locate this path in the three-row triangle above.

## Round 5

### Student

Starting at 3, I choose the larger 5 from 2 and 5, then 6 from 6 and 1. Is it the path 3, 5, 6? The unchosen siblings are 2 and 1, but 2 plus 1 equals 3, not the bottom 6. Did I forget the top 3? This part is a bit confusing. Could you label only the numbers to add in the diagram?

### Teacher

Your path is correct: **3 → 5 → 6**.

We add the "unchosen number" at each step, but must also include the top:

```text
          [3]
        +2   *5
      *4   *6   +1
```

The actual equations are:

- `5 = 3 + 2`
- `6 = 5 + 1 = 3 + 2 + 1`

Thus the endpoint 6 indeed equals **the top 3 plus the unchosen siblings 2 and 1**.

## Round 6

### Student

Breaking it into 5 equals 3 plus 2, then adding 1, lets me connect it. Replacing the lower numbers with 2 and 3 and the upper with 1, choosing 3 gives 1 plus 2 equals 3, also correct. But how does this path calculating correctly let us judge all 2018 rows? I still cannot see where something will not fit or will repeat. Could you next tell me only what this path constrains?

### Teacher

This path constrains the following: it selects **one number from each row**, giving \(n\) distinct positive integers.

Thus in a complete \(n\)-row triangle using 1 to \(N\), their sum is at least:

\[
1+2+\cdots+n
\]

while the endpoint cannot exceed the whole-triangle maximum \(N\). Therefore this path forces its selected numbers to be the smallest \(n\) numbers: **1 to \(n\)**.

This is not yet a contradiction, only a strong restriction on the whole triangle.

## Round 7

### Student

I am mixing up n and N again. With three rows, the summands were 3, 2, 1, summing to 6. Replacing 3 with 4 makes 4 plus 2 plus 1 equal 7, exceeding 6 and therefore impossible. Is that what you mean? But I cannot calculate the sum of 2018 numbers. Please write out the two large numbers clearly, then explain why not even one number can be replaced.

### Teacher

Yes, you understand the three-row example correctly:

- \(n\): the row count. With three rows, \(n=3\).
- \(N\): the total cell count. With three rows, \(N=1+2+3=6\).

The endpoint is the sum of these \(n\) numbers on the path. With three rows:

\[
3+2+1=6=N
\]

Replacing 3 with 4 gives:

\[
4+2+1=7>N
\]

which is impossible because the endpoint is itself a number in the triangle and cannot exceed \(N\).

With 2018 rows:

\[
N=1+2+\cdots+2018
=\frac{2018\times2019}{2}
=2,037,171
\]

The path has 2018 distinct positive integers, whose minimum sum is exactly:

\[
1+2+\cdots+2018=N
\]

Thus they must be exactly **1 to 2018**; replacing any one makes the sum exceed \(N\).

## Round 8

### Student

I remember the row count is 2018 and the largest number is 2037171. I still cannot do that multiplication and division myself, but I can follow the small example: we already used the smallest three, so replacing one with a larger number exceeds the limit. By numbers on the path, do you mean the summands? The visited 3, 5, 6 are not 1, 2, 3. This restriction is still no contradiction, so which two things cannot both hold next?

### Teacher

Yes, you have distinguished them:

- The visited path: for example \(3\to5\to6\);
- The actual summands: the unchosen number at each step plus the top, giving \(3,2,1\) in the small example.

The next conflict is between these two conditions:

1. The main path already occupies \(1\) to \(n\), so other positions can contain only numbers greater than \(n\).
2. A relatively large side triangle can still be found beside the main path; following another path within it also makes its endpoint a sum of several numbers.

All those numbers exceed \(n\), forcing the new endpoint to become too large and exceed the whole-triangle maximum \(N\).

## Round 9

### Student

I cannot see the triangle beside it. The three-row triangle clearly works, even though 4, 5, 6 beside the path exceed 3. Why does it not exceed the limit? Does it require enough rows? Could you label the side region in a small diagram, or specify the minimum number of summands for 2018 rows? Just saying it will become too large is not enough evidence for me yet.

### Teacher

Yes, enough rows are needed; with three rows, the side triangle is too small, containing only one number, so there is no contradiction.

Think of the main path as going from the top to the final pair of bottom cells:

```text
                 Main path
                    ↓
              ……  ● ●
Left side triangle  ◢   ● ●   ◣  Right side triangle
```

The main path first forces occupation of all \(1\) to \(n\), so all numbers in the side triangles exceed \(n\).

For 2018 rows, the larger side triangle has at least

\[
\left\lceil\frac{2018-2}{2}\right\rceil=1008
\]

rows. A path within it therefore adds at least 1008 numbers:

\[
2019+2020+\cdots+3026=2,542,680
\]

But the whole-triangle maximum is only:

\[
N=2,037,171
\]

Thus the endpoint inside this side triangle is forced above the whole-triangle maximum, a contradiction.

## Round 10

### Student

Comparing the totals, I see that 2542680 exceeds 2037171, so if we really must add that many numbers, it will not fit. I cannot calculate these sums myself yet. But I cannot understand this diagram. Why must there be 1008 rows on the side? Might it touch cells already using 1 to 2018? Could you draw five or six rows clearly, labeling only the occupied small-number cells and one remaining region? I want to understand just this point first.

### Teacher

First consider a six-row schematic. Suppose the main path finally lands between the two middle bottom cells:

```text
                 ×
               ×   ×
             ×   ×   ×
           L  ×   ×   R
         L   L  ×   ×  R
       L   L   L  ×   ×  R
```

Here:

- `×` represents the "strip" formed by the main path and its neighbors; the numbers \(1\) to \(6\) forced to be occupied all lie here.
- L and R are the triangles on the main path's left and right, avoiding these small numbers.
- With six rows, the larger side has at least  
  \[
  \left\lceil\frac{6-2}{2}\right\rceil=2
  \]
  rows.

Thus the side triangle avoids the previously used \(1\) to \(6\), so its numbers must exceed 6. With 2018 rows, the same geometric relationship increases the side triangle's minimum row count to 1008, producing the earlier numerical contradiction.

## Round 11

### Student

Counting the left side from one L to two Ls and then three Ls, it seems to have three rows; you said at least two, and three is also at least two, which I understand. But row three above is all crosses, so I still cannot find our actual path. If it turns left and right, must such a region still remain? Could you show the actually visited cells as arrows and the summands beside them as plus signs? Please do not make them all crosses; I confuse them easily.

### Teacher

Yes. Use `P` for the actual path and `+` for unvisited cells that may participate in accumulation:

```text
              P1
            +    P2
          P3    +    +
        +    P4    +    +
      +    +    P5    +    +
    +    +    +    P6    + 
```

This path is:

\[
P1\to P2\to P3\to P4\to P5\to P6
\]

It can sometimes move right and sometimes remain near the same position; however it moves, a strip forms around the path. To its left or right there is at least one complete side triangle; the continuous `+` region in the diagram is that triangle.

With six rows it has at least 2 rows; with 2018 rows, the larger region has at least 1008 rows.

## Round 12

### Student

Following the diagram, P2 is on the right of row two, so its adjacent children should be the middle and right cells of row three, right? But P3 is at the far left, so I cannot make that step. Also, all the other cells have plus signs, so again I cannot tell which ones really need adding. Could you fix only this six-row diagram, use dots for ordinary cells, and plus signs only for actual summands? I still cannot say I understand the side triangle.

### Teacher

You are right; the previous path was drawn incorrectly. Correct adjacent choices can be drawn as follows:

```text
              P1
            P2    +
          +    P3    ·
        ·    P4    +    ·
      ·    +    P5    ·    ·
    ·    ·    P6    +    ·    ·
```

Here:

- `P1 → P2 → P3 → P4 → P5 → P6` is the actual path;
- Each `+` is the unchosen cell at that step that must be included in the sum;
- `·` is just an ordinary other cell.

For example:

\[
P2=P1+(\text{the + in row 2})
\]

\[
P3=P2+(\text{the + in row 3})
\]

Thus the path can change direction, but every step must reach one of the two adjacent cells directly below. The previous diagram indeed made the path skip a cell.

## Round 13

### Student

Now I can follow P, with every step adjacent. But the right dot in row three has a plus below it; the far-right dot in row four has two dots below it, and row five also has dots further below. Should we circle a small region starting at the far right of row four? I want to count myself. Just tell me which cell starts the region and which endpoints it reaches at the bottom, without mentioning 1008 again yet.

### Teacher

First look at this region on the left: it starts at **the leftmost dot of row five** and expands downward to the two leftmost dots of the bottom row:

```text
      Row five:   ·   +   P5   ·   ·
      Row six:  ·   ·   P6    +   ·   ·
                └────┘
```

Circle:

- The leftmost 1 cell in row five;
- The leftmost 2 cells in row six.

These three cells form a small two-row triangle, all outside both the main path `P` and the `+` cells beside it.

## Round 14

### Student

This time I can circle one cell on the left and two below it, making two rows. These three dots are neither P nor plus signs, so they cannot use 1 to 6 again; I can connect that now. If we put 7 at the top of this piece and 8 in one lower cell, the other must be 15 for the difference to be 7, which still does not exceed 21. This six-row diagram only helps me see positions; it is not proving six rows impossible, right? But I still cannot judge for myself how to guarantee a sufficiently large region remains after changing paths.

### Teacher

Yes, this six-row diagram mainly clarifies positions and **cannot prove that six rows must be impossible**.

But note in your small calculation: if the side triangle has two rows, the path endpoint is

\[
7+8=15
\]

rather than adding 15 again. The 15 is the endpoint itself, so it does not exceed \(N=21\).

Changing the main path changes the final pair's position, but the row counts of the side triangles to its left and right always sum to \(n-2\). Thus at least one side is no smaller than the other; choosing the larger guarantees sufficient depth. Only with 2018 rows does this "larger side" reach 1008 rows.

## Round 15

### Student

I also meant 7 plus 8 equals 15; I did not add 15 again. I can do that and do not need it explained again. I am still stuck on positions: you say looking at the final pair tells us both sides, but I worry the plus signs above may extend into that region. Could you circle both regions directly on the same six-row diagram and count their combined 4 rows for me? Just saying it always works this way does not let me check for myself yet.

### Teacher

We can first extract the "final pair" of the six-row triangle separately:

```text
Left side triangle        Final pair        Right side triangle
   L                         A  B                  R
  L L                                            R R
 L L L                                          R R R
```

Here, from the six rows we remove:

- The final pair: 2 positions;
- The remaining positions: \(6-2=4\) "horizontal positions."

These are distributed on the pair's left and right, so their row counts total 4. For example:

```text
Left 2 rows + Right 2 rows = 4 rows
```

The `+` cells above the main path cannot extend into the chosen side triangles because they lie in the strip leading to the final pair, while the side triangles lie outside it.

### Student

I can count six positions minus two leaving four, two on each side. But you changed diagrams again, and I cannot place these two regions back in the original six-row diagram. I have asked several times and still cannot connect it. I want to stop here today: I can calculate small triangles, check differences, and see that an excessively large number cannot fit. I still do not understand why 2018 rows must leave that region, so I cannot say I can prove it.

### Teacher

This teaching session has been confirmed as ended.
