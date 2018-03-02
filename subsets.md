# [Subsets](https://leetcode.com/problems/subsets/description/) [Medium]

Given a set of **distinct** integers, nums, return all possible subsets (the power set).

**Note:** The solution set must not contain duplicate subsets.

For example,  
If **nums** = `[1,2,3]`, a solution is:
```
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

## [Java solution](https://leetcode.com/submissions/detail/143112776/)
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        result.add(new ArrayList<>());
        for (int i = 0; i < nums.length; i++) {
            addAll(result, new ArrayList<>(), i, nums);
        }
        return result;
    }
    
    void addAll(List<List<Integer>> result, List<Integer> list, int index, int[] nums) {
        if (index == nums.length) {
            return;
        }
        list.add(nums[index]);
        result.add(list);
        for (int i = index + 1; i < nums.length; i++) {
            addAll(result, new ArrayList<>(list), i, nums);
        }
    }
}
```
