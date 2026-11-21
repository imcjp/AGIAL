# P01 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P01 |

## Round 1

### Student

Teacher, I want to try a small one first. For two rows using 1, 2, 3, I put 1 and 3 below and 2 above, because 3 minus 1 equals 2. Does that follow the rules? There are too many rows in 2018, and I still do not know where to start judging it. Could I try three rows first? Please do not tell me how to arrange them yet.

### Teacher

Yes, your two-row arrangement follows the rules: 1, 2, 3 are each used once, and the upper 2 equals the absolute difference between the two lower numbers.

Of course you can try three rows first. Try arranging them yourself and tell me your arrangement or working afterward.

## Round 2

### Student

Three rows contain 6 cells, so I tried using 1 to 6. Putting 1, 6, 4 below gives 5, 2 in the middle and 3 above, exactly without repetitions! Is my calculation right? But finding that three rows work does not mean 2018 rows work. What should I look at next? I would lose track arranging so many at once; could you give me a smaller direction?

### Teacher

Your calculation is right: the middle numbers are \(|6-1|=5\), \(|6-4|=2\), and the top is \(|5-2|=3\), using each number from 1 to 6 once.

You are also right that arranging three rows establishes only three-row feasibility and does not yet decide feasibility for 2018 rows.

Let us set aside the large triangle. Looking back at your two- and three-row arrangements, what could you try observing or ask about next? Just choose one direction that interests you.

## Round 3

### Student

I see that the largest numbers, 3 and 6, are both at the bottom. It seems the largest number cannot be above, because subtracting two smaller positive numbers cannot give a difference larger than them. But even knowing that, I still do not know how to move toward 2018 rows. When you ask me to choose a direction myself, I find it hard to choose. Could you give me a specific small question or hint? A little at a time; I want to continue calculating myself.

### Teacher

Your reasoning is right: every upper cell is smaller than the larger positive number below it, so the largest number in the whole triangle must be in the bottom row.

Let us look only at your three-row triangle. Apart from the largest number's position, can you pose a small question you would like to investigate? You need not think of 2018 rows immediately or answer it right away.

## Round 4

### Student

I want to ask whether, since putting 6 in the middle of the bottom row works for three rows, putting it at an edge also works. I could try different arrangements. But I really want to know how to judge 2018 rows. You keep asking me to think of a question myself, and I do not know what this trying will help with. Could you give me a specific place to check this time and explain why I should check it?

### Teacher

You are right; I did not explain the connection between trial arrangements and the 2018-row problem. Your question about whether 6 can go at an edge is specific: trials can help us understand the possibilities for small triangles, but their results alone cannot decide 2018 rows.

Let us start with your question: can you construct a valid three-row triangle with 6 at a bottom edge? Try it and notice which necessary conditions you use. Then we can look together at which conditions also apply to taller triangles.

## Round 5

### Student

I first tried 6, 1, 3, giving 5, 2 in the middle and another 3 at the top. Switching to 6, 2, 5 gives 4, 3 in the middle and 1 at the top. This time all of 1 to 6 appear, so 6 can be at an edge too. I know we must do more than subtract correctly each time: we must check that no number repeats throughout the triangle. Checking a large one this way would require many calculations, and I still cannot judge 2018 rows. You said we would look together at applicable conditions; could you guide me through one now? I do not want to keep trying different numbers.

### Teacher

Your check is right: the second arrangement uses each number from 1 to 6 once and shows that 6 can occupy a bottom edge.

You identified a condition applying to the large triangle: **no cell numbers can repeat**. In the first arrangement, although every difference was correct, the repeated 3 invalidated it; 2018 rows must satisfy the same condition.

We need not continue changing numbers and trying arrangements. Can you consider how to use "all numbers are different" to constrain how large or small some numbers in the triangle can be? You need not find a complete decision method immediately; just offer one idea.

## Round 6

### Student

I can only think that two numbers cannot be equal, because subtracting equal numbers gives 0. But that still seems not to say how large they can be. I do not know how to get from "no repetitions" to your size restriction. Could you take my 6, 2, 5 and point to two numbers to explain one step? Just asking me to think of an idea has left me stuck several times already.

