# Day 2 Daily Reflection

## Date

2026-03-30

## Day Number

Day 2

## Theme

Hash Map and Hash Set

## Problems Practiced

- Problem 1: Two Sum
- Problem 2: Valid Anagram
- Problem 3: Longest Consecutive Sequence

## Pattern Summary

- Key pattern 1: use a hash map to store past information while scanning once
- Key pattern 2: use counting to compare two inputs efficiently
- Key pattern 3: use a set for fast existence lookup and avoid repeated work

## What Clues Pointed to the Pattern

- `Two Sum`: needed fast complement lookup
- `Valid Anagram`: needed frequency comparison instead of position comparison
- `Longest Consecutive Sequence`: needed repeated existence checks, which suggests a set

## Mistakes

- Bug: the first `Two Sum` idea stored everything first, which made duplicate handling less natural
- Why it happened: the map was treated as a full lookup table instead of past information
- How to prevent it next time: first ask whether the hash table should store "all data" or only "past data"

- Bug: `Valid Anagram` initially focused on implementation, but the stronger view is "net count goes back to zero"
- Why it happened: the counting idea was there, but the pattern name was not explicit yet
- How to prevent it next time: summarize the counting rule in one sentence before coding

- Bug: `Longest Consecutive Sequence` could easily become repeated expansion from many numbers
- Why it happened: without the "start of sequence" condition, the same sequence would be revisited
- How to prevent it next time: ask whether every candidate really needs to start a new search

## Complexity

- `Two Sum`: Time `O(n)`, Space `O(n)`
- `Valid Anagram`: Time `O(n)`, Space `O(n)`
- `Longest Consecutive Sequence`: Time `O(n)` average, Space `O(n)`

## Rewrite Check

- Could I rewrite the core solution without looking: yes for all three, but `Two Sum` and `Longest Consecutive Sequence` are the two most important to remember well

## Confidence Score

- Topic confidence from 1 to 5: 4 / 5

## Best Takeaways Today

- A hash map often stores past information, not all information
- Counting can be expressed as positive and negative updates
- A set is powerful when the core question is "does this exist"
- A small condition like "is this the start" can remove repeated work

## Next Review Dates

- +2 days: 2026-04-01
- +7 days: 2026-04-06
- +14 days: 2026-04-13

## Tonight's Review Focus

- Rewrite `Two Sum` once from memory
- Remember the "net count returns to zero" idea for `Valid Anagram`
- Be able to explain why `Longest Consecutive Sequence` only expands from sequence starts
