# [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/) [Easy]

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following `[1,2,2,null,3,null,3]` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```
**Note:**  
Bonus points if you could solve it both recursively and iteratively.

## [Recursive Java solution](https://leetcode.com/submissions/detail/147157457/)
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
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }
        return areEqual(root.left, root.right);
    }
    
    private boolean areEqual(TreeNode left, TreeNode right) {
        if (left == null && right == null) {
            return true;
        }
        if (left == null || right == null || left.val != right.val) {
            return false;
        }
        return areEqual(left.left, right.right) && areEqual(left.right, right.left);
    }
}
```

## [Iterative Java solution](https://leetcode.com/submissions/detail/147158950/)
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
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }
        
        LinkedList<TreeNode> leftNodes = new LinkedList<>();
        LinkedList<TreeNode> rightNodes = new LinkedList<>();
        leftNodes.add(root.left);
        rightNodes.add(root.right);
        
        while (!leftNodes.isEmpty() && !rightNodes.isEmpty()) {
            TreeNode leftNode = leftNodes.poll();
            TreeNode rightNode = rightNodes.poll();
            
            if (leftNode == null && rightNode == null) {
               continue; 
            }
            if (leftNode == null || rightNode == null || leftNode.val != rightNode.val) {
                return false;
            }
            leftNodes.addLast(leftNode.left);
            leftNodes.addLast(leftNode.right);
            rightNodes.addLast(rightNode.right);
            rightNodes.addLast(rightNode.left);
        }
        
        return true;
    }
}
```
