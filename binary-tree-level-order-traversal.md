# [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/description/) [Medium]

Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its level order traversal as:
```
[
  [3],
  [9,20],
  [15,7]
]
```

## [Java solution](https://leetcode.com/submissions/detail/143347908/)
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        addNodes(result, root, 0);
        return result;
    }
    
    private void addNodes(List<List<Integer>> result, TreeNode root, int level) {
        if (root == null) {
            return;
        }
        
        if (result.size() == level) {
            List<Integer> newList = new ArrayList<>();
            newList.add(root.val);
            result.add(newList);
        } else {
            result.get(level).add(root.val);
        }
        
        addNodes(result, root.left, level+1);
        addNodes(result, root.right, level+1);
    }
}
```
