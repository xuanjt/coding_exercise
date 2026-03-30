# Day 1: Arrays and Simulation

## Today's goal

Learn how to solve array problems with careful indexing, traversal order, and boundary control.

Today is not about fancy algorithms. It is about building reliability.

If you can keep loops, indices, and edge cases under control, many later topics become easier.

## What you should understand today

- How to traverse an array from left to right and right to left
- How to update elements in place
- How to avoid off-by-one bugs
- How to simulate a process step by step
- How to reason about boundaries such as empty array, one element, first index, and last index

## Core ideas

### 1. Array problems often test implementation discipline

A lot of day 1 problems are not mathematically hard. They are easy to get almost right.

Common failure points:

- using the wrong loop boundary
- forgetting to update an index
- overwriting a value too early
- confusing result length with array length
- not handling empty input

### 2. Simulation means following the rules exactly

If a problem describes a process, do not jump to a complicated trick too early.

First ask:

- What is the state?
- What changes each step?
- When do we stop?

### 3. In-place array problems usually need a write pointer

Very often:

- one pointer reads
- one pointer writes

This is a core pattern for removing elements, deduplicating sorted arrays, and compacting valid values.

## A simple template to think before coding

Before you write code, answer these:

1. What do my indices mean?
2. Am I reading and writing in the same array?
3. What happens on empty input?
4. What should the final returned value represent?
5. Can I dry-run the sample by hand?

## Problems for today

Do them in this order.

### Problem 1: Remove Element

- Goal: practice read pointer and write pointer
- Focus: in-place overwrite and final length
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/remove-element/

What to notice:

- the write pointer only moves when you keep a value
- values beyond the returned length do not matter

### Problem 2: Merge Sorted Array

- Goal: practice filling from the back
- Focus: avoiding overwrite when two arrays must end up in one array
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/merge-sorted-array/

What to notice:

- if you fill from the front, you may destroy useful values
- filling from the back is safer when the destination has extra space

### Problem 3: Spiral Matrix

- Goal: practice boundary updates in a simulation problem
- Focus: top, bottom, left, right boundaries
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/spiral-matrix/

What to notice:

- every traversal changes one boundary
- after each pass, check whether the boundaries are still valid

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- array indexing
- `for` vs `while`
- how to dry-run with pencil and paper

### Step 2: Solve Problem 1

Time limit: 25 to 30 minutes

Targets:

- explain what `read` means
- explain what `write` means
- return the correct new length

### Step 3: Solve Problem 2

Time limit: 30 to 35 minutes

Targets:

- explain why you fill from the end
- keep pointer movement clear

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- define all four boundaries before coding
- update them in a stable order
- avoid repeated cells

### Step 5: Rewrite one solution from memory

Spend 20 to 30 minutes rewriting either:

- Remove Element, if you still feel shaky
- Spiral Matrix, if you want the bigger challenge

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- which bug almost happened
- which bug actually happened
- what rule would have prevented it

## What a strong answer should include

For array implementation problems, a strong answer usually has:

- correct handling of edge cases
- clear pointer meaning
- no unnecessary extra space
- a short explanation of time and space complexity

## Typical mistakes today

- Using `<=` when you meant `<`
- Forgetting that array indices start at `0`
- Updating a boundary twice
- Forgetting to check whether `top <= bottom` or `left <= right`
- Returning the wrong size after in-place modification

## Interview habit to build today

Say your invariants out loud before coding.

Examples:

- "`write` is the next valid position"
- "`k` is the last index I should fill"
- "`top`, `bottom`, `left`, and `right` describe the remaining unvisited rectangle"

This habit makes debugging much easier.

## Notes from today's practice

### Remove Element

- A simpler and more stable solution uses a read pointer and a write pointer
- `read` scans every element
- `write` points to the next position where a valid element should be written
- When `nums[read] != val`, write it to `nums[write]` and move `write`
- The answer is the final value of `write`

Key lesson:

- For in-place filtering problems, the cleanest template is often "scan with `read`, keep valid values with `write`"

### Merge Sorted Array

- There are two valid ways to solve it
- Version 1: copy `nums1[:m]` first, then do a normal merge
- Version 2: the stronger interview version is to fill from the back

Why fill from the back:

- If you write from the front, you may overwrite valid values in `nums1`
- If you write from the back, the empty space at the end becomes safe working space

Core pointer meanings:

- `p1`: last valid element in `nums1`
- `p2`: last element in `nums2`
- `write`: position where the next largest value should go

Key lesson:

- When the destination array already has buffer space at the end, and front-writing may overwrite useful values, consider filling from right to left

### Python detail clarified today

- `nums[:m]` already returns a new list
- `nums[:m].copy()` is usually unnecessary if the goal is just to copy that slice
- `nums[:m] = ...` is slice assignment and directly modifies the original list

### Matrix problem lesson from Spiral Matrix

- For matrix problems, slicing often makes the solution more complicated instead of simpler
- `matrix[a:b][c:d]` is not true 2D slicing in Python
- Repeatedly slicing a matrix may create extra copies and make boundary handling harder
- When a matrix problem depends on row and column boundaries, coordinates are usually safer than slicing

Key lesson:

- In 2D matrix problems, prefer `top`, `bottom`, `left`, `right`, or direct index access like `matrix[i][j]`

## If you finish early

Pick one extra array problem:

- Best Time to Buy and Sell Stock
- Majority Element
- Product of Array Except Self

## End-of-day checklist

- I can explain read pointer vs write pointer
- I can explain why some merges must be done from the back
- I can manage four boundaries in a matrix simulation
- I wrote down at least one bug pattern to remember

## What to write in your daily template

- Theme: Arrays and Simulation
- Main pattern: indexing and boundary control
- Biggest risk: off-by-one mistakes
- Confidence score: rate yourself honestly from 1 to 5
