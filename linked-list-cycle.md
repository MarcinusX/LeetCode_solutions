# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description/) [Easy]

Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?

## [Java solution](https://leetcode.com/submissions/detail/144132390/)
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        } else if (head.next.next == head) {
            return true;
        }
        
        ListNode node1 = head;
        ListNode node2 = head.next;
        ListNode node3 = node2.next;
        node1.next = null;
        
        while (node3 != null && node3 != head) {
            node2.next = node1;
            node1 = node2;
            node2 = node3;
            node3 = node3.next;
        }
        
        return node3 == head;
    }
}
```
