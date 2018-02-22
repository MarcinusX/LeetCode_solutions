# [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/) [Medium]

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

## [Java Solution](https://leetcode.com/submissions/detail/141874823/)
```
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0) {
            return -1;
        }
        
        if (target == nums[0]) {
            return 0;
        } else if (target > nums[0]) {
            int index = 1;
            while (index < nums.length && target > nums[index]) {
                index++;
            }
            if (index != nums.length && target == nums[index]) {
                return index;
            } else {
                return -1;
            }
        }  else {//target < nums[0]
            int index = nums.length-1;
            while (index > -1 && target < nums[index]) {
                index--;
            }
            if (index != -1 && target == nums[index]) {
                return index;
            } else {
                return -1;
            }
        }
    }
}
```

## [Other Java Solution](https://leetcode.com/submissions/detail/141880314/)
```
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0) {
            return -1;
        }
        
        int left = 0;
        int right = nums.length -1;
        while (left <= right) {
            int mid = left + (right - left)/2;
            
            if (target == nums[mid]) {
                return mid;
            }
            
            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (target >= nums[left] || target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
        }
        return -1;
    }
}
```
