# P03 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P03 |

## Round 1

### Student

Teacher, I tried two rows first: 1, 3 below gives 2 above, using 1 to 3 once each, so it should follow the rules, right? With 2018 rows, following adjacent subtraction seems easy, but ensuring no number repeats means we cannot fill them arbitrarily. Could you first give me a small three-row exercise to try? Please do not give the answer yet.

### Teacher

Yes, your two-row triangle follows the rules: 1 and 3 below have absolute difference 2 above, using 1, 2, 3 once each. The "no repetitions" condition you noticed must indeed hold simultaneously.

Try this three-row exercise:

Use each of **1 to 6** once to fill the cells below so that every non-bottom number equals the absolute difference of the two adjacent numbers directly below.

```text
        [ ]
      [ ] [ ]
    [ ] [ ] [ ]
```

Choose three bottom numbers first, calculate the upper two rows, and check whether you used exactly 1 to 6. Send me your arrangement afterward and we can check together.

## Round 2

### Student

I found one: bottom 6, 1, 4, middle 5, 3, top 2, with no repeated numbers. The calculation was quick. But arranging a small one does not show 2018 rows can be arranged, right? Continually trying entries would be too much. Is there a condition to examine first that can help judge whether the large triangle is possible? Give me one direction first and I will try deriving it myself.

### Teacher

Your three-row arrangement is correct: the difference between 6 and 1 is 5, between 1 and 4 is 3, and between 5 and 3 is 2; each of 1 to 6 is used once.

You are right that arranging three rows does not establish feasibility for 2018 rows. Start with a local relationship:

If the upper cell is \(a\), the larger lower number \(b\), and the smaller \(c\), then by the difference rule, **how does \(b\) relate to \(a,c\)?**

Start at the top, descend to the larger child each time, and connect the relationships along the way. See which numbers can sum to the bottom number eventually reached.

## Round 3

### Student

Then b=a+c. Following my triangle: from the top 2, choose 5 below, with 5=2+3; then choose 6, with 6=5+1, so 6=2+3+1. It really connects. For 2018 rows, would the final bottom number equal the top number plus the unchosen child at each step? But could those unchosen numbers count the same cell twice? Also, merely knowing it is a sum of many numbers, how can we see impossibility?

### Teacher

Yes, your generalization is correct: the final bottom number equals the top number plus the unchosen child number at every step.

These summands do not count the same cell twice: the top is in row 1, and the unchosen children come from rows 2, 3, …, 2018, respectively, so they occupy different rows. The original problem also uses every number only once, so these **2018 summands are distinct positive integers**.

Next, rather than rushing to impossibility, compare two bounds:

- What is the minimum sum of these 2018 distinct positive integers?
- What is the maximum possible endpoint, which is itself a number in the triangle?

Combine these bounds with "endpoint equals the summands' sum" and see what conditions are forced.

## Round 4

### Student

Different rows mean different cells; that is clear. The minimum should be 1+2+…+2018=2018×2019÷2=2037171. The endpoint maximum is also 2037171, exactly the same, so the endpoint must be the largest number and the summands exactly 1 to 2018, right? Any larger number would increase the total beyond it. But there is no contradiction yet; my small triangle also has 6=1+2+3. Does satisfying this condition make an arrangement possible, or must we use other cells? I cannot think of this step. Could you give another hint?

### Teacher

Your reasoning is right: the endpoint must be the maximum 2037171, and the 2018 summands must be precisely 1 to 2018.

Your small triangle illustrates that this is only a **necessary condition**: satisfying it does not guarantee the whole triangle can be arranged; all remaining cells must also satisfy differences and non-repetition simultaneously.

Next notice the path's last step: there is an adjacent pair of bottom children, one chosen as the endpoint and the other the sibling summand. The bottom cells to the left and right of this pair can support two smaller triangles, respectively.

First draw a six-row cell diagram, choose a top-to-bottom path, and label its final child pair and the triangles on both sides. Consider: **what is the sum of the row counts of these two triangles, and what minimum row count must at least one side have?** Focus on positions first, without numbers.

## Round 5

### Student

I understand the distinction of a necessary condition: equality does not mean the whole triangle can be filled. For six rows I labeled bottom positions 1 to 6 and supposed the final child pair is cells 3, 4. Taking "both sides" to mean the remaining 1, 2 on the left and 5, 6 on the right, each supports a two-row triangle, with row counts totaling 4 and at least one side having two rows. Is that what you mean? Or must a triangle also include one of cells 3, 4? With only text I am unsure. Could you draw the boundary or specify the bottom-edge cells? Let us clarify positions before calculating numbers, or we may calculate for the wrong object.

### Teacher

Yes, exactly: **neither side triangle includes cells 3, 4**. Their bases are cells 1, 2 and cells 5, 6, respectively.

Here are the positions in a six-row triangle. `L` and `R` label the left and right side triangles, `×` the final child pair, and `·` other positions:

```text
Row 1             ·
Row 2           ·   ·
Row 3         ·   ·   ·
Row 4       ·   ·   ·   ·
Row 5     L   ·   ·   ·   R
Row 6   L   L   ×   ×   R   R
Column  1   2   3   4   5   6
```

The left base consists of cells 1, 2 of row 6, together with the cell directly above, making a two-row triangle; similarly on the right. Your combined row count of 4, with at least one side having 2 rows, is also correct.

This diagram shows only cell positions, rather than an already completed valid six-row number triangle.

## Round 6

### Student

