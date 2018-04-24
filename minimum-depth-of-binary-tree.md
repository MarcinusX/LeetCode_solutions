# [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/) [Easy]

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Note: A leaf is a node with no children.

Example:

Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its minimum `depth = 2`.

## [Java solution]()
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
    
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        List<TreeNode> list = new ArrayList<>();
        list.add(root);
        
        int level = 1;
        while (!list.isEmpty()) {
            List<TreeNode> newList = new ArrayList<>();
            for (TreeNode node : list) {
                if (node.left == null && node.right == null) {
                    return level;
                } else {
                    if (node.left != null) {
                        newList.add(node.left);
                    }
                    if (node.right != null) {
                        newList.add(node.right);
                    }
                }
            }
            list = newList;
            level++;
        }
        return level;
    }
}
```
