# [Next Permutation](https://leetcode.com/problems/next-permutation/description/) [Medium]

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

`1,2,3` → `1,3,2`

`3,2,1` → `1,2,3`

`1,1,5` → `1,5,1`

## [Java solution](https://leetcode.com/submissions/detail/141749297/)
```
class Solution {
    public void nextPermutation(int[] nums) {
        if (nums.length == 0 || nums.length == 1) {
            return;
        }
        
        int indexLeft = -1;
        int indexRight = -1;
        
        for (int mainIndex = nums.length-1; mainIndex > -1; mainIndex--) {
            for (int index = mainIndex-1; index > -1; index--) {
                if (nums[mainIndex] - nums[index] > 0) {
                    if (index > indexLeft) {
                        indexLeft = index;
                        indexRight = mainIndex;
                    }
                    continue;
                }    
            }
        }
        
        if (indexLeft != -1) {
            swap(nums, indexRight, indexLeft);
            Arrays.sort(nums, indexLeft+1, nums.length);
        } else {
            // no arrangement possible -> sort
            Arrays.sort(nums);
        }

        return;
    }
    
    void swap(int[] nums, int i1, int i2) {
        int temp = nums[i1];
        nums[i1] = nums[i2];
        nums[i2] = temp;
    }
}
```
