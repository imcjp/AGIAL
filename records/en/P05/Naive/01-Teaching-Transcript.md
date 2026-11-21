# P05 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | Naive |
| Participant ID | P05 |

## Round 1

### Student

Teacher, I want to confirm the rules: with two rows, bottom numbers 1 and 3 give 2 above, using 1 to 3 once each. That works, right? But I do not know where to start judging existence for 2018 rows, and cannot keep trying arrangements forever. Could you guide me through a small example to identify what to notice?

### Teacher

Yes, the two-row example works:

```text
  2
1   3
```

Because \(|3-1|=2\), and 1, 2, 3 are each used once.

Now consider a four-row example:

```text
       5
     7   1
   8   3  10  9
```

Check cell by cell:

- \(|8-3|=5\)
- \(|3-10|=7\)
- \(|10-9|=1\)

Thus it is indeed a valid arrangement, using 1 to 10 exactly once each.

This small example reminds us of two points:

1. Locally, each upper cell depends only on the difference of a pair below.
2. Globally, all numbers must also be used exactly once; checking a few differences is insufficient.

Thus 2018 rows cannot be handled by endless trials. The key is to derive a “necessary global numerical condition” from local differences, then judge whether that condition contradicts itself.

## Round 2

### Student

Teacher, I checked it: bottom row 8, 3, 10, 9 should give 5, 7, 1 above, but the diagram says 7, 1, and another row above is missing. Continuing, 5, 7, 1 gives 2, 6 above and 4 at the top. So bottom to top should be 8, 3, 10, 9 / 5, 7, 1 / 2, 6 / 4, using exactly 1 to 10. Did the diagram omit something? Also, I still do not know specifically what “global numerical condition” means. I can calculate every difference but do not know how to connect them. Could you give just one small next-step hint for me to try?

### Teacher

Your check is correct; my earlier diagram omitted two rows. The correct four-row triangle is:

```text
        4
      2   6
    5   7   1
  8   3  10  9
```

Your calculated relationships are completely correct.

Here is a next-step hint:

Start at the top and always follow “the larger lower cell.” Notice:

\[
\text{larger lower cell}
=
\text{upper cell}
+
\text{smaller lower cell}.
\]

In this four-row example, the path is:

\[
4\to6\to7\to10.
\]

Record the “smaller lower cell” at each step and see whether bottom number 10 can be written as a sum of “the other number in each row along the path.” Then consider how large these numbers must be with \(n\) rows.

## Round 3

### Student

I tried writing 6=4+2, 7=6+1, 10=7+3, so 10=4+2+1+3. The summands are the top and each smaller lower cell, 4 numbers in total, rather than the path values 4, 6, 7, 10 themselves. Their positions differ and repetition is prohibited, so the minimum is 1+2+3+4=10. Likewise, with n rows the bottom number is at least 1+2+…+n=n(n+1)/2, but the largest number is also exactly that. Does this force equality? If so, what does equality constrain in the whole triangle? I currently see only that these summands must be 1 to n, not a contradiction.

### Teacher

Completely correct. The key “equality” conclusion is:

\[
b_n\ge 1+2+\cdots+n=N,
\qquad b_n\le N.
\]

Equality is the only possibility. Thus:

- The \(n\) accumulated numbers must be exactly \(1,2,\ldots,n\);
- The path endpoint must be the global maximum \(N\);
- Other positions cannot contain \(1,\ldots,n\), so must all exceed \(n\).

This is the first global constraint obtained from “local subtraction.”

Next we need only examine positions: the path leading to the final bottom pair occupies only a middle strip. On its sides there is at least one larger side triangle containing none of \(1,\ldots,n\), so every number there exceeds \(n\).

Hint: if this side triangle has \(\ell\) rows, what minimum bottom endpoint follows from another larger-child path within it? Comparing it with the whole triangle’s maximum \(N\) yields a contradiction for 2018 rows.

## Round 4

### Student

If the side triangle has ℓ rows, the earlier method initially gives a bottom endpoint at least (n+1)+(n+2)+…+(n+ℓ)=nℓ+ℓ(ℓ+1)/2, because its ℓ summands are distinct and all exceed n. Is this lower bound correct? But I still cannot see “at least one larger side triangle.” Could you mark its cells in the previous four-row diagram, then explain the general minimum row count? I cannot draw it from “strip” alone and worry about including the path’s neighboring 1, 2, 3.

### Teacher

That lower bound is correct:

\[
(n+1)+(n+2)+\cdots+(n+\ell)
= n\ell+\frac{\ell(\ell+1)}2.
\]

In the four-row example, follow:

\[
4\to6\to7\to10,
\]

whose final child pair is bottom numbers \(3,10\). The path and its “other-side” numbers \(4,2,1,3\) occupy a slanting strip:

```text
        4
      2   6
    5   7   1
  8   3  10   9
          ↑  ↑
```

