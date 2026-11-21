# P02 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P02 |

## Round 1

### Student

Teacher, I want to look at a small one first. Putting 2 and 3 below and 1 above, because 3 minus 2 is 1, uses 1, 2, 3 once each in two rows, right? Does "absolute value" just mean larger minus smaller? There are too many rows in 2018. Please explain one step at a time first and give me a small one to try myself.

### Teacher

Yes, your two-row triangle follows the rules and uses 1, 2, 3 once each.

The **absolute difference** between two numbers can be understood as the larger minus the smaller; if they are equal, the result is 0.

Now try three rows: use **each of 1 to 6 once** to fill these cells, making every upper cell equal the absolute difference of the two adjacent cells below.

```text
      □
    □   □
  □   □   □
```

Try arranging them first and tell me your result.

## Round 2

### Student

I first put 4, 5, 6 below. Above 4 and 5 is 1, and above 5 and 6 is also 1, so the top becomes 0. That repeats 1 and uses the disallowed 0, so my arrangement fails. But changing the three bottom numbers around, I do not know which to change first. Could you just hint at which position to look at first? I want to calculate the rest myself.

### Teacher

Your judgment is right: this arrangement repeats 1 and uses the disallowed 0.

Which bottom position would you like to change first? Choose one, change it, and calculate what appears above yourself.

## Round 3

### Student

I changed the middle 5 to 1, making the bottom 4, 1, 6. Above I get 3 and 5, and at the top 2. So it is 2; 3, 5; 4, 1, 6, all six numbers different and all of 1 to 6 included! I found this one myself. But if three rows can be arranged, can 2018 rows? I do not know how this small one tells us about the large one. Could you first use small numbers to show what to notice?

### Teacher

Yes! Your three-row triangle follows the rules and uses each of 1 to 6 once.

Arranging three rows establishes **three-row feasibility**; this example alone does not establish feasibility for 2018 rows.

You now have two- and three-row examples. Which aspects would you like to compare first to look for a pattern worth investigating?

## Round 4

### Student

In both examples the largest numbers, 3 and 6, are at the bottom. I want to look at that. For example, putting 6 above means the two numbers below are both less than 6, so their difference seems unable to reach 6. Does that mean 6 must be at the bottom? But I still do not know what to look at next. You keep asking me to choose, and I feel directionless. Could you give me one specific small question, just one step, so I can continue trying?

### Teacher

Yes, your reasoning holds: if 6 is above the bottom, the two positive integers below are both less than 6, so their difference cannot equal 6. Thus 6 must be at the bottom.

Next look only at your three-row triangle:

```text
      2
    3   5
  4   1   6
```

Start at the top **2** and always move to the larger of the two adjacent numbers below. Which numbers do you visit?

## Round 5

### Student

First 5, because 5 is greater than 3; then 6, because 6 is greater than 1. I visit 2, 5, 6. I can follow one step like this. But why choose the larger one? What can this path help us know?

### Teacher

Yes, the path is **2 → 5 → 6**.

Choosing the larger one lets us observe the relationship between the path numbers and those beside them. First look only at the first step: below 2 are 3 and 5.

Can you express 5 using **addition of 2 and 3**?

## Round 6

### Student

2 plus 3 equals 5. The next step is also 5 plus 1 equals 6, so we add the unchosen sibling, right? I can calculate both. Would another triangle do this too, or is it just a coincidence in mine?

### Teacher

Yes, both steps are correct: each number reached equals the number at the previous cell plus the unchosen sibling.

We can use the triangle rule to test whether it is coincidental. Suppose the larger number below a cell is **7** and the smaller **4**. According to the rule, what is the upper cell?

## Round 7

### Student

7 minus 4 is 3, so the upper cell is 3. Adding 4 back makes 3 plus 4 equal 7. Now I understand why addition works in this step. But these are still just a few small numbers, and I do not know how it affects 2018 rows. Do we next add all the siblings along the path? Could you point out the summands in the same diagram, without switching to letters at once?

### Teacher

Yes, we can try your idea. Returning to your diagram, the path is **2 → 5 → 6**:

```text
      2
    3   5
  4   1   6
```

You have written **2+3=5** and **5+1=6**. Now connect the two steps: can one addition starting at the top 2 directly give the bottom 6?

## Round 8

### Student

