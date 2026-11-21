# P09 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P09 |

## Round 1

### Student

Teacher, I want to get the rules right first. Putting 1 and 3 below gives 2 above, so two rows use 1, 2, 3 once each, right? With so many cells in 2018 rows, trying each arrangement clearly will not work. I usually check quantities and repeats; what is useful to examine first for deciding whether an arrangement exists? Start with concrete small examples; I need time with letter formulas.

### Teacher

Yes, your two-row example is entirely correct:

```text
  2
1   3
```

The upper cell is `|3−1|=2`, so 1, 2, 3 are each used exactly once.

The first step for judging a large triangle is indeed to consider two simple facts rather than try each cell:

1. How many cells there are.
   Two rows have \(1+2=3\) cells, three have \(1+2+3=6\), and 2018 have

   \[
   1+2+\cdots+2018=2037171
   \]

   cells, so exactly 1 to 2037171 must be used.

2. Whether absolute differences produce repeats or omissions.
   For example, bottom `1, 3, 6` yields `2, 3` above, repeating the bottom's 3 and violating requirements.

The example shows that each local step being calculable does not guarantee a valid whole triangle. As rows increase, the focus changes from “can we continue arranging?” to “must some numbers repeat, or must some regions contain only large values?”

The next useful observation is following the larger lower number in each row. In two rows, moving from top 2 to larger bottom 3 gives:

\[
3=2+1
\]

Thus along this downward path, at each step the endpoint equals a sum of collected positive integers. This “stepwise accumulation” structure suits studying 2018 rows better than cell-by-cell trials.

## Round 2

### Student

I understand the repeating example. Following larger values downward means the upper is a difference, so the larger lower value equals that difference plus the other smaller value, increasing downward. But I have not followed exactly which cells are the “collected values.” Could you go through three rows with concrete numbers, recording each added value? Then give me a small example without the answer to follow myself. I also cannot yet see whether accumulation proves 2018 rows impossible or merely finds clues.

### Teacher

Certainly. First a complete three-row example:

```text
        3
      5   2
    1   6   4
```

Check:

- \(|6-1|=5\)
- \(|6-4|=2\)
- \(|5-2|=3\)

Now follow the “always choose the larger child” path:

```text
        3
      5
    1
```

Record the unchosen neighboring number at each step:

- Top 3, collected neighbor 2, so \(3+2=5\)
- At 5, collected neighbor 1, so \(5+1=6\)

Finally:

\[
6=3+2+1
\]

The “collected value” is the child not selected for the path, which together with the larger path child produces the upper difference. These values are not arbitrary; the path uniquely determines them.

Try this example yourself:

```text
        4
      7   3
    1   8   5
```

Start at the top, always choose the larger child, record the unchosen number each step, then check “endpoint = top + sum of recorded numbers.”

For 2018 rows, accumulation is only a clue so far. Its real role is that a valid triangle gives many distinct positive integers collected by this path; the longer the path, the larger its endpoint must be. Finding another region forced to use still larger numbers could then produce a contradiction: “some cell must exceed the overall allowed maximum.”

## Round 3

### Student

I tried: below 4 choose 7, record 3; below 7 choose 8, record 1, ending with 8=4+3+1. I can follow that accounting. But your first path diagram ends with 1; should it not be 6? From the equations I interpret it as 3→5→6. Also, the exercise has 8−5=3, repeating second-row 3, so it only practices the route rather than being a valid triangle, right? Please next explain how to find “another region,” one part at a time; distinct collected values alone do not yet let me deduce anything exceeding 2037171.

### Teacher

Your judgment is exactly right:

- The earlier path should be \(3\to5\to6\), rather than ending with 1.
- In the exercise, \(8-5=3\), and 3 already occurs, so it is not a valid triangle, only practice for “accounting along larger values.”

Now “another region.”

Suppose we have followed larger values nearly to the bottom. The last step lands on an adjacent bottom pair, for example:

```text
        ·
      ·   ·
    ·   ·   ·
  ·   ·   ·   ·
```

The path passes through a “strip” above that pair. Each step only moves lower left or lower right, so its collected small values also lie near this strip.

If the final pair is not far left or right, a whole triangle remains beside it. For example:

```text
          Path region
        /-----------\
       /             \
Left small triangle       Right small triangle
```

First consider only the left triangle. It does not overlap the path region, so it cannot contain collected path values.

We previously know those collected values already include 1, 2, 3… through all small numbers required by some row count. Thus the left triangle cannot reuse them and must contain larger numbers.

That is the role of “another region”:

- The path occupies small values;
- the neighboring triangle must use only large values;
- following another “larger-value path” there makes its endpoint a sum of many large values.

There is no need to calculate 2037171 immediately. First understand that one path gives an “accumulation lower bound,” and the neighboring triangle gives a larger one. Only when the latter exceeds the allowed maximum does a contradiction arise.

## Round 4

### Student

I cannot connect this: how does “distinct collected values” become “already includes 1, 2, 3 through some number”? Like recording warehouse item IDs, three different IDs might be 2, 5, 9, not necessarily 1, 2, 3. Can we only say three distinct positives total at least 1+2+3? Then uncollected neighboring IDs might still include 1, so we cannot directly say all neighboring numbers are large? Also, what if the path lands at an extreme edge? Please verify these two grounds before continuing; otherwise it only sounds plausible to me.

### Teacher

You are right; my earlier account skipped a step. Merely “collecting \(n\) distinct positive numbers” gives only:

\[
\text{their sum is at least }1+2+\cdots+n.
\]

They need not already be \(1,2,\ldots,n\).

The crucial additional fact is “the endpoint cannot exceed the overall maximum.”

Suppose the path collects \(n\) values. Accumulating from the top makes the endpoint their sum. Since all values come from \(1\) to \(N\), the endpoint is at most \(N\). Meanwhile, \(n\) distinct positive integers sum to at least:

\[
1+2+\cdots+n=N.
\]

Thus:

\[
\text{endpoint}\ge N,\qquad \text{endpoint}\le N.
\]

Equality is forced. These \(n\) values must be exactly the smallest \(n\) positive integers:

\[
\{1,2,\ldots,n\}.
\]

So “all are small numbers” follows not from “no repeats” alone, but jointly from:

1. Distinctness;
2. all being positive integers;
3. their sum not exceeding \(N\).

These three together imply it.

For the neighboring region:

- Collected path values occupy exactly \(1,\ldots,n\);
- each value can appear only once;
- the neighboring region cannot reuse \(1,\ldots,n\);
- so all its numbers exceed \(n\).

Your question about the extreme edge is important too. The proof does not require triangles on both sides; use the larger side only:

- Path near the left: the right triangle is larger;
- path near the right: the left triangle is larger;
- path in the middle: choose the larger side.

Wherever it ends, at least one side leaves a sufficiently tall complete triangle, at least 1008 rows for 2018 rows. Next accumulate again in this triangle “containing only numbers greater than 2018.”

## Round 5

### Student

I understand the explanation of “both bounds fixed at the same total”: the minimum needs that much, and no more is allowed, so only the smallest set works. For 2018 rows, there are 2017 steps plus the top value, totaling 2018, right? Please include the top so I do not miss a term. I want to check next: in at least 1008 side rows with every value above 2018, a path adds 1008 values. At 2019 each that is 2035152, still below 2037171. So distinctness is also needed, right? Please verify my count, then draw a smaller example showing why 1008 rows must remain; verbally saying one side is large does not yet make it clear.

### Teacher

Yes, the first path does involve 2018 values:

- 1 top value;
- 2017 downward steps, adding 1 collected neighbor each;
- totaling \(1+2017=2018\).

Your counting approach is correct.

For 1008 side rows with values above 2018, the minimum is not all 2019 but:

\[
2019,2020,2021,\ldots,3026
\]

because they must also differ. Their sum is:

\[
2019+2020+\cdots+3026=2542680.
\]

This exceeds the overall maximum:

\[
2037171.
\]

Your \(1008\times2019=2035152\) is the lower bound “with repeats allowed.” Distinctness adds:

\[
0+1+\cdots+1007=507528,
\]

raising the total lower bound to 2542680.

Why must at least 1008 rows remain? First consider a small 8-row diagram, with the final pair at middle bottom columns 4, 5:

```text
Bottom:  1  2  3 [4  5] 6  7  8
                    ↑
                 Final pair
```

The left side supports a 3-row small triangle, and the right side also supports a 3-row small triangle:

```text
             Path strip
          /-----------\
       Left triangle   Right triangle
          3 rows          3 rows
```

With 8 rows overall, removing the top path strip and final pair leaves \(8-2=6\) rows distributed between the sides. They need not have equal heights, but the taller has at least:

\[
\left\lceil\frac{8-2}{2}\right\rceil=3
\]

rows.

Replacing 8 by 2018 gives:

\[
\left\lceil\frac{2018-2}{2}\right\rceil
=\left\lceil1008\right\rceil
=1008.
\]

