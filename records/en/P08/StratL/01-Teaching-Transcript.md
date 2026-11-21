# P08 · StratL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used exactly once, be arranged in an anti-Pascal number triangle with 2018 rows? |
| Method | StratL |
| Participant ID | P08 |

## Round 1

### Student

Let me check the rules first: for two rows, 1, 3 at the bottom gives 2 above, using exactly 1 to 3, so two rows are possible. Generally, the maximum cannot be the difference of two positive numbers and should lie at the bottom. But I have not worked out how to turn this local restriction into an existence judgment for 2018 rows. Could you give a small question or direction suitable for independent attempts, without the complete proof?

### Teacher

Your two-row example follows the rules, and the observation about the maximum being at the bottom is valuable.

First try a small question: **For three rows, can you arrange 1 to 6, each once, in a number triangle following the rules?** Try arranging them and see whether the maximum's position narrows your choices. Whether you find an arrangement or encounter difficulties, tell me your process.

## Round 2

### Student

I found one: bottom 6, 1, 4, middle 5, 3, top 2, using all six exactly once. Placing 6 at the edge and then trying 1 in the middle makes the differences relatively large and did narrow the search. But one feasible small example does not reveal a pattern for 2018 rows. The maximum is at the bottom because a difference is strictly smaller than the larger child; can this ordering give a stronger restriction? Please give one local hint; I want to continue myself.

### Teacher

Your three-row construction is correct: adjacent bottom pairs differ by 5 and 3, whose difference is 2.

You have noticed the ordering between an upper cell and its larger child. Could you apply this observation across **more than one row** to find a restriction on the whole triangle? Start with your three-row example, then consider the general case.

## Round 3

### Student

Choosing the larger child downward from each upper cell gives a strictly increasing path; in my three-row example it is 2→5→6. Reversing it, each upward step decreases by at least 1, so values in row r are at most N−(2018−r), where N=2037171. But this seems to restrict only a few of the largest numbers and is far from a contradiction. My difficulty is turning one path's restriction into a quantitative restriction using non-repetition across the whole triangle. Your instruction to extend across rows got me this far, but I need more specific guidance, such as which numbers to track or which quantities to compare.

### Teacher

Your derivation is valid: following larger children downward makes path values strictly increasing, giving a necessary row-by-row upper bound. You also correctly noticed that **this upper bound alone does not fully use distinctness throughout the triangle**.

You have a concrete path \(2\to5\to6\). Could you examine each change along it more closely and describe those changes using values in other cells? Then consider whether the resulting numbers share any restrictions.

## Round 4

### Student

This hint is more concrete: 5−2=3 and 6−5=1, exactly the unchosen child at each step. Generally, if the path is x1<…<xn, each increment di is the smaller sibling cell, so xn=x1+Σdi. These n summands come from different cells: sibling cells are in different rows and outside the path, so all are distinct. The sum is at least 1+…+n=N, forcing xn=N and summands exactly 1 to n. For 2018 rows, the penultimate path value is at least N−2018. But I still have no contradiction: how does such a large number conflict with sibling values 1 to 2018? First check my equality reasoning for omissions, then give the next local hint.

### Teacher

Your equality reasoning is correct and uses all key conditions: the \(n\) summands are distinct positive integers, so their sum is at least \(1+\cdots+n=N\); the endpoint itself is a triangle value, at most \(N\). Equality must hold on both sides, and the summands are exactly \(1,\ldots,n\). The penultimate path value being at least \(N-2018\) is also correct.

Next consider: with these small numbers fixed in specific cells, **what restriction applies to every other cell's value**? Can you combine this with the path method already used to obtain further constraints?

## Round 5

### Student

All remaining cells exceed 2018; that is clear. I want to start at one and follow larger children again, summing the starting value and siblings. But the second path might approach the first, and new siblings might meet already occupied small numbers, so I cannot simply say every summand exceeds 2018. I lack control of geometric positions, rather than summation itself. Could you explicitly suggest where the second path should start and give a small schematic without the complete conclusion? Earlier broad hints cost me effort guessing the goal; I hope this step can be more specific.

