# [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/) [Medium]

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow a node to be a descendant of itself).”
```
        _______3______
       /              \
    ___5__          ___1__
   /      \        /      \
   6      _2       0       8
         /  \
         7   4
```
For example, the lowest common ancestor (LCA) of nodes `5` and `1` is `3`. Another example is LCA of nodes `5` and `4` is `5`, since a node can be a descendant of itself according to the LCA definition.

## [Java solution](https://leetcode.com/submissions/detail/145590455/)
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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null) {
            return root;
        }
        Result res = search(root, p, q);
        return res.lca;
    }
    
    Result search(TreeNode current, TreeNode p, TreeNode q) {
        if (current == null) {
            return new Result();
        }
        
        Result resultLeft = search(current.left, p, q);
        if (resultLeft.lca != null) {
            return resultLeft;
        }
        
        Result resultRight = search(current.right, p, q);
        if (resultRight.lca != null) {
            return resultRight;
        }
        
        Result result = new Result();
        result.containsP = resultLeft.containsP || resultRight.containsP || current == p;
        result.containsQ = resultLeft.containsQ || resultRight.containsQ || current == q;
        if (result.containsP && result.containsQ) {
            result.lca = current;
        }
        
        return result;
    }
    
    static class Result {
        TreeNode lca;
        boolean containsP;
        boolean containsQ;
    }
}
```
