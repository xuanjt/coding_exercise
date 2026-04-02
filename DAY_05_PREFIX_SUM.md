# Day 5: Prefix Sum

## Today's goal

Learn how to turn repeated range-sum questions into constant-time queries.

Today is about precomputing cumulative information so that later checks become simple.

## What you should understand today

- What a prefix sum means
- How to compute subarray sum with prefix sums
- When a hash map can be combined with prefix sums
- How to recognize "sum of a range" patterns
- Why prefix sums often replace repeated summation

## Core ideas

### 1. Prefix sum stores cumulative total up to a position

If:

```python
prefix[i]
```

means the sum of the first `i` elements, then:

```python
sum(nums[l:r]) = prefix[r] - prefix[l]
```

This turns repeated range-sum calculation into `O(1)`.

### 2. Prefix sum is useful when ranges are asked many times

Common signs:

- sum of a subarray
- sum from left to right
- count of ranges matching a target
- many repeated sum checks

### 3. Prefix sum + hash map is a strong pattern

Sometimes the problem is not asking for one fixed range, but:

- how many subarrays sum to `k`
- whether a past prefix sum already makes the current sum useful

In those cases:

- prefix sum gives the cumulative total
- hash map stores past prefix sums

### 4. The hard part is index meaning

Before coding, be clear about:

- whether `prefix[i]` includes `nums[i]`
- whether the prefix array starts with `0`
- what `prefix[r] - prefix[l]` really means

## A simple template to think before coding

Before you write code, ask:

1. What exactly does `prefix[i]` represent?
2. What range do I want to compute?
3. Can I turn the range question into subtraction of two prefix sums?
4. Do I need only one answer, or many repeated checks?
5. Do I need a hash map of past prefix sums?

## Problems for today

Do them in this order.

### Problem 1: Find Pivot Index

- Goal: practice left sum vs right sum
- Focus: total sum and running prefix sum
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/find-pivot-index/

What to notice:

- the left sum can be tracked while scanning
- the right sum can be derived from total sum

### Problem 2: Range Sum Query - Immutable

- Goal: practice explicit prefix array construction
- Focus: fast range sum queries
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/range-sum-query-immutable/

What to notice:

- build once
- answer many range queries quickly
- this is the cleanest prefix sum template

### Problem 3: Subarray Sum Equals K

- Goal: practice prefix sum + hash map
- Focus: counting how many past prefix sums make the current one useful
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/subarray-sum-equals-k/

What to notice:

- if current prefix sum is `curr`, then you want to know whether `curr - k` appeared before
- the hash map stores counts of past prefix sums, not just whether they exist

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- cumulative sum
- subarray index meaning
- left-closed and right-open thinking

### Step 2: Solve Problem 1

Time limit: 20 to 30 minutes

Targets:

- explain why total sum helps
- explain how left and right sums are derived

### Step 3: Solve Problem 2

Time limit: 20 to 30 minutes

Targets:

- define clearly what `prefix[i]` means
- explain why each query becomes `O(1)`

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- explain why `curr - k` matters
- explain why the hash map stores frequencies of prefix sums

### Step 5: Rewrite one solution from memory

Spend 20 minutes rewriting:

- `Range Sum Query - Immutable` if you want the cleanest prefix sum template
- `Subarray Sum Equals K` if you want the stronger pattern

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- what your prefix sum meant
- what subtraction represented
- whether the problem needed just prefix sums or prefix sums plus a hash map

## What a strong answer should include

- a clear prefix sum definition
- correct range meaning
- correct subtraction logic
- correct complexity explanation

## Typical mistakes today

- Not being clear about what `prefix[i]` includes
- Off-by-one errors in prefix indices
- Forgetting to initialize prefix sum with `0`
- Using a set when the problem needs counts of prefix sums
- Computing subarray sums repeatedly instead of reusing prefix information

## Interview habit to build today

Before coding, say:

"`prefix[i]` means ___, so this range sum equals ___."

That sentence prevents many prefix-sum mistakes.

## Notes from today's practice

### Find Pivot Index

- A clean way to think about this problem is:
- left sum is maintained while scanning
- right sum can be derived from the total sum

Useful way to think:

- if the total sum is known, then for index `i`:
- `right_sum = total - left_sum - nums[i]`

Key lesson:

- When the total sum is known, you often do not need to maintain both sides explicitly; one side can be derived from the total

### Range Sum Query - Immutable

- The core pattern is to preprocess cumulative sums once, then answer each query by subtraction
- A more standard version is to let the prefix array start with `0`

Useful way to think:

- if `prefix[i]` means the sum of the first `i` numbers, then:
- sum of `[left, right]` = `prefix[right + 1] - prefix[left]`

Key lesson:

- When the prefix array starts with `0`, range-sum formulas become more uniform and easier to write without edge cases

### Subarray Sum Equals K

- The key equation is:
- current prefix sum `curr`
- need a past prefix sum `curr - k`

Useful way to think:

- the subarray must be formed by "later prefix sum minus earlier prefix sum"
- so while scanning once, only past prefix sums matter
- the hash map should store how many times each prefix sum has appeared

Key lesson:

- In counting prefix-sum problems, store frequencies of past prefix sums, not all of their positions

## If you finish early

Pick one extra prefix-sum problem:

- Continuous Subarray Sum
- Product of Array Except Self
- Running Sum of 1d Array

## End-of-day checklist

- I can define prefix sum clearly
- I can compute a range sum by subtraction
- I can explain when a hash map should be added
- I wrote down at least one mistake pattern
