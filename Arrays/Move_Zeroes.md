# Move Zeroes

**Topic:** Arrays, Two Pointers  
**Difficulty:** Easy  
**LeetCode:** 283

## Problem

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

You must do this in-place without making a copy of the array.

## Examples

**Example 1**

- Input: `nums = [0, 1, 0, 3, 12]`
- Output: `[1, 3, 12, 0, 0]`

**Example 2**

- Input: `nums = [0]`
- Output: `[0]`

## Approach: Two Pointers

Use a pointer `insert_pos` to track where the next non-zero element should be placed.

1. Traverse the array from left to right.
2. Whenever a non-zero element is found, place it at `nums[insert_pos]`.
3. Increment `insert_pos`.
4. After processing all elements, fill the remaining positions with zeroes.

This preserves the relative order of all non-zero elements and modifies the array in-place.

## Python 3 Solution

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        insert_pos = 0

        for num in nums:
            if num != 0:
                nums[insert_pos] = num
                insert_pos += 1

        while insert_pos < len(nums):
            nums[insert_pos] = 0
            insert_pos += 1
```

## Complexity Analysis

- **Time Complexity:** `O(n)` — the array is traversed twice at most.
- **Space Complexity:** `O(1)` — the changes are made in-place.

## Constraints

- `1 <= nums.length <= 10^4`
- `-2^31 <= nums[i] <= 2^31 - 1`

**Practice Tip:** Dry-run the solution with `[0, 1, 0, 3, 12]` and track `insert_pos` after each non-zero element.
