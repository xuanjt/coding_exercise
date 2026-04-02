# Day 4: Sliding Window

## Today's goal

Learn how to maintain a valid subarray or substring while scanning only once.

Today is about turning repeated range checking into a moving window.

## What you should understand today

- What a window means
- When the window should expand
- When the window should shrink
- How to track information inside the window
- How to recognize "longest", "shortest", or "at most" patterns

## Core ideas

### 1. A sliding window is a dynamic interval

Typical meaning:

- current valid substring
- current valid subarray
- current range that satisfies a condition

You usually maintain:

- `left`
- `right`
- extra information about what is inside the window

### 2. Expand first, shrink when invalid

The most common pattern is:

- move `right` to include a new element
- update window state
- if the condition is broken, move `left` until the window is valid again

### 3. The key is not the window itself, but the condition

Before coding, say:

- what makes the window valid?
- what makes it invalid?
- what information do I need to know that quickly?

Typical extra information:

- character count
- sum
- number of distinct values
- current maximum or minimum

### 4. Different questions use the same pattern

Common forms:

- longest valid window
- shortest valid window
- count of windows
- maximum sum in a window

## A simple template to think before coding

Before you write code, ask:

1. What does the window `[left, right]` represent?
2. What condition makes this window valid?
3. What data do I need to maintain that condition?
4. When do I move `right`?
5. When do I move `left`?

## Problems for today

Do them in this order.

### Problem 1: Longest Substring Without Repeating Characters

- Goal: practice shrinking when duplicates appear
- Focus: character set or last-seen index
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/longest-substring-without-repeating-characters/

What to notice:

- `right` expands the string
- duplicates break validity
- `left` moves until the window is valid again

### Problem 2: Minimum Size Subarray Sum

- Goal: practice shortest valid window
- Focus: running sum and shrinking
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/minimum-size-subarray-sum/

What to notice:

- the window becomes useful once the sum reaches the target
- after that, keep shrinking to find the shortest valid one

### Problem 3: Permutation in String

- Goal: practice fixed-size and count-based window thinking
- Focus: frequency matching
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/permutation-in-string/

What to notice:

- window size is constrained by the length of `s1`
- the challenge is comparing counts efficiently

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- left and right pointer meaning
- how to update counts or sums
- the difference between "expand" and "shrink"

### Step 2: Solve Problem 1

Time limit: 35 to 45 minutes

Targets:

- explain what makes the window valid
- explain exactly when `left` should move

### Step 3: Solve Problem 2

Time limit: 30 to 40 minutes

Targets:

- explain why this is a shrinking problem
- explain why the answer updates only when the window is valid

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- explain what state the window needs to track
- explain why the window length matters

### Step 5: Rewrite one solution from memory

Spend 20 minutes rewriting:

- `Longest Substring Without Repeating Characters` if you want the most classic pattern
- `Minimum Size Subarray Sum` if you want the cleaner shrinking template

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- what condition defined a valid window
- what information you stored for the window
- what event caused `left` to move

## What a strong answer should include

- a clear window definition
- a clear validity condition
- correct expand and shrink logic
- correct complexity explanation

## Typical mistakes today

- Expanding the window without updating state
- Shrinking the window before the condition is checked
- Forgetting to update the answer at the right moment
- Confusing "longest valid" with "shortest valid"
- Using a window when the problem does not have a monotonic property

## Interview habit to build today

Before coding, say:

"The window is valid when ___, and I move `left` when ___."

That sentence is the core of most sliding window problems.

## Notes from today's practice

### Longest Substring Without Repeating Characters

- The main idea is correct: keep a window with no duplicate characters
- The next improvement is to maintain window state with a `set` or `dict`, instead of checking `s[right] in s[left:right]`

Key lesson:

- In sliding window problems, the value comes from maintaining window state directly, not rebuilding it from slicing

### Minimum Size Subarray Sum

- The window expands with `right` until the sum reaches the target
- Once the window becomes valid, the next goal is to shrink it as much as possible
- Even if the code has both a `for` loop and a `while` loop, the total complexity is still `O(n)` because `left` and `right` only move forward

Key lesson:

- In sliding window problems, complexity depends on how many times the pointers move in total, not on whether the code visually contains nested loops

### Permutation in String

- This is a fixed-length window problem
- The window length should always stay equal to `len(s1)`
- Each time the window slides by one step, update the state in two parts:
- remove the left character
- add the new right character

Useful way to think:

- fixed window means "slide one step, delete one old value, add one new value"
- if both counting dictionaries are equal, the current window is a valid permutation

Key lesson:

- In fixed-size sliding window problems, moving the pointers is not enough; the window state must slide together with them

## If you finish early

Pick one extra sliding-window problem:

- Longest Repeating Character Replacement
- Find All Anagrams in a String
- Fruits Into Baskets

## End-of-day checklist

- I can explain what the window means
- I can explain what breaks validity
- I can explain exactly when `left` should move
- I wrote down at least one mistake pattern
