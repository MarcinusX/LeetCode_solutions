# [3sum](https://leetcode.com/problems/3sum/description/) [Medium]

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:** The solution set must not contain duplicate triplets.

```
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

## [Java Solution](https://leetcode.com/submissions/detail/140411853/)

```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {        
        Arrays.sort(nums);
        Map<Integer, Integer> map = new HashMap<>(); //number, index
        for (int i = 0; i < nums.length; i++) {
                map.put(nums[i], i);
        }
        
        List<List<Integer>> results = new ArrayList<>();
        for (int index1 = 0; index1 < nums.length; index1++) {
            if (index1 != 0 && nums[index1] == nums[index1-1]) {
                continue;
            }
            
            for (int index2 = index1+1; index2 < nums.length; index2++) {
                if (index2 != index1+1 && nums[index2] == nums[index2-1]) {
                    continue;
                }
                
                int number1 = nums[index1];
                int number2 = nums[index2];                
                int number3 = -(number1+number2);
                Integer index3 = map.get(number3);
                if (index3 != null && index3 > index2) {
                    results.add(Arrays.asList(number1, number2, number3));
                }
            }
        }
                           
        return results;
    }

}
```
