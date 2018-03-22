# [Rotate array](https://leetcode.com/problems/rotate-array/description/) [Easy]
Rotate an array of n elements to the right by k steps.

For example, with `n = 7` and `k = 3`, the array `[1,2,3,4,5,6,7]` is rotated to `[5,6,7,1,2,3,4]`.

## [Java solution](https://leetcode.com/submissions/detail/146422128/)
```
class Solution {
    public void rotate(int[] nums, int k) {
        if (nums.length == 0 || nums.length == 1) {
            return;
        }
        k = k % nums.length;
        if (k == 0) {
            return;
        }
        reverse(nums, 0, nums.length-k-1);
        reverse(nums, nums.length-k, nums.length-1);
        reverse(nums, 0, nums.length-1);
    }
    
    //both are inclusive
    void reverse(int[] nums, int start, int end) {
        for (int i = start; i <= start + (end -start)/2 ; i++) {
            int temp = nums[i];
            nums[i] = nums[end+start-i];
            nums[end+start-i]=temp;
        }
    }
}
```
