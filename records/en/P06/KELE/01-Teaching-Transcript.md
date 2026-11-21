# P06 · KELE: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | KELE |
| Participant ID | P06 |

## Round 1

### Student

Teacher, I want to confirm the rules: with two rows, putting 1, 3 below gives 2 above, using exactly 1 to 3, so that is valid, right? But constructing a small triangle does not seem to show 2018 rows work too. I do not know whether to try constructing first or seek a necessary constraint. Could this small example lead us to a direction I can check? Please do not give the complete proof yet; I want to try one step myself.

### Teacher

Yes, this two-row triangle is valid: the upper 2 equals |3−1|, and all three numbers are used once each. You are right that a feasible small triangle does not show feasibility for 2018 rows.

First find a relationship every valid triangle must obey. In your example, consider upper 2 and lower 1, 3: **if the larger lower number stands alone on the left of an equation, how does it relate to the other two numbers?**

## Round 2

### Student

3=2+1. Generally, the larger lower number equals the smaller lower number plus the upper cell, so also exceeds the upper cell. I can see this from the difference definition. But it is only a relationship in each small triangle. How does it constrain the whole triangle? I conjecture the largest number can only be at the bottom, since above it would require an even larger lower cell. Does that hold?

### Teacher

It holds. Your reasoning identifies the key: every non-bottom cell has two children, and the larger equals the upper cell plus another positive integer, so strictly exceeds it. The largest number therefore cannot be above the bottom row.

Check the condition on which this depends: **if 0 were allowed, could you still guarantee the larger child strictly exceeds the upper cell?**

## Round 3

### Student

No. For example, lower 0 and 3 give upper 3, so the larger lower cell only equals the upper. Strict increase therefore depends on the other lower cell being positive. The problem also prohibits repetition, so this example is invalid, but shows the difference rule alone is insufficient. I now understand why the maximum is at the bottom, but locating one number still seems far from excluding or constructing 2018 rows. Could you give a specific small task using this relationship several times?

### Teacher

Your judgment is correct: allowing 0 can invalidate strict increase; the original positivity condition guarantees it.

Try this four-row triangle, listed from top to bottom:

```text
       4
     2   6
   5   7   1
 8   3  10   9
```

Start at top 4 and always follow the larger of the two cells immediately below, down to the bottom. **Can you express the bottom number reached as the top plus the number not chosen at each step?**

## Round 4

### Student

The path is 4→6→7→10, leaving 2, 1, 3 unchosen. Since 6=4+2, 7=6+1, 10=7+3, we get 10=4+2+1+3. This example shows how local relationships connect, and calculating one step at a time is easier to follow. With 2018 rows, the bottom endpoint equals the top plus 2017 unchosen numbers, whose cells belong to different rows and cannot coincide. They are also distinct, so can we use the sum from 1 to 2018 as a lower bound? But that sum is exactly 2037171, the allowed maximum. Does this only force equality, without establishing nonexistence yet?

### Teacher

Yes, your reasoning holds: if such a 2018-row triangle exists, the endpoint is at least 2037171 and at most 2037171, so must equal it. **Equality itself has not produced a contradiction**, so cannot yet establish nonexistence.

Consider one further step: why does a sum of 2018 distinct positive integers equal to \(1+2+\cdots+2018\) force them to be exactly \(1,2,\ldots,2018\)?

## Round 5

### Student

Sort them ascending: the first is at least 1, the second at least 2, and so on, with the 2018th at least 2018. If any exceeds its corresponding position, others cannot be smaller to compensate, so the total exceeds it. They must therefore be exactly 1 to 2018. I can explain that now. But their order in the triangle is not ascending, and selected intermediate values might already be large. I am seeking a repetition contradiction: could the sums in the first few path steps encounter one of 1 to 2018? How can we guarantee they encounter one rather than jump above 2018 immediately?

### Teacher

Your sorting argument is correct, and your concern about “skipping small numbers” is justified: **increasing partial sums alone do not ensure encountering another collected small number**. For example, the four-row path \(4\to6\to7\to10\) jumps from 4 to a number above 4 at its first step.

Change direction and examine positions not occupied by collected small numbers. Again consider this four-row triangle:

```text
       4
     2   6
   5   7   1
 8   3  10   9
```

The final lower pair is 3 and 10, and collected small numbers are 4, 2, 1, 3. **Can you find a small triangle of uncollected cells to the left or right of that pair?**

## Round 6

### Student

I examined the three small triangles between row three and the bottom: 5 has 8, 3 below, including collected 3; 7 has 3, 10, also including 3; 1 has 10, 9, including collected 1. None seems suitable. In row two, 2 has 5, 7 below, but 2 is collected; 6 has 7, 1, including collected 1. Did I misunderstand “small triangle”? If it means three adjacent cells, I cannot find one made entirely of uncollected cells here. Could you identify the three positions you want me to examine?

### Teacher

