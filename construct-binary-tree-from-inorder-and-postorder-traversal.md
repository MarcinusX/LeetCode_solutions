# [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/) [Medium]

Given inorder and postorder traversal of a tree, construct the binary tree.

**Note:**  
You may assume that duplicates do not exist in the tree.

For example, given

inorder = `[9,3,15,20,7]`  
postorder = `[9,15,7,20,3]`  
Return the following binary tree:
```
    3
   / \
  9  20
    /  \
   15   7
```

## [Java result](https://leetcode.com/submissions/detail/151256530/)
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
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        return helper(inorder, postorder, 0, inorder.length, 0, postorder.length);
    }
    
    private TreeNode helper(int[] inorder, int[] postorder, int startIn, int endIn, int startPost, int endPost) {
        if (startPost == endPost) {
            return null;
        }
        TreeNode root = new TreeNode(postorder[endPost-1]);
        
        int rootIndex = startIn;
        while(inorder[rootIndex] != root.val) {
            rootIndex++;
        }
        int leftLength = rootIndex - startIn;

        root.left = helper(inorder, postorder, startIn, rootIndex, startPost, startPost+leftLength);
        root.right = helper(inorder, postorder, rootIndex+1, endIn, startPost+leftLength, endPost -1);
        return root;
    }
}
```
