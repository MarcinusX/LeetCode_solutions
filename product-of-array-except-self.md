# [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description/) [Medium]
Given an array of n integers where n > 1, `nums`, return an array `output` such that `output[i]` is equal to the product of all the elements of nums except`nums[i]`.

Solve it **without** division and in O(n).

For example, given `[1,2,3,4]`, return `[24,12,8,6]`.

Follow up:  
Could you solve it with constant space complexity?  
(**Note**: The output array does not count as extra space for the purpose of space complexity analysis.)

## [Java solution](https://leetcode.com/submissions/detail/145454567/)
```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        if (n == 0 || n ==1) {
            return nums;
        }
        int[] res = new int[n];
        res[0] = nums[0];
        
        for (int i = 1; i < n-1; i++) {
            res[i] = res[i-1]*nums[i];
        }
        
        res[n-1] = res[n-2];
        int temp = nums[n-1];
        for (int i = n-2; i > 0; i--) {
            res[i]=res[i-1]*temp;
            temp *= nums[i];
        }
        res[0] = temp;
        return res;
    }
}
```
