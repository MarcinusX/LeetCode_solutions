# [Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/description/) [Medium]
Given a binary tree
```
struct TreeLinkNode {
  TreeLinkNode *left;
  TreeLinkNode *right;
  TreeLinkNode *next;
}
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

Note:  
You may only use constant extra space.  
Recursive approach is fine, implicit stack space does not count as extra space for this problem.

Example:  
Given the following binary tree,
```
     1
   /  \
  2    3
 / \    \
4   5    7
```
After calling your function, the tree should look like:
```
     1 -> NULL
   /  \
  2 -> 3 -> NULL
 / \    \
4-> 5 -> 7 -> NULL
```

## [Java solution](https://leetcode.com/submissions/detail/151565215/)
```
/**
 * Definition for binary tree with next pointer.
 * public class TreeLinkNode {
 *     int val;
 *     TreeLinkNode left, right, next;
 *     TreeLinkNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void connect(TreeLinkNode root) {
        helper(root);
    }
    
    void helper(TreeLinkNode node) {
        if (node == null) {
            return;
        }

        if (node.left != null) {
            if (node.right != null) {
                node.left.next = node.right;
            } else {
                node.left.next = findChildNext(node.next);
            }
        }
        if (node.right != null) {
            node.right.next = findChildNext(node.next);
        }
        helper(node.right);
        helper(node.left);
    }
    
    TreeLinkNode findChildNext(TreeLinkNode node) {
        if (node == null) {
            return null;
        }
        if (node.left != null) {
            return node.left;
        } else if (node.right != null) {
            return node.right;
        } else {
            return findChildNext(node.next);
        }
    }
}
```
