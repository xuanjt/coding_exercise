# Day 1 Daily Reflection

## Date

2026-03-29

## Day Number

Day 1

## Theme

Arrays and Simulation

## Problems Practiced

- Problem 1: Remove Element
- Problem 2: Merge Sorted Array
- Problem 3: Spiral Matrix

## Pattern Summary

- Key pattern 1: use `read` and `write` pointers for in-place filtering
- Key pattern 2: when front-writing may overwrite useful values, consider writing from right to left
- Key pattern 3: for matrix traversal, boundaries are often clearer than slicing

## What Clues Pointed to the Pattern

- `Remove Element`: the problem asks for in-place removal and returning the new length, which suggests a write pointer
- `Merge Sorted Array`: `nums1` has free space at the end, which suggests merging from the back
- `Spiral Matrix`: the task is repeated boundary traversal, which suggests `top`, `bottom`, `left`, `right`

## Mistakes

- Bug: early `Remove Element` logic was correct in direction but too dependent on complicated boundary handling
- Why it happened: the pointer meaning was not simple enough
- How to prevent it next time: prefer the clean `read` and `write` template for filtering problems

- Bug: `Spiral Matrix` used matrix slicing at first, which made the logic harder
- Why it happened: slicing looked concise, but Python matrix slicing is not true 2D slicing
- How to prevent it next time: use coordinates and boundaries first in matrix problems

- Bug: `range` boundaries were easy to misread, especially when deciding whether the end is included
- Why it happened: Python `range` is left-closed and right-open
- How to prevent it next time: explicitly ask whether the boundary should be included before writing the loop

## Complexity

- `Remove Element`: Time `O(n)`, Space `O(1)`
- `Merge Sorted Array` optimized version: Time `O(m + n)`, Space `O(1)`
- `Spiral Matrix`: Time `O(m * n)`, Space `O(1)` besides output

## Rewrite Check

- Could I rewrite the core solution without looking: mostly yes for `Remove Element` and `Merge Sorted Array`
- `Spiral Matrix` still needs one more review for boundary confidence

## Confidence Score

- Topic confidence from 1 to 5: 3.5 / 5

## Best Takeaways Today

- Simpler pointer meaning usually leads to more reliable code
- Writing from the back can avoid overwrite problems
- In matrix problems, slicing can increase complexity
- `range(start, stop)` includes `start` but excludes `stop`

## Next Review Dates

- +2 days: 2026-03-31
- +7 days: 2026-04-05
- +14 days: 2026-04-12

## Tonight's Review Focus

- Rewrite `Merge Sorted Array` once from memory
- Review `Spiral Matrix` boundaries and `range` usage
- Be able to explain why `top < bottom` or `left < right` checks matter
