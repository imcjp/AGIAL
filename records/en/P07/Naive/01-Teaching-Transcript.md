# P07 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P07 |

## Round 1

### Student

Teacher, I will try two rows first: putting 1 and 3 below gives 2 above, using 1, 2, 3 once each, so that should follow the rules? For three rows, I want to arrange the bottom first and calculate upward, but might get repeated numbers. Could you first let me try three rows? Please do not give the complete arrangement; I want to calculate and see where I get stuck.

### Teacher

Your two-row attempt is correct: \(|3-1|=2\), so it does use \(1,2,3\) once each.

Now try three rows:

Place three numbers at the bottom. The middle row consists of absolute differences of adjacent cells, and the top is the absolute difference of the middle numbers. Three rows must use exactly \(1\) to \(6\).

Choose any three bottom numbers first, calculate the two rows above, then check for repeats or omissions. Send me your arrangement or difficulty, and I will give only local feedback.

## Round 2

### Student

I tried bottom 1, 6, 4, middle 5, 2, top 3, using 1 to 6 exactly once! Calculating row by row is clear. But making three rows does not mean 2018 works too, right? I can only try numbers now and cannot try that many. Which relationship should I observe next to judge the large triangle? Could you demonstrate an observation using this small triangle?

### Teacher

Your judgment is precise: three rows being feasible shows only that “a small-scale example exists,” not directly that 2018 rows are feasible.

First observe a “larger-child path.” In your triangle:

```text
        3
      5   2
    1   6   4
```

Start at the top and always move to the larger lower child:

- \(5=3+2\)
- \(6=5+1\)

So the endpoint \(6\) can be written:

\[
6=3+2+1.
\]

This is no accident. In an \(n\)-row triangle, this path expresses the endpoint as a sum of \(n\) distinct positive integers. Meanwhile, all numbers are from \(1\) to \(N\), so the endpoint cannot exceed \(N\).

The sum of \(n\) distinct positive integers is at least:

\[
1+2+\cdots+n=N.
\]

Thus both bounds must be equal. If the large triangle exists, it must meet a strong condition: the numbers selected along this path are exactly \(1,2,\ldots,n\).

First consider: which three numbers are selected in your example? Why do they reach the minimum possible sum?

## Round 3

### Student

The summands are top 3, beside it 2, and bottom 1: 1, 2, 3, totaling 6. I easily confuse the visited 3, 5, 6 with the summands: 5, 6 are just intermediate results, right? I can follow your expansion. But even if 2018 rows requires 1 to 2018, those numbers are in the triangle anyway, so why impossible? What further restriction produces a contradiction? Please go step by step and first give me a relationship to check next.

### Teacher

Yes, 5 and 6 are intermediate path results; the summands are \(3,2,1\).

Next look at “which positions these small numbers occupy.”

In the three-row example, the path and nearby numbers cover:

- Top \(3\)
- Middle \(2\)
- Bottom \(1\)

They concentrate in a strip leading to a bottom-row position. Thus some small triangles completely outside this strip remain on the sides.

The key restriction is:

> These small side triangles cannot contain \(1,2,3\) again, because cells beside the path already use them.

So every number in them must exceed \(3\). This is not enough for a contradiction in three rows, but with 2018 rows the side triangles are large; another larger-child path inside one gives “a sum of many numbers all greater than 2018.”

Next check one small question: why can \(1,2,3\), already fixed by the path relationship, not appear elsewhere in the three-row triangle?

## Round 4

### Student

Because the problem requires each number only once; after 1, 2, 3 are used, another occurrence repeats them. That is clear and needs no more practice. The remaining three-row numbers are 5, 6, 4, but some are on the visited path too, and I still cannot see the side triangles' positions. Could you draw a slightly larger schematic marking the occupied small-number cells and remaining triangles? Especially, how do we guarantee a sufficiently large one for 2018 rows? Otherwise I cannot compare “many numbers” yet.

### Teacher

Exactly right. Once used, the same number cannot appear elsewhere.

First consider an abstract \(n\)-row diagram. Suppose the “larger-child path” ultimately reaches adjacent bottom cells \(P,Q\):

```text
                         ●
                       ●   ●
                     ●   ●   ●
                   ●   ●   ●   ●
                         ⋮
               ┌────Path strip────┐
Bottom:   L L L L L L | P Q | R R R R R
         └─Left triangle─┘   └─Right triangle─┘
```

The path and the “summand” beside it at each step all lie in the central strip. Thus:

- The left side triangle contains none of the path's \(1,\ldots,n\);
- the right side triangle likewise contains none of \(1,\ldots,n\);
- all numbers in both side triangles must exceed \(n\).

The final bottom pair's position is key. Suppose they occupy columns \(p,p+1\):

- There are \(p-1\) bottom cells on the left;
- there are \(n-p-1\) bottom cells on the right.

Together they have \(n-2\) cells, so the larger side has at least