### Teacher

You are right; I repeatedly asked you to think independently without helping you past the obstacle. Let us look at the bottom **6 and 2**.

They are two distinct positive integers. For any two distinct positive integers, the smaller is at least 1 and the larger at least 2, so their sum is at least **1+2=3**.

In your example, 6+2=8 also satisfies this restriction. The key is that this lower bound depends only on "positive integers" and "distinct," not the specific arrangement.

Now try one step: what is the smallest possible sum of **three distinct positive integers**?

## Round 7

### Student

The smallest are 1, 2, 3, summing to 6. We cannot use 1, 1, 2 because that repeats; replacing them with 1, 2, 4 gives 7, which is larger. I can follow when you give one step like this. But the triangle uses subtraction, so why are we looking at sums now? Which cells should we add to help judge the large triangle?

### Teacher

Yes, three distinct positive integers sum to at least **6**. Your question is crucial: to make this lower bound useful, we cannot just add arbitrary cells; we need a group related to some number in the triangle.

Look at your arrangement:

```text
    1
   4 3
  6 2 5
```

The middle-left 4 comes from \(6-2=4\), which can also be reversed as **\(6=4+2\)**: the larger lower cell equals the upper cell plus the other lower cell.

Starting at the top 1, look at 4 and 3 below. Can you write a similar addition equation?

## Round 8

### Student

4 minus 3 equals 1, so 4 equals 1 plus 3. Substituting into 6 equals 4 plus 2 gives 6 equals 1 plus 3 plus 2, and the sum really is 6! Looking at the connections helps me understand a little. But this is only my arrangement; if the larger lower number were on the other side in another triangle, could we keep adding this way? Could I try another small example?

### Teacher

You connected it correctly: \(6=4+2=(1+3)+2\).

Yes, try another small example. Let us use your original three-row triangle:

```text
    3
   5 2
  1 6 4
```

Start at the top 3 and always move to the larger of the two adjacent cells below. Can you write two addition steps along this path and connect them? This time, notice whether the larger number is on the left or right at each step.

## Round 9

### Student

First I move from 3 to the left 5, with 5 equal to 3 plus 2. Then I move from 5 to the right 6, with 6 equal to 5 plus 1, so 6 equals 3 plus 2 plus 1. We do not need to keep going the same way, just choose the larger number. Both examples end with three distinct numbers added. With four rows, would it become four distinct numbers summing to at least 10? I worry the numbers recorded along the way might come from the same cell. How can we check?

### Teacher

Yes! With four rows you obtain the sum of four distinct positive integers, at least \(1+2+3+4=10\).

To check repetition, look at **which row each recorded number comes from**:

- Record the top cell first, from the first row.
- At each downward step, record the unchosen lower cell: from the second, third, and fourth rows, respectively.

They occupy different rows and therefore cannot be the same cell; since the problem also forbids repeated numbers in the whole triangle, their numbers are distinct too.

Try generalizing: for \(n\) rows, descending through larger lower cells to the bottom, how many distinct positive integers are added, and what is their minimum sum?

## Round 10

### Student

One is recorded per row, so four rows give four and 2018 rows give 2018. They cannot repeat, so the minimum uses 1, 2, 3 all the way to 2018. I am not good at writing letters, so I will say it this way first. But does their sum not equal the whole triangle's cell count, 2037171? The bottom number could equal the largest number, 2037171, so it has not exceeded it yet. How do we decide whether it works next?

### Teacher

You are right: **there is no contradiction yet**. Your explanation in words is also clear; there is no rush to use letters.

Assuming the 2018-row triangle can be arranged, the bottom cell reached along the path is at least 2037171, while the largest permitted number is also 2037171, so this cell must **equal** 2037171 **exactly**.

Next we can study this "exactly." Return to three familiar numbers: if three distinct positive integers sum to the minimum, 6, which three must they be? What do you think the same reasoning implies for the 2018 recorded numbers?

