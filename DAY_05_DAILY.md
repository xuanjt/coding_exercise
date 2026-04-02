# Day 5 Daily Reflection

## Date

2026-04-02

## Day Number

Day 5

## Theme

Prefix Sum

## Problems Practiced

- Problem 1: Find Pivot Index
- Problem 2: Range Sum Query - Immutable
- Problem 3: Subarray Sum Equals K

## Pattern Summary

- Key pattern 1: total sum can help derive one side from the other
- Key pattern 2: range sums can be turned into subtraction of prefix sums
- Key pattern 3: prefix sum plus hash map can count useful past states in one pass

## What Clues Pointed to the Pattern

- `Find Pivot Index`: needed left sum and right sum at each position
- `Range Sum Query - Immutable`: needed many repeated range-sum queries
- `Subarray Sum Equals K`: needed to count how many earlier prefix sums make the current sum useful

## Mistakes

- Bug: in `Find Pivot Index`, the first version explicitly maintained both sides
- Why it happened: the total-sum shortcut was not used immediately
- How to prevent it next time: when one side and total sum are known, check whether the other side can be derived

- Bug: in `Range Sum Query - Immutable`, the first version used a dictionary for prefix sums
- Why it happened: the cumulative idea was correct, but the storage choice was less natural than a list
- How to prevent it next time: if indices are continuous, prefer a list and consider adding a leading `0`

- Bug: in `Subarray Sum Equals K`, the first version stored all prefix-sum positions and compared them later
- Why it happened: the prefix-difference equation was correct, but the counting requirement was not simplified enough
- How to prevent it next time: ask whether the problem needs exact positions or only frequencies

## Complexity

- `Find Pivot Index`: Time `O(n)`, Space `O(1)`
- `Range Sum Query - Immutable`: Build `O(n)`, Query `O(1)`, Space `O(n)`
- `Subarray Sum Equals K`: Time `O(n)`, Space `O(n)`

## Rewrite Check

- Could I rewrite the core solution without looking: yes for all three
- The most important thing to remember is the meaning of prefix sum and what the hash map stores

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Best Takeaways Today

- Prefix sum is about reusing cumulative information instead of recomputing ranges
- If total sum is known, one side can often be derived
- A leading `0` in the prefix array can remove edge cases
- For counting problems, storing prefix-sum frequencies is often enough

## Next Review Dates

- +2 days: 2026-04-04
- +7 days: 2026-04-09
- +14 days: 2026-04-16

## Tonight's Review Focus

- Rewrite `Range Sum Query - Immutable` using a prefix array that starts with `0`
- Be able to explain why `curr - k` matters in `Subarray Sum Equals K`
- Be able to explain why the hash map stores frequencies instead of positions
