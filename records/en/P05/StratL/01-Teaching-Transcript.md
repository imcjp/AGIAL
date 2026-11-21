# P05 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | StratL |
| Participant ID | P05 |

## Round 1

### Student

Teacher, I want to confirm the rules: with two rows, putting 1, 3 below gives 2 above, using exactly 1 to 3, so that should work, right? But I do not know where to start judging 2018 rows, and cannot keep filling by trial forever. Could you give me a smaller direction to try calculating myself, then see which relationships apply to the large triangle?

### Teacher

Yes, your two-row example works: the upper number is |3−1|=2, and 1, 2, 3 are each used once.

Next try **three rows**, with 6 cells requiring 1 to 6 once each. Do you conjecture that such a triangle can be constructed? Try intuitively first, and record any relationships you discover.

## Round 2

### Student

I guess three rows work too. Trying bottom row 1, 6, 4 gives 5, 2 in the middle and 3 at the top, all six numbers distinct, so it does work. Success with two and three rows still does not show 2018 rows work, right? I noticed the upper difference is always smaller than the larger lower number, so 6 can only be at the bottom. Is this useful? What should we compare next to move beyond trial filling?

### Teacher

Your three-row triangle works: the middle is 5, 2, the top is 3, and 1 to 6 occur exactly once each. You are also right that constructibility for two and three rows does not show constructibility for 2018 rows.

Your magnitude relationship is useful. First state it more precisely: if a cell is \(a\) and its adjacent lower cells are \(b\), \(c\), can you express your observation with equations and inequalities?

Also consider why this relationship shows the maximum 6 can only be at the bottom. Does your reasoning generalize to any row count?

## Round 3

### Student

We can write a=|b-c|<max(b,c), because b and c are positive; if b exceeds c, for instance, a=b-c<b. If the maximum were above the bottom, a larger number would have to lie below it, contradicting maximality. This works for every row count, so here 2037171 must also be at the bottom. I can explain that now. But knowing only the maximum’s position does not show how to judge existence of the whole triangle. Could you give a small question using this relationship next, or a hint about which other positions to observe?

### Teacher

Your explanation is correct: positivity makes the upper difference strictly smaller than the larger lower number, so the global maximum must be at the bottom. This reasoning applies to any row count.

Next revisit your three-row triangle and use this relationship to examine more cells. Can you propose a conjecture about the positions or magnitudes of its numbers? You need not prove it or immediately generalize to 2018 rows.

## Round 4

### Student

I see 5 in row two with 6 below; the top 3 has 5 below and can also reach 6 farther down. So I conjecture every non-bottom number can follow larger lower numbers to a larger bottom number. But we cannot say all numbers in an upper row are smaller than all in the row below, since second-row 5 exceeds bottom numbers 1 and 4. This conjecture seems merely to repeat the original relationship. I am stuck: continuing to observe positions leaves me unsure what to test. Could you be explicit, perhaps give a true-or-false conjecture for me to seek reasoning or a counterexample?

### Teacher

Your path conjecture holds, and your three-row example rules out the conjecture that “every number in an upper row is smaller than every number in the lower row.”

Let us test a more specific conjecture:

**Starting at the top cell and always following the larger adjacent lower number must end at the global maximum.**

Check it in your three-row triangle first, then consider whether it necessarily holds in other triangles. You may seek reasoning or try a counterexample.

## Round 5

### Student

My three-row path is 3→5→6 and does reach the maximum. But choosing only the larger of two neighbors each time may not reach the global maximum, I think. Under just the difference rule, bottom 10, 9, 1 gives middle 1, 8 and top 7, producing 7→8→9 and missing 10. But this repeats 1 and does not use all consecutive integers, so it does not meet all original requirements. I am unsure: must the “other triangles” also use exactly 1 to the cell count? If so, this is no counterexample. The specific conjecture tells me how to check, but I still need the conditions clarified and its connection back to 2018 rows.

### Teacher

You are right; my previous question did not state the conditions clearly. To reconnect to the original problem, restrict the conjecture to: **a triangle with \(n\) rows, using 1 to \(N=n(n+1)/2\) exactly once each, with each upper cell the absolute difference of its adjacent lower cells.**