This diagram helps; it really excludes those two middle cells. With 2018 rows, removing the pair leaves 2016 bottom positions, so the side-triangle row counts total 2016, with at least 1008 rows on one side. If the final pair is near an edge, one side may be empty and the other larger, but at least 1008 still holds. Yet the numbers in this triangle need not include every number from 1 to some bound, so does the earlier path summation still apply? I can think of descending through its larger children again, but its endpoint is still at most 2037171, and a sum of 1008 numbers seems insufficient to exceed it. Which property of this triangle should we use next?

### Teacher

Your row count is correct, including the case where the final pair lies near an edge.

Although a side triangle need not contain consecutive numbers, both adjacent children below every non-bottom cell remain within it. Thus the original difference relationship still applies; you can follow larger children inside it and obtain a sum of 1008 distinct positive integers.

The next property is: **the side triangle contains none of the summands collected by the original path**. Those summands are precisely 1 to 2018, and no numbers repeat globally, so all numbers in the side triangle exceed 2018.

This "absence of collected summands" requires proof from path positions; it cannot be inferred just from those two bottom cells. You can temporarily use this conclusion to find the minimum possible sum of the 1008 summands inside the side triangle, then we will prove the positional relationship.

## Round 7

### Student

If everything inside exceeds 2018, the minimum uses the 1008 numbers from 2019 to 3026, summing to (2019+3026)×1008÷2=2542680, which exceeds 2037171 by 505509. The endpoint also belongs to the triangle and cannot exceed 2037171, so that is indeed a contradiction. I can follow the calculation and do not need it broken down further. But I still cannot treat "the side triangle contains none of the original summands" as proved: the path can turn left and right, so could an earlier unchosen cell fall into that side? Could you show a turning path on the six-row diagram and explain why it still cannot touch it? Only once that positional relationship is clear can I say the whole proof holds.

### Teacher

Your calculation and contradiction are correct, and the positional issue you raised does need proof. First use a **turning path** to see it clearly, then explain why it holds for arbitrary paths.

In this six-row diagram, `P` is a chosen path cell, `C` the unchosen sibling at each step, and `L`, `R` the side triangles. The path's column numbers, counted from left to right, are **1, 2, 2, 3, 3, 4**, so it turns left and right:

```text
Row 1             P
Row 2           C   P
Row 3         ·   P   C
Row 4       ·   C   P   ·
Row 5     L   ·   P   C   R
Row 6   L   L   C   P   R   R
Column  1   2   3   4   5   6
```

The original summands are the top cell and each row's `C`. All lie outside `L`, `R` here. `P`, `C` only mark positions and do not represent an already completed valid six-row number triangle.

Why can no turn make a sibling enter a side triangle? Suppose the final bottom child pair occupies columns \(p\), \(p+1\). Their path parent occupies column \(p\) in the penultimate row.

Consider a path cell and sibling in any row \(r\). Their shared parent occupies column \(q\) in the preceding row. From this parent, the path requires \(k=2018-r\) more steps to reach column \(p\) of the penultimate row, each leaving the column unchanged or increasing it by 1. Thus:

\[
p-k\le q\le p.
\]

The pair occupies columns \(q\) and \(q+1\), so both lie in \([p-k,p+1]\). **The sibling need not itself reach the endpoint**; this range follows from its shared parent with the path cell.

In the same row:

- The rightmost left-side-triangle cell is at most column \(p-k-1\);
- The leftmost right-side-triangle cell starts at column \(p+2\).

Neither range intersects \([p-k,p+1]\), so however the path turns, each row's sibling remains outside both side triangles. The top cell is outside both too.

Thus the top and all siblings, these 2018 summands, exhaust \(1\) to \(2018\). With no repetitions globally, every number in both side triangles exceeds 2018. Together with your lower bound, this completes that step in the contradiction proof.

## Round 8

### Student

I substituted values into the six-row diagram: p=3, and in row 5, k=1, so the parent q can only be 2 or 3, placing the sibling in columns 2 to 4, while the left side in that row reaches only column 1 and the right begins at column 5. They really cannot touch. It does not require the sibling to reach the endpoint; the shared parent constrains its position. That explanation resolves my question. If the final pair changes to columns 2, 3, then the row 5 sibling lies in columns 1 to 3 and the right triangle starts at column 4, still separate. Now I can connect the proof: the whole-triangle path first forces all of 1 to 2018 into the top and siblings, then we find a side triangle of at least 1008 rows whose numbers all exceed 2018; another path sum exceeds the maximum, so it does not exist. One small question remains: if that side has more than 1008 rows, can we take a 1008-row subtriangle inside it? That keeps all children inside and avoids recalculating a longer path sum.

### Teacher

Yes. If the side triangle has more than 1008 rows, select **1008 consecutive cells on its base**, together with the complete small triangle supported above that base segment.

This gives exactly 1008 rows, with both adjacent children below every non-bottom cell remaining inside. You can therefore descend through larger children and reuse your existing 1008-term lower bound without recalculating a longer path.

Your connection of the overall proof is also correct; your positional check in row 5 captured the key role of the shared parent in restricting the sibling's position.

### Student

I will stop here today. I understand that taking 1008 consecutive bottom cells and their supported complete triangle avoids cutting off needed children. We cannot guess a large triangle works just because a small one can be filled; two path sums together with non-repetition establish nonexistence. I can do the calculation myself, but connected the positional step through your diagram and shared-parent explanation. I did not independently invent this proof method, but can now check it position by position. Thank you.

### Teacher

This teaching session has been confirmed as ended.
