# P04 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | KELE |
| Participant ID | P04 |

## Round 1

### Student

Teacher, I want to confirm the rules first. With two rows, putting 1, 3 below gives 2 at the top, using exactly 1 to 3, right? But 2018 rows is so large that I do not know where to start judging existence or nonexistence. Could you let me try a small example first, then see what I should pay attention to?

### Teacher

Yes. With 1 and 3 in the bottom row, the top cell is |3−1|=2, and the three cells use 1, 2, 3 exactly once each.

We can try three rows next: use **1 to 6** exactly once each, with every upper cell equal to the absolute difference of the two adjacent cells below.

Can you try constructing a three-row number triangle that follows the rules?

## Round 2

### Student

I tried 1, 6, 3 in the bottom row, giving 5, 3 in the middle and 2 at the top, but 3 repeats and 4 is missing. Changing it to 1, 6, 2 gives 5, 4 in the middle and 1 at the top, another repetition. I can check what breaks the rules, but changing numbers one by one feels confusing. Could you give me a hint for choosing the bottom numbers? Please do not give me the whole triangle directly yet.

### Teacher

Both your calculations and checks are correct: besides checking adjacent differences, we need to check that each number occurs exactly once in the whole triangle.

Here is a hint for choosing the bottom row: both times you put **6 in the middle**. Keep it fixed for now and systematically change the numbers on either side. For each choice, first check whether the two differences repeat bottom-row numbers, then calculate the top cell.

Can you try another choice this way?

## Round 3

### Student

Checking in that order is easier. I tried 1, 6, 4, giving 5, 2 in the middle without repeating bottom numbers, and 3 at the top, so all of 1 to 6 are present. I think three rows work. But a small construction seems insufficient to show that 2018 rows work too. What relationship should we seek next to judge so many rows?

### Teacher

Yes, your three-row triangle follows the rules:

```text
    3
   5 2
  1 6 4
```

Your judgment is also correct: three rows being feasible establishes only that case, not whether 2018 rows are feasible.

Next, examine **the relationship between one upper cell and the two cells below it**. For example, below the middle 5 are 1 and 6. If we add the upper number to the smaller lower number, what do we get?

## Round 4

### Student

5 plus 1 equals 6, the larger number below. I also checked 6 and 4 below 2: 2 plus 4 equals 6 too. Since the upper number is the larger minus the smaller, adding the smaller back gives the larger. I understand this relationship, but it holds in every small triangle. How can it constrain the whole triangle?

### Teacher

Yes, we can connect the relationship across steps. Imagine starting at the top and always moving to **the larger** of the two cells below, until reaching the bottom row.

Predict this: after following such a path to the bottom, which numbers along the way, together with the top, sum to the bottom number? Try describing your idea using your three-row triangle.

## Round 5

### Student

I drew 3 going to 5, then to 6. The first step is 5=3+2, the second 6=5+1, so 6=3+2+1. It seems to be the top plus the smaller number not chosen each time, without adding the visited 5 again. With 2018 rows we would add many numbers… They are all distinct. Could we estimate using the smallest few numbers? But I have not counted how many there are.

### Teacher

Your idea is correct: the bottom cell equals the top plus the number not selected at each downward step. A three-row triangle has two steps, so three numbers are added altogether.

For 2018 rows, going from top to bottom takes **2017 steps**. Including the top, the sum has **2018 numbers**. They come from different rows and are distinct positive integers.

Can you use the smallest 2018 positive integers to write a lower bound for the bottom number?

## Round 6

### Student

The lower bound is 1+2+…+2018. Pairing the ends gives 2019 times 1009=2037171, exactly the largest allowed number. Thus the bottom cell must equal 2037171 and the summands must be 1 to 2018, right? But this only reaches the limit rather than exceeding it, so I cannot claim impossibility yet. Should we next see where equality causes a conflict?

### Teacher

Yes. **If such a triangle exists**, the path’s bottom cell must be 2037171, and the summands occupy exactly 1 to 2018. Equality alone has not produced a contradiction.

Next, find a region not occupied by these small numbers. Consider the two adjacent bottom cells faced by the path’s final step. The bottom cells to their left support a side triangle above them, and those to their right similarly support another side triangle.

Can you consider why the summands collected along the path lie in neither side triangle?

## Round 7

### Student

I am having trouble following this. I can find the earlier summands in the diagram, but I am unsure exactly which cells “the bottom cells on the left support above them.” If the path turns left and right, could unchosen numbers also be on the sides? Could you draw four or five rows, labeling the path, collected numbers, and one side triangle? Introducing two regions at once is a little confusing.

### Teacher

Certainly. I introduced the two regions together too quickly. First consider a specific four-row example:

```text
          4*               * Top: collected
       2+    6→            → Visited by the path
    [5]   7→    1+         + Unchosen child: collected
  [8]  [3]   10→   9+      [ ] Left triangle
```

Every upper cell is the absolute difference of the two adjacent cells below. The path is **4 → 6 → 7 → 10**, turning both left and right. Collecting the top and each unchosen child gives 4, 2, 1, 9, so 10=4+2+1+9.

The final step faces bottom numbers **10 and 9**. To their left are 8, 3. The 5 immediately above these cells forms the left triangle with them, marked by square brackets. “Support” here means that **both children of 5 belong to this region**.

Check row by row: do any of the collected 4, 2, 1, 9 lie in the bracketed side triangle?

## Round 8

### Student

No. The brackets contain 5, 8, 3, while the collected numbers are 4, 2, 1, 9. This diagram lets me distinguish the region. The turning path does not enter it here. But I have checked only this path, and do not know why a different sequence of turns always avoids it. Is it because cells in the side triangle can reach only the bottom segment 8, 3, while the path ends at 10, so neither the path nor its collected neighboring cells can enter? I am still unsure about the latter claim concerning neighboring cells.

### Teacher

Yes, your check is accurate. Using “which bottom cells can be reached” is a good way to judge positions. You also noticed that **path cells** and **collected neighboring cells** need separate explanations.

First consider a cell on the path. If it lay in the left triangle, why could following adjacent children downward never reach either 10 or 9 in the final pair?

## Round 9

### Student

Because both children of every cell in this triangle are also inside it. Continuing downward never leaves it and only reaches 8 or 3, not 10 or 9. So path cells are outside it; I understand that part. But my sticking point was the unchosen child: it no longer follows the path. Could it be inside? Could you explain that next?

### Teacher

Yes. You are correct: **the path avoiding the side triangle does not by itself imply that unchosen neighboring cells also avoid it**. We must examine their relative positions.

Let the left cell of the final child pair be bottom cell \(p\). For any choice along the path, suppose the cell before the choice lies in row \(r-1\), column \(q\). It can follow the path to column \(p\) in the penultimate row, so

\[
q\le p\le q+n-r.
\]

Its children are in columns \(q\) and \(q+1\) of row \(r\). Whichever is unchosen, its column index is at least \(q\), hence at least \(p-(n-r)\).

But a cell in row \(r\) of the left triangle must have all bottom-row descendants to the left of cell \(p\), so its column index is at most \(p-(n-r)-1\). This is one column smaller than the leftmost possible unchosen child. Thus **the unchosen child also cannot lie in the left triangle**. This judgment does not depend on the path’s particular turns.

Returning to 2018 rows: the collected summands occupy exactly 1 to 2018. What magnitude constraint applies to every number in a side triangle avoiding these summands?

## Round 10

### Student

If it really avoids all these summands, the side triangle can contain only 2019 and larger numbers. I understand that constraint. But introducing q, p, r together was hard to follow, and I cannot say I can prove the positions yet. Could you substitute n=5, with the final pair at cells 3 and 4, and choose one row to examine? I want to check the “one-column gap” before continuing.

### Teacher

Yes, numbers in the side triangle are at least 2019. As you request, let us check only the positions in a five-row triangle, without rushing onward.

The final bottom pair is in **columns 3, 4**, so \(n=5\), \(p=3\). Consider **row 4**, that is, \(r=4\):

```text
Row 3:          ·     A     ·
Row 4:       [Side]   B     C     P
Bottom:      [Side] [Side] Cell 3  Cell 4   ·
```

Count columns from left to right in each row. Brackets mark the left triangle. **P** in row 4 is in column 3, and its children are bottom cells 3, 4.

Now consider path cell A in row 3. To reach P later, A must be in column 2 or 3. If A is in column 2, its children are B, C in the diagram; if A is in column 3, they are C, P. Whichever the path chooses, the other collected child lies in **column 2 or farther right**.

For a row-4 cell to belong to the left triangle, both bottom children must be in bottom columns 1, 2, so it can only be the cell in **column 1**.

That is the “one-column gap”: the collected child is no farther left than column 2, whereas this row’s side triangle reaches at most column 1. Substituting into the formula gives \(p-(n-r)=3-(5-4)=2\), and subtracting one more for the side-triangle boundary gives 1.

In this example, if A is in column 2 and the path chooses C in column 3, which column contains the unchosen B, and does it belong to the left triangle?

## Round 11

### Student

According to the text, B is in column 2 and does not belong to the left triangle, which ends at column 1. Substituting numbers is easier to understand. But counting row 4 in the diagram gives [Side], B, C, P, so P seems to be in column 4 rather than column 3 as the text says. Should I regard C as the cell ultimately reached in column 3? I want to confirm that. Then can we count the right side in reverse to obtain the same avoidance relationship?