## Round 11

### Student

The three can only be 1, 2, 3, in any order. Replacing 3 with 4 increases the sum by 1, and no positive integer smaller than 1 can offset it. Then the 2018 numbers must also be exactly 1 to 2018, right? So the recorded number from each row is no greater than 2018. But the bottom endpoint is still 2037171, and I cannot see a clash. Should we next look at the visited cells or the unvisited ones?

### Teacher

Yes, assuming the triangle can be arranged, the 2018 recorded numbers are exactly **1 to 2018**, possibly in a different order. You explained it clearly.

Next look at **the cells not recorded**. Since all of 1 to 2018 have been recorded and no number can repeat in the triangle, all other cell numbers exceed 2018.

This is still not a contradiction but gives a new size restriction. If we could find a complete small number triangle among these unrecorded cells, could we apply the same method of "descending through larger numbers and adding them" inside it?

## Round 12

### Student

If there really is a complete small triangle, the numbers below still subtract, so we should be able to walk as before. But the "unrecorded" cells are scattered, and I cannot imagine how to guarantee they form a triangle. Could you draw a smaller diagram labeling visited, recorded, and remaining cells for me to look through? With words alone I find these three kinds hard to distinguish.

### Teacher

Yes. First use a six-row schematic **showing positions only, without numbers**. Assume the path follows the directions shown; it only helps us see positions and does not represent a six-row triangle already satisfying the number rules.

```text
              ◎
            C  P
          R  C  P
        R  R  P  C
      R  R  C  P  R
    R  R  R  C  P  R
```

- **◎**: the top cell, both the path's starting point and the first recorded cell.
- **P**: a visited path cell.
- **C**: the cell recorded on the other side at each downward step.
- **R**: a remaining cell, neither visited nor recorded.

For example, from the P in row three to the P in row four, the path moves down-left and the cell beside it is recorded as C.

First look for connected R cells forming a small triangle **containing an upper cell and both adjacent cells below it**. Tell me how many rows it has once you find it.

## Round 13

### Student

I found three rows at the bottom left: the far-left R in row four, the two far-left R cells in row five, and the three far-left R cells in row six. We cannot include the far-left cell of row three because cell three of row five is C, leaving a piece missing. With this drawing I can check. But this is only this path; if it keeps going left, there is no bottom-left triangle, so would we find it on the right? How large a small triangle must we guarantee?

### Teacher

You found it correctly, and your concern is reasonable: when the path stays left, look right instead. Let us count using six rows first, without guessing where the path goes.

The last step involves two adjacent bottom cells: one P and one C. They occupy 2 cells, leaving **4 cells** distributed to the left and right of this pair.

- If the final pair is at the far left, there are 4 cells on the right.
- If it is in the middle, there are 2 cells on each side.

Regardless of how these 4 cells are split, **what is the minimum number on the larger side**? This will help us judge the minimum size of a small side triangle we can find.

## Round 14

### Student

At least 2 cells. Splitting them 2 and 2 makes the larger side 2; splitting them 1 and 3 or 0 and 4 makes it larger. With 2018 rows, removing those two leaves 2016 cells, so one side has at least 1008 cells. But even if the bottom row is long enough, could the C cells above extend into this small triangle? I still do not understand why counting the bottom row guarantees completeness. Could you explain using a small two-row piece?

### Teacher

Your concern is right: **counting only the bottom row does not establish that the cells above were unrecorded**. Let us first examine a two-row piece.

Suppose just before the last step the path reaches cell \(P\) in the penultimate row. The two adjacent cells below it form the final pair:

```text
Penultimate row:     A   P
Bottom row:         a   b   c   d
                          ↑   ↑
                         Final pair
```

Here the children of \(A\) are \(a,b\), and those of \(P\) are \(c,d\). Thus \(A,a,b\) form a two-row small triangle.

