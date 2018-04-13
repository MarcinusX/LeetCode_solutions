# [Single Number](https://leetcode.com/problems/single-number/description/) [Easy]
Given an array of integers, every element appears twice except for one. Find that single one.

Note:  
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## [Java solution](https://leetcode.com/submissions/detail/149834350/)
```
class Solution {
    public int singleNumber(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            if (set.contains(nums[i])) {
                set.remove(nums[i]);
            } else {
                set.add(nums[i]);
            }
        }
        return set.iterator().next();
    }
}
```
