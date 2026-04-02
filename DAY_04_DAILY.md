# Day 4 Daily Reflection

## Date

2026-04-01

## Day Number

Day 4

## Theme

Sliding Window

## Problems Practiced

- Problem 1: Longest Substring Without Repeating Characters
- Problem 2: Minimum Size Subarray Sum
- Problem 3: Permutation in String

## Pattern Summary

- Key pattern 1: maintain a valid window instead of checking every range
- Key pattern 2: expand with `right`, then shrink with `left` when needed
- Key pattern 3: fixed-size windows must update state as they slide

## What Clues Pointed to the Pattern

- `Longest Substring Without Repeating Characters`: needed the longest valid substring with no duplicates
- `Minimum Size Subarray Sum`: needed the shortest valid subarray once the sum reached a target
- `Permutation in String`: needed to compare many windows of the same fixed length

## Mistakes

- Bug: in `Longest Substring Without Repeating Characters`, the first version checked duplicates using string slicing
- Why it happened: the window itself was recognized, but the window state was not maintained directly
- How to prevent it next time: for sliding window problems, ask what state should be stored in a `set`, `dict`, or running sum

- Bug: in `Minimum Size Subarray Sum`, the complexity could look suspicious because the code had both `for` and `while`
- Why it happened: it is easy to judge by loop shape instead of total pointer movement
- How to prevent it next time: count how many times `left` and `right` move in total

- Bug: in `Permutation in String`, the first version moved the window bounds without updating the counting dictionary
- Why it happened: the pointer movement was separated from the window state update
- How to prevent it next time: in fixed-length windows, always think "remove left, add right"

## Complexity

- `Longest Substring Without Repeating Characters`: Time `O(n)`, Space `O(k)` for window state
- `Minimum Size Subarray Sum`: Time `O(n)`, Space `O(1)`
- `Permutation in String`: Time `O(n)` with fixed-size window updates, Space `O(k)`

## Rewrite Check

- Could I rewrite the core solution without looking: mostly yes
- The most important thing to remember is the window validity rule and the state update rule

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Best Takeaways Today

- Sliding window is about maintaining state, not rescanning a range
- Expand first, then shrink when the condition is broken or satisfied
- Fixed-size windows need synchronized state updates
- A `for` + `while` sliding window can still be `O(n)` if both pointers only move forward

## Next Review Dates

- +2 days: 2026-04-03
- +7 days: 2026-04-08
- +14 days: 2026-04-15

## Tonight's Review Focus

- Rewrite `Minimum Size Subarray Sum` once from memory
- Be able to explain why pointer movement total can still be `O(n)`
- Be able to explain why `Permutation in String` is a fixed-size window problem
