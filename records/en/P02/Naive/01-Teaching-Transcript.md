# P02 · Naive: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | Naive |
| Participant ID | P02 |

## Round 1

### Student

Teacher, this triangle is too large. I want to try two rows first. I put 1 and 3 below and 2 above because 3 minus 1 is 2. That uses 1, 2, 3 once each, right? I do not quite understand the two lines at the sides. Do they mean always subtracting the smaller from the larger? Please explain a little at a time first.

### Teacher

Yes, your two-row example is correct:

```text
    2
  1   3
```

The upper number equals the absolute difference between the adjacent numbers below:

\[
|3-1|=2
\]

Thus 1, 2, 3 are indeed each used once.

The "lines at the sides" mean the upper cell connects to the two adjacent cells below. The calculation does not fix which subtracts from which; it takes the absolute value, or "larger minus smaller":

- Left relationship: \(|2-1|=1\)
- Right relationship: \(|3-2|=1\)

However, the actual triangle rule requires each upper cell to equal the difference of the two adjacent cells directly below; your two-row example satisfies it.

## Round 2

### Student

By two lines I meant the vertical bars outside |3-1|. Now I know they mean larger minus smaller. But when you also calculated 2 minus 1 and 3 minus 2, I became confused: do those two 1s need to be entered too? Could you first explain only which numbers to enter? Then give me a small three-row bottom row to try, without telling me the upper numbers yet.

### Teacher

I understand: you mean the connecting lines in the diagram, not additional numbers to enter.

Enter numbers only in the "cells." The two lines merely mean:

- One upper cell corresponds to the left and right cells below;
- Subtract the two lower numbers and take the absolute value;
- Enter the calculated result in the upper cell.

Thus intermediate calculation results do not occupy extra cells.

Try this bottom row for a three-row number triangle:

```text
      ?
    ?   ?
  5   7   1
```

First calculate and enter only the two cells above; you may also try continuing to the top yourself for now.

## Round 3

### Student

7 minus 5 is 2 and 7 minus 1 is 6, so the middle contains 2 and 6, and the top is 6 minus 2, or 4. I can follow calculating two neighbors at a time. But I still meant the vertical bars outside the expression, not connecting lines in the diagram. Also, this triangle contains 7 and lacks 3; is it only calculation practice rather than the kind the problem requires? Should three rows use 1 to 6?

### Teacher

Your calculations are exactly right:

\[
|7-5|=2,\quad |7-1|=6,\quad |6-2|=4
\]

The "vertical bars outside the expression" are absolute-value symbols, for example \(|3-1|\). They mean taking a positive result, rather than lines in the triangle, and require no number entries.

That three-row example only practiced calculation, so it used 5, 7, 1 and did not meet the complete problem's requirement of "using all consecutive numbers."

A three-row triangle has:

\[
1+2+3=6
\]

cells, so following the original rules requires exactly 1 to 6, each once. You have identified two levels:

1. First check absolute differences between adjacent cells;
2. Then check whether all cells use exactly the required numbers.

## Round 4

### Student

Then I tried bottom row 1, 6, 2, giving 5, 4 in the middle and 1 at the top. The 1 repeats and 3 is missing, so it fails. I can check a small triangle now, but one failed attempt does not mean every arrangement fails, right? With so many rows in 2018, I do not know how to begin judging it. Could you guide me through one small point that helps judge it? Please do not give many steps at once.

### Teacher

Yes, one failed bottom row establishes only that "this arrangement fails," not that all arrangements fail.

First consider a useful small observation. Take this four-row triangle:

```text
          4
       2     6
     5   7   1
   8   3  10  9
```

Starting at the top 4, always move to the larger child:

\[
4\rightarrow6\rightarrow7\rightarrow10
\]

At every step, the larger number equals "current number + other child":

\[
6=4+2,\quad 7=6+1,\quad 10=7+3
\]

Thus the final 10 is actually:

\[
10=4+2+1+3
\]

This shows that, in judging a large triangle, we can study "a top-to-bottom path" rather than enumerate all arrangements from the start. Next we can focus only on why those numbers on the path must be distinct positive integers.

## Round 5

### Student

I followed the calculation: 6 minus 2 is 4, so 6 is also 4 plus 2; adding 1 and then 3 really reaches 10. I can understand concrete equations like this. But the bottom differences are 8 minus 3 giving 5, 3 and 10 giving 7, and 10 and 9 giving 1. Did I find two 4s in the whole triangle? The top 4, and another… I counted again and there is no second 4. Is something missing besides the number 4? I am getting confused counting. By "must be distinct," do you mean the problem already forbids repetition? Also, why must this path always choose the larger number? Can we not add when choosing the smaller? Please explain choosing the larger first.

### Teacher

You counted correctly: this four-row triangle uses exactly 1 to 10 once each, with no second 4.

The problem already requires "each of 1 to \(N\) once," so numbers must be distinct. Here \(N=10\).

As for choosing the larger: let the upper cell be \(u\) and the lower cells \(x<y\). The rule is

\[
u=|y-x|=y-x
\]

so:

\[
y=u+x
\]

Thus the larger child \(y\) can be expressed as "upper cell \(u\) plus other child \(x\)," allowing continuous accumulation.

Choosing the smaller \(x\) gives only:

\[
x=y-u
\]

This is subtraction and cannot create that same continuous additive relationship.

