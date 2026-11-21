# P09 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P09 |

## Round 1

### Student

Teacher, I want to get the rules right first. For two rows, 1 and 3 below gives 2 above, using 1, 2, 3 exactly once, right? I cannot try every cell for 2018 rows. Like checking inventory, matching the cell count does not mean an arrangement exists. Which concrete relationship should we start with? Please go step by step without giving the whole proof first.

### Teacher

Yes, your two-row example follows the rules: 1 and 3 below, |3−1|=2 above, with each number used exactly once.

First examine only this relationship: **How can the larger bottom number 3 be expressed using upper number 2 and smaller bottom number 1?**

## Round 2

### Student

3=2+1: the larger amount equals the difference plus the smaller. With 4 and 9 below and 5 above, similarly 9=5+4. But that only concerns three adjacent values; I do not see how it restricts the entire triangle. Should we focus on the maximum 2037171 first? If it were above, two lower numbers would need that large a difference, which seems impossible since all values lie from 1 to 2037171. So must it be at the very bottom?

### Teacher

Yes, the maximum must be at the bottom: two allowed positive integers have maximum absolute difference 2037171−1, smaller than 2037171.

Now return to your local relationship. Suppose a cell is 5 and the smaller of its two adjacent children is 4. One row farther down, starting from the larger number, suppose the smaller of its two adjacent children is 2.

**Using “larger = upper + smaller,” what larger number do you finally obtain?**

## Round 3

### Student

First 5+4=9, then 9+2=11, so finally 11, or 5+4+2. I can follow this row-by-row addition. But your 4, 2 were assumed; in a real triangle, do we always choose the larger child below the current cell to continue, recording the smaller? Reaching the bottom would give a string of summands. Could they encounter a previously recorded cell or count the same number twice? Could you point this out using positions in three or four rows?

### Teacher

Yes, your route is correct: always move from the current cell to the larger child, recording the other value as a summand.

In this four-row example, `→` means moving to the larger number, and the numbers in parentheses are the summands recorded at each step:

```text
        4          Start, also recorded as a summand
      2   6        4 → 6, record 2
    5   7   1      6 → 7, record 1
  8   3  10   9    7 → 10, record 3
```

Thus the endpoint is 10=4+2+1+3. The start and later recorded numbers belong to different rows, so they are different cells. Since each number is used once throughout the original problem, distinct cells also cannot repeat values.

Now generalize: **for n rows, how many summands are recorded in total when moving from the top to the bottom this way?**

## Round 4

### Student

For four rows, top 4 plus one from each of three lower rows makes 4; n rows gives n. The diagram is clearer than addition alone. I now understand neither cells nor values repeat. So 2018 distinct positive integers minimally use 1 to 2018, summing to exactly 2037171? That equals the allowed maximum, so it only says the endpoint exactly reaches the maximum without exceeding it; we cannot conclude nonexistence yet. Is that correct? Should we check whether this “exactness” can hold next? I want to try finding the contradiction myself; just give me a direction.

### Teacher

Your judgment is correct: the endpoint is at least 2037171 and at most 2037171, so it must equal 2037171; no contradiction has arisen yet.

Pursuing restrictions from “exact equality” is appropriate. However, this round's teaching-support call could not complete because the request update failed, and resubmission reported the previous call unresolved. I temporarily cannot give the next hint according to the selected method.

## Round 5

### Student

Let us continue from there. I think “exactness” is like minimum inventory: 2018 distinct positive integers already total the minimum, so the recorded values must be exactly 1 to 2018, with no larger replacement. But I do not know how these small values scattered among rows force a contradiction. Could you give a position or small example to check next, leaving calculations to me first?

### Teacher

Yes: assuming the triangle exists, equality forces the recorded 2018 numbers to be exactly 1 to 2018.

Look back at the four-row example. The path ends at **10**, paired with **3** in that row as the final two children:

```text
        4
      2   6
    5   7   1
  8   3  10   9
```

The bottom cell left of this pair is 8, which forms a two-row small triangle with 5, 7 above. First check these cells: **do any occur among recorded summands 4, 2, 1, 3?**

## Round 6

### Student

None of 8, 5, 7 is in 4, 2, 1, 3. But I cannot match the two-row triangle in this diagram: 8 and 3 differ by 5, and 3 and 10 by 7, so 5, 7 should have 8, 3, 10 below, including recorded 3. Which cells exactly are your region? Also, the final pair 3 and 10 has 8 on its left here, but if the original path ends far left or right, the same left region may not exist. How do we check such edge cases?

### Teacher

You are right; my diagram was wrong, sorry. **8, 5, 7 cannot form the two-row triangle I claimed**: 5 has 8 and 3 below, while 7 has 3 and 10. In this four-row example, only bottom 8 lies left of final pair 3, 10, and only bottom 9 right; each is only a one-row small region.

Your edge case matters too. Consider **both sides** of the final pair simultaneously: when one side has no space, the other still does. Removing the final pair from 2018 bottom cells leaves 2016 distributed across both sides.

Calculate: **wherever the pair lies, how many bottom cells must the larger side have at least?**

## Round 7

