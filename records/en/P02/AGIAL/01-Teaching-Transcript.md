# P02 · AGIAL: Teaching transcript

| Item | Content |
| --- | --- |
| Learning topic | Anti-Pascal number triangle: from trial arrangements to an impossibility proof |
| Learning problem | Can the numbers 1 to 2037171, each used once, be arranged into an anti-Pascal number triangle with 2018 rows? |
| Method | AGIAL |
| Participant ID | P02 |

## Round 1

### Student

Teacher, I cannot take in 2018 rows at once. Could we first look at just two rows? Putting 1 and 3 below gives 2 above; we subtract the smaller number from the larger, right? These three numbers also do not repeat. Next let me try a small one, and give me one requirement at a time.

### Teacher

Yes, with 1 and 3 below, the upper number is \(|3-1|=2\). The three numbers are exactly 1, 2, 3, each used once.

Next: try arranging a three-row number triangle using each of 1 to 6 once.

## Round 2

### Student

I first put 1, 2, 3 on the bottom. The difference between 1 and 2 is 1, and between 2 and 3 is also 1, so the middle has two 1s. That does not work. I do not know how to choose the three bottom numbers. Could you choose one number first and leave the rest for me to try?

### Teacher

Your check is right: two 1s in the middle violate the requirement to use each number only once.

Let us fix the leftmost bottom number as **1**. Choose the other two bottom numbers yourself and see whether they make a valid three-row triangle.

## Round 3

### Student

I tried 1, 4, 6. The middle is 3 and 2, and the top is 1, repeating the bottom 1 again. I can calculate the differences, but changing numbers is still random trying. Could you tell me where to check first, without giving me the whole triangle at once?

### Teacher

Your calculation is correct this time: the middle 3, 2 do not repeat bottom numbers, but the top 1 repeats.

When changing bottom numbers, first check only **the two calculated middle numbers**: are they different from one another and from all bottom numbers? Once this check passes, calculate the top.

## Round 4

### Student

I checked the middle first as you said. Trying 1, 6, 4 gives 5 and 2 in the middle, with no bottom repetitions; then the top is 3. That uses all of 1 to 6! I can follow checking separately. But now that I arranged this small one, can 2018 rows also be arranged? I do not know how this tells us about the large one. Please explain just a little of the reason first.

### Teacher

Your arrangement is right: 1, 6, 4 at the bottom, 5, 2 in the middle, and 3 at the top use each of 1 to 6 exactly once.

But arranging three rows **does not directly show that 2018 rows can also be arranged**. As rows are added, every new cell must simultaneously satisfy the difference rule and non-repetition; an arrangement found in a small triangle may not keep extending.

In fact, 2018 rows cannot be arranged under the original conditions. To establish this, we need restrictions applying to the entire large triangle rather than just checking a few small ones.

## Round 5

### Student

I somewhat understand that a small one working does not mean the large one works, because adding rows might create repetitions. But you say 2018 rows cannot be arranged, and I still do not know why. What is the restriction on the whole triangle? Could you use a few small numbers to show me how it constrains things?

### Teacher

We can use the three-row triangle you just arranged to see a key restriction:

```text
      3
    5   2
  1   6   4
```

Starting at the top **3**, always move down to the larger of the adjacent numbers, giving the path:

**3 → 5 → 6**

At each downward step, the larger number reached equals the number above plus the smaller sibling:

- First step: 5 = 3 + 2
- Second step: 6 = 5 + 1

Together this gives **6 = 3 + 2 + 1**. What we collected is the top 3 and the unchosen sibling numbers 2 and 1.

For a three-row triangle, these three collected numbers must be distinct positive integers, so their sum is at least **1 + 2 + 3 = 6**. The endpoint cannot exceed 6, so the sum must be exactly 6: the collected numbers must be exactly 1, 2, 3.

The same reasoning applies to 2018 rows: the 2018 numbers collected along such a path are constrained to be exactly **1 to 2018**. This is already a strong restriction, but **this alone has not proved the large triangle impossible**; we must continue examining whether forcing larger numbers into the other cells produces a contradiction.

## Round 6

### Student

That was a bit much this time. I could not follow the later part about 2018 numbers. Let me walk through the small triangle: below 3 I choose 5, not 2; below 5 I choose 6, not 1. The collected numbers are 3, 2, 1, summing to 6. I can do that part now. Why must this addition also work in another triangle? Is it because we always choose the larger number, so reversing it means adding the sibling? Let us confirm just that first, without explaining the later parts together.

### Teacher

Yes, that is exactly why.

The upper number equals the difference between the two lower numbers. Choosing the larger one each time gives, in reverse:

**Chosen larger number = upper number + smaller sibling.**

Thus every step allows this addition; connecting the steps shows that the bottom number equals the top number plus all the unchosen siblings along the way.

### Student

For example, replacing the lower numbers with 4 and 7 gives 3 above; choosing 7 yields 7=3+4. I can use this step now, and explaining separately is easier to follow than before. I still do not understand the restriction from adding many numbers, and listening further now feels confusing. I want to stop here today. I still cannot explain myself why 2018 rows do not work.

### Teacher

This teaching session has been confirmed as ended.
