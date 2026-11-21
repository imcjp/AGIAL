# P09 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P09 |

## Round 1

### Student

Teacher, I want to check the rules with small numbers first. For two rows, putting 1 and 3 below gives 2 above, using exactly 1, 2, 3, right? With so many cells in 2018 rows, trial arrangements alone probably cannot finish. I usually check quantities and repeats; which easily checked restriction should I start with here? Explain one small step first for me to try.

### Teacher

Yes, your two-row triangle follows the rules: the upper number is \(|3-1|=2\), and the three cells use 1, 2, 3 once each.

First check a local magnitude relationship: the larger lower number in your triangle is **3 = 2 + 1**, or “upper cell + smaller lower number.”

Now look at this small three-row triangle:

```text
    2
  5   3
6   1   4
```

Start from top 2 and always move to the larger of the two numbers directly below. Can you list the visited values and express each step using that relationship?

## Round 2

### Student

The visited values are 2, 5, 6. First 5=2+3, then 6=5+1, so finally 6=2+3+1. Each downward row adds another small number to the existing value rather than recalculating randomly; I can follow concrete numbers. But I do not yet see how this restricts 2018 rows: must all the added numbers differ? Could a later step count an earlier number again?

### Teacher

Your calculation is right, and your question is crucial: **the added numbers really are distinct**.

Starting at the top, each downward row adds the number not chosen for the path. Added numbers occupy different rows and therefore different cells; the problem forbids repeats throughout the triangle, so they are distinct. The top occupies a separate row and differs from them too.

In your example, the collected summands are top **2** and neighboring **3, 1** in two rows. Path value **5** is an intermediate sum already obtained, not a new summand, so nothing is double-counted.

For 2018 rows, the endpoint equals the top plus a neighboring number from every later row, totaling **2018 distinct positive integers**.

One small question: what is the minimum possible sum of 2018 distinct positive integers?

## Round 3

### Student

With no repeats and all positive, the smallest choice is 1 through 2018. Pairing the ends gives 2019 per pair, with 1009 pairs; I get 2037171, exactly the maximum allowed. This leaves me a little stuck: since it does not exceed the limit, can we only say the endpoint must be the maximum and the summands exactly 1 to 2018? I cannot conclude nonexistence yet. Where should I check next? This row-by-row accounting is easier to follow than many letters at once.

### Teacher

Your judgment is exactly right: the endpoint is at least 2037171 and cannot exceed it, so it must be the maximum, and the summands exactly 1 to 2018. **This step alone does not establish nonexistence of the whole triangle.**

Next check the space beside the bottom maximum. At the last path step, we reach an adjacent bottom pair and choose the larger, 2037171.

Temporarily cover this pair. How many bottom cells remain on the left and right together? How many must the longer part have at least? First do only this quantity accounting.

## Round 4

### Student

There are 2018 bottom cells; covering two adjacent cells leaves 2016. Split left and right, the longer side has at least 1008, and if the pair is near an edge the other side is longer still. This count is clear. But how do these 1008 cells connect to the earlier path? Should we take another path there? Please first clarify the positions to examine; I cannot yet imagine the upper-row ranges.

### Teacher

Yes, later we can take a new path on the longer side. First see the region supported upward by these bottom cells.

Suppose the covered adjacent cells are bottom cells \(p\), \(p+1\):

```text
Bottom:  Some left cells  | Cell p  Cell p+1 |  Some right cells
```

On the left, take bottom cells 1 to \(p-1\) as the base. Retain upper-row cells only if **both child cells below lie within this range**, repeating upward to the top. This yields a complete small triangle. The right is similar.

For example, a base with 4 cells supports:

```text
       ○
     ○   ○
   ○   ○   ○
 ○   ○   ○   ○
```

Thus the longer side's at least 1008 bottom cells support a complete triangle of at least 1008 rows. Both lower neighbors of every non-bottom cell remain inside, so the difference rule holds and another “always choose the larger child” path is possible.

To connect the two accounts, we still need to establish **whether all original collected summands are outside this small side triangle**. Only then can we judge the size of the new path's collected values.

## Round 5

### Student

Four base cells with 3, 2, 1 above makes sense. But I cannot simply assert all original sibling values are outside. For a smaller case with 6 bottom cells and final pair 4, 5, the penultimate path can occupy cell 4. If the previous row moves right to this cell 4, could neighboring cell 3 extend into the left triangle? I want to check these grazing-edge positions. Could you explain with these 6 indexed cells? If they really are outside, 1 to 2018 are already all occupied by the original summands, so every new-triangle value must exceed 2018.

### Teacher

In six-row positions, your cell 3 indeed does not enter the left triangle. Take bottom cells 4, 5 as the final pair:

```text
Row 6 (bottom):  1   2   3 | 4   5 | 6
                 ← Left base →       Right
```

The left triangle is supported by bottom cells 1, 2, 3, with ranges:

```text
Row 4: cell 1
Row 5: cells 1, 2
Row 6: cells 1, 2, 3
```

In your case, the path is at row 5 cell 4, with its parent in row 4. If it arrives diagonally right from row 4 cell 3, that parent's other child is **row 5 cell 3**.

