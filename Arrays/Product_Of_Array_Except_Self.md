# Product of Array Except Self

**Topic:** Arrays, Prefix and Suffix Products  
**Difficulty:** Medium  
**LeetCode:** 238

## Problem

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

You must solve the problem without using division and in `O(n)` time.

## Examples

**Example 1**

- Input: `nums = [1, 2, 3, 4]`
- Output: `[24, 12, 8, 6]`

**Example 2**

- Input: `nums = [-1, 1, 0, -3, 3]`
- Output: `[0, 0, 9, 0, 0]`

## Constraints

- `2 <= nums.length <= 10^5`
- `-30 <= nums[i] <= 30`
- The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

## Approach: Prefix and Suffix Products

1. Create an answer array filled with `1`.
2. Traverse from left to right, storing the product of all elements to the left of each index.
3. Traverse from right to left, multiply each answer value by the product of all elements to its right.
4. Update the running suffix product after processing each index.

This avoids division and uses constant extra space apart from the output array.

## Python 3 Solution

```python
from typing import List

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        answer = [1] * n

        prefix = 1
        for i in range(n):
            answer[i] = prefix
            prefix *= nums[i]

        suffix = 1
        for i in range(n - 1, -1, -1):
            answer[i] *= suffix
            suffix *= nums[i]

        return answer
```

## Complexity Analysis

- **Time Complexity:** `O(n)` — two traversals of the array.
- **Space Complexity:** `O(1)` auxiliary space, excluding the output array.

**Practice Tip:** Dry-run the solution with `[1, 2, 3, 4]` and write down the prefix and suffix products at every index.
