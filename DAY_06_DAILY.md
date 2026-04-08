# Day 6 Daily Reflection

## Date

2026-04-03 to 2026-04-07

## Day Number

Day 6

## Theme

Binary Search

## Problems Practiced

- Problem 1: Find First and Last Position of Element in Sorted Array
- Problem 2: Find Minimum in Rotated Sorted Array
- Problem 3: Koko Eating Bananas

## Actual Progress

- Practiced Problem 1 and Problem 3 in detail
- Problem 2 had already been done before, so it was reviewed conceptually instead of solved again
- This topic was spread across several days because of travel

## Pattern Summary

- Key pattern 1: boundary search is often more important than exact-match search
- Key pattern 2: left-closed right-open intervals are often easier for boundary problems
- Key pattern 3: binary search can be applied to answer space when feasibility is monotonic

## What Clues Pointed to the Pattern

- `Find First and Last Position of Element in Sorted Array`: needed left and right boundaries, not just one target position
- `Find Minimum in Rotated Sorted Array`: needed to use partial order to discard one half
- `Koko Eating Bananas`: needed the minimum feasible speed, and feasibility changes monotonically

## Mistakes

- Bug: boundary search was first approached with exact-match thinking
- Why it happened: it is natural to first think "find target" instead of "find first or last valid position"
- How to prevent it next time: first say clearly whether the task is finding a value or finding a boundary

- Bug: closed interval and left-closed right-open interval logic felt easy to mix
- Why it happened: both are valid, but their initialization and updates are different
- How to prevent it next time: fix the interval type before coding and keep the same meaning throughout

- Bug: in answer-space binary search, it is easy to focus on `mid` and forget the monotonic feasibility condition
- Why it happened: the search space is no longer array indices, so the binary-search intuition needs to shift
- How to prevent it next time: explicitly define the `can_do(mid)` or `can_finish(mid)` function before writing updates

## Complexity

- `Find First and Last Position of Element in Sorted Array`: Time `O(log n)`, Space `O(1)`
- `Find Minimum in Rotated Sorted Array`: Time `O(log n)`, Space `O(1)`
- `Koko Eating Bananas`: Time `O(n log m)`, where `m = max(piles)`, Space `O(1)`

## Rewrite Check

- Could I rewrite the core solution without looking: yes for boundary search and for Koko
- The main thing to remember is the interval meaning and why each half can be discarded

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Best Takeaways Today

- Boundary binary search asks for the first or last valid position, not just any match
- In boundary problems, `[left, right)` is often easier to reason about
- `right = len(nums)` means the position after the valid search space, not a real index to access
- In answer-space binary search, the core is a monotonic feasibility check

## Next Review Dates

- +2 days: 2026-04-09
- +7 days: 2026-04-14
- +14 days: 2026-04-21

## Tonight's Review Focus

- Re-explain why `find_left` and `find_right` can locate boundaries
- Be able to say the difference between `[left, right]` and `[left, right)`
- Remember that Koko is binary search on the answer, not on array positions
