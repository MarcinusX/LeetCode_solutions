# [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/description/) [Medium]

Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

For example:  
Given the following binary tree,
```
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
```
You should return `[1, 3, 4]`.

## [Java solution](https://leetcode.com/submissions/detail/144517020/)
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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        
        List<TreeNode> nodeList = new ArrayList<>();
        nodeList.add(root);
        
        while (!nodeList.isEmpty()) {
            result.add(nodeList.get(0).val);
            List<TreeNode> newList = new ArrayList<>();
            for (TreeNode node : nodeList) {
                if (node.right != null) {
                    newList.add(node.right);    
                }
                if (node.left != null) {
                    newList.add(node.left);
                }
            }
            nodeList = newList;
        }
        return result;
    }
}
```
