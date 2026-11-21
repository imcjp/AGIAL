# P04 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | Naive |
| Participant ID | P04 |

## Round 1

### Student

Teacher, I want to confirm the rules first. With two rows, putting 1, 3 below gives 2 above and uses 1 to 3 exactly once, right? But 2018 rows is so large that I do not know where to start judging it. Could you let me try a smaller case first, then help me see which relationships to notice?

### Teacher

Yes, completely correct: with two rows, 1, 3 below gives \(|3-1|=2\) above, using 1, 2, 3 exactly once each.

Try three rows first. There are \(1+2+3=6\) cells, using 1 to 6:

```text
      a
    b   c
  d   e   f
```

These conditions must all hold:

- \(a=|b-c|\)
- \(b=|d-e|\)
- \(c=|e-f|\)
- Each of 1 to 6 occurs once.

You can begin with arbitrary trials. Focus on how each upper number is determined by “the difference of the two adjacent cells immediately below,” while all numbers must be distinct.

## Round 2

### Student

I tried 1, 6, 2 below, giving 5, 4 in the middle and 1 at the top, a repetition. Changing to 1, 6, 3 gives 5, 3 in the middle, another repetition. Changing numbers arbitrarily gives me little direction. I noticed 6 cannot be the difference of two smaller numbers, so 6 should be in the bottom row. Is that correct? Could we use this to narrow the possibilities, leaving a next step for me to try?

### Teacher

Yes, that judgment is correct. Since an upper number is the difference of two bottom numbers, and any two numbers from 1 to 6 differ by at most 5, 6 must be in the bottom row.

Now use horizontal symmetry to try just one case first: put 6 in the bottom-left corner:

```text
      a
    b   c
  6   e   f
```

Then:

\[
b=|6-e|=6-e,\qquad c=|e-f|.
\]

Next you only need to try \(e=1,2,3,4,5\), checking whether \(b\) already repeats \(e\).

For example, if \(e=3\), then \(b=3\), an immediate repetition. Continue judging which other \(e\) values are excluded, then try the remaining cases.

## Round 3

### Student

Checking separately is better than changing randomly. When e=1, b=5; e=2 gives b=4; e=4 gives b=2; e=5 gives b=1. None seems to repeat immediately, so only 3 is excluded. Trying e=1, f=4 gives bottom row 6, 1, 4, middle row 5, 3, and top 2, using 1 to 6 exactly once. Does that establish that three rows really exist? Also, reflecting left to right only moves 6 from the left to the right, not from the middle to a corner. I worry about overlooking the case with 6 in the middle when claiming impossibility later. How do we move from this small example to 2018 rows? Please explain one key relationship first; too many steps together may be hard to connect.

### Teacher

Yes, your three-row number triangle works:

```text
      2
    5   3
  6   1   4
```

Because \( |5-3|=2\), \(|6-1|=5\), \(|1-4|=3\), and exactly 1 to 6 are used. Your understanding of symmetry is also correct: horizontal reflection exchanges left and right, but cannot turn “middle” into “corner.”

One key relationship in moving from small examples to large cases is:

Follow “the larger child cell” downward in each row. If the preceding cell is \(b_{r-1}\) and the other child is \(a_r\), the larger child satisfies

\[
b_r=b_{r-1}+a_r.
\]

Thus at the bottom:

\[
b_n=a_1+a_2+\cdots+a_n.
\]

Here \(a_1,\ldots,a_n\) are \(n\) distinct positive integers, so their sum is at least

\[
1+2+\cdots+n=N.
\]

On the other hand, no cell exceeds the whole triangle’s maximum \(N\), so \(b_n\le N\). Equality must hold:

\[
b_n=N,\qquad \{a_1,\ldots,a_n\}=\{1,\ldots,n\}.
\]

This is the first foundation of the large-case proof: one path is forced to “collect” all small numbers 1 to \(n\). First consider why “sum at least \(N\)” together with “bottom cell at most \(N\)” forces exact equality.

## Round 4

### Student

If a number is both at least N and cannot exceed N, it can indeed only equal N. But I have not matched the earlier addition yet. In the previous triangle, the top is 2; choosing the larger 5 below leaves 3, so 5=2+3. Then choosing 6 below 5 leaves 1, so 6=5+1. Thus we collect 2, 3, 1, right, and a1 is the top 2? These numbers are in different rows, so cannot be the same cell. I can follow this example now. But why does collecting 1 to 2018 in a 2018-row triangle make the whole triangle impossible? I still do not see the contradiction.

