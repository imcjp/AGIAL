# P03 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | KELE |
| Participant ID | P03 |

## Round 1

### Student

Teacher, I tried two rows first: 1, 3 below gives 2 above, using 1 to 3 once each. Three rows require 1 to 6, so I casually tried bottom row 1, 6, 4, giving 5, 2 above and 3 at the top, which also seems to work exactly. We cannot keep trying one by one for 2018 rows, right? If a small one can be arranged, does that mean there is a way to keep adding rows? I want to clarify that first.

### Teacher

Both your two- and three-row arrangements follow the rules. To judge whether rows can keep being added, first consider a small question:

Starting from your completed three-row triangle, what conditions would a new four-row triangle need to satisfy?

## Round 2

### Student

Four rows have 10 cells, so each of 1 to 10 must be used once. Keeping the original three rows means the four new numbers below can only be 7, 8, 9, 10, whose adjacent differences must be 1, 6, 4 in order. But their largest difference is only 3, so 6 and 4 are impossible. My three-row triangle therefore cannot directly gain a row below. But could changing the original arrangement work? Finding only this extension impossible should not establish that four rows do not exist, right? What should we check next to avoid just randomly changing numbers?

### Teacher

Yes, you distinguish accurately: this only shows that **retaining this three-row triangle and directly adding a row below** fails, rather than establishing that a four-row triangle does not exist.

Try another perspective without rushing to change numbers: for any upper cell and its two adjacent lower numbers, if the upper number and the smaller lower number are known, how can you express the larger lower number?

## Round 3

### Student

The larger number is the upper cell plus the smaller lower number. For example, my 1, 6 have 5 above, so 6=5+1; 6, 4 have 2 above, so 6=2+4. I can use this relationship, but the larger lower number may be on the left or right. What can it rule out? I still cannot see how one small triangle constrains the whole 2018-row triangle. Could you give me a direction to try next, without telling the whole solution yet?

### Teacher

Yes, the larger number may lie on either side, but you can always choose to move to it.

First try your own three-row triangle: start at the top **3** and choose the larger of the two adjacent cells below each time until reaching the bottom. Record each step using the additive relationship you discovered.

**Which numbers sum to the bottom number finally reached?**

## Round 4

### Student

From 3 choose 5, then 6. First 5=3+2, then 6=5+1, so finally 6=3+2+1. The added numbers are the smaller unchosen numbers at each step, rather than the visited 3, 5, 6. For 2018 rows, would it be the top plus 2017 unchosen numbers? If these are different cells, their sum is at least 1+2+…+2018=2037171, exactly the permitted maximum. I see no contradiction yet: could it just equal it?

### Teacher

Yes, there is no contradiction yet. Assuming such a triangle exists, the bottom path number is at least 2037171 and cannot exceed 2037171, so it **must equal it exactly**.

The top and the unchosen numbers occupy different rows, so they are 2018 distinct positive integers. Their sum attains the minimum possible value \(1+2+\cdots+2018\).

What restriction does this impose on those 2018 numbers themselves?

## Round 5

### Student

Then those 2018 numbers can only be exactly 1 to 2018, though their order may vary. Ordering them from smallest to largest, the first is at least 1, the second at least 2, through the 2018th at least 2018; if any is larger, the total exceeds it. The three-row example also has exactly 3, 2, 1. But these small numbers are scattered across rows and still seem able to fit. Should we next see whether intermediate path numbers repeat them? I could try that direction but have not found a number that must repeat.

### Teacher

Your ordering argument is correct: these numbers exhaust 1 to 2018. You are also right that **there is still no contradiction at this point**; we need not assume the intermediate path numbers must repeat.

Look at the regions outside the path. Suppose the final path step involves two adjacent bottom cells. There are cells to the left and right, each side supporting a complete side triangle.

**What minimum number of rows must the larger of these two side triangles have?**

## Round 6

### Student

