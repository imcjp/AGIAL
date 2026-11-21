# P07 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P07 |

## Round 1

### Student

I will try two rows first: 1 and 3 below gives 2 above, using 1, 2, 3 once each, which should follow the rules? 2018 rows is too large; I do not know where to begin judging it. Could you give a small attempt for me to calculate myself first, then see what to watch for?

### Teacher

Yes, your two-row triangle follows the rules: the upper value is |1−3|=2, and 1, 2, 3 each appears once.

Next try a **three-row triangle**: use 1 to 6 once each, with every upper cell the absolute difference of adjacent cells below. Decide for yourself where to begin placing numbers.

After trying, tell me your arrangement or process; whether successful or not, we will examine it together.

## Round 2

### Student

I put larger numbers below first, trying bottom 1, 6, 2, giving 5, 4 above and top 1, a repeat. Changing 2 to 3 gives 5, 3 and top 2, repeating 3. I can calculate it, but it feels like changing numbers randomly. Can anything be fixed first to reduce attempts? For example, must 6 be at the very bottom?

### Teacher

You identified repeats in both attempts and proposed a conjecture worth testing first: “6 must be at the bottom.”

Do not rush to change bottom numbers again. From the triangle's rules, **if 6 were not at the bottom, what conditions would its cell need to satisfy**? Explain in your own words and see whether this judges your conjecture.

## Round 3

### Student

If 6 is above, the two below must differ by 6. But among 1 to 6, the largest difference is only 6 minus 1, giving 5, so impossible. Thus 6 really must be at the bottom. This reminder showed me to exclude positions first. But there are three bottom positions, and I still do not know whether to put 6 in the middle or at an edge. Which case should I check next?

### Teacher

Yes, your reasoning holds: the maximum difference of usable numbers is 5, so 6 must be at the bottom.

Next check **6 in the middle of the bottom row** first. You have tried two sets; can you systematically check the possible arrangements for this position? Ignore edge cases for now and tell me your method and findings.

## Round 4

### Student

I want to fix 1 on the left and check 2, 3, 4, 5 on the right. Bottom 1, 6, 4 gives 5, 2 and top 3, seemingly using all of 1 to 6! Finding one workable three-row arrangement means I need not check every case with 6 in the middle, right? But I still cannot connect three rows to 2018. Could you give a concrete direction? Trying each row like this seems endless.

### Teacher

Your three-row triangle is correct:

```text
    3
   5 2
  1 6 4
```

If the aim is to judge **whether three rows are possible**, finding this one example suffices without checking other arrangements.

For 2018 rows, trying each arrangement is indeed difficult. Without enumerating every position, you proved 6 must be at the bottom. Look back at this example: beyond one particular number's position, can you propose a **conjecture that might hold for any row count**? No complete proof is needed immediately; first state what you notice.

## Round 5

### Student

I can think of this: whatever the row count, the maximum must be at the bottom because the difference of two positive numbers is smaller than the larger. I also see 6 and neighboring 1 giving 5 in three rows, but cannot say whether that is a general pattern. You ask me to observe again, and I do not know whether to look at sizes, positions, or something else. Could you demonstrate how to think next directly, then leave a little for me to try?

### Teacher

You are right: the maximum must be at the bottom in such triangles, and your reason applies to any row count.

Your observation that “6 and neighboring 1 give 5” is concrete; generalizing it requires distinguishing what depends on particular numbers from what depends only on the rules.

Let us narrow the question: besides **6, 1, and 5** in your triangle, which adjacent group follows the same rule? Write its relationship as an equation, then compare the two equations.

## Round 6

### Student

There are also 6−4=2 and 5−2=3. Like 6−1=5, each is larger minus smaller equals upper; they can also become 1+5=6, 4+2=6, 2+3=5. But is that not just rewriting the rule? I can already calculate these differences and still do not know how it helps judge 2018 rows. Please directly tell me what to check with this relationship, then let me calculate one small step; otherwise I keep going in circles.

### Teacher

You are right; I repeatedly asked you to observe without clarifying what to check. The next question is: **Can equations from different rows be linked to restrict a bottom-row number?**

In your three-row triangle, start from top 3 and always go to the larger adjacent child: first 5, then 6. You already wrote:

\[
3+2=5,\qquad 5+1=6.
\]

Substituting the first into the second gives \(6=3+2+1\), connecting the relationships into a sum.