### Student

At least 1008. Splitting 2016 evenly gives 1008; shifting to one side only increases the larger, and at the extreme the other side has 2016. Looking at both sides includes edge cases. But could the small triangle above those bottom cells meet previously recorded small values? I only know the bottom row outside the final pair is unrecorded; overlap above is unclear. Could you explain why the ranges do not overlap, then let me try comparing magnitudes?

### Teacher

Your count is correct: the larger side has at least 1008 bottom cells. Here is why there is “no overlap.”

Let the final pair occupy bottom columns **p, p+1**. The side triangles are built wholly upon left bottom cells (columns 1 to p−1) and right bottom cells (column p+2 onward).

The key is: **every path cell's bottom-row descendant range contains column p**. Continuing from it along the path reaches penultimate-row column p and then column p of the final pair. “Descendant range” means all bottom cells reachable through successive downward moves.

Each recorded other child is adjacent to the selected child, so its bottom-row descendant range meets at least column p or p+1 of the final pair. In contrast, every side-triangle cell's descendants all lie on the same side of that pair and meet neither column. Thus **side triangles contain no recorded cells**; the top is outside them too.

So the recorded cells occupying 1 to 2018 are all outside. Continue calculating: in the side triangle with at least 1008 rows, following larger children again, what lower bound do the summands give?

## Round 8

### Student

For the smallest case of 1008 rows, every value exceeds 2018 without repeats, so its 1008 summands are at least 2019 through 3026. Pairing the ends gives 5045 per pair, 504 pairs, totaling 2542680, already exceeding 2037171; a taller triangle needs more summands. Thus its endpoint exceeds the allowed range, proving the original triangle nonexistent. I can connect this comparison now. But I read the column argument slowly and want to check in my own words: each downward move reaches an adjacent cell, so recorded-cell descendants at least touch the final pair; a triangle supported entirely on outer bottom cells cannot touch it, excluding recorded cells. Do we still need to explain why a recorded cell must cover the final pair, beyond merely saying it is adjacent to the path? I fear leaving that step empty in a written proof.

### Teacher

Your calculation is correct: 2542680 exceeds 2037171, producing a contradiction. You are right that spatial non-overlap **cannot follow merely from adjacency of the two children**; I omitted the column relationship that needs explanation.

Let the full triangle have \(n\) rows and the final bottom pair occupy columns \(p\), \(p+1\). Consider a path cell in row \(r-1\), column \(q\). It follows the path to penultimate-row column \(p\), with each downward row keeping the column or adding one, so:

\[
q\le p\le q+n-r.
\]

Its children occupy row \(r\), columns \(q\), \(q+1\). The recorded child is one of these. Let its column be \(j\), so \(j=q\) or \(q+1\). Its bottom-row descendant range is:

\[
[j,\;j+n-r].
\]

- If \(j=q\), the inequality shows this range contains column \(p\).
- If \(j=q+1\), the same inequality shows it contains column \(p+1\).

Thus every recorded child's descendant range genuinely meets at least one of the final pair. Side-triangle cells cover only bottom cells left or right of the pair and cannot be recorded cells; the top is outside too.

That supplies the step you were concerned about. Now can you connect “equality, small-number positions, side-triangle lower bound, and contradiction” in your own words as a complete proof outline?

## Round 9

### Student

My account: first assume the triangle can be arranged. Starting at the top, always move to the larger lower value, record the smaller, and record the top too. Larger equals upper plus smaller; accumulating to the bottom makes the endpoint the sum of 2018 recorded values. They are distinct positive integers, with minimum total 2037171. The endpoint cannot exceed that, so the recorded values are exactly 1 to 2018.
Outside the final pair remain 2016 bottom cells, at least 1008 on one side, supporting a side triangle. Recorded-cell descendants cover at least one of the final pair, while side-triangle cells cover only outer bottom cells, so all these small numbers are outside. I understand your addition: a recorded left child covers p, a right child p+1, rather than relying only on adjacency.
Thus every side value is at least 2019. Following the same route gives at least 1008 distinct summands, minimally 2019 through 3026, totaling 2542680. Its endpoint exceeds the maximum, a contradiction, so no triangle exists.
I can explain the arithmetic and overall relationships, but without your column formulas I cannot guarantee an independent complete account and need to check slowly against a diagram. This is enough for today; please check whether I misstated any key idea without expanding a new method.

### Teacher

Your proof outline is correct and connects all key steps: accumulation forces recorded values to exhaust 1 to 2018; the side triangle avoids these recorded cells; accumulation there gives lower bound 2542680, exceeding the allowed maximum 2037171, a contradiction.

In writing, retain the column formulas to support “non-overlap”: a left child's descendant range contains \(p\), and a right child's contains \(p+1\). You can now justify it with the formula; writing it independently without looking still needs careful diagram checks today. As you requested, we will stop here.

### Student

I will stop here today. Small examples and stepwise calculations helped me connect the overall proof, and diagram-position errors have been clarified. I still need the column formulas for checking and will not yet claim I can independently write the full proof. Thank you.

### Teacher

This teaching session has been confirmed as ended.
