# [Jump Game](https://leetcode.com/problems/jump-game/description/) [Medium]
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:  
A = `[2,3,1,1,4]`, return `true`.

A = `[3,2,1,0,4]`, return `false`.

## [Java solution](https://leetcode.com/submissions/detail/147677705/)
```
class Solution {
    public boolean canJump(int[] nums) {
        int index2 = nums.length-1;
        int index = nums.length-1;
        while (index > -1) {
            if (index+nums[index] >= index2) {
                index2 = index;
            }
            index--;
        }
        return index2 == 0;
    }
}
```
