# [Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/) [Easy]

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its bottom-up level order traversal as:
```
[
  [15,7],
  [9,20],
  [3]
]
```

## [Java solution](https://leetcode.com/submissions/detail/150080180/)
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
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        helper(result, 1, root);
        return result;
    }
    
    private void helper(List<List<Integer>> result, int level, TreeNode node) {
        if (node == null) {
            return;
        }
        if (level > result.size()) {
            result.add(0,new ArrayList<>());
        }
        int index = result.size() - level;
        result.get(index).add(node.val);
        
        helper(result, level+1, node.left);
        helper(result, level+1, node.right);
    }
}
```
