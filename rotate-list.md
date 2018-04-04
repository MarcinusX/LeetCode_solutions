# [Rotate List](https://leetcode.com/problems/rotate-list/description/) [Medium]
Given a list, rotate the list to the right by k places, where k is non-negative.


**Example:**
```
Given 1->2->3->4->5->NULL and k = 2,

return 4->5->1->2->3->NULL.
```
## [Java Solution]()
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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) {
            return head;
        }
        
        int size = 1;
        ListNode node = head;
        while (node.next != null) {
            size++;
            node = node.next;
        }
        
        int actualK = k % size;
        
        if (actualK == 0) {
            return head;
        }
        
        int fromStart = size - actualK - 1;

        ListNode newLastNode = head;
        for (int i = 0; i < fromStart; i++) {
            newLastNode = newLastNode.next;
        }
        
        ListNode newFirstNode = newLastNode.next;
        newLastNode.next = null;
        node.next = head;
        
        return newFirstNode;
    }
}
```