Removing the final adjacent pair leaves 2016 bottom cells on both sides combined, so the larger side has at least 1008 cells, corresponding to a side triangle of at least 1008 rows, right? But I am unsure how these side triangles separate from the path. The path may turn left and right; could earlier unchosen small numbers fall inside a side triangle? Could you explain with a small diagram of about five rows or cell positions? The sudden shift to both sides leaves me unable to connect it.

### Teacher

Yes, the larger side has at least **1008 rows**. Your spatial question is crucial; first use five rows to examine a turning path.

Here `P` marks path cells and `a` the unchosen adjacent cells; the final bottom pair occupies cells 2, 3. `L` and `R` mark the side triangles beside that pair:

```text
            P
          a   P
        ·   P   a
      L   P   a   R
    L   P   a   R   R
```

The top and all `a` cells are the earlier summands. None falls inside `L` or `R` here. But **one example does not prove this for all turns**.

Check the general case by considering which bottom positions each cell can reach downward. Since the path cells eventually reach the final pair, they must be able to reach the corresponding positions in it; side-triangle cells can reach only one side outside that pair.

First examine **`L` and `R` in row four**: which bottom cells can each reach?

## Round 7

### Student

Row four's L reaches bottom cells 1, 2, and R reaches cells 4, 5. But cell 2 belongs to the final pair, does it not? Also, below row four's L are L and P, not two Ls, so this L does not seem part of a side triangle supported only by bottom cell 1. The right R is fine. Did the diagram label one extra L on the left? I also want to confirm: I understand that path cells reach the final pair, but why must unchosen a cells also stay outside both sides? Could you explain that further?

### Teacher

You are right; I incorrectly labeled the left cell of row four `L`. Sorry. The left base has only cell 1, so the left triangle contains only that cell. Corrected:

```text
            P
          a   P
        ·   P   a
      ·   P   a   R
    L   P   a   R   R
```

`·` marks cells labeled neither as path nor as side triangle. This diagram shows one path; next explain why unchosen `a` cells for **any path** avoid both sides.

Consider a path cell with two adjacent children: one chosen as the next path cell, the other `a`. Since the chosen child can continue along the path to its penultimate-row cell:

- If unchosen `a` lies to the chosen cell's left, moving down-right from `a` once reaches the same next-row cell as the chosen cell; it can then follow the same route to the penultimate path cell.
- If `a` lies to the right, similarly move down-left once, then follow the same route.

One final downward step then reaches at least one cell of the final bottom pair. For the penultimate path cell, its children are already that pair, so the step also holds.

But side-triangle cells reach only bottom cells on the corresponding side **outside** the final pair. Thus unchosen `a` cannot lie in a side triangle; neither can the top.

Now reconsider: since the top and all unchosen `a` cells exhaust 1 to 2018, what is the minimum number in the larger side triangle?

## Round 8

### Student

If they really do not overlap, every number in the side triangle is at least 2019; I understand that, and the corrected diagram is clearer too. But your claim that a can rejoin the subsequent path in one step seems not always true when I try going right repeatedly: choose the right P in row two, then the far right in row three. The left a of row two can move down-right only to the middle of row three, not to the far-right P. It may not subsequently reach the penultimate path cell either. Do we only need to show it can reach one of the final pair, rather than rejoin the original path? Could you clarify the reasoning for this example? Otherwise I still cannot be sure the 2019 lower bound applies.

### Teacher

You are right: my claim that "`a` can rejoin the original path in one step" was wrong. Sorry. **Rejoining the original path is unnecessary**; we only need to show that `a` can reach at least one cell of the final bottom pair.

First consider your five-row example: choose right in row two, then far right in row three. The left `a` of row two can descend three steps to bottom cells **1 to 4**, while the far-right path cell of row three can descend two steps to bottom cells **3 to 5**. The final pair must be `(3,4)` or `(4,5)`, so however the path continues, `a` reaches at least one cell of it.

The general reasoning is similar. Suppose an unchosen `a` occupies column \(j\) in row \(r\) of a triangle with \(n\) rows:

- From `a`, the reachable bottom columns are \(j\) through \(j+n-r\).
- Its adjacent chosen path cell is in column \(j-1\) or \(j+1\). Thus at least one of the two bottom children of the final penultimate path cell lies within `a`'s reachable range.
- Side-triangle cells reach only bottom cells **outside** the final pair, so `a` cannot belong to them.

