# Day 7 Daily Reflection

## Date

2026-04-08

## Day Number

Day 7

## Theme

Review Day

## What I Reviewed

- Rewrote `Merge Sorted Array`
- Rewrote `Longest Consecutive Sequence`
- Reviewed `Sliding Window` and `Prefix Sum` concepts again
- Practiced new contrast problems to compare similar patterns

## Pattern Recall Summary

- Day 1: Arrays and Simulation
  Define variable meaning and boundaries clearly, then simulate step by step
- Day 2: Hash Map and Hash Set
  Use a hash table to store past information or counts so repeated lookup becomes fast
- Day 3: Two Pointers
  Let two pointers play different roles so one scan can replace repeated work
- Day 4: Sliding Window
  Use `left` and `right` to maintain a continuous range and update window state as it moves
- Day 5: Prefix Sum
  Turn range-sum questions into subtraction of cumulative sums
- Day 6: Binary Search
  In an ordered or monotonic search space, safely discard half of the remaining answers each step

## New Contrast Problems Practiced

- `Remove Duplicates from Sorted Array`
- `Find All Anagrams in a String`
- `Continuous Subarray Sum`
- `Capacity To Ship Packages Within D Days`

## Best Takeaways Today

- A solution can be correct but still miss the main structural advantage of the problem, such as using a set when sorted order is enough
- A hash map can appear inside sliding window, but that does not make the main pattern a hash-map problem
- Prefix sum plus remainder logic can replace slow comparison of all prefix-sum pairs
- Answer-space binary search is now becoming a recognizable standard pattern

## Mistakes

- Bug: sometimes I still reach for extra data structures before fully using sorted structure
- Why it happened: the general solution came to mind before the more specific structural shortcut
- How to prevent it next time: ask what extra structure the input already gives me

- Bug: similar patterns can still feel mixed when a problem uses more than one tool
- Why it happened: the support tool and the main pattern are easy to confuse
- How to prevent it next time: ask what the main movement or state update is

- Bug: I can understand a pattern but still feel unsure about its complexity at first glance
- Why it happened: nested loops look scary even when repeated work is actually controlled
- How to prevent it next time: count total pointer movement or total useful expansions, not only the visual loop structure

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Most Helpful Comparisons Today

- Arrays vs Two Pointers
- Hash Map vs Sliding Window
- Prefix Sum vs Sliding Window
- Binary Search vs Two Pointers

## What Still Needs More Repetition

- Faster pattern recognition when multiple techniques appear in the same problem
- More confidence explaining why a solution is `O(n)` even if it contains nested loops

## Next Review Dates

- +2 days: 2026-04-10
- +7 days: 2026-04-15
- +14 days: 2026-04-22

## Next Step

- Start Day 8 with linked list basics
