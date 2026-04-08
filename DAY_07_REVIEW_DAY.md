# Day 7: Review Day

## Today's goal

Consolidate the first six days instead of learning a new pattern.

Today is for strengthening recognition, fixing recurring mistakes, and turning separate topics into reusable problem-solving habits.

## What today should feel like

- less new knowledge
- more recall
- more rewriting from memory
- more comparison between patterns

If the first six days built the pieces, today is where they start connecting.

## Topics to review

- Day 1: Arrays and Simulation
- Day 2: Hash Map and Hash Set
- Day 3: Two Pointers
- Day 4: Sliding Window
- Day 5: Prefix Sum
- Day 6: Binary Search

## Key Pattern Recall

### Day 1: Arrays and Simulation

- Define variable meaning and boundaries clearly, then simulate step by step

### Day 2: Hash Map and Hash Set

- Use a hash table to store past information or counts so repeated lookup becomes fast

### Day 3: Two Pointers

- Let two pointers play different roles so one scan can replace repeated work

### Day 4: Sliding Window

- Use `left` and `right` to maintain a continuous range and update window state as it moves

### Day 5: Prefix Sum

- Turn range-sum questions into subtraction of cumulative sums

### Day 6: Binary Search

- In an ordered or monotonic search space, safely discard half of the remaining answers each step

## Main review task

Redo 2 to 3 old problems without looking at your past code.

Recommended set for today:

### Review Problem 1: Merge Sorted Array

- Topic: arrays, pointer movement, overwrite avoidance
- LeetCode: https://leetcode.com/problems/merge-sorted-array/

Review focus:

- why writing from the back avoids overwrite
- what each pointer means

### Review Problem 2: Longest Consecutive Sequence

- Topic: set lookup and repeated-work elimination
- LeetCode: https://leetcode.com/problems/longest-consecutive-sequence/

Review focus:

- why only sequence starts should expand
- why `set` is enough

### Review Problem 3: Koko Eating Bananas

- Topic: answer-space binary search
- LeetCode: https://leetcode.com/problems/koko-eating-bananas/

Review focus:

- what the answer space is
- why feasibility is monotonic

## Optional extra review

If you still have time, pick one more:

- Spiral Matrix
- Move Zeroes
- Minimum Size Subarray Sum
- Subarray Sum Equals K

## Pattern comparison review

Try to answer these from memory:

### 1. Arrays vs Two Pointers

- When is plain traversal enough?
- When do two pointers avoid repeated work?

### 2. Hash Map vs Sliding Window

- When do you store global past information?
- When do you store only current window information?

### 3. Prefix Sum vs Sliding Window

- When does the problem ask for many range sums?
- When does the window stay valid only under monotonic expansion and shrink?

### 4. Binary Search vs Two Pointers

- When can you discard half the space?
- When can you only shrink one side at a time?

## Pattern comparison with examples

### 1. Arrays vs Two Pointers

Example problem:

- `Move Zeroes`
- LeetCode: https://leetcode.com/problems/move-zeroes/

Why this is Two Pointers, not plain array traversal:

- plain traversal only reads values
- this problem also needs in-place reordering
- one pointer reads every element
- one pointer writes the next valid position

Core solution idea:

- let `read` scan the array from left to right
- let `write` mark the next position for a non-zero value
- every time `read` sees a non-zero, move it to `write`

What this comparison teaches:

- array problems often focus on indexing and simulation
- two-pointer problems become useful when one traversal role is not enough

### 2. Hash Map vs Sliding Window

Example problem:

- `Longest Substring Without Repeating Characters`
- LeetCode: https://leetcode.com/problems/longest-substring-without-repeating-characters/

Why this is Sliding Window, not only Hash Map:

- the target is a current valid substring
- the valid region changes over time
- you need both boundaries and window state
- a hash map or set is only the tool used to maintain the window

Core solution idea:

- expand `right` to include a new character
- if the window becomes invalid, move `left` until it is valid again
- use a set or map to track which characters are inside the current window

What this comparison teaches:

- hash map stores information
- sliding window decides which continuous range is currently active
- many sliding window problems use a hash map, but the main technique is still the moving window

### 3. Prefix Sum vs Sliding Window

Example problem:

- `Minimum Size Subarray Sum`
- LeetCode: https://leetcode.com/problems/minimum-size-subarray-sum/

Why this is Sliding Window, not Prefix Sum:

- the array contains positive numbers, so expanding increases the sum monotonically
- once the sum is large enough, the left side can safely shrink
- the goal is the shortest valid window, not many repeated arbitrary range-sum queries

Core solution idea:

- move `right` to grow the sum
- once the sum is at least `target`, update the answer
- then move `left` to shrink the window as much as possible

What this comparison teaches:

- prefix sum is great for repeated range-sum calculation
- sliding window is better when a monotonic validity rule lets the window expand and shrink efficiently

