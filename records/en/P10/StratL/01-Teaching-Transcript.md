# P10 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the integers from 1 to 2037171 each be used once to form an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P10 |

## Round 1

### Student

I want to check the rules first. With two rows, 1, 3 at the bottom gives 2 at the top, using exactly 1 to 3, so at least two rows are possible. I know a small example cannot prove that 2018 rows are possible too, but currently I do not know whether to seek a construction or a contradiction. Could you first give me a starting point I can try myself, without giving the complete proof directly yet?

### Teacher

Your two-row example satisfies the rules, and you have also noticed its limitations.

There is no need to decide immediately between a construction and a contradiction. Intuitively, do you think satisfying the rules gets easier or harder as the number of rows increases? You can refer to the two-row example and explain what gives you that feeling; your conjecture need not be proved yet.

## Round 2

### Student

Intuitively I suspect it gets harder: once the bottom row is chosen, all the differences above are determined. With more rows, avoiding repetition and covering every number exactly seem more restrictive. The two-row 1, 3 easily produces 2, but further differences might produce 1 or 2 again. However, there are also more choices for the bottom row, so this is only a conjecture. I want to turn this intuition into something checkable: could we first investigate which row the largest number can occupy? Because the difference of two positive numbers is less than the larger, I think the whole triangle's maximum can only lie in the bottom row. Is this observation useful?

### Teacher

It is useful, and your observation is correct: **the largest number in the whole triangle can only lie in the bottom row**. You have also distinguished the intuition that “the restrictions seem stronger” from a proved positional conclusion.

Can you try writing an argument for this positional conclusion that applies to any number of rows? Then consider: is knowing only that the maximum is in the bottom row enough to determine whether the whole triangle can be arranged? What would you like to investigate next from this observation?

## Round 3

### Student

Let the maximum in the whole triangle be M. If M is not in the bottom row, it equals the absolute difference of two positive numbers a, b below it. But |a-b|<max(a,b)≤M, a contradiction, so M is in the bottom row. This argument does not depend on the number of rows. That alone is certainly insufficient, since the bottom row still has many positions. I want to look at the second-largest number next, but it could apparently be M minus a very small number, so we cannot directly say it is also at the bottom. For example, the second-largest number 2 in the two-row case is at the top. So locating numbers one at a time by size seems blocked. Should we instead consider a whole class of large numbers, such as those greater than M/2? The difference of two such numbers is always less than M/2, but I do not yet know how to turn this local restriction into a counting restriction for the whole triangle. Could you give an intermediate question for me to try?

### Teacher

Your proof holds, and the two-row example also shows why it cannot directly be extended to “the second-largest number is also in the bottom row.”

You have proposed investigating numbers greater than \(M/2\). Could you first write your local restriction as a precise statement, then consider what information is still missing to obtain a counting restriction for the whole triangle? Even if you can only list conjectures or difficulties for now, you can write those down.

## Round 4

### Student

Precisely: if M/2<a,b≤M, then |a-b|<M/2. Thus an upper number greater than M/2 cannot have two large numbers below it; nor can it have two numbers at most M/2, so it must have one large and one small number. But adjacent upper cells share lower cells, and one large number may support more than one upper large number, so I cannot directly match them one to one. What is missing is a counting bound that still holds with this sharing. Asking me to organize the statement helped clarify the local relation, but repeatedly asking me to identify what is missing has not resolved this specific difficulty. Could you explicitly give me a counting conjecture to test, or demonstrate how to handle sharing in a simplified three- or four-row diagram? You need not present the complete 2018-row solution all at once.

### Teacher

You are right: I did not adequately address your difficulty with counting shared cells. We can first test this **conjecture**:

> For two adjacent rows, the number of cells greater than \(M/2\) in the upper row is at most twice the number greater than \(M/2\) in the lower row.

For now, call cells “large” if their numbers exceed \(M/2\). Why conjecture a factor of two? Every large upper cell requires at least one large cell below, and one lower cell can be shared by at most two upper cells, one on each side.

For example, suppose the lower row has size labels

```text
small   large   small
  large   large
```

The middle large cell can support both large cells above, so a one-to-one correspondence is impossible, but it supports at most two. This concerns size labels only; the diagram does not yet guarantee actual numbers satisfying the difference rule.

Try proving this “factor-of-two” counting bound, then consider: **Can it further constrain the total number of large cells in the whole triangle?** There is no need to rush to decide whether it suffices for 2018 rows.

## Round 5

### Student