2 plus 3 plus 1 equals 6. We do not add 5 again because the earlier 2 plus 3 already makes 5. But why not add the unvisited 4? Do we add only the number immediately beside the path at each step? I can connect it in this diagram now but still cannot count how many numbers the large triangle needs.

### Teacher

Yes, **2+3+1=6**, and your explanation is right: 5 already comes from 2+3, so it is not added again.

Each step adds **the unchosen one of the two numbers below the current cell**. Moving 2 → 5 adds 3; moving 5 → 6 adds 1. Although 4 is unvisited, it is not the "other number" selected in either step, so it is not added.

We can count similarly for a large triangle: include the top first, then consider how many numbers each downward row adds. How many downward steps go from the top to row 4?

## Round 9

### Student

One step from row one to two, two to row three, and three to row four. So one top cell plus three additions gives four numbers. I can count with your explanation. Does 2018 rows mean 2017 steps plus the top, making 2018 numbers? Their sum must equal that bottom number, but I do not know how to calculate without trying one by one.

### Teacher

Yes! With 2018 rows there are 2017 steps plus the top, giving **2018 numbers** in the sum.

We need not first guess each value; we can ask **how small the sum can be**. First try one step with small numbers:

What is the smallest sum of **3 distinct positive integers**?

## Round 10

### Student

Choose 1, 2, 3, summing to 6. We cannot choose all 1s because repetition is forbidden, and 0 is disallowed too. Replacing one with 4 increases the sum. But the three-row triangle is also exactly 2 plus 3 plus 1 equals 6, without a problem. For 2018 numbers, do we add from 1 all the way to 2018? I cannot calculate such a long sum. Could you teach me a shorter way?

### Teacher

Yes, the minimum sum of 2018 distinct positive integers is from 1 to 2018.

**Pair the first and last terms** instead of adding one by one:

- 1+2018=2019
- 2+2017=2019
- 3+2016=2019
- …

This gives 2018÷2=1009 pairs, each totaling 2019, so:

**1+2+…+2018=2019×1009=2037171.**

You also noticed that in the three-row example, the minimum sum 6 exactly equals the bottom cell reached by the path.

## Round 11

### Student

I understand pairing a front and back number to get 2019. For the 1009 pairs and the multiplication afterward, I am following your result; I still cannot calculate numbers this large myself. The minimum sum already equals the maximum 2037171, so the bottom must equal it and cannot be larger, right? It still seems not to exceed anything, so how does this tell us whether it can be arranged?

### Teacher

Yes, **assuming the triangle can be arranged**, the endpoint cannot be smaller or larger than 2037171, so must equal 2037171.

You are right: no contradiction has arisen yet, so this step alone cannot decide feasibility. First consider the restriction that "must equal" imposes on the summands.

Returning to the small example, if three distinct positive integers sum to exactly the minimum 6, what can they be?

## Round 12

### Student

Still 1, 2, 3, in any order. Substituting a larger number exceeds 6. Must the large triangle likewise use only 1 to 2018 as summands? But the summands are beside the path, and the path still has numbers such as 5. I am getting confused. Could you write "summands" and "visited numbers" separately, then tell me which group to look at next?

### Teacher

Yes. Assuming the large triangle can be arranged, these 2018 summands must attain the minimum sum exactly, so they can only be **1 to 2018**, possibly in a different order.

Separate them using your three-row triangle:

```text
      2
    3   5
  4   1   6
```

- **Visited numbers:** 2 → 5 → 6.
- **Summands:** the top 2 plus the unchosen siblings 3 and 1, or 2+3+1=6.

The top 2 belongs to both groups; the path's 5 is an intermediate result, not added again as a summand.

Next focus on **the summands**. In the hypothetical large triangle, all of 1 to 2018 are already in this group. Can the other cells contain these numbers too?

## Round 13

### Student

No, because that would repeat them. In my diagram, 1, 2, 3 are used and the other cells are 4, 5, 6. The other cells in the large triangle must be 2019 or greater. Writing them separately makes it a little clearer. But what is wrong with those cells containing large numbers? I still see no repetition.

### Teacher

You are right: **large numbers do not themselves violate the rules**. We have not yet found repetition or any other contradiction.

Let us use the three-row triangle for a small step:

```text
      2
    3   5
  4   1   6
```

