# [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/) [Medium]

Given a binary tree, return the inorder traversal of its nodes' values.

**Example:**
```
Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```
**Follow up:** Recursive solution is trivial, could you do it iteratively?

## [Java solution](https://leetcode.com/submissions/detail/152065843/)
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        
        TreeNode current = root;
        Stack<TreeNode> checkedLeft = new Stack<>();    
        
        while(current != null || !checkedLeft.isEmpty()) {
            if (current != null) {
                checkedLeft.push(current);
                current = current.left;
            } else {
                TreeNode node = checkedLeft.pop();
                result.add(node.val);
                current = node.right;
            }
        }
        
        return result;
    }
}
```