This diagram makes the counting of shared cells clear. Let row r have B_r large cells. Each upper large cell has exactly one large cell below it; assign it to that cell. Each lower large cell receives at most two assignments, so B_r≤2B_(r+1). But repeating upward gives factors of 2, 4, 8, quickly exceeding the number of cells in that row. I do not see how this could restrict large cells to less than half the whole triangle. The problem requires 1018586 large cells, so we need a stronger global bound or a different property. This help resolved the local counting, but not the direction of progress. Could you give a key relation that really leads onward to a global constraint, and explain why we should change direction this way? I am willing to supply the subsequent calculations myself.

### Teacher

Your judgment has a basis: repeated application of the factor-of-two bound quickly becomes loose, so it is worth switching to a relation spanning multiple rows.

The key approach is: **start at the top cell and always move down to the larger of the two adjacent child cells.** If the current cell is \(x\), with larger child \(y\) and smaller child \(z\), the difference rule gives

\[
y=x+z.
\]

On reaching the bottom row, we can combine these relations into an equation relating one bottom number to the sum of several cell values. The reason for changing direction is that this connects local differences in every row into one equation spanning the whole triangle, which we can compare with the maximum, without handling shared-large-cell counting.

First try writing which numbers sum to this bottom number, then check whether those numbers are distinct and what minimum sum they have.

Also, one small counting point deserves checking: \(M=2037171\) is odd. What are the first and last integers **strictly greater than** \(M/2\)? Count again using the endpoints and see whether you still get the same number.

## Round 6

### Student

The large numbers run from 1018586 to 2037171, totaling 2037171−1018586+1=1018586. Rechecking gives my original count; was there actually no mistake here? The path method is indeed more direct than the earlier counting. Let the path be x_1 through x_2018, with z_r the smaller child unselected at step r. Then x_(r+1)=x_r+z_r, so x_2018=x_1+z_1+…+z_2017. These 2018 summand cells lie in different rows (the top cell plus one unselected cell per row), are distinct, and have minimum sum 1+…+2018=2037171. The bottom number also cannot exceed that value. Thus equality must hold, and the summand cells use exactly 1 to 2018. So far I have only this strong necessary condition, without a contradiction. Should we next examine the intermediate path cells, which cannot use 1 to 2018 again?

### Teacher

Yes, your count was correct. The integers strictly greater than \(M/2\) do run from 1018586 to 2037171, totaling **1018586**. I asked you to recheck because my judgment was mistaken; I am sorry.

Your path reasoning also holds: the sum of these 2018 distinct positive integers is at least \(2037171\) and cannot exceed it, so equality must hold. The summand cells occupy exactly \(1\) to \(2018\), and the bottom endpoint of the path is \(2037171\).

Examining intermediate path cells is a reasonable next step. Note that the top cell \(x_1\) itself belongs to the summand cells; the path cells from \(x_2\) onward are different from these summand cells, so none can use \(1\) to \(2018\) again.

Try continuing in this direction: these intermediate cells must satisfy the recurrence and all exceed 2018. Can this give a new restriction? If there is no contradiction yet, you can explain what you can derive and what is still missing.

## Round 7

### Student

I can derive x_2=x_1+z_1>2018; subsequent steps add positive numbers, so the path strictly increases. But this condition alone does not seem contradictory: considering just this recurrence, we could add 2018 and 2017 as the first two terms, then add the remaining 1 to 2016 in order. All intermediate sums exceed 2018, and the final sum is exactly M. Of course, that is not a valid whole triangle; it only shows these path conditions alone do not directly rule one out. My difficulty now is that we have not used the difference constraints between cells outside the path. Could you specify which adjacent cells to examine and demonstrate that relation? I already follow the path sum; repeating “keep looking for restrictions” does not help me much.

### Teacher

You are right: the path recurrence alone does not suffice for a contradiction. We can examine **the regions beside the path's final pair of child cells** to use the difference relations outside the path.

Let the path cell in the penultimate row be \(x_{2017}\), with its two children the bottom endpoint \(x_{2018}=M\) and the unselected cell \(z_{2017}\). Now look at the bottom cells **to the left** of these two adjacent cells: they form the base of a complete smaller triangle above them; the cells on the right do likewise.

Within either side triangle, any upper cell \(u\) and its adjacent children \(v,w\) still satisfy

\[
u=|v-w|,\qquad \max(v,w)=u+\min(v,w).
\]

Thus, the summation relation you just used also holds inside a side triangle.

First test a spatial question: **Could the 2018 summand cells collected by the original path fall inside either side triangle?** If they all lie outside, what restriction does your established fact that “all the small numbers have been used” impose on the side-triangle numbers?