Your example effectively shows that the difference rule alone does not establish the conjecture, but does not refute it with the added condition “each consecutive integer used once.”

If the restricted conjecture can be proved for every \(n\), it also applies to a hypothetically existing 2018-row triangle. How could we use “1 to \(N\), each used once” to examine that top-down path?

## Round 6

### Student

I can see that the path contains n distinct increasing integers between 1 and N. But that alone cannot guarantee it ends at N: choosing 1, 2, 4 from 1 to 6 meets those conditions too. Using each consecutive integer once may require numbers outside the path, but I do not know how to connect them. I cannot currently prove the path conjecture, and even if it reaches N, I still do not see a contradiction with 2018. Could you explain one key connection first or suggest a specific inequality? Just continuing to guess leaves me unsure what step to take.

### Teacher

Your judgment is correct: increasing, distinct path values do not guarantee endpoint \(N\). You have identified this reasoning gap.

Since you want a more specific task, return to the three-row triangle and its path \(3\to5\to6\). How much does the path value increase at each step? Which numbers in the triangle are these increments?

Write the relationships for this example first, then see whether they can express the path endpoint.

## Round 7

### Student

5−3=2 and 6−5=1, precisely the adjacent number not chosen at each step. Thus 6=3+2+1. In general, if upper a=b−c and we follow larger b, then b=a+c. Adding along the path makes the endpoint equal the top plus each unchosen neighboring number. Asking about increments lets me calculate and is clearer than asking only about positions. These n numbers are distinct, so I can infer the endpoint is at least 1+2+…+n=N, and cannot exceed N, hence equals N! Does this also show these n summands are exactly 1 to n? I want to confirm I have not mixed path numbers with unchosen neighboring numbers.

### Teacher

Yes, your derivation holds: **these \(n\) summands are exactly \(1,2,\ldots,n\)**.

Distinguish two sets: numbers visited successively on the path, and the numbers you add, namely **the top cell** and the unchosen neighbor at each step. The top belongs to the path, while subsequent summands are sibling cells; they lie in different rows, so do not repeat.

You have proved that these \(n\) distinct positive integers sum to \(1+\cdots+n\). If one were outside \(1\) to \(n\), could their sum still attain this minimum?

Now this set of small numbers occupies certain positions. How could “they are all already occupied” yield constraints on other positions?

## Round 8

### Student

If one summand exceeds n, even the smallest other distinct positive integers cannot compensate, and the total exceeds the sum from 1 to n. Now each row has one occupied small number, and all other cells must exceed n. I thought two adjacent small numbers in one row would have a difference less than n above them, perhaps repeating a number. But with only one such number per row, that situation does not arise directly. In my three-row example, neighboring small numbers are 2 in row two and 1 at the bottom, while remaining 4, 5, 6 all exceed 3. Could you point to a specific position in this diagram for me to derive a constraint using “other cells exceed n”? I still cannot turn that statement directly into a 2018-row contradiction.

### Teacher

Yes, you have explained why equality forces summands exactly \(1\) to \(n\). Thus all cells outside this set of one small number per row exceed \(n\).

In your three-row example, the final comparison is between bottom numbers **6 and 1**, leaving bottom cell **4** beside them. Regard 4 as a one-row small triangle: it contains none of those small numbers and \(4>3\).

Can you try finding analogous regions on either side of the final bottom pair in a larger triangle? Draw five rows and any top-to-bottom path through adjacent cells, then observe the shapes remaining on both sides. No numbers need be filled yet.

## Round 9

### Student

I first drew a path always going left, marking path cells P and unchosen small numbers s: row one P; row two P s; row three P s x; row four P s x x; row five P s x x x. The x cells on the right do form a three-row small triangle, all greater than 5. But if the path turns right midway, s positions change, and I am unsure whether complete triangles remain on both sides. Should we outline triangles upward from the final adjacent bottom pair? Could you demonstrate an outline with turns, or tell me how to count the small triangle’s rows? I could then try using the small-number condition.

### Teacher