In this example, each side triangle has only one cell:

- Left: \(8\)
- Right: \(9\)

Neither belongs to \(1,2,3,4\), so both exceed 4.

In general, if the final bottom child pair occupies columns \(p,p+1\):

- The left triangle has \(p-1\) rows;
- The right triangle has \(n-p-1\) rows.

Their row counts sum to \(n-2\), so the larger has at least

\[
\ell\ge \left\lceil\frac{n-2}{2}\right\rceil
\]

rows. The key is precisely that \(1,\ldots,n\) are all occupied by the path strip, leaving side-triangle numbers all greater than \(n\).

## Round 5

### Student

With four rows, p=2, and I can match one cell on each side. But I am not ready to use the general row-count formula directly: if the final bottom pair occupies columns 3, 4, an upper cell over bottom columns 1, 2 forms a two-row triangle. How can we ensure that upper cell and column 2 are not earlier smaller lower cells? The path may turn; can its final position determine the boundary of the whole earlier strip? Could you explain more specifically why “the side triangles contain none of 1 to n”? Without certainty here, even calculating the later lower bound cannot establish nonexistence.

### Teacher

Your concern is correct; “the path can turn” must be addressed explicitly. The key is not whether the path is straight, but each cell’s “bottom-row descendant range.”

Suppose the path occupies column \(q\) in row \(r-1\) and ultimately reaches the final bottom child pair in columns \(p,p+1\). The bottom-row descendant range of cell \(q\) in row \(r-1\) is:

\[
[q,\ q+n-r].
\]

Since the path reaches column \(p\), necessarily:

\[
q\le p\le q+n-r.
\]

Thus the other lower cell selected beside the path at this step can only occupy column \(q\) or \(q+1\), and must lie within

\[
[p-(n-r),\ p+1].
\]

Now consider the left triangle. Its cells satisfy:

\[
j+n-r\le p-1,
\]

meaning their columns lie entirely to the left within

\[
j\le p-(n-r)-1,
\]

which does not intersect the range of path-related numbers.

Similarly, all right-triangle cells satisfy:

\[
j\ge p+2,
\]

also disjoint from path-related numbers.

Thus, even with repeated turns, the produced \(1,\ldots,n\) remain within a strip. Both side triangles avoid it entirely and contain none of \(1,\ldots,n\). All their numbers are therefore at least \(n+1\), establishing the later summation bound.

## Round 6

### Student

The bottom-descendant range is clearer than “strip,” but I am struggling with subscripts: when n=4, r=2, row r−1 is the top and q=1, which should reach bottom columns 1 to 4. Yet your [q,q+n−r] is [1,3]. Is it short by 1? Also, the final pair is p, p+1, so earlier path cells should reach both. Must both conditions be used together? Substituting the later numbers gives ℓ at least 1008 and 2018×1008+1008×1009÷2=2542680, greater than 2037171. Thus if the side triangle is justified, nonexistence follows. I want the earlier subscripts correct too, rather than simply copying the conclusion.

### Teacher

You are right: the earlier subscript is short by 1 and needs correction.

Continuing downward from row \(r-1\), cell \(q\), its bottom-row descendant range is:

\[
[q,\ q+n-(r-1)]
=
[q,\ q+n-r+1].
\]

For example, when \(n=4,r=2,q=1\), the top cell’s descendant range is:

\[
[1,1+4-1]=[1,4],
\]

covering exactly the four bottom columns.

You are also right that both final child columns \(p,p+1\) must be used. The path strip ultimately needs to cover both positions, so:

\[
q\le p,
\qquad
q+n-r+1\ge p+1.
\]

Thus:

\[
p-(n-r)\le q\le p.
\]

The other lower cell beside the path occupies column \(q\) or \(q+1\), so its column lies within:

\[
[p-(n-r),\ p+1].
\]

Both side triangles lie outside this range and therefore indeed contain none of \(1,\ldots,n\).

Your numerical calculation is also correct:

\[
\ell\ge \left\lceil\frac{2018-2}{2}\right\rceil=1008,
\]

\[
(n+1)+\cdots+(n+\ell)
=2018\cdot1008+\frac{1008\cdot1009}{2}
=2542680,
\]

while

\[
N=\frac{2018\cdot2019}{2}=2037171.
\]

The lower bound exceeds the maximum allowed in the whole triangle, establishing the contradiction.

### Student

I will stop here today. I can explain the steps: the larger lower cell equals the upper plus the smaller lower cell, giving a sum of n distinct numbers along the path; equality makes them 1 to n. A side triangle avoiding them then gives a larger lower bound contradicting the maximum. The four-row diagram and substitution at the top helped me check the formula, and I can connect it after correction. But I still need the explanation in front of me to write the general side-triangle column range, and cannot say I can independently discover this proof. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
