# [Remove nth node from end of list](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/) [Medium]

Given a linked list, remove the nth node from the end of list and return its head.

For example,
```
   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given n will always be valid.
Try to do this in one pass.

## [Java solution](https://leetcode.com/submissions/detail/140712521/)
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode current = head;
        ListNode nthFromEnd = head;
        for (int i = 0; i < n; i++) {
            current = current.next;
        }
        
        if (current == null) {
            return head.next;
        }
                
        while (current.next != null) {
            current = current.next;
            nthFromEnd = nthFromEnd.next;
        }
        
        nthFromEnd.next = nthFromEnd.next.next;
        
        return head;
    }
}
```
