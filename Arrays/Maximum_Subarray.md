# Maximum Subarray

**Topic:** Arrays, Dynamic Programming  
**Difficulty:** Medium  
**LeetCode:** 53

## Problem

Given an integer array `nums`, find the subarray with the largest sum, and return its sum.

A subarray is a contiguous, non-empty part of the array.

## Examples

**Example 1**

- Input: `nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`
- Output: `6`
- Explanation: The subarray `[4, -1, 2, 1]` has the largest sum, which is `6`.

**Example 2**

- Input: `nums = [1]`
- Output: `1`

**Example 3**

- Input: `nums = [5, 4, -1, 7, 8]`
- Output: `23`

## Approach: Kadane's Algorithm

Maintain two values:

- `current_sum`: maximum subarray sum ending at the current position.
- `max_sum`: maximum subarray sum found so far.

At each element, decide whether to extend the previous subarray or start a new one from the current element.

## Python 3 Solution

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        current_sum = max_sum = nums[0]

        for num in nums[1:]:
            current_sum = max(num, current_sum + num)
            max_sum = max(max_sum, current_sum)

        return max_sum
```

## Complexity Analysis

- **Time Complexity:** `O(n)` — each element is visited once.
- **Space Complexity:** `O(1)` — only two variables are used.

## Constraints

- `1 <= nums.length <= 10^5`
- `-10^4 <= nums[i] <= 10^4`

**Practice Tip:** Trace the algorithm with `[-2, 1, -3, 4, -1, 2, 1, -5, 4]` and track `current_sum` and `max_sum` after every element.
