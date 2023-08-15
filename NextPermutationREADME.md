# leet-day32

# Next Permutation

## Problem Statement

Given an array of integers `nums`, find the next permutation of `nums`. The next permutation is the next lexicographically greater permutation of the integers. If such an arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

## Example

### Input

```
nums = [1,2,3]
```

### Output

```
[1,3,2]
```

## Approach

To solve this problem, we can perform the following steps:

1. Traverse the array from right to left and find the first element `nums[i]` such that `nums[i]` is smaller than the element on its right side (`nums[i+1]`).
2. If no such element is found, it means the entire array is in descending order, which is the largest permutation. In this case, we reverse the entire array to get the smallest permutation.
3. If such an element is found, it means there is a possibility of generating the next permutation. We need to find the smallest element to the right of `nums[i]` that is greater than `nums[i]`.
4. Swap `nums[i]` and the smallest greater element found in step 3.
5. Reverse the subarray to the right of index `i`, ensuring that it's sorted in ascending order, as we want the next permutation.

## Algorithm

1. Initialize `i` as `nums.size() - 2`.
2. Traverse `i` from right to left until `nums[i]` is smaller than `nums[i+1]`.
3. If no such `i` is found, reverse the entire `nums` array and return.
4. Initialize `j` as `nums.size() - 1`.
5. Traverse `j` from right to left until `nums[j]` is greater than `nums[i]`.
6. Swap `nums[i]` and `nums[j]`.
7. Reverse the subarray to the right of index `i`.

## Complexity Analysis

- Time complexity: O(n), where n is the number of elements in the array.
- Space complexity: O(1), as we are using constant extra memory.

## Implementation

Here's the implementation of the approach in C++:

```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int i = nums.size() - 2;
        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }
        if (i >= 0) {
            int j = nums.size() - 1;
            while (j >= 0 && nums[j] <= nums[i]) {
                j--;
            }
            swap(nums[i], nums[j]);
        }
        reverse(nums.begin() + i + 1, nums.end());
    }
};
```

## Conclusion

Finding the next permutation of an array involves finding the elements to swap and then reversing the subarray. The provided C++ solution demonstrates this approach, providing an efficient solution to the problem.
