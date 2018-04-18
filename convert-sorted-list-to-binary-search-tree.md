# [Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/description/) [Medium]

Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

**Example:**
```
Given the sorted linked list: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
```

## [Java solution](https://leetcode.com/submissions/detail/150555358/)
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
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
    public TreeNode sortedListToBST(ListNode head) {
        if (head == null) {
            return null;
        }
        int length = 0;
        ListNode current = head;
        while (current != null) {
            current = current.next;
            length++;
        }
        return getRoot(head, length);
    }
    
    TreeNode getRoot(ListNode start, int length) {
        if (length == 1) {
            return new TreeNode(start.val);
        }
        if (length == 2) {
            TreeNode root = new TreeNode(start.val);
            root.right = new TreeNode(start.next.val);
            return root;
        }
        ListNode middle = middle(start, length);
        TreeNode root = new TreeNode(middle.val);
        root.left = getRoot(start, length/2);
        root.right = getRoot(middle.next, (length-1)/2);
        return root;
    }
    
    ListNode middle(ListNode start, int length) {
        ListNode current = start;
        for (int i = 0; i < length/2; i++) {
            current = current.next;
        }
        return current;
    }
}
```