The top is also outside the side triangles. Thus, after the top and all `a` cells exhaust 1 to 2018, every side-triangle number is indeed at least **2019**.

Now can we reuse the method of "choosing larger children and accumulating" inside this side triangle with at least 1008 rows to determine a lower bound for one of its bottom numbers?

## Round 9

### Student

The five-row example connects now: a reaches 1 to 4, and at least 4 or 3 from the final pair lies there; no rejoining is needed. Walking similarly through the side triangle's at least 1008 rows gives at least 1008 distinct summands, each at least 2019. First I calculate 1008×2019=2035152, which is 2019 below 2037171 and insufficient. But since these numbers cannot repeat either, the minimum is 2019+2020+…+3026, or (2019+3026)×1008÷2=2542680, already exceeding 2037171. So the whole triangle does not exist, right? Unlike multiplying only by 2019, this uses non-repetition. If repetitions were allowed, the proof could not be applied unchanged, correct?

### Teacher

Yes, your calculation and conclusion hold: a bottom number in the side triangle is at least 2542680, exceeding the permitted maximum 2037171, a contradiction.

You also correctly identified the condition's role: **with repetitions allowed, this proof cannot be applied unchanged**. We used non-repetition twice: first to force the collected numbers to be exactly 1 to 2018, and second to obtain the side-triangle summation lower bound. A changed condition requires reconsideration rather than directly asserting the conclusion.

The general relationship used here is that, in a triangle satisfying the absolute-difference rule, starting at the top and always choosing the larger child makes the endpoint equal the top plus all unchosen child numbers along the way.

Can you connect the complete proof in your own words, from "suppose a 2018-row triangle exists" to the contradiction?

## Round 10

### Student

Let me try. Suppose the triangle exists. Start at the top and always descend to the larger number. Since larger number = upper cell + smaller number, the endpoint equals the top plus the unchosen number at every step, giving 2018 distinct positive integers. Their sum is at least the sum from 1 to 2018, 2037171, and cannot exceed that maximum, so equality holds and these 2018 numbers exhaust 1 to 2018. Outside the final adjacent pair, 2016 bottom cells remain, so at least one side has 1008 cells, supporting a small triangle of at least 1008 rows. Cells containing the small numbers can reach at least one cell of the final pair downward, while the small side triangle's cells reach only the outside, so it contains none of 1 to 2018; all numbers are at least 2019. Descending through larger numbers again inside it gives at least 1008 distinct summands, at minimum 2019+…+3026=2542680, greater than 2037171: contradiction, so it does not exist. This chain shows why success with three rows cannot predict success with 2018. The side-position step was hardest; the earlier diagram and rejoining claim caused a detour, and only the account of reachable bottom cells connected it.

### Teacher

You have now connected the complete proof, with the correct conclusion: **a 2018-row anti-Pascal number triangle satisfying the original conditions does not exist**.

The key chain is: descending through larger children expresses a bottom number as the sum of 2018 distinct positive integers; the lower and upper bounds force precisely 1 to 2018 as summands. Cell positions then provide a side triangle of at least 1008 rows containing none of these small numbers. Repeating accumulation inside gives a bottom number at least 2542680, exceeding the whole-triangle maximum 2037171, a contradiction.

This also answers the initial question: arranging two or three rows proves only those small cases feasible and does not guarantee rows can keep being added. The condition "each number used only once" is indispensable to this proof; with repetitions allowed, a new investigation is needed.

Your follow-up questions about side positions were valuable. My earlier extra cell label and incorrect one-step rejoining claim did obstruct understanding; checking "which bottom cells can be reached" clarified that link.

### Student

I will stop here today. Now I can explain why 2018 rows do not exist and know the proof cannot directly be applied when repetitions are allowed. The small examples and calculating the lower bound myself were useful; the side positions became clear only after correction. Thank you, teacher.

### Teacher

This teaching session has been confirmed as ended.
