# [Path Sum II](https://leetcode.com/problems/path-sum-ii/description/) [Medium]
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:  
Given the below binary tree and `sum = 22`,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```
return
```
[
   [5,4,11,2],
   [5,8,4,5]
]
```

## [Java solution](https://leetcode.com/submissions/detail/150688160/)
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        List<Integer> currentSolution = new ArrayList<>();
        helper(result, currentSolution, sum, 0, root);
        return result;
    }
    
    void helper(List<List<Integer>> result, List<Integer> currentSolution, int target, int sum, TreeNode node) {
        sum += node.val;
        currentSolution.add(node.val);
        
        if (sum == target && node.left == null && node.right == null) {
            result.add(new ArrayList<>(currentSolution));
        } else {
            if (node.left != null) {
                helper(result, currentSolution, target, sum, node.left);
            }
            if (node.right != null) {
                helper(result, currentSolution, target, sum, node.right);
            } 
        }
        
        currentSolution.remove(currentSolution.size()-1);
    }
}
```