## Round 8

### Student

If the side triangle really avoids all summand cells, every number in it exceeds 2018. Along a larger-child path in a side triangle with h rows, the bottom number sums h such numbers, so it is at least 2019h. This seems capable of yielding a global restriction. But I do not understand the spatial premise: the original path can turn left and right, and unselected cells lie on both sides. Why can they not fall inside the side triangles you defined? Also, if the final pair is near an edge, one side may have no cells. Could you clearly label a turning path, the unselected cells, and both side triangles in a 5-row diagram, or give row and column coordinate definitions? I want to test the non-intersection claim first; I cannot accept it just because it leads to a contradiction.

### Teacher

Your challenge is necessary: because the path turns, we need to prove that **regardless of its turns**, the summand cells avoid the side triangles. Coordinates make this clear.

Suppose the triangle has \(n\) rows, each numbered from left to right. The path cell in row \(n-1\) occupies column \(p\), so the final pair of child cells occupies bottom-row columns \(p\), \(p+1\).

There are \(p-1\) bottom cells to the pair's left, forming the left side triangle's base, and \(n-p-1\) to its right, forming the right side triangle's base. If \(p=1\), the left is empty; if \(p=n-1\), the right is empty. The two sides have \(n-2\) cells altogether, so at least one has \(\lceil(n-2)/2\rceil\) rows.

Now consider the unselected cell in row \(r\), where \(2\le r\le n\). Suppose its parent path cell in the preceding row occupies column \(q\). Since the path must subsequently reach row \(n-1\), column \(p\), and each downward step leaves the column unchanged or increases it by 1,

\[
q\le p\le q+n-r.
\]

The unselected cell occupies only column \(q\) or \(q+1\), so it lies within

\[
p-(n-r)\ \le\ \text{column number}\ \le\ p+1.
\]

In row \(r\), left-side-triangle columns are at most \(p-(n-r)-1\), and right-side-triangle columns are at least \(p+2\). Thus **every unselected cell lies outside both side triangles**, as does the top cell. This proves the required non-intersection without assuming the path does not turn.

Your lower bound \(2019h\) holds. Now substitute the lower bound just obtained for the larger side triangle's row count: does this already exceed the whole triangle's maximum? If not, consider what other known condition these summands satisfy besides all exceeding 2018.

## Round 9

### Student

At least one side has 1008 rows. Using only 2019×1008=2035152 gives 2019 less than M, so it is indeed insufficient. But these summands are also distinct, so their sum is at least 2019+2020+…+3026=(2019+3026)×1008/2=2542680, exceeding 2037171, a contradiction. Thus such a 2018-row triangle does not exist. The coordinate explanation lets me check turning paths: unselected-cell columns lie in the middle interval, side triangles outside it, and if the path is near an edge we use the other side. This step was previously only conditional, and now has a basis. I also tried checking applicability: for 5 rows, the same method guarantees only a 2-row side triangle, with sum at least 6+7=13, which does not exceed 15, so this argument cannot claim nonexistence for 5 rows. Is my understanding of the proof and its scope correct?

### Teacher

Yes, your understanding of both the proof and its scope is correct.

For 2018 rows, you used the crucial condition that the summands in the side triangle are **distinct**, obtaining a lower bound of 2542680, exceeding the permitted maximum 2037171 and producing a contradiction. The coordinate argument ensures this side triangle really avoids all the small numbers already used.

For 5 rows, the guaranteed lower bound \(6+7=13\) does not exceed the maximum 15, so this argument cannot rule out 5 rows; this step alone also does not prove that 5 rows must be possible.

Looking back, why do you think the move from “the path sum is at least the permitted maximum” to “all the small numbers are exactly used up” is the key connection between the local rule and the global contradiction?

### Student

The key is that equal bounds force equality, giving not merely a numerical lower bound but also the set of summands. If any of 2018 distinct positive integers falls outside 1 to 2018, at least one term in sorted order exceeds its minimum possible value, making the total exceed M. Thus all numbers 1 to 2018 occupy these specified cells. Distinctness throughout the triangle and non-intersection with the side triangles then push every side-triangle number above 2018, enabling the second path sum to exceed M. Without “using them all up,” the first summation inequality alone cannot impose this restriction on cells outside the path. I will stop here today. The concrete path equation and later coordinate explanation helped most; earlier, when repeatedly asked to find restrictions myself, I did not know how to proceed for a while, but later I could supply the calculations and check the scope. Thank you.

### Teacher

This teaching session has been confirmed as ended.