The summands 2, 3, 1 occupy the smallest three numbers. The remaining 4, 5, 6 are larger. Can you find a small triangle consisting only of these remaining cells that is itself a number triangle?

## Round 14

### Student

I cannot. Below 5 are 1 and 6, including 1; below 3 are 4 and 1, also including 1. The 4 and 6 have 1 between them, so we cannot directly subtract them, right? Also, 6 minus 4 is 2, not 5. Am I looking incorrectly, or do the remaining cells not necessarily form a small triangle? Could you point out the specific three cells?

### Teacher

You are not mistaken; my question was wrong. **The remaining 4, 5, 6 in this three-row triangle cannot form a three-cell triangle**. The 4 and 6 are not adjacent and cannot be treated as a pair below one cell. Thank you for checking carefully.

But the remaining **4 alone** can count as a one-row triangle. In this three-row example it is too small to produce a contradiction.

Next we can set numbers aside and consider only positions: with more rows, if the final two adjacent cells reached by the path split the bottom into left, middle, and right parts, which part might leave a larger triangular region?

## Round 15

### Student

Your acknowledging the error tells me I did not miss something. But I do not understand "the final two adjacent cells reached": does the path not reach only one bottom cell? I cannot picture left, middle, and right either. Could you draw a four-row positional diagram labeling visited cells and summands, then let me find unused places? Please do not ask me to imagine many rows at once.

### Teacher

You are right; the path finally reaches only one cell. My wording was inaccurate: the final step compares the **two adjacent cells** below it, then moves to the larger.

Here is a four-row triangle:

```text
            4  Path, Sum
         2  Sum     6  Path
      5  Sum     7  Path     1
   8  Sum    3  Path    10       9
```

"Path" marks visited cells: 4 → 6 → 7 → 3? The final step must choose the larger, so it should go to **8**. Correcting the labels:

```text
            4  Path, Sum
         2  Sum     6  Path
      5        7  Path     1  Sum
   8       3  Sum    10  Path     9
```

The path is **4 → 6 → 7 → 10** and the summands are **4, 2, 1, 3**. The last step compares bottom numbers **3 and 10**, goes to 10, and uses 3 as a summand.

Now look only at cells marked neither "Path" nor "Sum": on which side do you think an unused small triangle lies?

## Round 16

### Student

There is 5 on the left, with 8 and 3 below, all unlabeled, and 8 minus 3 is 5. But I calculate that above 5 and 7 should be 2, whereas your diagram has 6 there; above 7 and 1 should be 6, whereas the diagram has 2. Is this triangle still arranged incorrectly? The labels changed several times and I am confused now. Please first give me a checked diagram, then I will look at the small triangle.

### Teacher

Sorry, I first wrote the wrong path, then crowded the positions with text labels. I have rechecked the diagram below; first, numbers only:

```text
          4
        2   6
      5   7   1
    8   3  10   9
```

Your two calculations are correct: above 5 and 7 is 2, and above 7 and 1 is 6. The adjacent bottom differences are 5, 7, 1, and the top is also 6−2=4.

Here the path is **4 → 6 → 7 → 10** and the summands are **4, 2, 1, 3**. Thus your small left triangle 5, 8, 3 indeed satisfies 8−3=5, but its **3 is a summand**.

Using this diagram again, can you find a small triangle containing no summands at all? A single cell also counts as a one-row triangle.

## Round 17

### Student

This numbers-only diagram is clearer; I misread the positions before. Since 3 is a summand, those three left cells do not work either. Below 7 there is also 3, and 1 is itself a summand. The single 8 or 9 works, but I still cannot find three cells none of which were added. Continually finding single cells does not tell me how to reach the 2018-row conclusion. Could you directly state what needs proving next, then explain using a small diagram?

### Teacher

Next we need to prove: **in the large triangle, a sufficiently large small side triangle exists whose cells all avoid the summands collected the first time**. Then all its numbers exceed 2018, allowing us to study their sum further.

First look at the final step's positions in the four-row triangle:

```text
      7
    /   \
   3    10
```

The path moves from 7 to 10, and 3 is this step's summand. Putting these bottom cells back into the whole triangle shows one cell remaining on each side:

```text
          4
        2   6
      5   7   1
    8   3  10   9
    Left └─Pair─┘ Right
```

Here the left and right each have a one-row side triangle, 8 and 9. Neither was selected as a summand. The four-row example only clarifies positions and **does not yet prove** how large a side triangle is with 2018 rows.

