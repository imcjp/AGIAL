# P03 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P03 |

## Round 1

### Student

Teacher, I tried two rows first: 1 and 3 below gives 2 above, using exactly 1, 2, 3, which should follow the rules, right? But 2018 rows certainly cannot be handled by continual trials. I want to try three rows first but do not know whether to choose bottom numbers or start with the maximum. Could you give me a direction and let me try myself?

### Teacher

The two-row arrangement is correct: \([1,3]\) has difference \(2\).

For three rows, start with the maximum. Let the bottom be \(a,b,c\); the middle is \(|a-b|\), \(|b-c|\), and the top their difference.

Notice that no "difference" can equal 6 (there is no 0 in the triangle), so 6 must be at the bottom. By left-right symmetry, first put 6 in the bottom-left corner, try the other two bottom numbers, and check whether you used exactly 1 to 6.

## Round 2

### Student

I tried bottom 6, 1, 4, giving middle 5, 3 and top 2, exactly all of 1 to 6. The idea that the maximum must be at the bottom is useful. But left-right symmetry only exchanges right and left, does it not? If 6 is in the bottom middle, reflecting still leaves it in the middle, so we cannot just say it is in the bottom-left corner. I have found a three-row example; how do we next use the maximum to judge 2018 rows? Merely knowing it is at the bottom seems insufficient.

### Teacher

You are completely right; my earlier "bottom-left corner" statement needs correction: a bottom-middle maximum remains in the middle after reflection. Your three-row example

\[
[2],\quad [5,3],\quad [6,1,4]
\]

is correct.

For 2018 rows, the key is not only locating the maximum but tracking a path downward from the top:

1. At each next row, choose the larger child, called \(b_r\), and call the other \(a_r\).
2. Since the upper cell is their difference, the larger child satisfies  
   \[
   b_r=b_{r-1}+a_r.
   \]
3. Thus the bottom endpoint equals  
   \[
   a_1+a_2+\cdots+a_n.
   \]

Now consider: how many distinct positive integers are these \(a_r\), and what is their minimum sum? The endpoint also cannot exceed the whole-triangle maximum \(N\).

This turns the local observation "the maximum must be at the bottom" into a sum constraint on the whole path.

## Round 3

### Student

I can try following larger numbers: in the three-row example, from 2 to 5 to 6, the unchosen numbers are 3 and 1, so 6=2+3+1. Your sum should also include the top, right? For 2018 rows there are 2017 steps plus the top, giving 2018 distinct positive integers, with minimum sum 1+2+…+2018=2037171, exactly N. That does not exceed N, so does it still fail to establish nonexistence? If equality holds, does that mean the numbers must be 1 to 2018? I have not thought beyond that yet. Please explain this step first without jumping too far.

### Teacher

Your correction is right: the top must also count in the path, giving 2018 numbers.

Let them be \(a_1,\ldots,a_{2018}\). They:

- Are positive integers;
- Are distinct;
- All come from \(1,\ldots,N\) in the triangle.

Thus

\[
a_1+\cdots+a_{2018}\ge 1+2+\cdots+2018=N.
\]

Conversely, this sum is the endpoint, and no triangle number exceeds \(N\), so

\[
a_1+\cdots+a_{2018}\le N.
\]

Combining these forces equality:

\[
a_1+\cdots+a_{2018}=N.
\]

Why does this imply precisely \(1,2,\ldots,2018\)?

Because the smallest possible total of 2018 distinct positive integers is

\[
1+2+\cdots+2018.
\]

If any number exceeds 2018, the total strictly exceeds this minimum. Since the total equals the minimum, we must have

\[
\{a_1,\ldots,a_{2018}\}=\{1,2,\ldots,2018\}.
\]

This step alone still gives no contradiction; it tells us that this path already "exhausts" the smallest 2018 numbers in the triangle.

## Round 4

### Student

I understand: for three distinct positive integers the minimum is 1, 2, 3; changing to 1, 2, 4 increases the sum by 1. But I need to distinguish that 1 to 2018 are the top and the unchosen number in each row, rather than all visited cells; my small example also visited 5, 6. These small numbers are used, but the remaining cells may contain large numbers, so where is the contradiction? Could you identify the next specific positions to check? I want to calculate their differences myself.

### Teacher

Your distinction is accurate: \(1,\ldots,2018\) are not all "cells visited by following larger numbers." In particular:

- The top is \(a_1\);
- Each row's other child, not chosen for the "larger-number path," is \(a_r\);
- The larger-number path itself also contains numbers such as \(5,6\).

Next check "the final child pair when the larger-number path reaches the bottom."

Suppose these bottom cells occupy columns \(p,p+1\). Their upper cell is the path's penultimate-row cell. Now look at the two side triangles beside this pair:

- Left: the remaining triangle to its left;
- Right: the remaining triangle to its right.