Your check is correct, and my question was imprecise: this four-row triangle **has no suitable three-cell small triangle**. I meant the single cells 8 and 9 on either side of bottom pair 3, 10; a single cell also counts as a “one-row triangle.” Sorry for making you search for three cells unnecessarily.

Check side regions this way: first mark the final lower pair at the bottom, then examine the remaining consecutive cells to its left and right. The cells supported above each side form a side triangle. In the four-row example each side leaves only one cell, so each side triangle has just one row.

Do not generalize to 2018 rows yet: **if 3 consecutive bottom cells remain left of the final pair, how many rows does the triangle supported by these 3 cells have?**

## Round 7

### Student

Three rows: 3 below give 2 adjacent differences above, then 1 farther up. Now I understand you mean the whole side region, not necessarily a three-cell small triangle. With 2018 bottom cells, excluding the final pair leaves 2016 on the sides, so at least one side has 1008 cells supporting 1008 rows. But I cannot directly assume that entire region is uncollected, since the path may previously have moved that way. Could you explain through positions why collected cells cannot lie inside this side triangle? Please do not omit that part.

### Teacher

Your concern is entirely correct: the path may have moved sideways above, so we need a proof rather than looking only at the bottom. Use column indices to make positions explicit.

Suppose there are \(n\) rows, numbered left to right within each. The path finally passes through cell \(p\) of row \(n-1\), whose final child pair is bottom cells \(p\), \(p+1\).

Consider any path cell in row \(r-1\), column \(q\). Reaching row \(n-1\) takes \(n-r\) further steps. Each step leaves the column index unchanged or increases it by 1. To reach column \(p\), necessarily

\[
q\le p\le q+n-r.
\]

Its children occupy columns \(q\), \(q+1\) in row \(r\), one being the cell collected at this step. Its column \(j\) therefore satisfies

\[
p-(n-r)\le j\le p+1. \tag{1}
\]

Meanwhile, expanding cell \(j\) in row \(r\) down to the original bottom covers descendant columns \(j\) through \(j+n-r\). Thus:

- Left-triangle cells have all bottom descendants left of column \(p\), so \(j+n-r\le p-1\), or \(j\le p-(n-r)-1\).
- Right-triangle cells have all bottom descendants right of column \(p+1\), so \(j\ge p+2\).

Both ranges are disjoint from (1). The top also belongs to neither side triangle, so **all collected cells lie outside both side triangles**.

Since collected cells already occupy \(1\) to \(2018\) and all numbers are distinct, every number in the larger side triangle exceeds \(2018\). You already know it has at least 1008 rows: **if we follow larger children downward there again, can the earlier accumulation method give a lower bound for its bottom endpoint?**

## Round 8

### Student

I read the column section slowly but can match it: a collected cell’s bottom expansion cannot lie wholly left or right of the final pair, so it is outside the side triangles. This is no longer guessing from a diagram. If the side triangle has m rows, m≥1008, another path collects m distinct numbers, each at least 2019. Calculating only 1008×2019=2035152 leaves a gap of 2019 to the maximum, so gives no direct contradiction. But distinctness strengthens it to at least 2019+2020+…+3026. Adding 0+1+…+1007 to the first bound certainly adds more than 2019, exceeding 2037171. Is that the contradiction? Can this rough comparison replace calculating the whole large sum?

### Teacher

Yes, the contradiction holds, and your rough comparison can replace the full sum if “more than 2019” is justified. For example, take only three increments:

\[
0+1+\cdots+1007\ge 1005+1006+1007>2019.
\]

The side-triangle path endpoint is therefore at least

\[
1008\times2019+(0+1+\cdots+1007)
>2035152+2019=2037171,
\]

but every number in the whole triangle is at most 2037171, a contradiction.

The general rule is that following larger children makes the endpoint the top plus unchosen children at each step. With distinctness, the smallest available numbers give a lower bound.

Now connect the steps: **how does assuming a 2018-row triangle exists lead to a complete contradiction?** You may cite our proven separation of the side-triangle positions.

### Student

Assume existence. Starting at the top, always follow the larger lower cell. Since larger lower = upper + smaller lower, the endpoint is the top plus unchosen numbers at each step. These are 2018 distinct positive integers, summing to at least 1+…+2018=2037171 while not exceeding that maximum. Equality forces the collected numbers to be exactly 1 to 2018. Outside the final bottom pair, 2016 cells remain, so one side has at least 1008 cells. By the column proof, the triangle supported on that side contains no collected cells, so every number exceeds 2018. Following the same route again gives endpoint at least 2019+…+3026, equal to 1008×2019 plus 0+…+1007. Even increments 1005+1006+1007 exceed 2019, so the endpoint exceeds 2037171, contradicting the problem. Thus the triangle does not exist. I can now connect the reasoning, especially why the first equality cannot directly settle it. I can follow and check the column separation, but cannot yet discover it independently; the small example and stepwise accumulation helped most. I want to stop here today.

### Teacher

This teaching session has been confirmed as ended.