### Teacher

Yes, \(a_1\) is the top cell; your three-row path collects \(2,3,1\).

The key is that this path ultimately leads to a final pair of adjacent bottom cells. Its cells and their “other child cells” form a strip, leaving a whole triangular region on the sides entirely without \(1,\ldots,n\).

We have already proved that the path occupies exactly \(1,\ldots,n\). Therefore every number in a side triangle must exceed \(n\).

For \(n=2018\):

- The side has at least \(1008\) rows;
- Following “larger children” downward within it, the numbers collected at each step are at least \(2019,2020,\ldots\);
- Hence its bottom cell is at least

\[
2019+2020+\cdots+3026=2542680.
\]

But no number in the whole triangle can exceed

\[
N=1+2+\cdots+2018=2037171.
\]

The same cell is thus both at least \(2542680\) and at most \(2037171\), a contradiction. Therefore a 2018-row number triangle cannot exist.

## Round 5

### Student

I understand the later magnitude contradiction: if a bottom cell really must exceed the whole triangle’s largest number, it cannot be arranged. But I cannot explain “the side has at least 1008 rows” yet. The path may turn left and right; why must it leave a complete triangle containing none of the collected small numbers? Could you draw five or six rows, mark the path and other children, then explain how to count 1008? Also, 5 and 6 on the earlier three-row path are not among 1 to 3. It should be the collected numbers using up 1 to n, rather than all path cells being small numbers, right?

### Teacher

Yes, your correction is completely right: the “other cell” chosen in each row, \(a_1,\ldots,a_n\), is forced to occupy \(1,\ldots,n\), rather than all cells visited by the path itself.

Here is a five-row schematic. Suppose the accumulation path ultimately leads to the bottom pair in columns \(p,p+1\):

```text
              P
            P   A
          P   A   P
        A   P   A   P
      P   A   P   B   ...
                  ↑
             Near the final pair
```

Here:

- `P` marks cells visited by the accumulation path;
- `A` marks the “other child cell” selected at each step, whose values are ultimately forced to be \(1,\ldots,n\);
- The path may move left and right, but always advances toward the final bottom pair.

If that pair occupies columns \(p,p+1\):

- The left has \(p-1\) columns remaining, forming a complete side triangle;
- The right has \(n-p-1\) columns remaining, forming another complete side triangle.

The path and its corresponding A cells lie within the strip leading to the final pair, so enter neither side triangle. Thus at least one side triangle has row count satisfying

\[
\ell\ge \max(p-1,n-p-1)\ge \left\lceil\frac{n-2}{2}\right\rceil.
\]

Why does the final inequality hold? The two side row counts sum to \(n-2\), so the larger is at least half.

When \(n=2018\):

\[
\ell\ge \left\lceil\frac{2016}{2}\right\rceil=1008.
\]

That is where “at least 1008 rows” comes from.

## Round 6

### Student

The sides total 2016, so at least one has 1008; I understand that now. But the diagram has several Ps in one row, so I cannot tell which one to follow or find the vertices of the complete side triangles. Imagine a six-row path whose column indices are 1, 1, 2, 2, 3, 3. Its final pair is columns 3, 4. Is the left two-row triangle’s vertex row five, column 1, and the right one row five, column 5? This path really avoids both. Please check this specific arrangement, then explain why these vertices remain safe with a different path. This is my main sticking point, so there is no need to repeat the final addition conclusion.

### Teacher

Your specific judgment is basically correct. Take \(n=6\), with the final child pair in columns 3, 4 of row 5:

```text
Row 5:  [Left side]  3   4  [Right side]
Row 6:  1   2    3   4    5   6
```

The left two-row triangle is:

```text
Row 5: column 1
Row 6: columns 1, 2
```

The right two-row triangle is:

```text
Row 5: column 5
Row 6: columns 5, 6
```

Thus the two vertices you named—row 5 column 1 and row 5 column 5—are indeed the respective side-triangle vertices.

The key is not whether the path specifically goes “left, left, right, right” or otherwise, but that it must ultimately lead to columns 3, 4 of row 5. If the path occupies column \(q\) in row \(r\), continuing to column 3 of row 5 requires:

\[
q\le 3\le q+(6-r).
\]

Thus the path-related cells can only lie in a middle strip. Left-triangle cells satisfy