The left triangle reaches only cell 2 in row 5, so sibling cell 3 is just outside it. Although this cell connects bottom cells 3 and 4, 3 belongs to the left base but 4 does not, so the cell itself is not a left-triangle member.

The right base here is only cell 6, and the side triangle contains only that cell. The final pair is cells 4, 5, likewise outside the right triangle.

Your later inference is correct too: **if the original top and all sibling cells are proved outside the side triangle**, these summands exhaust 1 to 2018, and distinctness forces every side-triangle value above 2018. These indices check your edge case; a complete proof still requires confirming every other row and allowed path behaves likewise.

## Round 6

### Student

So both lower cells must be inside the range; touching just one left-side cell is insufficient. That is clear now. Generally, once a path enters the complete left triangle, no later downward choice can leave, so it cannot reach the covered final pair. But a sibling is not the path itself, and I cannot connect that step. Can the same “cannot leave once inside” explain why siblings cannot be inside either? Once this is clear, I want to calculate the final comparison myself without receiving the result first.

### Teacher

Your “cannot leave once inside” directly excludes **path cells** from side triangles; siblings require an extra step because the path does not descend from them.

Let the final bottom pair be cells \(p\), \(p+1\). Consider a pair in row \(r\), one path cell and one sibling, sharing a parent in column \(q\) of the previous row.

This parent must follow the path to column \(p\) of the penultimate row. Suppose row \(r\) is \(k=2018-r\) steps from the penultimate row; each downward step leaves the column unchanged or adds 1. Thus the parent's column must satisfy:

\[
p-k\le q\le p.
\]

Its children occupy columns \(q\), \(q+1\), so **both path and sibling cells lie between columns \(p-k\) and \(p+1\)**.

For side triangles in the same row:

- All bottom descendants of left-side cells must lie at column \(p-1\) or farther left, so the rightmost left-side column is \(p-k-1\).
- Right-side descendants must start at column \(p+2\) or farther right, so the leftmost right-side column is \(p+2\).

Both sides are offset by one column from the path/sibling range. The top is outside both too. Thus the original top and all collected siblings are outside the side triangles.

Now calculate the final comparison yourself: follow larger children again in a side triangle with at least 1008 rows, record how many distinct values are collected and their minimum sizes, and compare with the allowed maximum.

## Round 7

### Student

For the final count, taking 1008 rows collects 1008 distinct values all greater than 2018. They cannot all be 2019; the smallest choice is 2019, 2020 through 3026. There are 504 pairs of 5045, totaling 2542680, exceeding 2037171. Thus assuming the triangle exists breaches the upper limit, so it should not exist. If the side has more than 1008 rows, taking a complete 1008-row small triangle inside still obeys the restriction, right? But I have not fully absorbed q, r, k together, especially the steps “from row r to the penultimate row” seeming to be 2017-r instead? I follow unchanged columns or increases by 1; could you verify the steps and keep only one indexing scheme to strengthen this evidence?

### Teacher

Your final comparison is correct: if the side exceeds 1008 rows, take 1008 consecutive cells of its base and form a complete 1008-row triangle upward, then accumulate the same way.

You also identified my wording error correctly: row \(r\) to the penultimate row is indeed **\(2017-r\) steps**. I used \(2018-r\) but described incorrect starting and ending positions. Here is a new explanation using only row \(r\) and column \(q\).

Let the final bottom pair occupy columns \(p\), \(p+1\). Consider the row-\(r\) path and sibling cells, whose common parent is at row \(r-1\), column \(q\).

1. When this parent follows the path to **row 2017**, it must reach column \(p\), because the two children of column \(p\) are bottom columns \(p\), \(p+1\). From row \(r-1\) to row 2017 there are \(2018-r\) steps, so:
   \[
   p-(2018-r)\le q\le p.
   \]

2. The row-\(r\) path and sibling cells are this parent's children at columns \(q\), \(q+1\). Both lie in:
   \[
   p-(2018-r)\quad\text{to}\quad p+1
   \]
   this range.

3. Row \(r\) to **bottom row 2018** also takes exactly \(2018-r\) steps. A left-triangle cell's rightmost bottom descendant cannot exceed column \(p-1\), so its rightmost column in row \(r\) is \(p-(2018-r)-1\). The right triangle starts at column \(p+2\) in this row.

Thus path and sibling cells lie between the side triangles, offset from each by one column. The top is outside too. This supplies the reason “all originally collected values lie outside the side triangles.”

The two \(2018-r\) counts refer respectively to **parent to penultimate row** and **row \(r\) to bottom row**; they are equal counts with different endpoints.

### Student

I can distinguish the starting points now. Checking 6 rows and the row-4 pair: its parent is in row 3, with 2 steps to row 5; the pair is in row 4, also 2 steps from row 6. With the final pair in columns 4, 5, the parent can only occupy columns 2 to 4, and the child pair columns 2 to 5. The left triangle has only column 1 in row 4, and the right has no cell there, so no overlap. Now I understand this is not merely checking one coincidental route. I can connect the main reasons: the first path occupies all the smallest 2018 numbers, the complete side triangle cannot use them, and the second path's minimum total exceeds the full triangle's upper limit. I can explain this idea now, although I still need to slowly check the general row-column notation against the record. This is enough for today, thank you.

### Teacher

This teaching session has been confirmed as ended.
