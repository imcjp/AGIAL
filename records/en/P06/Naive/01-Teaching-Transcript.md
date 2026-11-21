# P06 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | Naive |
| Participant ID | P06 |

## Round 1

### Student

Teacher, I want to confirm the rules. With two rows, bottom 1, 3 gives top 2, using exactly 1 to 3, so at least small triangles are possible. But with 2018 rows I do not know whether to start constructing or seeking a contradiction. Could you give a three-row exercise without the answer, so I can try identifying the key constraints?

### Teacher

Yes. First try this three-row exercise without the answer:

Use \(1,2,3,4,5,6\) once each to form a three-row number triangle:

\[
\begin{array}{c}
\Box\\
\Box\quad\Box\\
\Box\quad\Box\quad\Box
\end{array}
\]

The rule remains: an upper cell equals the absolute difference of its two adjacent cells immediately below.

Focus on these observations:

1. What relates the top cell to the second-row numbers?
2. After selecting a “larger-child” path, which numbers sum to its endpoint?
3. Which magnitudes constrain such a path?

First find a feasible arrangement, then write what you consider the key constraint.

## Round 2

### Student

I tried bottom 1, 6, 4, second row 5, 2, and top 3, all six numbers once each. Top 3 equals 5 minus 2, so larger 5 equals 3 plus 2; then 6 equals 5 plus 1, giving endpoint 6=3+2+1. It feels as if large numbers must be below, but that is only this example. Do all numbers increase along a path? If so, how can that constrain 2018 rows rather than just describe the triangle’s shape? Please clarify exactly which cells are added first, without jumping to large calculations.

### Teacher

You have grasped the key, but distinguish “path numbers” from “all triangle numbers.”

Define a path from the top:

- Call the top \(b_1\);
- In the next row choose the larger of the two cells immediately below, calling it \(b_2\);
- From \(b_2\), again choose the larger lower cell, calling it \(b_3\);
- Continue likewise.

At each step call the unchosen cell \(a_r\). Since the absolute difference of the lower cells equals the upper and \(b_r\) is the larger,

\[
b_r-b_{r-1}=a_r,
\]

or

\[
b_r=b_{r-1}+a_r.
\]

Values therefore strictly increase along this “larger-child path.” This does not mean every adjacent path in the whole triangle increases, only the path we deliberately select.

Your example is precisely:

\[
b_1=3,\quad a_2=2,\quad b_2=5,\quad a_3=1,\quad b_3=6,
\]

so

\[
6=3+2+1.
\]

What is actually “collected along the path” is

\[
a_1=b_1,\ a_2,\ a_3,
\]

rather than all the path’s \(b_r\). Next answer just one question: with three rows, why must these three \(a\) values be distinct positive integers?

## Round 3

### Student

The three a values lie in rows one, two, three, hence different cells. The problem requires global distinctness and positive integers. This distinction makes it clear: we add the top and each unchosen cell, not 3, 5, 6. With 2018 rows we collect 2018 distinct positive integers whose minimum sum is 1+2+…+2018, exactly the global cell count 2037171. But the endpoint is also at most 2037171, apparently forcing only equality, not a contradiction. I originally thought “rapid growth of large numbers” implied impossibility, but now see a missing step. Which cells does equality constrain?

### Teacher

Yes, “increasing along the path” alone is insufficient; the real constraint comes from equality.

Suppose there are \(n\) rows. The collected \(a_1,\dots,a_n\) are \(n\) distinct positive integers, so

\[
a_1+\cdots+a_n\ge 1+2+\cdots+n=N.
\]

Meanwhile, path endpoint \(b_n\) is a number in the whole triangle, so

\[
b_n\le N.
\]

But

\[
b_n=a_1+\cdots+a_n.
\]

Both sides must therefore equal \(N\), forcing:

\[
\{a_1,\dots,a_n\}=\{1,2,\dots,n\},
\qquad b_n=N.
\]

Thus the constraint is more than “one path increases”:

- The “unchosen cells” in each row along the path occupy all small numbers \(1,\dots,n\);
- The path endpoint occupies the maximum \(N\);
- Global distinctness prevents all other cells using \(1,\dots,n\), so they must exceed \(n\).

In the three-row example, collected \(3,2,1\) occupy all small numbers \(1,2,3\), and the endpoint is \(6\). Next observe whether there is a triangular region beside this path avoiding all those small numbers. That is where a second lower bound arises.

## Round 4

### Student

I can connect equality: if any of the 2018 distinct collected numbers exceeded 2018, the sum would exceed the minimum, so they must be exactly 1 to 2018. But I still cannot see your triangular region. My three-row path 3→5→6 goes left then right, leaving only bottom-right 4. A large path can also turn; how can we guarantee a sufficiently large complete triangle remains beside it? Could you draw a smaller example with row indices and left-right positions, showing which cells necessarily avoid the collected small numbers? I need specific positions here; “beside it” alone cannot be checked.

### Teacher

