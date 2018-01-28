# [Two Sum](https://leetcode.com/problems/two-sum/description/)

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

**Example:**
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## [Java solution](https://leetcode.com/submissions/detail/138085857/)
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i=0; i<nums.length; i++) {
            Integer matchingIndex = map.get(nums[i]);
            if (matchingIndex == null) {
                map.put(target-nums[i], i);
            } else {
                return new int[]{matchingIndex, i};
            }
        }
        return new int[]{};
    }
}
```