### 4. Binary Search vs Two Pointers

Example problem:

- `Koko Eating Bananas`
- LeetCode: https://leetcode.com/problems/koko-eating-bananas/

Why this is Binary Search, not Two Pointers:

- the search space is possible eating speeds
- the condition is monotonic: if a speed works, larger speeds also work
- there is no continuous active interval to maintain

Core solution idea:

- binary search the answer range from `1` to `max(piles)`
- define a feasibility check: total hours needed at speed `mid`
- if `mid` works, search smaller feasible speeds
- otherwise, search larger speeds

What this comparison teaches:

- binary search is used when half the answer space can be discarded safely
- two pointers are used when a moving interval or two moving positions reveal the answer step by step

## Pattern Contrast Practice

Use these as new practice problems to strengthen the difference between similar patterns.

### 1. Arrays vs Two Pointers

- Problem: `Remove Duplicates from Sorted Array`
- LeetCode: https://leetcode.com/problems/remove-duplicates-from-sorted-array/
- Why this is useful:
- it looks like an array editing problem
- but the clean solution is really a same-direction two-pointer pattern

Review note:

- A `set`-based solution can work, but it does not fully use the fact that the array is already sorted
- Because duplicates are adjacent in a sorted array, comparing with the last kept value is enough

Key lesson:

- When the array is sorted, adjacent structure often removes the need for extra hash-based memory

### 2. Hash Map vs Sliding Window

- Problem: `Find All Anagrams in a String`
- LeetCode: https://leetcode.com/problems/find-all-anagrams-in-a-string/
- Why this is useful:
- it uses counting dictionaries
- but the main pattern is a fixed-size sliding window

Review note:

- The counting dictionary is only the tool for maintaining window state
- The real pattern is that the window has fixed length and slides one step at a time

Key lesson:

- If the main work is "remove left, add right, compare current window", the core pattern is sliding window, even if a hash map is used inside

### 3. Prefix Sum vs Sliding Window

- Problem: `Continuous Subarray Sum`
- LeetCode: https://leetcode.com/problems/continuous-subarray-sum/
- Why this is useful:
- it involves continuous subarrays
- but the stronger pattern is prefix sum plus hash map, not ordinary sliding window

Review note:

- A direct prefix-sum difference solution is correct but too slow if it compares all pairs
- The key optimization is to compare prefix-sum remainders modulo `k`

Key lesson:

- When the condition is about divisibility of a subarray sum, repeated prefix-sum remainders are often the real signal

### 4. Binary Search vs Two Pointers

- Problem: `Capacity To Ship Packages Within D Days`
- LeetCode: https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/
- Why this is useful:
- it may look like interval control at first
- but the real pattern is binary search on the answer space with a monotonic feasibility check

Review note:

- The solution is standard answer-space binary search
- The key is not the package positions, but whether a capacity is feasible

Key lesson:

- In answer-space binary search, complexity is "feasibility check cost" times "number of binary-search steps"

## Notes from today's review

### Longest Consecutive Sequence

- This is still `O(n)` on average even though the code has a `for` loop and a `while` loop

Why it is still `O(n)`:

- `set` lookup is average `O(1)`
- the code only starts expanding from true sequence starts
- if `num - 1` exists, that number is not a start, so it is skipped
- this prevents the same consecutive sequence from being expanded again and again from the middle

Key lesson:

- A nested loop does not always mean `O(n^2)`; what matters is whether repeated work is actually happening

## Memory drills

Pick any 3 of these and explain them without notes:

- `read` vs `write` pointer
- `dict` vs `set`
- why sliding window can still be `O(n)`
- why prefix sums often start with `0`
- why left-closed right-open intervals help in boundary binary search

## Common mistake list to build today

Write down your top mistakes from the first six days.

Suggested categories:

- off-by-one mistakes
- wrong pointer meaning
- wrong window update order
- confusing "store positions" with "store frequencies"
- mixing interval definitions in binary search

## Recommended study flow for today

### Step 1: 20-minute recall

Without opening old code, write down:

- one key pattern from each of days 1 to 6

### Step 2: 60 to 90-minute problem redo

Redo 2 or 3 old problems from memory.

### Step 3: 20-minute compare-and-summarize

Write:

- one thing that now feels easier than three days ago
- one pattern you still need more repetition on

### Step 4: 10-minute mistake review

Make a short "watch out for this" list for next week.

## What a strong review day should produce

- fewer forgotten patterns
- clearer distinction between similar techniques
- a shorter list of repeated mistakes
- more confidence rewriting from memory

## End-of-day checklist

- I reviewed at least 2 old problems without looking
- I wrote down recurring mistakes
- I compared similar patterns instead of treating them as isolated topics
- I know which topic needs the most extra repetition next week