Coordinates can clarify “avoidance.” Denote row \(r\), cell \(j\) by \((r,j)\), with \(1\le j\le r\).

Suppose the final step uses bottom columns \(p,p+1\), so the path passes through column \(p\) of the penultimate row. For a path cell in row \(r-1\), let its column be \(q\). Reaching column \(p\) requires

\[
q\le p\le q+n-r.
\]

The unchosen \(a_r\) in this row must therefore lie in the strip

\[
p-(n-r)\le j\le p+1.
\]

For example, take \(n=8\), with final pair in columns \(4,5\), so \(p=4\). Then:

- \(a_8\) in row \(7\) can only lie near columns \(4\) or \(5\);
- \(a_7\) in row \(6\) can only lie in columns \(2\) through \(5\);
- \(a_6\) in row \(5\) can only lie in columns \(1\) through \(5\);
- Higher up, the allowed range widens, but never enters the complete regions on the far left or right.

The schematic below uses `Strip` for possible collected small-number positions; the left and right regions are completely avoided:

```text
                 ·
              Strip Strip
           Strip  Strip  Strip
        Left Strip Strip Strip Right
     Left Left Strip Strip Right Right
  Left Left Left Strip Strip Right Right Right
```

The key is not whether the path turns, but that reaching the final child pair constrains all \(a_r\) to the same “strip.” Complete small triangles form on its left and right; choosing the larger gives at least

\[
\left\lceil\frac{n-2}{2}\right\rceil
\]

rows.

These regions contain none of \(1,\dots,n\), so all their numbers exceed \(n\). This is the second constraint arising after equality.

## Round 5

### Student

Coordinates are easier to check than the schematic, but are the row indices wrong? a8 should be in row 8, not 7. With your range, n=8, p=4 gives a6 in row 6 columns 2 to 5, a7 in row 7 columns 3 to 5, and a8 in row 8 column 4 or 5. Then row 6 column 1, row 7 columns 1 to 2, and row 8 columns 1 to 3 really form a three-row left triangle. The right also has three rows starting at row 6 column 6. Is this correction right? If so, 2018 rows yield a 1008-row triangle whose numbers all exceed 2018. Following larger children there, can we sum 1008 numbers exceeding 2018 to obtain a contradiction with the maximum? I have not calculated the bound clearly; please check it.

### Teacher

Yes, your row correction is right: \(a_8\) is in row 8. With \(n=8,p=4\), both sides indeed have complete three-row triangles.

Generalizing to \(n=2018\):

\[
\ell=\left\lceil\frac{2018-2}{2}\right\rceil=1008.
\]

This triangle avoids \(1,\dots,2018\), so its \(1008\) collected larger-child-path numbers are at least

\[
2019,2020,\dots,3026.
\]

Its endpoint is at least

\[
2019+2020+\cdots+3026
=\frac{1008(2019+3026)}2
=2\,542\,680.
\]

But the whole triangle uses only \(1\) to

\[
N=\frac{2018\cdot2019}{2}=2\,037\,171,
\]

so no cell can exceed \(2\,037\,171\). Thus

\[
2\,542\,680>2\,037\,171,
\]

a contradiction.

Therefore the assumption that such a 2018-row number triangle exists is false: a 2018-row anti-Pascal number triangle does not exist.

## Round 6

### Student

I calculated 504×5045=2542680, which really exceeds 2037171. I understand “at least 2019 through 3026” as term-by-term comparison after sorting collected numbers, not that they can only take those 1008 values. The proof chain now connects: equality on the first path uses all small numbers, the side region has none, and the second path is forced to grow too large. To avoid merely repeating it, I checked three rows: only one side row is guaranteed, collecting one number at least 4, but 4≤6 gives no contradiction, consistent with my three-row construction. One scope question: proving impossibility for 2018 does not mean that failure of this method to contradict three rows conversely proves three-row existence, right? The specific coordinates let me check the regions; the earlier schematic instead confused me somewhat.

### Teacher

Yes, both judgments are correct.

“At least \(2019\) through \(3026\)” gives term-by-term lower bounds after sorting. The \(1008\) numbers need only be distinct and greater than \(2018\), not exactly those numbers.

With three rows the side triangle has only one row, lower bound \(4\), and \(4\le6\), so the method merely yields no contradiction and cannot establish existence alone. Three-row existence is proved directly by your specific arrangement

\[
\begin{array}{c}
3\\
5\quad2\\
1\quad6\quad4
\end{array}
\]

Therefore distinguish strictly:

- 2018 rows: coordinate avoidance plus two path sums give a contradiction, hence impossibility;
- Three rows: a specific construction exists, hence feasibility;
- General row counts: this contradiction provides a necessary condition, without automatically classifying every count.

### Student

I will stop here today. I can explain the main grounds for impossibility with 2018 rows and distinguish absence of contradiction from existence by construction. I still need to write the coordinate-region derivation with a reference and cannot yet say I could independently discover the whole proof. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