\[
\left\lceil\frac{n-2}{2}\right\rceil
\]

rows. For \(n=2018\), that is at least

\[
\left\lceil\frac{2016}{2}\right\rceil=1008
\]

rows.

This is where “sufficiently large” comes from: wherever the final pair lands, at least one side has 1008 rows. Next repeat “accumulating downward along larger child cells” inside that side triangle of 1008 rows or more.

## Round 5

### Student

The two bottom sides total 2016, so at least one has 1008; I can calculate that. But the path strip looks centered in the diagram, while each actual step can go left or right, right? If it first goes right then left, could earlier small summands fall in the left triangle defined by final P, Q? Could you work through specific row-column positions in five rows? I need to check that region really has no summands before using “greater than 2018.”

### Teacher

Your concern is correct, so we cannot judge merely by its “looking centered.” We must check row-column positions.

Take a five-row example. Suppose the final child pair \(P,Q\) is at row 4, columns 3, 4:

```text
Row 1                 b₁
Row 2               b₂   a₂
Row 3             a₃   b₃   ·
Row 4           ·   b₄=P  a₄=Q   ·
Row 5         L   L   L   P   Q   R
```

The path may shift sideways. For example, its column indices can be:

\[
1\to2\to2\to3.
\]

It can indeed move right, stay in the same column, then move right, without descending in a straight line.

Now consider any step. A path cell in row \(r-1\), column \(q\) must subsequently reach row \(n-1\), column \(p\), so:

\[
q\le p\le q+n-r.
\]

The sibling \(a_r\) included in the accumulation can only be in column \(q\) or \(q+1\), so its column lies in:

\[
[p-(n-r),\ p+1]
\]

this interval.

Left-side cells satisfy:

\[
j+n-r\le p-1,
\]

thus

\[
j\le p-(n-r)-1.
\]

This lies one cell left of even \(a_r\)'s leftmost position, preventing overlap. Similarly, right-side columns are at least \(p+2\), also preventing overlap.

So even if the path first goes right then left, all small summands \(a_1,\ldots,a_n\) still avoid both side triangles. Thus neither contains \(1,\ldots,n\), and all its numbers must exceed \(n\).

## Round 6

### Student

There are a lot of symbols here; I can only grasp that each downward row increases the column by at most 1, so a cell too far from the final position cannot meet it. But row 5 has six cells in the diagram, when five rows should have only five; the text places P, Q in row 4 columns 3, 4, while the diagram looks like 2, 3 and repeats P, Q at the bottom. Checking against it confuses me. Could you correct the five-row diagram, marking just one path, four sibling positions, and one remaining triangle? Then directly help me calculate the minimum sum of 1008 distinct numbers greater than 2018. I want to understand positions and numbers separately.

### Teacher

You are right; the previous diagram was wrong: five rows should have \(1+2+3+4+5\) cells. I will correct it and first apologize for the diagram error.

Here is a five-row schematic. `b` marks the path, `a` the neighboring summands, and parentheses on the right mark one remaining side triangle:

```text
Row 1                 b₁

Row 2               a₂   b₂

Row 3             ·    b₃   a₃

Row 4           ·    P    Q   (R)

Row 5         ·    b₅   a₅  (R) (R)
```

Here:

- Path: \(b_1\to b_2\to b_3\to P\to b_5\)
- Four neighboring numbers: \(a_2,a_3,Q,a_5\)
- Additionally, the top cell \(a_1=b_1\)
- The remaining right triangle consists of row 4's \(R\) and row 5's two \(R\) cells

Even as the path shifts sideways, these four neighboring numbers all stay outside the parenthesized side triangle; their positions remain constrained by the range of the path ultimately reaching \(P,Q\).

Now calculate the numerical part separately. For 2018 rows, the larger side triangle has at least

\[
1008
\]

rows. All its numbers exceed \(2018\) and are distinct, so the smallest possible set is:

\[
2019,2020,\ldots,3026.
\]

Their sum is:

\[
\frac{(2019+3026)\times1008}{2}
=2,542,680.
\]

But the full triangle uses only \(1\) to \(2,037,171\), so no cell can exceed:

\[
2,037,171.
\]

Thus a bottom endpoint inside this side triangle is both at least \(2,542,680\) and at most \(2,037,171\), a contradiction.

### Student

This time the five rows have the right cell counts; I can follow b1, b2, b3, P, b5 and see that the three R cells on the right do not meet the neighboring numbers. I understand the numerical part: the smallest 1008 numbers run from 2019 to 3026, pairing to total 2542680, exceeding the allowed maximum 2037171. So if the side-triangle guarantee holds, a 2018-row triangle is impossible. I can explain this example now, but still cannot write the row-column proof that every turning path avoids the region independently. Separating positions from calculation helped a lot; the earlier incorrect diagram kept me stuck for a while. I will stop here today.

### Teacher

This teaching session has been confirmed as ended.
