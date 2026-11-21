# P06 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial constructions to an impossibility proof |
| Learning problem | Can the numbers from 1 to 2037171, each used once, be arranged into a 2018-row anti-Pascal number triangle? |
| Method | StratL |
| Participant ID | P06 |

## Round 1

### Student

Teacher, I want to confirm the rules. With two rows, putting 1 and 3 below gives 2 above, using exactly 1, 2, 3. That should work, right? But 2018 rows is so large that I do not know how to move from small examples to a justified existence or nonexistence judgment. Could you help me find a starting point I can try myself?

### Teacher

Yes, your two-row example works: bottom 1 and 3 gives top |3−1|=2, using 1, 2, 3 exactly once each.

Do not rush to prove anything. Based on this example, what is your intuition: **can a number triangle always be constructed as rows increase, or might construction fail at some row count?** Make a conjecture freely and explain what suggests it. Uncertainty is fine.

## Round 2

### Student

I lean toward failure with more rows, because each added number must satisfy adjacent differences without repeating upper numbers, so constraints seem to accumulate. But that is only a feeling: the range of available numbers also grows, so “many constraints” alone cannot settle it. I tried three-row bottom 1, 6, 2, giving 5, 4 above and 1 again at the top, a repetition. This failure excludes only that arrangement. How should I choose further attempts to discover something more useful than random filling?

### Teacher

Your three-row calculation and assessment of the failure’s scope are correct: this repetition only excludes bottom **1, 6, 2**.

You have noticed two constraints, “adjacent differences” and “no repetition.” Which seems more likely to yield a rule **every arrangement must satisfy**? Propose a specific conjecture to test; even one eventually refuted by an example has value.

## Round 3

### Student

I want to examine adjacent differences first because they directly connect rows. One rule I can identify is that the difference of two positive numbers is smaller than the larger one, so the maximum cannot be above the bottom, or it would need a larger number below. Thus 6 must be at the bottom with three rows, and 2037171 with 2018 rows. This should hold for all arrangements. But it only fixes a position and is far from nonexistence. Could you narrow the next step, perhaps with a small unanswered question that lets me continue this rule rather than guess again from scratch?

### Teacher

Your reasoning is correct: positivity makes every non-bottom cell smaller than its larger lower neighbor, so the global maximum must lie at the bottom.

Consider just one small question next: **can you apply this magnitude relationship across several consecutive rows? Starting from the top, what relationship can you obtain?** Try expressing it with three rows first, without rushing to 2018.

## Round 4

### Student

Narrowing it to three rows lets me act. Let the top be a and the larger second-row number b, so a<b. Choose larger c below b, giving a<b<c. Since these are integers, each step adds at least 1, so a three-row top is at most 4. Similarly, 2018 rows yield 2018 increasing numbers, but with 2037171 numbers altogether I see no contradiction. Also, we can only select one downward route, right? We cannot say every next-row number exceeds the top, because the difference is only guaranteed smaller than the larger lower number. Have I overextended the conditions? Should we next observe how much this path increases?

### Teacher

You have not overextended them: each step can select a larger adjacent lower cell, forming an increasing route, without guaranteeing every next-row number exceeds the top. Your inference that a three-row top is at most 4 also holds.

You propose observing **the increase at each step**, a direction we can explore. Using your three-row notation, express increments \(b-a\) and \(c-b\). What do you find?

## Round 5

### Student

Call the other second-row number d. Since b is larger, a=b-d, so b-a=d. Call the other number below b, besides c, e. Similarly b=c-e, so c-b=e. Thus c=a+d+e: the increments are themselves triangle numbers, and d, e are in different rows and cannot coincide. This is stronger than adding at least 1 per step: the two increments sum to at least 1+2. But with 2018 rows, the minimum sum of only 2017 distinct increments still seems below the total upper limit. I can follow this step but do not know how to make it strong enough. Could you give a specific hint rather than simply ask me to keep observing?

### Teacher

Your derivation is correct: \(c=a+d+e\), with increments \(d,e\) distinct positive integers.

