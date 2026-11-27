# Contains Duplicate

**Topic:** Arrays  
**Difficulty:** Easy  
**LeetCode:** 217

## Problem

Given an integer array `nums`, return `True` if any value appears at least twice in the array, and return `False` if every element is distinct.

## Examples

**Example 1**

- Input: `nums = [1, 2, 3, 1]`
- Output: `true`
- Explanation: The number `1` appears more than once.

**Example 2**

- Input: `nums = [1, 2, 3, 4]`
- Output: `false`
- Explanation: Every element is distinct.

**Example 3**

- Input: `nums = [1, 1, 1, 3, 3, 4, 3, 2, 4, 2]`
- Output: `true`

## Approach: Using a Set

A set stores only unique values. Traverse the array and check whether the current number is already in the set.

- If it is already present, return `True`.
- Otherwise, add it to the set.
- If the loop finishes, return `False`.

## Python 3 Solution

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()

        for num in nums:
            if num in seen:
                return True
            seen.add(num)

        return False
```

## Complexity Analysis

- **Time Complexity:** `O(n)` on average, because each set lookup and insertion takes `O(1)` on average.
- **Space Complexity:** `O(n)` in the worst case, for storing unique elements.

## Constraints

- `1 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

**Practice Tip:** Try solving this problem using sorting as well, then compare its time and space complexity with the set approach.
