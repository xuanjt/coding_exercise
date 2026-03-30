# Day 2: Hash Map and Hash Set

## Today's goal

Learn how to use hash tables to trade space for speed.

Today is about recognizing when "store information while scanning" is better than repeated searching.

## What you should understand today

- When to use `dict`
- When to use `set`
- How to do counting
- How to do fast membership lookup
- How to store useful past information while traversing once

## Core ideas

### 1. Hash map is for key -> information

Typical use:

- number -> index
- character -> count
- prefix sum -> frequency

If you need to quickly ask "have I seen this before" or "what information belongs to this value", think about a hash map.

### 2. Hash set is for fast existence check

Typical use:

- remove duplicates
- check whether a value exists
- mark visited values

If you only care whether something exists, `set` is often enough.

### 3. Many nested loops can be reduced to one pass

If your first instinct is:

- for each number, search another number
- for each character, rescan the whole string

then a hash table may reduce the time complexity.

## A simple template to think before coding

Before you write code, ask:

1. What do I want to look up quickly?
2. Do I need existence only, or extra information too?
3. What should the key be?
4. What should the value be?
5. Can I solve this in one pass?

## Problems for today

Do them in this order.

### Problem 1: Two Sum

- Goal: practice complement lookup
- Focus: value -> index
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/two-sum/

What to notice:

- when you see `x`, you want to know whether `target - x` appeared before
- the hash map stores past numbers and their indices

### Problem 2: Valid Anagram

- Goal: practice counting
- Focus: character frequency
- Difficulty: easy
- LeetCode: https://leetcode.com/problems/valid-anagram/

What to notice:

- compare counts, not positions
- `dict` counting or `Counter` both work

### Problem 3: Longest Consecutive Sequence

- Goal: practice set-based optimization
- Focus: only start counting from the beginning of a sequence
- Difficulty: medium
- LeetCode: https://leetcode.com/problems/longest-consecutive-sequence/

What to notice:

- turn the list into a set first
- only start expanding from a number if `num - 1` is not in the set

## Recommended study flow for today

### Step 1: Warm-up review

Spend 15 minutes reviewing:

- `dict` get and update
- `set` membership check
- counting patterns

### Step 2: Solve Problem 1

Time limit: 20 to 30 minutes

Targets:

- say what the key and value mean
- explain why one pass works

### Step 3: Solve Problem 2

Time limit: 20 to 30 minutes

Targets:

- keep the counting logic clean
- explain why equal counts mean an anagram

### Step 4: Solve Problem 3

Time limit: 40 to 50 minutes

Targets:

- explain why checking only sequence starts avoids repeated work
- explain why the set makes lookup fast

### Step 5: Rewrite one solution from memory

Spend 20 minutes rewriting:

- `Two Sum` if you want speed and confidence
- `Longest Consecutive Sequence` if you want the more valuable pattern

### Step 6: Reflection

Spend 10 to 15 minutes writing:

- what was the key used in the hash table
- what was the value used in the hash table
- what repeated work the hash table helped you avoid

## What a strong answer should include

- clear key and value design
- no unnecessary repeated scanning
- simple explanation of why lookup is fast
- correct time and space complexity

## Typical mistakes today

- Using a list when a set would be faster
- Storing the wrong thing in the map
- Updating the map in the wrong order
- Forgetting that duplicate values may appear
- Failing to explain what the key and value mean

## Interview habit to build today

Before coding, say this sentence:

"My hash table key is ___, and the value means ___."

That one sentence will make your code much easier to design.

## Notes from today's practice

### Two Sum

- The clean hash-map pattern is not "store everything first"
- The cleaner pattern is "check first, then store current value"
- The map stores past information, not future information

Useful way to think:

- when you are visiting the current number, ask whether its complement has already appeared
- if yes, the answer is formed by "one past number + the current number"
- if not, store the current number for later

Key lesson:

- In many hash-map problems, the table is used to store past information while scanning once

### Valid Anagram

- A clean way to think about this problem is "net count"
- Add `+1` for each character in `s`
- Add `-1` for each character in `t`
- In the end, every character count should return to `0`

Key lesson:

- In counting problems, sometimes one hash map is enough if you let counts cancel out

### Longest Consecutive Sequence

- The key optimization is to avoid starting from every number
- Only start expanding if `num - 1` is not in the set
- That means the current number is the beginning of a sequence

Useful way to think:

- `set` gives fast existence lookup
- sequence expansion should only happen from true starting points

Key lesson:

- In set problems, a small condition like "is this the start?" can remove a lot of repeated work

## If you finish early

Pick one extra hash-table problem:

- Group Anagrams
- Top K Frequent Elements
- Contains Duplicate

## End-of-day checklist

- I can tell when to use `dict` vs `set`
- I can explain key and value design clearly
- I can use a hash table to replace repeated searching
- I wrote down at least one mistake pattern
