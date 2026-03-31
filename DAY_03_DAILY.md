# Day 3 Daily Reflection

## Date

2026-03-31

## Day Number

Day 3

## Theme

Two Pointers

## Problems Practiced

- Problem 1: Valid Palindrome
- Problem 2: Move Zeroes
- Problem 3: Container With Most Water

## Pattern Summary

- Key pattern 1: opposite-direction pointers compare from both ends
- Key pattern 2: same-direction pointers often separate reading from writing
- Key pattern 3: two pointers are powerful when pointer movement can safely discard impossible cases

## What Clues Pointed to the Pattern

- `Valid Palindrome`: the comparison naturally happens from both ends inward
- `Move Zeroes`: needed in-place reordering while keeping relative order
- `Container With Most Water`: needed to avoid checking all pairs, which suggests pruning with two pointers

## Mistakes

- Bug: in `Valid Palindrome`, the boundary check came after character access in the inner `while`
- Why it happened: pointer safety was not checked first
- How to prevent it next time: in pointer problems, check boundary first, then access the element

- Bug: in `Move Zeroes`, the first version tried to track both a zero position and a non-zero position
- Why it happened: the traversal job and the writing job were mixed together
- How to prevent it next time: let `read` keep moving forward, and let `write` only maintain the valid front region

- Bug: in `Container With Most Water`, the first idea tried to enumerate who is the shorter side
- Why it happened: the short-side intuition was correct, but it was used for local search instead of global pruning
- How to prevent it next time: ask whether the key observation can be used to safely discard part of the search space

## Complexity

- `Valid Palindrome`: Time `O(n)`, Space `O(1)`
- `Move Zeroes`: Time `O(n)`, Space `O(1)`
- `Container With Most Water`: Time `O(n)`, Space `O(1)`

## Rewrite Check

- Could I rewrite the core solution without looking: mostly yes
- The most important thing to remember is the movement rule, not just the final code

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Best Takeaways Today

- In two-pointer problems, each pointer must have a clear role
- In same-direction pointer problems, `read` scans and `write` maintains order
- In opposite-direction problems, boundary safety comes before element access
- In stronger two-pointer problems, the real value is often safe pruning

## Next Review Dates

- +2 days: 2026-04-02
- +7 days: 2026-04-07
- +14 days: 2026-04-14

## Tonight's Review Focus

- Rewrite `Move Zeroes` once from memory
- Be able to explain why `Valid Palindrome` checks boundary before access
- Be able to explain why `Container With Most Water` moves the shorter side