### Teacher

Your concern is correct: choosing a starting value above 2018 alone does not guarantee subsequent siblings also exceed 2018. The earlier hints did leave too much guessing to you.

First draw the initial path and every sibling on a smaller triangle diagram. Can you find a **complete subtriangle** all of whose cells avoid these marked cells? If so, try starting the second path at that subtriangle's top.

## Round 6

### Student

In the three-row example, I marked path 2, 5, 6 and siblings 3, 1, leaving bottom value 4, which is indeed a one-row subtriangle. But that does not establish how tall an unoccupied subtriangle a large triangle must contain. If it has h rows, all values exceed n, and another path has h distinct summands totaling at least hn+h(h+1)/2; I can derive that. The key now is guaranteeing h, but your new hint still leaves me guessing the geometry. Please directly state the guaranteed height and selection method, especially why turns in the first path do not enter the subtriangle. I need a local explanation here; I can continue the summation myself.

### Teacher

You have derived the summation part; next we only need a sufficiently tall subtriangle containing none of the marked small numbers. You identified the difficulty accurately: when the path turns, visual intuition alone cannot establish it stays outside a region.

Use **the two bottom-row cells involved in the first path's last step** as reference points. All other bottom-row cells lie to their left or right: looking for complete subtriangles upward from each side, can their bottom-row cell counts estimate the larger one's number of rows?

As for turns meeting it, first consider: what positional condition must a first-path cell satisfy to ultimately reach this final pair of children?

## Round 7

### Student

If the final bottom pair is j, j+1, the sides have lengths j−1 and 2018−j−1, totaling 2016, so the larger has at least 1008 rows. Positionally, cell c in row r can reach bottom columns [c,c+2018−r]. A path cell's interval contains the final path endpoint; a sibling is adjacent in the same row, and its interval should meet at least one of the final pair, so subtriangles lying wholly to the left or right avoid all the small numbers. I think this interval argument handles turns; please especially check the sibling claim. Taking a 1008-row subtriangle, path summation is at least 2018×1008+1008×1009/2=2542680, greater than 2037171, a contradiction, so it does not exist. This bottom-pair reference finally connected the reasoning, making it easier to act than repeated requests to find restrictions. If the sibling argument holds, I also want to check whether this works only for sufficiently large row counts and does not conflict with the three-row example.

### Teacher

Your sibling argument holds and the calculation is correct; you have completed the proof by contradiction for 2018 rows.

For the sibling check, the key is that it and the same-row path cell are **children of the same upper cell**. Suppose their upper cell is in row \(r-1\), column \(q\). Since the first path eventually passes through column \(j\) of the penultimate row,

\[
q\le j\le q+2018-r.
\]

Thus each child's bottom-row descendant interval meets at least one of the final pair \(j,j+1\). Bottom-row descendants of side subtriangles lie wholly outside this pair, so both avoid path and sibling cells, including when the path turns.

You also understand correctly: **this numerical contradiction depends on the row count and does not conflict with the feasible three-row example.** For three rows, the guaranteed side triangle has only one row, and your lower bound \(3+1=4\) does not exceed the maximum \(6\). In your example it corresponds exactly to bottom value 4.

Looking back, why did changing from “path values increase” to “record each increment” allow distinctness throughout the triangle to play a role?

### Student

Increasing alone only gives at least 1 per step, reusing the same lower bound. Recording increments makes each correspond to an actual sibling cell; with the top, they are n distinct positive integers, allowing 1+…+n rather than just n. Equality then fixes all small-number positions, enabling the second path's larger lower bound. Your common-upper-cell coordinates removed the ambiguity in my sibling argument based merely on adjacency. Checking applicability: allowing repeats invalidates the first lower bound on n summands; retaining distinctness without requiring exactly 1 to N could remove the endpoint upper bound N, so the proof cannot be used unchanged. I can now connect both sums and the geometric separation between them, and have checked the three-row example. I will stop here for this session, thank you.

### Teacher

This teaching session has been confirmed as ended.
