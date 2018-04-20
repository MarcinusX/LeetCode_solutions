# [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/) [Medium]

Given a binary tree, flatten it to a linked list in-place.

For example, given the following tree:
```
    1
   / \
  2   5
 / \   \
3   4   6
```
The flattened tree should look like:
```
1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```

## [Java solution](https://leetcode.com/submissions/detail/150889313/)
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
    public void flatten(TreeNode root) {
        if (root == null) {
            return;
        }
        flat(root);
    }
    
    TreeNode flat(TreeNode node) {
        if (node.left == null && node.right == null) {
            return node;
        } else if (node.left == null) {
            return flat(node.right);
        } else if (node.right == null) {
            node.right = node.left;
            node.left = null;
            return flat(node.right);
        } else {
            TreeNode right = node.right;
            TreeNode flatted = flat(node.left);
            node.right = node.left;
            node.left = null;
            flatted.right = right;
            return flat(right);
        }
        
    }
}
```
