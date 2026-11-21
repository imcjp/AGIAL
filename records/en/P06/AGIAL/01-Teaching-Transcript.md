# P06 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | AGIAL |
| Participant ID | P06 |

## Round 1

### Student

Teacher, I want to confirm the rules: with two rows, putting 1, 3 below gives 2 above, using 1 to 3 exactly once each, right? With 2018 rows, my intuition is that repetitions are very likely, but that is not yet a basis for nonexistence. Could you give me a smaller example to try myself, then help me find a starting point for moving from examples to justified judgment? Please do not give the complete proof at once; I need to take complex relationships more slowly.

### Teacher

Yes, your two-row triangle follows the rules:

```text
   2
 1   3
```

Because |3−1|=2, and 1, 2, 3 are each used once. You are also careful about “likely repetition”: repetitions in one or many trials do not exclude every arrangement.

First try a **three-row triangle**. It has 6 cells, using 1 to 6 once each:

```text
      [ ]
    [ ] [ ]
  [ ] [ ] [ ]
```

Choose three bottom numbers yourself and calculate upward using adjacent absolute differences. Check whether the result uses exactly 1 to 6. If the first attempt fails, record any repetitions or missing numbers.

One starting point for moving from examples to justified judgment can be examined slowly: in your confirmed two-row triangle, the top is 2, the larger lower number is 3, and the other is 1. Besides **3−1=2**, we can write **3=2+1**.

After constructing a three-row triangle, start at the top and always follow the larger lower number, seeing whether similar addition relationships hold. Observe just that step first, without rushing to prove the large-triangle conclusion.

## Round 2

### Student

I first tried bottom 1, 6, 2, giving middle 5, 4 and top 1, repeating 1 and missing 3. Replacing bottom 2 with 3 gives middle 5, 3, repeating 3 again. At least I understand that changing the bottom requires checking the whole triangle, not only the top.
Your suggestion to rewrite differences as addition helps. In the first failed example, the path goes from top 1 to 5, then 6, with 5=1+4 and 6=5+1, so it really increases. But numbers repeat, so it is not a valid triangle. I have not found a valid three-row example and am stuck choosing numbers. Could you give the position of one bottom number or a selection clue so I can continue filling? Also, why does increasing along the path constrain 2018 rows? So far I only see that it cannot increase indefinitely, not a specific quantity.

### Teacher

Your checks are correct: bottom 1, 6, 2 repeats 1 and misses 3; changing to 1, 6, 3 repeats the middle 3 and bottom 3, so still fails. Your two addition relationships for the first triangle are correct too; although the triangle is invalid, the local difference and addition relationships still hold.

Here is a clue: **put 1 in the middle of the bottom row of a three-row triangle**. Choose two distinct numbers from 2 to 6 on either side, calculate upward, and check whether the six cells use exactly 1 to 6. Try without worrying about selecting correctly immediately.

The key to connecting “increase” with a specific quantity is **how much each step adds**. On your earlier path:

- Reaching 5 adds neighboring 4: \(5=1+4\);
- Reaching 6 adds neighboring 1: \(6=5+1\).

Combining them gives \(6=1+4+1\). The two 1s reflect repetition in your example.

In a **valid** three-row triangle, the top and the sibling cells left behind during the two downward steps come from different cells, so they are three distinct positive integers. What is the minimum sum of three distinct positive integers? How does this sum relate to the maximum allowed bottom number, 6?

Examine this with three rows first; the same counting approach can later apply to 2018 rows.

## Round 3

### Student

With 1 in the middle I tried 4 and 6 on the sides: middle 3, 5, top 2. The six numbers are 2, 3, 5, 4, 1, 6, each once. The path is 2→5→6, with 6=2+3+1, exactly 1+2+3=6. That clue spared me blindly changing all positions.
Three distinct positive integers have minimum sum 6, and the bottom maximum is also only 6, so the minimum must be attained. Generalizing: 2018 rows give the top plus 2017 siblings, making 2018 distinct positive integers, at least 1+2+…+2018, apparently exactly the global maximum 2037171. Thus the path must end at the maximum and summands must be exactly 1 to 2018, right? That looks restrictive but is not a contradiction yet. Should we next examine which rows contain these small numbers? Please let me handle a specific positional constraint first rather than jumping to the entire proof.

### Teacher

Yes, your generalization holds. Following larger children to the bottom makes the endpoint the sum of the top and 2017 siblings. These 2018 distinct numbers sum to at least \(1+2+\cdots+2018=2037171\), while the endpoint cannot exceed it. Equality is forced: the endpoint is the maximum, and the collected summands are exactly 1 to 2018. You are also right that **this constraint alone is not a contradiction**.

Next examine the positions of these small numbers. First use a six-row **position diagram**, without assuming it is already a valid filled triangle:

```text
Row 1           P
Row 2         C   P
Row 3       ·   P   C
Row 4     ·   C   P   ·
Row 5   L   ·   P   C   R
Row 6 L   L   C   P   R   R
```

Here `P` marks the larger-child path and `C` the unchosen sibling at each step. We collect **the top and every C**; the other Ps are successive sums.

First consider only the bottom row: the final adjacent child pair is cells 3, 4, labeled C, P respectively. Cells 1, 2 to the left are L, and cells 5, 6 to the right are R.

In this diagram, could bottom L or R cells be among the collected numbers? Looking one row up, how are L and R in row 5 positioned relative to P and C? Answer only for this diagram first; do not rush to all paths.

## Round 4

### Student