First look at the bottom: excluding the middle pair 3, 10, how many cells remain on the left and right altogether?

## Round 18

### Student

Two remain: 8 on the left, 9 on the right. Subtracting two from 2018 gives 2016; I can do that subtraction. But I do not know why a remaining bottom row means the triangle above also avoids those summands. I remember you said this still needs proving; counting the bottom alone does not mean it is proved. Please explain this first; I am afraid of losing track of the numbers in the middle again.

### Teacher

You are right; the **positional relationship** needs explaining. The key is which bottom positions a cell can reach by descending.

Call the final two compared bottom cells the "middle pair." Continuing down the original path from any path cell reaches that pair, while each sibling selected as a summand is adjacent to the path's next cell.

Now consider any cell in the left triangle: descending from it, regardless of choosing left or right each time, can reach only bottom cells **to the left of the middle pair**. Similarly, right-triangle cells can reach only bottom cells to the right of the pair.

Each summand along the way and the next path cell are adjacent children of the same upper cell: if the next cell continues toward the middle pair, then the summand can also descend to at least one position in that pair. Thus it cannot lie in a triangle whose cells lead only to left or right bottom cells. The top cell is outside the side triangles too.

Therefore both side triangles avoid all summands from the first collection. This is guaranteed by **adjacency and the range of positions reachable downward**, rather than merely by cells remaining on both sides at the bottom.

Pause here: can you explain in your own words why descending from a cell in the left triangle cannot reach the middle pair?

## Round 19

### Student

I can only say that below the small triangle are those left cells, so going downward inside it cannot reach the middle. But that feels like repeating your words; I cannot see where the boundary is. In particular, I still cannot check "the sibling can also reach at least one middle position" myself. I could not connect that long explanation. Could you draw five rows of empty cells and circle only the three left cells, so I can follow each route as if with my finger?

### Teacher

Yes. First suppose the final two compared bottom cells occupy positions **3, 4**; circles mark only the three cells of the small left triangle:

```text
                 □
              □     □
           □     □     □
        (□)    □     □     □
     (□)   (□)    □     □     □
      1     2      3     4     5
                   └─Pair─┘
```

First follow only **the uppermost circled cell**: one downward step reaches only its two adjacent circles directly below, bottom cell 1 or 2.

Try following both routes: can either reach cell 3 or 4? Let us clarify this boundary first, then examine summands beside the path.

## Round 20

### Student

No. Left reaches 1, right reaches 2, and that is the bottom; it cannot move sideways to 3. Circling it makes it clear. But this diagram still has no path or sibling summands; I only understand these three circles, so we cannot say I already understand why none can be summands. Please label one sibling summand for me to check.

### Teacher

Yes, seeing those three circles alone does not establish that all summands avoid them.

This is still a five-row positional diagram. Suppose the path reaches **P** in row four, then moves to bottom cell 4; cell 3 is the final step's sibling summand **A**:

```text
                 □
              □     □
           □     □     □
        (□)    □     P     □
     (□)   (□)    A     □     □
      1     2      3     4     5
```

Check only this **A**, in bottom cell 3. Is it inside the circled small left triangle?

## Round 21

### Student

A is not inside: it is cell 3, while the circles occupy cells 1, 2. But you gave the final step; what about earlier summands? I feel we keep looking at the final pair without resolving earlier steps. Could you label cell 2 in row four and see whether it could be the previous step's summand? It is close to the circles, and I want to check it.

### Teacher

Yes, earlier summands need checking too. Label cell 2 of row four **B**:

```text
                 □
              □     □
           □     Q     □
        (□)    B     P     □
     (□)   (□)    A     □     □
      1     2      3     4     5
```

**Q** in row three is directly above B and P. If the path moves from Q to P, B is that step's sibling summand. Although it is immediately beside the left circles, **it is not itself inside them**.

Descend one step from B: which two bottom cells can it reach?

### Student

Cells 2 and 3, and cell 3 is A. So this B really is outside the circles and can reach the middle by moving right. I understand this step now. But checking many more earlier steps leaves me unable to distinguish how the initial summands, path, and small triangle connect. I want to stop here today: I can follow calculations in small diagrams, but still do not understand whether 2018 rows can be arranged, so I cannot say it is proved.

### Teacher

This teaching session has been confirmed as ended.