### Teacher

Your count is correct; my diagram was wrong: **C is the cell ultimately reached in row 4, column 3**. I added an extra P. Sorry.

With columns labeled explicitly, this portion should be:

```text
Row 3 columns:   1       2       3
                         A
                        / \
Row 4 columns:   1       2       3       4
               [Side]    B       C       ·
Bottom columns:[1]     [2]     3       4       5
                               └─Final pair─┘
```

Here A is in column 2, the path chooses C, and the unchosen B is in column 2. The left triangle contains only column 1 in row 4, so B is outside it.

**We can also count the right side in reverse.** In general, if the final bottom pair is in columns \(p\), \(p+1\), all bottom cells reachable from a cell in the right triangle lie to the right of column \(p+1\). Thus a right-triangle cell in row \(r\) has column index at least \(p+2\).

The cell before a path choice is in column \(q\). Since it can reach column \(p\) in the penultimate row, \(q\le p\). Its children occupy columns \(q\), \(q+1\), so the unchosen one is at most in column \(p+1\), avoiding the right triangle.

In this five-row example, \(p=3\), and the right triangle contains only bottom cell 5. Can you use “the unchosen child lies at most in column \(p+1\)” to check why the child unchosen at the final step is outside the right triangle?

## Round 12

### Student

The final step chooses between cells 3, 4, and the unchosen cell is also one of those, reaching at most cell 4, never cell 5. After the diagram correction I can check by column. I still need to study the general formula for the left slowly, but roughly understand why both sides are avoided. Now both sides contain only numbers at least 2019, but their differences can still be large; for example, 5000 minus 2019 is still greater than 2019. I still do not see a conflict. Do we need another such path in the side triangle?

### Teacher

Yes, the second path you propose is exactly the next step. Your example also shows that merely knowing all side-triangle numbers are at least 2019 does not yield a contradiction from one difference.

Connect the reasoning so far:

1. Assume a 2018-row triangle exists. Starting at the top and always following the larger child makes the bottom cell the sum of the top and the unchosen child at each step: 2018 distinct positive integers.
2. Their sum is at least \(1+\cdots+2018=2037171\), and the bottom cell is at most 2037171. Equality must hold: the summands are exactly 1 to 2018.
3. The triangles on either side of the final child pair avoid these summands, so their numbers are at least 2019. We checked positions with a five-row example. You understand its specific boundaries, but still need time to absorb the general position proof.
4. The two side-triangle base lengths sum to \(2018-2=2016\), so the larger has at least **1008 rows**. Following larger children to its bottom again gives a bottom cell equal to a sum of at least 1008 distinct positive integers all greater than 2018, hence at least

   \[
   2019+2020+\cdots+3026=2542680.
   \]

5. But the largest allowed number in the entire triangle is 2037171, and \(2542680>2037171\), a contradiction. Therefore **the required 2018-row triangle does not exist**.

You independently identified the direction of the second path. We had not yet completed the general position proof and final numerical contradiction together, so this supplies the remaining argument, rather than implying that you have proved these parts independently.

## Round 13

### Student

Let me check the final section: the sides total 2016 cells, and if both had fewer than 1008 there would not be enough, so one always has at least 1008 rows. Its top and unchosen children all remain within the same side region, which guarantees every summand is at least 2019. We need not actually calculate the whole sum: 1008 numbers, each at least 2019, give at least 2035152, still slightly below the maximum. Distinctness then adds at least 0+1+…+1007, exceeding it. Is that understanding correct? If we only say each exceeds 2018 and omit distinctness, the simple multiplication is insufficient.

### Teacher

Yes, your understanding and calculations are correct. The side bases total 2016 cells, so the larger side has at least 1008 rows. Following larger children within a side triangle keeps the top and every unchosen child inside it, so all summands are at least 2019.

You have also accurately identified the role of **distinctness**:

\[
1008\times2019=2035152<2037171.
\]

The lower bound based only on “each number is at least 2019” is indeed insufficient for a contradiction. But sorting 1008 distinct summands makes them at least 2019, 2020, through 3026 respectively. Thus the product must be increased by at least

\[
0+1+\cdots+1007=507528,
\]

giving the lower bound \(2542680\), exceeding the largest allowed number \(2037171\).

The final step therefore depends on both **all side-region numbers exceeding 2018** and **all numbers in the triangle being distinct**. You understand this numerical contradiction correctly. The earlier general positional argument can still be checked further.

### Student

I will stop here today. I know the conclusion is nonexistence and can explain the conflicting lower bounds using two paths. The small diagram and substituted column indices helped. I still cannot write the general position proof in full myself and need to review it. I have checked the later calculations clearly and will not continue expanding them for now.

### Teacher

This teaching session has been confirmed as ended.