\[
j+(6-r)\le 2,
\]

and right-triangle cells satisfy

\[
j\ge 5.
\]

Both ranges avoid the path and its “other cell” in each row. Even if its left-right choices change, as long as it ends at the same final pair, both side triangles remain safe.

## Round 7

### Student

I am getting confused. My path is in row five, column 3, whose children are in row six, columns 3, 4. So the final pair should be in row six, not row five, right? From row r to row five, column 3, there are 5-r steps left. Why does the formula use 6-r? Does this affect the reason for excluding side cells? Please correct the row indices for my path, then explain only why the left vertex in row five, column 1 cannot be an A collected at some step. I can try the right side analogously.

### Teacher

You are right; I wrote the row indices incorrectly previously. For your path:

- The path is in row 5, column 3;
- Its children are in row 6, columns 3, 4;
- The “final pair” is therefore in row 6, not row 5.

From row \(r\) to row 5, column 3, there are indeed only \(5-r\) steps. The earlier \(6-r\) applies to reaching row 6.

Now consider only the left vertex: row 5, column 1.

For it to be an \(A\) collected at a step, it must be a child of some path cell in row 4. The only possible parent is row 4, column 1, because:

```text
Row 4 column 1
       ↙   ↘
Row 5 column 1  Row 5 column 2
```

But if the path occupies row 4, column 1, its next step can only reach column 1 or 2 of row 5, not your specified column 3 in row 5.

Thus, as long as the path ultimately reaches row 5, column 3, row 5, column 1 cannot be a collected \(A\). That is why the left vertex is safe.

## Round 8

### Student

Looking at the parent makes this understandable. Checking row six next: its columns 1, 2 can only be children of row five, columns 1 or 2, but the path is in row five, column 3, so they cannot be collected either. On the right, row five column 5 can only have row four column 4 as its parent, which cannot reach row five column 3; row six columns 5, 6 are also avoided. This is clearer than the earlier diagram with multiple Ps. My understanding is to force the collected numbers to be 1 to 2018, then find a large triangle without them and add within it to exceed the maximum. But I still cannot organize these six-row checks into a proof for arbitrary rows. Could you finally supply that connection using accurate row and column indices? Please do not treat my following these checks as already being able to prove it independently.

### Teacher

Your overall understanding is correct. We are just generalizing the six-row column indices to \(n\) rows.

Suppose the accumulation path finally reaches column \(p\) in row \(n-1\). The final bottom pair is then in row \(n\), columns \(p,p+1\).

If the path is in row \(r-1\), column \(q\), reaching column \(p\) in row \(n-1\), with each step moving at most one cell right, requires:

\[
q\le p\le q+(n-r).
\]

The other cell \(a_r\) collected in this row is in row \(r\), column \(q\) or \(q+1\). The inequality gives its column range:

\[
[p-(n-r),\ p+1].
\]

This is the “middle strip” containing all collected cells.

Now consider the left triangle. Its cells satisfy:

\[
j+(n-r)\le p-1,
\]

or

\[
j\le p-(n-r)-1.
\]

This lies strictly to the left of the middle strip, so the left triangle contains no \(a_r\). Similarly, the right satisfies \(j\ge p+2\), so contains no \(a_r\) either.

Therefore:

1. The collected \(a_1,\ldots,a_n\) are forced to be exactly \(1,\ldots,n\);
2. At least one complete triangle on the sides contains none of these small numbers;
3. Every number in that triangle exceeds \(n\);
4. Its row count is at least
   \[
   \left\lceil\frac{n-2}{2}\right\rceil.
   \]

This completes the connection from specific six-row checks to the general proof. You have now understood its key structure, but that indeed does not yet mean you can write the entire proof independently.

### Student

Substituting six rows and p=3: collected cells in row five lie in columns 2 to 4, so columns 1, 5 are safe; those in row six lie in columns 3 to 4, so columns 1, 2 and 5, 6 on the sides are safe too. The general expression now matches the specific checks. With 2018 rows, a side has at least 1008 rows, and its 1008 collected distinct numbers all exceed 2018, so their minimum values are 2019 through 3026. Their sum exceeds 2037171, so the triangle cannot exist. I can now follow and explain this reasoning, but still cannot derive the middle-strip formula myself from scratch. Breaking it down by parent cells helped greatly; the earlier multiple-P diagram and incorrect row indices made me take extra detours. I want to stop here today. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
