# [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) [Medium]

Given preorder and inorder traversal of a tree, construct the binary tree.

**Note:**  
You may assume that duplicates do not exist in the tree.

For example, given
```
preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
```
Return the following binary tree:
```
    3
   / \
  9  20
    /  \
   15   7
```

## [Java solution](https://leetcode.com/submissions/detail/151090699/)
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

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return helper(preorder, inorder, 0, preorder.length, 0, inorder.length);
    }
    
    TreeNode helper(int[] preorder, int[] inorder, int preStart, int preEnd, int inStart, int inEnd) {
        if (preEnd - preStart == 0) {
            return null;
        } else if (preEnd - preStart == 1) {
            return new TreeNode(preorder[preStart]);
        }
        TreeNode root = new TreeNode(preorder[preStart]);
        
        int inorderRootIndex = -1;
        for (int i = inStart; i < inEnd; i++) {
            if (inorder[i]==root.val) {
                inorderRootIndex = i;
                break;
            }
        }
        
        int leftLength = inorderRootIndex - inStart;
        TreeNode left = helper(preorder, inorder, preStart+1, preStart+leftLength+1, inStart, inStart+leftLength);
        TreeNode right = helper(preorder, inorder, preStart+leftLength+1, preEnd, inStart+leftLength+1, inEnd);
        
        root.left = left;
        root.right = right;
        return root;
    }
}
```