First draw them in the three-row example, then ask:

> Once \(1,2,3\) occur in the top or each row's "unchosen cells," can they still occur in a side triangle?

If side-triangle numbers really must exceed 2018, descend through larger children inside it again. This side triangle has at least

\[
\left\lceil\frac{2018-2}{2}\right\rceil=1008
\]

rows. First calculate its path endpoint's minimum value.

## Round 5

### Student

If it really has 1008 rows and everything exceeds 2018, the top plus 1007 unchosen numbers sum to at least 2019+…+3026. I get (2019+3026)×1008÷2=2542680, already exceeding 2037171 and causing a contradiction. That calculation is fine, but I cannot see the side triangle clearly: my three-row example ends at 6, the final pair is 6, 1, and only 4 remains on the right. How can the large triangle guarantee a full 1008 rows untouched by the small numbers? Can the final pair's position alone guarantee avoidance above too? Please draw four or five rows, labeling the path and side triangle; this is my main obstacle.

### Teacher

Your calculation is exactly right. The crucial distinction is that a side triangle is not "a region directly above the final pair," but "a region whose bottom-row descendants all lie to the left or right of the final pair."

Use five rows, with the final bottom pair in cells 3, 4:

```text
                    ·
                 ·     ·
              ·    ·    ·
           ·    ·    ·    ·
        L    L    B    B    R
```

Here:

- \(B,B\) is the final child pair;
- \(L\) is the left triangle;
- \(R\) is the right triangle;
- The middle dotted region is the "strip" leading to \(B,B\).

More precisely, a cell in row \(r\), column \(j\), covers the following bottom-column range:

\[
[j,\;j+5-r].
\]

Left-triangle cells satisfy

\[
j+5-r\le 2,
\]

so all their bottom descendants lie left of cell 3; right-triangle cells satisfy

\[
j\ge 5.
\]

Since the path cell in row \(r-1\) eventually reaches cells 3, 4, it must satisfy

\[
q\le 3\le q+5-r.
\]

Its unchosen sibling falls only within this "strip," outside both side triangles.

Thus, although the path may move left and right above, it and every row's unchosen \(a_r\) remain in this strip. Side-triangle cells are not occupied by \(1,\ldots,2018\) and must contain numbers greater than 2018. That is why another path inside a side triangle gives a sum of 1008 "large numbers."

## Round 6

### Student

Bottom coverage makes it clearer. In five rows with the final pair at columns 3, 4, the left base is columns 1, 2, and the first cell of row four also belongs to the left triangle, making two rows on the left and only one on the right. I am thinking that an unchosen cell is adjacent to the chosen cell in a row; even if it cannot reach the final 3, 4, its coverage still touches at least one of 3 or 4, so it cannot lie entirely outside. Is that right? With 2018 rows, removing the final pair leaves 2016 bottom cells, totaling 2016 on both sides, so at least one side has 1008 cells and therefore 1008 rows. If the pair is at the far edge, the other side has 2016 rows, which is stronger. Now I can connect the numerical lower bound and positions, but your diagram did not label row four's first cell L; initially I thought there were only the two bottom Ls. Please confirm my added position and reasoning.

### Teacher

Your understanding is basically correct, and your added five-row position is right: the first cell of row four does belong to the left triangle. Its bottom descendants cover only cells 1, 2 and cannot reach the final pair, cells 3, 4.

Your judgment about the "unchosen adjacent cell" is also key: although it may lie toward one side, its adjacency to a path cell still leading to the final pair forces its bottom coverage to intersect the strip at the final two columns, preventing it from lying completely in an outer triangle.

One small distinction needs precision:

- Excluding the final pair leaves \(2016\) bottom cells;
- The left and right bottom widths sum to \(2016\), so at least one reaches \(1008\);
- This corresponds to a side triangle with at least \(1008\) rows, rather than saying the side triangle has only 1008 cells.

For example, with five rows and the final pair in columns 3, 4:

```text
                    ·
                 ·     ·
              ·     ·     ·
           L     ·     ·     ·
        L     L     B     B     R
```

The left has two rows: the \(L\) in row four and the two bottom \(L\) cells; the right has one row. Both your added position and reasoning are correct.

### Student

I will stop here today. My judgment now is nonexistence: descending through larger children the first time makes the top plus the unchosen numbers in all rows exhaust exactly 1 to 2018; outside the final child pair at least one 1008-row side triangle remains, avoiding these small numbers. Descending through its larger numbers again gives an endpoint at least 2542680, exceeding the whole-triangle maximum, a contradiction. The 1008 is the row count and bottom width, not the total cell count. Calculating three rows first and then examining positions through coverage helped me; after adding L, the diagram was clearer too. I might not immediately think of finding a side triangle myself, but can now follow the explanation of the contradiction.

### Teacher

This teaching session has been confirmed as ended.
