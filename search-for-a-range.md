# [Search for a Range](https://leetcode.com/problems/search-for-a-range/description/) [Medium]

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return `[-1, -1]`.

For example,
Given `[5, 7, 7, 8, 8, 10]` and target value 8,
return `[3, 4]`.

## [Java solution](https://leetcode.com/submissions/detail/142032427/)
```
class Solution {
    
    public int[] searchRange(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return new int[]{-1,-1};
        }
        int low = 0;
        int high = nums.length - 1;
        while (low <= high) {
            int mid = low + (high - low)/2;
            
            if (nums[mid] < target) {
                low = mid + 1;
            } else if (nums[mid] > target) {
                high = mid - 1;
            } else {//nums[mid] == target
                return new int[]{searchLow(nums, mid, target), searchHigh(nums, mid, target)};
            }
        }
        return new int[]{-1,-1};
    }
    
    public int searchLow(int[] nums, int start, int target) {
        int index = start;
        while (index > -1 && nums[index] == target) {
            index--;
        }
        return index + 1;
    }
    
    public int searchHigh(int[] nums, int start, int target) {
        int index = start;
        while (index < nums.length && nums[index] == target) {
            index++;
        }
        return index - 1;
    }
}
```