You already considered the increments’ minimum sum. Return to **the whole equation**: besides the two increments, what other number appears? Use the problem’s conditions to judge its relationship to \(d,e\), then see how this affects the lower bound for \(c\).

## Round 6

### Student

There is also a, another cell distinct from d and e, so the three sum to at least 1+2+3=6. Thus three-row c is at least 6 and at most 6, forcing equality. I did overlook the top. But 2018 rows similarly yield 2018 distinct positive integers summing to at least 1+…+2018, exactly 2037171: still equality, not excess. Is the key that this forces the top and all increments to use exactly 1 to 2018, and the reached bottom cell to be the maximum? I hesitate to claim contradiction because two rows can satisfy equality. Could you use three rows to show what else equality forces?

### Teacher

Yes, your conclusion holds: if a 2018-row triangle exists, the top and increments collected along this route must be exactly \(1\) to \(2018\), and its bottom endpoint must be \(2037171\). You are also right that **equality itself is not a contradiction**.

Examine its consequences with three rows: since \(c=6\) and \(a,d,e\) are exactly \(1,2,3\), can you put them back into the triangle and see what constrains the remaining cells? No exhaustive search is needed; choose one arrangement first.

## Round 7

### Student

Choose a=1, d=3, e=2. Then b=a+d=4, c=6. Put 4, 3 in row two and start bottom 6, 2, x. The left difference is 4, and the right requires |2-x|=3, giving positive x=5. Thus top 1, second row 4, 3, bottom 6, 2, 5 uses exactly 1 to 6! Three rows really work, so cannot prove failure for large counts. This also shows equality does not automatically cause repetition. I am stuck on the bridge from small examples to 2018: could you explicitly identify which cells to compare or demonstrate a key relationship? Continuing with individual arrangements seems unable to exclude all large triangles.

### Teacher

Your construction fully works, and three rows really can be arranged. You are right that checking a particular arrangement cannot exclude every 2018-row arrangement.

We already have a conclusion for **any hypothetically existing arrangement**: the top and collected numbers along the route use all of \(1\) to \(2018\). We need not assign their exact order next.

Starting from this conclusion, **what can we establish about all other cells’ numbers?** Then consider whether their positions can help further reasoning.

## Round 8

### Student

Other cells must exceed 2018. Each collected number is the smaller lower cell along the route, so each row has exactly one number not exceeding 2018, including the top itself. In the three-row example, small-number positions are top 1, second-row 3, bottom 2, with other 4, 5, 6 all greater than 3, consistent with this. But two large numbers can differ very little, such as 2020 and 2021 differing by 1, so I still see no contradiction from “large numbers in other positions” alone. I have asked several times for a specific relationship, but your hints still ask me to find positions myself, which I truly cannot connect. Could you directly point out a local arrangement and explain one derivation, then let me apply it elsewhere?

### Teacher

Yes. Your point is crucial: two large numbers can indeed have a small difference, so “other cells are large” alone cannot establish contradiction.

Consider a local arrangement:

```text
      1
  2020  2021
```

It satisfies the difference rule, since \(|2021-2020|=1\). Conversely, the same relationship gives:

\[
2021=1+2020.
\]

Thus **the larger lower number equals the upper number plus the other lower number**—the relationship you already obtained along the path.

Now consider: if we find a region where every cell exceeds 2018 and repeatedly apply this relationship inside it, what can we say about a bottom cell? For this step we need not decide where the region lies.

## Round 9

### Student

If a complete three-row small triangle with all numbers greater than 2018 really exists, expansion along a path makes its bottom cell a sum of three distinct numbers at least 2019, hence at least 2019+2020+2021=6060. With h rows in such a complete region, at least h large numbers are added. This is a result I can apply. But your local equation is the relationship I already wrote earlier. What I really lack is why a sufficiently tall region must exist and how tall it needs to be to exceed 2037171. We cannot assume the desired region exists. I currently have only an increasing path and equality conditions, not an existence or nonexistence proof for 2018 rows. Finally, please explicitly explain how this region is guaranteed, rather than asking me to guess again. If it remains unsupported, I will leave it unresolved.

