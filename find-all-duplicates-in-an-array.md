# [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/) [Medium]

Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear **twice** and others appear **once**.

Find all the elements that appear **twice** in this array.

Could you do it without extra space and in O(n) runtime?
```
Example:
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
```

## [Java solution](https://leetcode.com/submissions/detail/147815543/)
```
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        List<Integer> results = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            int targetIndex = Math.abs(nums[i])-1;
            if (nums[targetIndex] > 0) {
                nums[targetIndex] = -nums[targetIndex];
            } else {
                results.add(targetIndex+1);
            }
        }
        return results;
    }
}
```
