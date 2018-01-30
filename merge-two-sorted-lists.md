# [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description/) [Easy]

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**
```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

## [Java Solution](https://leetcode.com/submissions/detail/138585331/)
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode result = null;
        ListNode current = null;
        ListNode node1 = l1;
        ListNode node2 = l2;
        
        while (node1 != null || node2 != null) {
            ListNode smallestNode;
            if (node1 == null) {
                smallestNode = node2;
                node2 = node2.next;
            } else if (node2 == null) {
                smallestNode = node1;
                node1 = node1.next;
            } else if (node1.val < node2.val) {
                smallestNode = node1;
                node1 = node1.next;
            } else {
                smallestNode = node2;
                node2 = node2.next;
            }
            
            if (result == null) {
                result = smallestNode;
                current = result;
            } else {
                current.next = smallestNode;
                current = smallestNode;
            }
        }
        return result;
    }
}
```
