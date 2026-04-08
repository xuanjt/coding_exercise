# Day 6: Binary Search

## Today's goal

Learn how to use binary search to locate answers in ordered or monotonic search spaces.

Today is about narrowing the answer range by half each time instead of checking one by one.

## What you should understand today

- When binary search applies
- How to define the search interval
- How to compute `mid` safely
- How to update `left` and `right`
- How to search for a value vs a boundary

## Core ideas

### 1. Binary search needs order or monotonicity

Typical signs:

- sorted array
- answer becomes possible after some point
- true/false condition changes only once

If the search space is ordered or monotonic, binary search may fit.

### 2. The hardest part is interval definition

Before coding, you must know:

- is the interval `[left, right]` or `[left, right)`?
- what does `left` mean?
- what does `right` mean?
- when should the loop stop?

Many binary-search bugs come from interval confusion, not from the idea itself.

### 3. Search target and search boundary are not the same

Two common types:

- find an exact target
- find the first or last position satisfying a condition

Boundary problems are often more important than exact-match problems.

### 4. Movement must preserve the answer

Each update should keep the possible answer inside the remaining interval.

Ask:

- if `mid` is too small, which side can be discarded?
- if `mid` is too large, which side can be discarded?

## A simple template to think before coding

Before you write code, ask:

1. What is the search space?
2. Is it ordered or monotonic?
3. What does `mid` tell me?
4. Which side can be safely discarded?
5. Am I finding a value, or the first/last valid boundary?

## Problems for today

Do them in this order.

### Problem 1: Find First and Last Position of Element in Sorted Array

- Goal: practice left boundary and right boundary search
- Focus: find a range instead of one exact position
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

What to notice:

- this is really two binary searches
- one finds the first valid position
- one finds the last valid position

### Problem 2: Find Minimum in Rotated Sorted Array

- Goal: practice identifying which side still contains the answer
- Focus: binary search on a rotated monotonic array
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

What to notice:

- the array is not fully sorted, but still has enough structure
- compare `nums[mid]` with `nums[right]` to decide which side may contain the minimum

### Problem 3: Koko Eating Bananas

- Goal: practice binary search on the answer itself
- Focus: monotonic feasibility check
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/koko-eating-bananas/

What to notice:

- the search space is not array indices, but possible eating speeds
- define a `can_finish(speed)` function
- once a speed works, larger speeds also work

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- left and right boundary meaning
- exact match vs boundary search
- how to avoid off-by-one mistakes

### Step 2: Solve Problem 1

Time limit: 30 to 40 minutes

Targets:

- explain why this needs two boundary searches
- explain what each returned boundary means

### Step 3: Solve Problem 2

Time limit: 30 to 40 minutes

Targets:

- explain which side may still contain the minimum
- explain why the discarded side is safe to remove

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- explain why the answer space is monotonic
- explain how the feasibility function guides the search

### Step 5: Rewrite one solution from memory

Spend 20 minutes rewriting:

- `Find First and Last Position of Element in Sorted Array` if you want to stabilize boundary search
- `Koko Eating Bananas` if you want to remember answer-space binary search

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- what interval you used
- what condition decided which half to discard
- whether you were searching for a value or a boundary

## What a strong answer should include

- a clear interval definition
- a clear loop condition
- correct boundary updates
- correct final return value

## Typical mistakes today

- Mixing `[left, right]` and `[left, right)`
- Infinite loop caused by wrong boundary update
- Returning the wrong boundary after the loop
- Forgetting whether the answer might still be at `mid`
- Solving a boundary problem as if it were only exact-match search
- Forgetting that binary search can also apply to answer space, not just array indices

## Interview habit to build today

Before coding, say:

"My search interval is ___, and after checking `mid`, I discard ___ because ___."

That sentence catches many binary-search bugs early.

## Notes from today's practice

### Boundary Search

- In boundary problems, the real target is often:
- the first position that satisfies a condition
- or the last position that satisfies a condition

Useful way to think:

- binary search updates depend on what the answer means
- before updating `left` or `right`, ask whether `mid` can still be the answer

### Closed Interval vs Left-Closed Right-Open

- Closed interval: `[left, right]`
- Left-closed right-open: `[left, right)`

Useful comparison:

- in `[left, right]`, `right` is a valid index
- in `[left, right)`, `right` is the position just after the valid search space
- in boundary search, `[left, right)` is often simpler and more uniform

Why `[left, right)` is often easier for boundary search:

- `right = len(nums)` is natural
- empty interval is simply `left == right`
- when `mid` can still be the answer, you can keep it with `right = mid`
- insert-position and left-boundary problems become more uniform

Key lesson:

- For "first/last valid position" problems, left-closed right-open intervals are often easier to reason about than closed intervals

## If you finish early

Pick one extra binary-search problem:

- Search in Rotated Sorted Array
- Capacity To Ship Packages Within D Days
- Median of Two Sorted Arrays

## End-of-day checklist

- I can recognize when binary search applies
- I can define the interval clearly
- I can explain exact match vs boundary search
- I wrote down at least one mistake pattern