Bottom L and R cells are neither the top nor C, so are uncollected. Assuming a valid six-row triangle, the collected numbers are exactly 1 to 6, so these L and R numbers all exceed 6. In row five, the left L is left of P, C and the right R is right of P, C; neither is collected, so they too exceed 6.
I also noticed the leftmost L in row five is the difference of the two bottom Ls, and the rightmost R is the difference of the two Rs. But the difference of numbers greater than 6 may be small or large: 8 and 9 differ by 1, while 7 and 20 differ by 13, so size alone gives no conclusion. The position diagram shows uncollected numbers clearly, but should we constrain differences next or follow downward paths on the sides? I am unsure.

### Teacher

Your observation is correct: subtracting two numbers greater than 6 need not give a large difference. We therefore need not judge their difference solely from the two lower numbers being large.

Your second direction is more useful: **follow larger children downward again within a small triangle on one side**. Consider these three left cells:

```text
    L
  L   L
```

In our temporarily assumed valid six-row triangle, you established that these positions are uncollected, so their numbers exceed 6 and are distinct.

Call the upper number \(a\), the larger lower number \(b\), and the other \(c\). The difference rule still applies:

\[
b=a+c
\]

Unlike the situation you described, we know not only that the lower numbers are large, but **that upper \(a\) also exceeds 6**.

Handle just these three cells: since \(a\) and \(c\) are distinct integers greater than 6, what is the minimum \(b=a+c\)? How does that lower bound compare with the six-row maximum 21?

## Round 5

### Student

a and c can be as small as 7, 8, so b is at least 15. Since 15 does not exceed 21, these three cells give no contradiction. For example, 7, 8, 15 themselves satisfy 15−8=7. I can follow this calculation and see why “a large lower bound” does not directly imply “impossible.”
If a side had three rows, following larger children would give endpoint at least 7+8+9=24, exceeding 21. But both complete small triangles in the six-row diagram seem to have only two rows. For 2018 rows, can we always find a sufficiently tall small triangle beside the main path containing no C? One diagram turning left and right cannot guarantee all paths behave this way. Could you first explain how to guarantee finding it and how many rows are needed?

### Teacher

Your judgment is accurate: both sides in the six-row diagram have only two rows, so a hypothetical three-row side triangle cannot be treated as already found. For 2018 rows, first fix the main path’s final location, then prove that sufficiently tall small triangles can be found regardless of earlier turns.

Let the final adjacent bottom pair be cells \(p\), \(p+1\). Divide the remaining bottom cells into left and right sections:

- The left has \(p-1\) cells supporting a complete small triangle;
- The right has \(2018-p-1\) cells also supporting a complete small triangle.

Their row counts sum to \(2018-2=2016\), so **at least one side has no fewer than 1008 rows**. We still need to prove it avoids every collected sibling C.

Consider any row \(r\), with \(k=2018-r\) steps remaining to the bottom. Its P and C have a common parent on the path, say in column \(q\). This parent must follow the main path to column \(p\) of the penultimate row. Each descent leaves the column index unchanged or increases it by 1, so:

\[
p-k\le q\le p.
\]

Its children P, C occupy columns \(q\), \(q+1\), so both lie within **\(p-k\) through \(p+1\)**.

In the same row, the left small triangle extends at most to column \(p-k-1\), while the right begins at column \(p+2\). Both ranges are separated from the P, C range. The top also belongs to neither side triangle. Regardless of the main path’s turns, both complete small triangles contain neither the top nor any C.

Combining this with your established conclusion that the top and all Cs occupy exactly 1 to 2018, and global distinctness, all side-triangle numbers exceed 2018. We now have **at least one complete 1008-row small triangle whose numbers all exceed 2018**. This step only guarantees its existence; the later accumulation and numerical comparison can use your earlier three-row approach.

## Round 6

### Student

First the numbers: following larger children to the bottom of a 1008-row side triangle adds 1008 distinct integers greater than 2018, with minimum values 2019 through 3026. Their average is 2522.5, times 1008 gives 2542680, greater than 2037171. Thus that path endpoint exceeds the permitted range, and the valid large triangle does not exist.
That was quite a lot of information, so I want to check the column boundaries once rather than merely accept them. Using p=3 in the six-row diagram, row five has k=1: your P, C range is columns 2 to 4, the left triangle ends at column 1 and the right starts at column 5, so they are separated. Row four has k=2, and neither side has cells there, so no inconsistency. Is my substitution correct? Also, if the final step has p=1, one side has 0 rows and the other 2016. We can extract 1008 rows there and use the same bound, right?

### Teacher

Yes, both substitutions and your numerical contradiction are correct.

In the six-row diagram, \(p=3\):

- Row five has \(k=1\), with P, C in columns 2 to 4; the left triangle reaches column 1 and the right starts at column 5, so they are separated.
- Row four has \(k=2\); the left requires column index at most \(3-2-1=0\), and the right at least 5. But row four has only columns 1 to 4, so both sides have no cells in that row.

When \(p=1\), the left has 0 rows and the right has \(2018-1-1=2016\), also correct. Choose 1008 consecutive cells along the right triangle’s base to obtain a complete 1008-row subtriangle. It remains within that side triangle, so its numbers exceed 2018. Accumulating along larger children gives the same lower bound \(2542680\).

Your specific check of “whether this row of the side region is empty” helps: the boundary formulas still apply, but the corresponding cell set is empty.

### Student

I will stop here today. My judgment is nonexistence: addition along the main path is constrained by the maximum, forcing all of 1 to 2018 into collected cells; one side must contain a sufficiently large complete triangle with larger numbers, whose accumulation then exceeds the maximum. I actually checked both the three-row trial construction and substitutions for empty side regions. You supplied the general column proof, and I can check examples but cannot claim to have independently thought of that step. Gradual clues let me participate; the final column section was dense, but adding two boundary examples clarified it greatly. Thank you.

### Teacher

This teaching session has been confirmed as ended.
