# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/) [Easy]
Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,  
the contiguous subarray `[4,-1,2,1]` has the largest sum = `6`.

## [Java solution](https://leetcode.com/submissions/detail/147942863/)
```
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = Integer.MIN_VALUE;
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            if (sum < 0) {
                sum = nums[i];
            } else {
                sum += nums[i];
            }
            
            if (sum > maxSum) {
                maxSum = sum;
            }
        }
        return maxSum;
    }
}
```