Yes, use a five-row position diagram with turns to count. No numbers are filled; `P` is the path and `s` the unchosen neighbor at each step:

```text
        P
       s P
      x P s
     x s P x
    x x s P x
```

The final adjacent bottom comparison is cells **3, 4**, leaving two cells on the left and one on the right. The two left cells support a **2-row** small triangle; the single right cell is a **1-row** small triangle. The `x` cells lie on neither the path nor sibling cells.

Outline both triangles and check whether every cell avoids `s`. Then generalize: if \(L\) bottom cells remain left of the final pair and \(R\) right, what is \(L+R\)? How many rows must the larger side triangle have at least?

## Round 10

### Student

The left two-row triangle has the leftmost x in the penultimate row and the two leftmost bottom x cells; the right is one cell, and all avoid s. L+R=n−2, so the larger side has at least (n−2)/2 rows; for 2018 rows that is at least 1008. Outlining it lets me count clearly. But I can only see from the diagram why arbitrary turning paths avoid these triangles; could you add a general reason? All numbers in the 1008-row small triangle exceed 2018, but are not consecutive integers starting from 1. Can the earlier “summand sum at least 1 to n” method still apply? If we take a path inside it with every summand at least 2019, is the endpoint at least 1008×2019?

### Teacher

Your lower bound \(1008\times2019\) holds: following larger adjacent cells inside this small triangle still makes the endpoint the sum of the top and each sibling cell. Taking 1008 rows gives 1008 summands all at least 2019; they need not be consecutive starting from 1.

To explain why turns still avoid the side triangles, consider **bottom-row descendant ranges**: the final compared cells are two bottom descendants of a cell. Each earlier path cell has a downward route to that pair, whereas every bottom descendant of a side-triangle cell lies left or right of the pair. Thus the path and each sibling avoid both side triangles.

Now calculate \(1008\times2019\) and compare with the largest allowed number \(2037171\). Is this bound sufficient for a contradiction? If not, you already know the summands are **distinct**. Can that strengthen the bound?

## Round 11

### Student

1008×2019=2035152, 2019 less than 2037171, so insufficient. With distinctness, the minimum values must be 2019, 2020 through 3026. These 1008 terms have sum (2019+3026)×1008÷2=2542680, already greater than 2037171. The small triangle’s path endpoint exceeds the allowed maximum, so the original 2018-row triangle does not exist. I can connect it now: first find the positions of 1 to 2018, then sum again in a side triangle avoiding them. One detail: if the side triangle has more than 1008 rows, can we directly take its bottom 1008 rows? That would be a trapezoid, so should we instead take a complete 1008-row triangle within it? I can roughly understand sibling avoidance from the diagram, but still cannot write a rigorous position proof independently.

### Teacher

Your calculation and conclusion are correct: the second sum gives lower bound \(2542680\), exceeding the allowed maximum \(2037171\), so the hypothesized 2018-row triangle does not exist.

Your comment about extraction is also right: if the side triangle exceeds 1008 rows, taking all its bottom 1008 rows gives a trapezoid. We should select a **complete 1008-row subtriangle** and follow a path inside it. My earlier wording “take 1008 rows” was imprecise.

You clearly recognize your current limit concerning the general position proof: understanding with a diagram does not yet mean writing it rigorously alone. Looking back from a successful three-row example to an impossibility proof using two path sums, what was the most important turning point? Why is it more powerful than continued trial filling?

### Student

The key was recognizing each path increment as a sibling number and writing “endpoint = top + sum of sibling cells.” Only then can distinctness give a minimum sum; trial filling proves a particular small triangle can be constructed but cannot exclude all 2018-row triangles. The first sum constrains the positions of 1 to 2018, and only the second sum within a side triangle yields a contradiction. Calculating 3→5→6 and the five-row diagram helped me connect it. Earlier repeated requests to guess positions left me unsure where to think. I want to stop here today. I can recount and explain the calculations and both sums, but still cannot independently write the general proof that sibling cells avoid the side triangles for arbitrary turns. I will leave that part as not yet mastered.

### Teacher

This teaching session has been confirmed as ended.
