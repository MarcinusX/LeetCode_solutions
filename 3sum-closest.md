# [3Sum Closest](https://leetcode.com/problems/3sum-closest/description/) [Medium]

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.
```
    For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

## [Java solution](https://leetcode.com/submissions/detail/141316362/)
```
class Solution {
    
    public int threeSumClosest(int[] nums, int target) {        
        Map<Integer, Integer> map = new HashMap<>(); //number, numberOfOccurences
        for (int i = 0; i < nums.length; i++) {
            Integer numberOfOccurences = map.get(nums[i]);
            if (numberOfOccurences == null) {
                map.put(nums[i], 1);
            } else {
                map.put(nums[i], numberOfOccurences + 1);
            }
        }
        
        int distance = 0;
        Integer closestSum = null;
        while (closestSum == null) {
            closestSum = closestThreeSumWithDistance(nums, target, distance, map);
            distance++;
        }
        return closestSum;
    }
    
    public Integer closestThreeSumWithDistance(int[] nums, int target, int distance, Map<Integer, Integer> map) {
        for (int i = 0; i < nums.length; i++) {
            if (closestTwoSum(nums, target - nums[i] - distance, i, map)) {
                return target - distance;
            } else if (closestTwoSum(nums, target - nums[i] + distance, i, map)) {
                return target + distance;
            }
        }
        return null;
    }
    
    public boolean closestTwoSum(int[] nums, int target, int excludedIndex, Map<Integer, Integer> map) {
        int excludedNumber = nums[excludedIndex];
        for (int i = 0; i < nums.length; i++) {
            if (i != excludedIndex) {
                Integer numberOfOccurences = map.get(target-nums[i]);
                if (numberOfOccurences != null) {
                    int requiredOccs = 0;
                    if (target - nums[i] == nums[i]) {
                        requiredOccs++;
                    }
                    if (target - nums[i] == excludedNumber) {
                        requiredOccs++;
                    }
                    if (numberOfOccurences > requiredOccs) {
                        return true;
                    }
                }
            }
        }
        return false;
    }
}
```