One small step for you: suppose an **\(n\)-row** triangle is followed downward the same way, always choosing the larger child. At the bottom, how many positive integers sum to its cell value? Can those integers repeat?

## Round 7

### Student

With a concrete route, I can follow now. Three rows gives top 3 plus unchosen 2 in the second row and unchosen 1 in the third. Four rows would add one more, making 4, so n rows gives n terms. Cells are from different rows, and repeats are forbidden, so the summands are distinct. Is the minimum sum of 2018 distinct positive integers 1 through 2018? I have not calculated it yet and do not know whether it gives a contradiction.

### Teacher

Yes, 2018 distinct positive integers sum to at least \(1+2+\cdots+2018\). Your reasoning is correct: the summands occupy different rows, and the problem forbids repeats.

Next calculate the minimum sum and compare it with **the maximum permitted value 2037171**. What two restrictions do they simultaneously impose on the endpoint?

## Round 8

### Student

I pair 1 with 2018 to make 2019, and 2 with 2017 likewise, with 1009 pairs. 2019×1009=2019000+18171=2037171, exactly the maximum. The bottom cell can be neither smaller nor larger, so must equal 2037171. No contradiction yet; the three-row 6 is also exactly 1+2+3. Should we use “exact equality” next?

### Teacher

Yes, we use “exact equality” next. Your calculation and judgment are correct: there is no contradiction yet, only a necessary condition. The three-row example also shows this condition alone does not establish nonexistence.

The path collects 2018 distinct positive integers whose sum equals the minimum possible:

\[
1+2+\cdots+2018=2037171.
\]

**Which numbers must these 2018 summands be?** If any exceeds its corresponding minimum choice, could the total stay unchanged?

## Round 9

### Student

They must be 1 to 2018, one each. Replacing one with 2019 or larger cannot be compensated because the others are already as small as possible. But their order remains undetermined, right? Three rows uses 3, 2, 1, not starting at 1. I understand the restriction but do not know where it leads. Could you point out the next two cells to examine?

### Teacher

Yes, **the summands are exactly 1 to 2018, but their order is undetermined**. Your example demonstrates that.

Next look at **the two adjacent bottom cells** involved in the path's last downward step: one is the reached maximum 2037171, and the other the final collected summand. Treat them as a middle pair in the bottom row, possibly with cells to their left and right.

One small calculation: of 2018 bottom cells, how many remain on both sides after removing the adjacent pair? How many must the longer side have at least?

## Round 10

### Student

There are 2016 left, averaging 1008, so the longer side has at least 1008. If the pair is far left, the left has 0 and right 2016, also consistent. I interpret “middle pair” as an adjacent pair, not necessarily centered, right? What do we do along the longer side next? A diagram of a few cells would help; hearing positions alone confuses me.

### Teacher

Yes, my “middle pair” wording could mislead: they are **the adjacent bottom pair in the final step, not necessarily centered**. Your 2016 and 1008 calculations are correct.

Next look upward from the longer side at the **side triangle** it supports. Here is a small schematic with 3 bottom cells on the left; `A, B` are the adjacent pair:

```text
       □
     □   □
   □   □   □ | A   B
```

Those three bottom cells and three above form a three-row triangle, still obeying the same adjacent-difference rule. The same applies with the right side longer, just reversed.

In the original problem, the longer side has at least 1008 bottom cells, supporting at least 1008 rows. **Next check whether this side triangle overlaps the collected 1 to 2018**, then consider repeating the larger-child path inside it.

First look at the bottom of the diagram: could any of the three left cells be the same cell as the final collected summand \(A\) or \(B\)?

## Round 11

### Student

Those three certainly are neither A nor B; they are three other cells beside them. The diagram is clearer. But I cannot see whether the boxes above might meet earlier summands: the original path could have come from the left? Could you mark the original path and unchosen small cells too? Confirming only that bottom cells differ seems insufficient to say the entire side triangle uses none of 1 to 2018.

### Teacher

You are right: **different bottom cells alone do not prove the whole side triangle avoids the collected numbers**. The original path can come from the left, but must still reach the cell above the final bottom pair.

Here is a six-row schematic. `P` marks path cells; `a` the unchosen child and collected summand at each step; `S` the left side triangle. The top `P` itself is also a collected summand.

```text
               P
             P   a
           a   P   ·
         S   P   a   ·
       S   S   P   a   ·
     S   S   S   P   a   ·
                 └─┬─┘
                Final pair
```

