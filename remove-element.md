# [Remove element](https://leetcode.com/problems/remove-element/description/) [Easy]

Given an array and a value, remove all instances of that value **in-place** and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**
```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```
## [Java Solution](https://leetcode.com/submissions/detail/139700331/)
```
class Solution {
    public int removeElement(int[] nums, int val) {
        int startIndex = 0;
        int endIndex = nums.length-1;
        while (startIndex < endIndex) {
            if (nums[startIndex] == val) {
                while (endIndex >= startIndex && nums[endIndex] == val) {
                    endIndex--;
                }
                if (endIndex < startIndex) {
                    return startIndex;
                }
                nums[startIndex] = nums[endIndex];
                endIndex--;
            }
            startIndex++;
        }
        if (startIndex == endIndex && nums[startIndex] != val) {
            startIndex++;
        }
        return startIndex;
    }
}
```

## [Better Java Solution]()
```
class Solution {
    public int removeElement(int[] nums, int val) {
        int startIndex = -1;
        for(int i = 0; i < nums.length; i++){
            if (nums[i] != val) {
                nums[++startIndex] = nums[i];
            }
        }
        return ++startIndex;
    }
}
```