Why cannot \(A\) be a previously recorded cell? Every previously recorded cell is the other lower child of a path cell. If it were \(A\), the other child of that same path cell would have to be immediately beside \(A\) on the left or right. But the path must then continue from that cell to \(P\): in the penultimate row, only one step remains, so the path cell can only be \(P\), and the recorded cell can only be the other child of \(P\), rather than \(A\) in the same row. The bottom \(a,b\) also lie outside the final pair, so neither can be the last recorded cell.

More generally, track the path upward from the final pair: each upward row expands the possible positions by at most one cell on each side; the recorded cell on the other side is constrained by that range too. The small side triangle lies completely outside this range.

First check the two-row diagram above: **which two cells are the children of \(P\)? Do they overlap the bottom cells of the small left triangle?** Then apply the same idea to taller side triangles.

## Round 15

### Student

You wrote that P has c, d below and A has a, b below, so those pairs do not overlap. But in my original three-row triangle, the middle 5 and 2 have 1, 6 and 6, 4 below them, sharing a 6. A and P look adjacent in the diagram, so why do they not share a lower cell? Is there a missing cell between A and P? I could not follow the long passage about tracing upward. Could you complete this diagram first, then label where the previous step went and what it recorded?

### Teacher

You are right: I **omitted a cell** in the previous diagram, and the subsequent explanation was invalid too. Adjacent upper cells do share a lower cell. Thank you for pointing it out.

After completing it, first consider a possible path through the last three rows:

```text
Third-to-last row:          Q (reached in previous step)
                           / \
Penultimate row:     A    B (recorded) P (visited)
                   / \  / \           / \
Bottom row:        a   b   x           c   d
                                      Final pair
```

The text may make the slashes difficult to align; use the following adjacency relationships as authoritative:

- The children of \(A\) are **a, b**; of \(B\), **b, x**; and of \(P\), **x, c**. Thus I must relabel the final pair as **x, c**, rather than the c, d indicated by the arrows.
- The previous step goes from \(Q\) to \(P\), recording \(B\).
- The final step goes from \(P\) to the larger of **x, c**, recording the other.
- On the left, \(A,a,b\) form a small two-row triangle; these cells were neither visited nor recorded in these two steps.

To avoid confusion from those arrows, here are the three rows aligned by columns again:

```text
Third-to-last row:        Q
                         / \
Penultimate row:    A   B   P
                  / \ / \ / \
Bottom row:       a  b  x  c
                       ↑  ↑
                      Final pair
```

Here \(Q\) is **directly above B and P**. First check: in this completed diagram, which lower cell do \(A\) and \(B\) share, and which do \(B\) and \(P\) share?

## Round 16

### Student

A and B share b, and B and P share x. In the final diagram, the small two-row triangle A, a, b really is unrecorded. This time it matches, but the previous diagram changed the final pair again, making me look back and forth and get confused easily. Please do not add a new diagram yet. I still cannot guarantee that region with 1008 rows myself, but if everything in it really exceeds 2018, would adding 1008 such numbers by walking to the bottom make it too large? Could you help me calculate it clearly first?

### Teacher

Yes, if **every number in that 1008-row small triangle really exceeds 2018**, descending through larger lower cells makes the bottom cell equal to the sum of 1008 distinct positive integers, all greater than 2018.

The smallest possible 1008 numbers are 2019, 2020, …, 3026, so their sum is at least:

\[
\frac{(2019+3026)\times1008}{2}
= \mathbf{2542680}.
\]

This exceeds the maximum **2037171** permitted in the whole triangle by **505509**.

Thus your judgment is right: **conditional on that small triangle existing and all its numbers exceeding 2018, a contradiction arises**. We still need to prove that condition clearly; the small diagram was only an example and cannot by itself guarantee this for all paths.

### Student

Let us stop here today. I can now follow how subtraction in the small triangle becomes addition and how to record one number per row. I also know that 2542680 exceeds 2037171 and that if that small triangle really exists, the arrangement fails. But I still do not understand why every possible path must leave a small triangle with 1008 rows, so I cannot say I have proved that 2018 rows are impossible. The earlier diagrams changed several times, and I am a bit confused now and do not want to look at new steps.

### Teacher

This teaching session has been confirmed as ended.