This is only **one possible path**, not a claim that every path looks this way. Each upper cell corresponds to two diagonally adjacent cells in the next row. For example, the fourth-row `P` has as its children the fifth-row `P` to the right of `S` and the adjacent `a`.

First follow `P` from top to bottom and check whether each step's other child is marked `a`. Then ask: if a path cell entered the left `S` triangle, could it still reach the final bottom pair? This helps explain **why every possible path** avoids the side triangle.

## Round 12

### Student

I counted by row and the other child is indeed always marked a. For example, the leftmost S in row four can reach at most bottom cell three in two downward steps, not the pair at four, five. So the path cannot enter S. But we need to exclude a, not just P; since a is not visited, why can it not enter S? Please explain this directly. I do not want to equate “the path stayed outside” with “the collected numbers stayed outside.”

### Teacher

You are right: **the path staying outside a side triangle does not automatically establish that neighboring collected cells stay outside**. We prove that separately.

Call the final bottom pair columns \(p\), \(p+1\) from left to right. For any collected non-top cell \(a\), consider its path cell above:

- This path cell continues along the original path to the cell above the final pair. Thus its bottom-row descendant range contains columns \(p\) and \(p+1\).
- This cell has two children, one being \(a\). Their bottom-row descendant ranges jointly cover the parent's range and meet or overlap in the middle. Thus **whether \(a\) is the left or right child, its bottom-row descendant range meets at least column \(p\) or \(p+1\)**.
- But every left-triangle cell's bottom-row descendants lie left of column \(p\), and every right-triangle cell's descendants lie right of column \(p+1\). Thus \(a\) belongs to neither side triangle.

The top cell is also a collected summand and clearly outside both side triangles. Therefore all collected \(1\) to \(2018\) are outside the side triangles.

Now use “no repeats” for one small step: **how does every number inside a side triangle compare with 2018?**

## Round 13

### Student

They all exceed 2018, since 1 to 2018 have each been used outside. In the small diagram, I understand your descendant ranges as each child dropping one end of the parent's range, so it cannot suddenly miss the central pair; that connects. Following larger children inside a side triangle of at least 1008 rows sums at least 1008 distinct numbers greater than 2018. I first use 2019×1008 for a lower bound: 2019000+16152=2035152, still 2019 short of 2037171. This rough bound is insufficient, right? Must we also account for “no repeats”?

### Teacher

Yes, your rough bound is calculated correctly but insufficient for a contradiction. The key is exactly what you noted: these summands **cannot all be 2019**, because they are distinct.

As with the first minimum sum, sort these at least 1008 distinct positive integers exceeding 2018: the smallest can be 2019; what is the second-smallest at least? The 1008th?

Write the minimum possible sum of these 1008 numbers, then compare with 2037171. You may first judge whether it exceeds the allowed maximum without calculating the exact value.

## Round 14

### Student

The second is at least 2020 and the 1008th at least 3026. The minimum sum is 2019 to 3026, paired into 504 pairs of 5045, totaling 2542680, greater than 2037171. So the endpoint reached in the side triangle exceeds the allowed range, and the original 2018-row triangle does not exist. I can connect it now: first force all of 1 to 2018 into collected cells, then use the same route in an unoccupied side triangle to force an excessive value. Three rows has no contradiction because too few side cells remain for a side triangle like 1008 rows. Have I understood the distinction correctly?

### Teacher

Yes, your understanding is precise and your calculation correct: \(504\times5045=2542680\), exceeding the allowed maximum and producing a contradiction.

More precisely, for three rows the side triangle is too small: the same method's lower bound does not exceed the allowed maximum 6. You also constructed a three-row triangle yourself, proving it feasible. **Feasibility at a small scale does not imply feasibility at a large scale.**

Looking back from trying individual arrangements to proving 2018 rows impossible, what was the key change in thinking?

### Student

The key was to assume the whole triangle had been arranged and ask what restrictions the rules force, rather than guessing its arrangement. I only learned to turn differences into successive addition along larger children after your demonstration; I could calculate the later minimum sums myself. The diagram and descendant ranges supplied the reason the side triangle used none of the small numbers. Earlier I really was stuck when only asked to observe. I will stop here on this problem; I still cannot explain the side-triangle positional proof fluently without the diagram, but do not want to repeat the calculations.

### Teacher

This teaching session has been confirmed as ended.