## Round 6

### Student

I cannot quite connect the letters together. Returning to 4 with 2, 6 below is clearer: 4 plus 2 gives 6, but moving to 2 does not add. Starting from 2 in row two, choosing 7 below and then 10 gives 2 plus 5 plus 3 equals 10, right? I can follow a path now. But how does reaching 10 this way relate to whether 2018 rows can be arranged? Please use small numbers first to tell me what kind of arrangement this path can rule out.

### Teacher

Yes, your path calculation is correct:

\[
2+5+3=10
\]

From 2 you first choose the larger 7, with 5 as the other number; from 7 you choose the larger 10, with 3 as the other number.

This method can rule out an entire class of arrangements. A four-row triangle has 10 cells, using 1 to 10. A "larger-number" path accumulates 4 distinct positive integers.

The minimum sum of 4 distinct positive integers is:

\[
1+2+3+4=10
\]

The endpoint cannot exceed 10, so it must use exactly 1, 2, 3, 4 and finally reach 10.

Thus if this path in a four-row arrangement is forced to sum to 11, or already contains a larger number such as 5, it cannot be a valid triangle using 1 to 10.

For 2018 rows the same idea applies, only with a longer path whose additive lower bound grows beyond the whole-triangle maximum.

## Round 7

### Student

I cannot quite distinguish whether you mean the visited numbers or the summands. The path from the top added 4, 2, 1, 3, summing to 10, but visited 4, 6, 7, 10, including numbers greater than 5, and it is still valid. Should we consider only the summands? Also, I cannot calculate the cell count for 2018 rows. Why would the minimum sum exceed the maximum? With four rows they are exactly equal.

### Teacher

You have distinguished correctly; these are two groups:

- Visited numbers: \(4,6,7,10\)
- Summands: \(4,2,1,3\)

It is the second group that is actually "accumulated." Large numbers among visited cells are no contradiction.

With four rows, the minimum sum of 4 distinct positive integers is:

\[
1+2+3+4=10
\]

The whole-triangle maximum is also 10, so they are only "exactly equal," without contradiction.

The first path with 2018 rows likewise yields only "exact equality." The key is then to find a small side triangle whose accumulated numbers all exceed 2018. It has at least 1008 such numbers, giving the minimum sum:

\[
2019+2020+\cdots+3026=2542680
\]

But the whole-triangle maximum is only:

\[
1+2+\cdots+2018=2037171
\]

Thus:

\[
2542680>2037171
\]

This is the actual impossibility: no cell in the same triangle can both be no greater than 2037171 and be required to reach at least 2542680.

## Round 8

### Student

With these two large numbers I can only see that 2542680 exceeds 2037171; I cannot check such a long sum myself. But the small side triangle appeared suddenly, and I do not know where it is or why all its numbers exceed 2018. Could you circle it on the four-row diagram above? If four rows do not illustrate it, first use a smaller example I can count clearly, rather than jumping straight to 1008 numbers.

### Teacher

That is a good question. The four-row diagram cannot fully display this contradiction because its side regions are too small; let us first examine "why the numbers inside are large."

Suppose a path in a small triangle has already selected:

\[
1,\ 2,\ 3
\]

Since the problem requires 1 to 6 each once, the numbers 1, 2, 3 already occupy this path and its paired positions. Any small triangle completely avoiding that region can therefore contain only:

\[
4,\ 5,\ 6
\]

so every number inside exceeds 3.

The same applies to 2018 rows, except that the first path exhausts:

\[
1,2,\ldots,2018
\]

Thus every number in a small triangle completely avoiding that path strip must exceed 2018.

A "small side triangle" means: first look at the path leading to some adjacent bottom pair; if an entire triangle remains to the strip's left or right, that region is the small side triangle. Its being called "side" is not the key; what matters is its non-overlap with the first path strip.

## Round 9

### Student

I understand that once 1, 2, 3 are used, other cells cannot reuse them. But there is still no diagram for the "path strip," so I cannot find your region. In the original four rows, crossing out the summands 4, 2, 1, 3 leaves 5, 6, 7, 8, 9, 10, all indeed greater than 4. Have I crossed them out correctly? Could you label only those crossed-out cells on that diagram, then let me find a remaining triangle? I want to point it out myself once, rather than just hear you say a region exists.

### Teacher

Your crossing out is correct: it removes "the summands" \(4,2,1,3\), rather than the whole visited path.

In the original diagram:

```text
          [4]
       [2]   6
      5    7   [1]
    8   [3]  10   9
```

The remaining numbers are indeed:

\[
5,6,7,8,9,10
\]

But first note a detail: in this four-row example, the remaining cells do not form a complete, clean small triangle. Your "crossing out" is right, but the example is still insufficient to directly circle the side triangle referred to in the proof.

First try finding which remaining positions connect into a small triangle. It is fine if you cannot; that is precisely where the four-row diagram is too small.

### Student

I looked: below 5 are 8 and 3, with 3 crossed out; below 7 are 3 and 10, again including 3; below 6 are 7 and 1, with 1 crossed out. So I found no upper cell with both lower cells uncrossed. Labeling is clearer than only saying "path strip," but I still do not know why one must be found with 2018 rows. Let us stop here today. I can calculate small triangles and check repetitions, but still cannot explain myself why 2018 rows do not work.

### Teacher

This teaching session has been confirmed as ended.