Thus “at least 1008 rows” comes from evenly dividing the areas on both sides, while “exceeding 2037171” comes from those 1008 values all exceeding 2018 and differing from one another.

## Round 6

### Student

I can calculate the distinct-value addition myself now: 1008 lots of 2019 plus 0 through 1007 is indeed 2542680, exceeding the limit, so if that complete triangle exists there is a contradiction. But the diagram shows only the bottom row and schematic outlines; I still cannot see its interior cells. Could a path going right then left cross the claimed left triangle or leave collected values inside? Could you specify exactly which rows and columns form the left 3-row triangle in 8 rows, and why no route collects those cells? I can recalculate numbers but cannot independently explain this step and do not want to treat a schematic as proof.

### Teacher

You identified the step most easily obscured by a diagram. Use 8 rows and suppose the path finally reaches row 7 cell 4, whose bottom children are row 8 cells 4, 5.

Write row \(r\), column \(j\) as \((r,j)\). The left 3-row triangle is exactly:

```text
Row 6:        (6,1)

Row 7:        (7,1) (7,2)

Row 8:        (8,1) (8,2) (8,3)
```

This is a complete 3-row triangle.

Now why can the path not collect these cells?

To reach row 7 cell 4, its row-\(r\) position cannot be too far left. Row \(r\) to row 7 allows at most \(7-r\) rightward moves, so in row \(r\) it must be at column:

\[
4-(7-r)=r-3
\]

or farther right.

The “other child” collected in row \(r\) can be at most one column right of the path cell, so it cannot be too far left either. Row by row:

- Row 6: collected cell at least column 2;
- row 7: at least column 3;
- row 8: column 4 or 5.

But the left triangle occupies only:

- Row 6 column 1;
- row 7 columns 1, 2;
- row 8 columns 1, 2, 3.

Thus they are completely disjoint.

The key is not that the path “cannot go right then left”; of course it can. Rather, eventually reaching row 7 cell 4 constrains every row's positions, preventing it from reaching as far back as the left triangle.

The general coordinates are the same: if the final selected row-\(n-1\) cell is in column \(p\), left-triangle cells satisfy

\[
j+n-r\le p-1,
\]

while collected cells are at least at

\[
j\ge p-(n-r)
\]

these positions. They remain separated by one column and cannot coincide.

## Round 7

### Student

Listing rows is clearer than the earlier schematic. Checking row 6: if column 1 were collected, the selected larger cell could be at most column 2; one more step to row 7 reaches at most column 3, not column 4, so column 1 cannot be collected. I understand the “not enough steps remaining” reason. But substituting n=8, r=6, p=4 into your final formulas, the left allows j≤1 while the collected cell only says j≥2? I get p−(n−r)=2, yes 2, so that row works; the left formula j+2≤3 also gives j≤1, a one-column difference. I can check concrete rows now. Please finally connect, briefly in ordinary language, how final-pair positions give the two side heights and why the conclusion is impossibility, without another new method.

### Teacher

Your substitution is correct: in row 6 the left reaches only column 1, while collected cells begin at column 2, with no overlap.

Connecting the proof:

Suppose the path finally reaches column \(p\) of the penultimate row, whose bottom children occupy columns \(p,p+1\).

- The left leaves a triangle of height \(p-1\);
- the right leaves height \(2018-p-1=2017-p\).

Their heights total:

\[
(p-1)+(2017-p)=2016.
\]

Thus the taller has at least:

\[
\frac{2016}{2}=1008
\]

rows.

The earlier path occupies \(1,\ldots,2018\), and coordinates ensure these path numbers do not enter the side triangle. Thus all its numbers exceed 2018 and are distinct.

Following larger cells again there, a 1008-row path accumulates at least:

\[
2019+2020+\cdots+3026=2542680.
\]

But the overall maximum is only:

\[
2037171.
\]

Thus a side-triangle number must exceed the overall allowed maximum, a contradiction. Therefore a 2018-row anti-Pascal number triangle cannot be arranged.

### Student

I will stop here today. I can now connect the key reasons: the first sum's 2018 distinct positives minimally reach the allowed maximum, so only the smallest set works; remaining side heights total 2016, giving at least 1008 rows on one side; those small values cannot be reused there, so another accumulation exceeds the limit. I also checked row 6 positions to see why no mixing occurs. Concrete numbers and row-by-row positions helped greatly; I could not follow when only told “occupy small values” with a strip diagram. I am not yet familiar with general letter formulas, but can check this specific case step by step. Thank you; I am ending this session.

### Teacher

This teaching session has been confirmed as ended.
