# [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/) [Medium]
Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its zigzag level order traversal as:
```
[
  [3],
  [20,9],
  [15,7]
]
```

## [Java solution](https://leetcode.com/submissions/detail/149947454/)
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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        if (root == null) {
            return new ArrayList<>();
        }
        Stack<TreeNode> currentStack = new Stack<>();
        List<List<Integer>> result = new ArrayList<>();
        
        boolean goRight = true;
        currentStack.push(root);
        while (!currentStack.empty()) {
            Stack<TreeNode> newStack = new Stack<>();
            List<Integer> row = new ArrayList<>();
            
            while( !currentStack.empty() ) {
                TreeNode node = currentStack.pop();
                row.add(node.val);
                
                if (goRight) {
                    if (node.left != null) {
                        newStack.push(node.left);
                    }
                    if (node.right != null) {
                        newStack.push(node.right);
                    }
                } else {
                    if (node.right != null) {
                        newStack.push(node.right);
                    }
                    if (node.left != null) {
                        newStack.push(node.left);
                    }
                }
            }
            result.add(row);
            goRight = !goRight;
            currentStack = newStack;
        }
        return result;
    }
}
```