### Teacher

Yes. You are right: existence of the region must be proved first. Repeatedly asking you to find positions did not address your request for a specific explanation. Sorry.

Number the bottom from left to right, \(1\) to \(2018\). Let the final adjacent bottom pair encountered by the larger-child path occupy columns \(p\), \(p+1\).

There are \(p-1\) cells on the left and \(2017-p\) on the right, totaling \(2016\), so **one side has at least \(1008\) cells**. Taking that side’s consecutive bottom cells as the base gives a complete side triangle of at least \(1008\) rows.

We must also show it avoids all small numbers. Every original path cell can reach the final pair downward, so its reachable bottom range intersects the pair. The other child collected at each step also lies within this strip leading to the final pair. In contrast, every bottom descendant of a side-triangle cell lies completely left or right of that pair, so such cells cannot coincide with collected cells. The top also lies outside the side triangles.

The side triangle therefore avoids the cells already occupying all of \(1\) to \(2018\), and **every number within it exceeds \(2018\)**. This justifies your accumulation lower bound rather than assuming the desired region in advance.

You already know how to calculate the lower bound for an all-large-number region with \(h\) rows. Take \(h=1008\), calculate the minimum sum, and compare with \(2037171\).

## Round 10

### Student

The side lengths and regional positions finally show me where to use the bound. The smallest 1008 distinct large numbers are 2019 through 3026, summing to (2019+3026)×1008÷2=2542680, greater than 2037171. If the side triangle really contains only large numbers, that is a contradiction, so the original triangle does not exist. To check rather than merely repeat: if the final pair is far left, the right has 2016 cells, more than 1008, so edge cases do not undermine the length guarantee. One small point remains: the other collected child need not belong to the chosen path, so why must its bottom range intersect the final pair too? I understand path cells, but could you explain this with interval endpoints for adjacent children? This is the only step I have not securely connected.

### Teacher

Your calculation and edge-case check are correct. This question deserves verification: when I said “the other child’s bottom range intersects the final pair,” I did not explain why.

Let the total row count be \(n\), with final bottom pair in columns \(p,p+1\). For a downward choice, suppose the path parent lies in row \(r-1\), column \(q\). It can follow the path to column \(p\) in the penultimate row, so

\[
q\le p\le q+n-r.
\]

Its children occupy columns \(q\), \(q+1\) of row \(r\). Whichever is collected, calling its column \(j\) gives

\[
p-(n-r)\le j\le p+1.
\]

Cell \(j\) in row \(r\) has bottom-descendant range \([j,\;j+n-r]\). The preceding inequalities give \(j\le p+1\) and \(j+n-r\ge p\), so this range indeed intersects \([p,p+1]\).

By contrast, every bottom descendant of a left-triangle cell lies strictly left of \(p\), and those of a right-triangle cell strictly right of \(p+1\). Thus the other collected child belongs to neither side triangle. The top lies outside them too, completing the justification that “the side triangle contains only large numbers.”

Together with your \(2542680>2037171\), the hypothesized triangle would require a cell exceeding the allowed maximum, a contradiction. Therefore **the original 2018-row triangle does not exist**.

### Student

This interval explanation fills the gap. Checking simple numbers: if n=6, r=4, and the final pair is 3, 4, the collected column lies between 1 and 4 and its descendant interval is [j,j+2], always meeting 3 or 4. Intervals wholly on either side therefore cannot belong to collected cells. The side triangle avoids all small numbers, and the sum of distinct large numbers exceeding the upper limit completes the nonexistence proof. Earlier conjectures gave me room to try, but after repeated difficulty, the specific region and endpoint explanations finally connected it. Repeating the familiar local equation did not resolve that gap. I can now explain the conclusion by following the reasoning, but still hesitate to say I could independently discover such a region. I will stop here today.

### Teacher

This teaching session has been confirmed as ended.
