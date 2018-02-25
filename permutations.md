# [Permutations](https://leetcode.com/problems/permutations/description/) [Medium]

Given a collection of distinct numbers, return all possible permutations.

For example,  
`[1,2,3]` have the following permutations:
```
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

## [Java solution](https://leetcode.com/submissions/detail/142302829/)
```
class Solution {
    
    public List<List<Integer>> permute(int[] nums) {
        if (nums.length == 0 || nums.length == 1) {
            List<List<Integer>> result = new LinkedList<>();
            List<Integer> inner = new LinkedList<>();
            if (nums.length == 1) {
                inner.add(nums[0]);
            }
            result.add(inner);
            return result;
        }
        
        List<List<Integer>> results = new LinkedList<>();
        List<Integer> permutation = Arrays.asList(new Integer[nums.length]);
        findPermutations(results, permutation, nums, new boolean[nums.length], 0);
        return results; 
    }
    
    void findPermutations(List<List<Integer>> allResults, List<Integer> permutation, int[] nums, boolean[] used, int index) {
        if (index == nums.length) {
            allResults.add(new ArrayList<>(permutation));
        } else {
            for (int i = 0; i < nums.length; i++) {
                if (!used[i]) {
                    used[i] = true;
                    permutation.set(index, nums[i]);
                    findPermutations(allResults, permutation, nums, used, index+1);
                    used[i] = false;
                }
            }
        }
    }
}
```
