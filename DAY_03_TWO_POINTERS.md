# Day 3: Two Pointers

## Today's goal

Learn how to use two pointers to reduce extra work and control traversal cleanly.

Today is about understanding how two indices can move with purpose instead of scanning blindly.

## What you should understand today

- When two pointers should move toward each other
- When two pointers should move in the same direction
- How to keep pointer meaning clear
- How to decide which pointer should move next
- How to avoid repeated work with pointer movement

## Core ideas

### 1. Two pointers means two positions with different roles

Typical roles:

- left and right boundary
- slow and fast pointer
- read and write pointer

Before coding, you should be able to say what each pointer means.

### 2. Opposite-direction pointers work well on ordered structure

If the array is sorted, or if the problem depends on the left and right ends, think about:

- one pointer from the left
- one pointer from the right

Typical use:

- finding a pair
- shrinking a range
- comparing mirrored positions

### 3. Same-direction pointers work well for compaction or skipping

Typical use:

- removing items in place
- deduplicating
- scanning while maintaining a valid region

### 4. Pointer movement should have a reason

Do not just move pointers because "the loop needs to continue".

Ask:

- What does this pointer represent?
- Why is moving it still safe?
- What information becomes impossible after I move it?

## A simple template to think before coding

Before you write code, ask:

1. What does `left` mean?
2. What does `right` mean?
3. What condition tells me which pointer should move?
4. Am I guaranteed not to miss the answer after moving this pointer?
5. What is the loop stop condition?

## Problems for today

Do them in this order.

### Problem 1: Valid Palindrome

- Goal: practice opposite-direction pointers
- Focus: compare from both ends while skipping invalid characters
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/valid-palindrome/

What to notice:

- both pointers move inward
- sometimes one pointer moves while the other waits
- pointer movement depends on whether the current character should be considered

### Problem 2: Move Zeroes

- Goal: practice same-direction pointers
- Focus: keep non-zero values compacted in front
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/move-zeroes/

What to notice:

- one pointer reads every element
- one pointer marks the next position for a useful value
- this is very close to the pattern from `Remove Element`

### Problem 3: Container With Most Water

- Goal: practice deciding which pointer should move
- Focus: eliminate impossible cases without checking all pairs
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/container-with-most-water/

What to notice:

- area depends on width and the shorter height
- moving the taller side does not help if the shorter side stays the limit
- the key is to move the pointer on the shorter side

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- left/right boundary thinking
- read/write pointer pattern
- what makes pointer movement safe

### Step 2: Solve Problem 1

Time limit: 25 to 30 minutes

Targets:

- explain when to skip a character
- explain why comparing from both ends is natural

### Step 3: Solve Problem 2

Time limit: 20 to 30 minutes

Targets:

- explain the meaning of the write pointer
- connect it with day 1 in-place filtering

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- explain why moving the shorter side is the only promising move
- explain what cases are safely discarded

### Step 5: Rewrite one solution from memory

Spend 20 minutes rewriting:

- `Move Zeroes` if you want to stabilize same-direction pointers
- `Container With Most Water` if you want the deeper idea

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- what each pointer represented
- what rule decided pointer movement
- what repeated work two pointers helped you avoid

## What a strong answer should include

- clear pointer roles
- correct movement rule
- no unnecessary rescanning
- correct complexity explanation

## Typical mistakes today

- Moving a pointer without a reason
- Using two pointers when one pointer is actually enough
- Forgetting to skip invalid characters before comparing
- In `Container With Most Water`, moving the taller pointer for no reason
- Mixing up read pointer and write pointer meaning

## Interview habit to build today

Before coding, say:

"`left` means ___, `right` means ___, and I move ___ because ___."

That sentence will make your pointer logic much easier to trust.

## Notes from today's practice

### Valid Palindrome

- The core pattern is: skip invalid characters, then compare from both ends
- A safe habit is: check boundary first, then access `s[left]` or `s[right]`

Better condition order:

```python
while left < right and not s[left].isalnum():
    left += 1
while left < right and not s[right].isalnum():
    right -= 1
```

Key lesson:

- In two-pointer problems, pointer safety comes before character access

Short clean version:

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        left, right = 0, len(s) - 1
        while left < right:
            while left < right and not s[left].isalnum():
                left += 1
            while left < right and not s[right].isalnum():
                right -= 1
            if s[left].lower() != s[right].lower():
                return False
            left += 1
            right -= 1
        return True
```

### Move Zeroes

- The key is to separate reading from writing
- `read` keeps moving forward and sees every element
- `write` only marks the next position where a non-zero value should go

Useful way to think:

- `read` is responsible for traversal
- `write` is responsible for keeping the front part valid and ordered

Key lesson:

- In same-direction pointer problems, the cleanest version is often "read keeps scanning, write keeps the valid region in order"

### Container With Most Water

- My original idea: treat each `height[i]` as the shorter side, then find the farthest boundary on the left or right that is at least as tall
- This idea correctly noticed that area is controlled by the shorter side
- But this way of thinking still tends to re-search many possibilities from many starting points

Standard idea:

- start with the widest container
- compute area using `left` and `right`
- move the shorter side inward

Difference between the two ideas:

- my idea tries to enumerate who is the shorter side
- the standard idea uses the shorter side to decide which part of the search space can be discarded

Key lesson:

- The standard solution is not just using the short side to calculate area, but using the short side to do safe pruning

## If you finish early

Pick one extra two-pointer problem:

- Two Sum II - Input Array Is Sorted
- Squares of a Sorted Array
- 3Sum

## End-of-day checklist

- I can explain opposite-direction vs same-direction pointers
- I can explain what each pointer means before coding
- I can justify pointer movement, not just write it
- I wrote down at least one mistake pattern
