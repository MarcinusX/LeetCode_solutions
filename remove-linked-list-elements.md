# [Remove Linked Lists Elements](https://leetcode.com/problems/remove-linked-list-elements/description/) [Easy]
Remove all elements from a linked list of integers that have value val.

Example:
```
Input:  1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5
```

## [Java solution](https://leetcode.com/submissions/detail/152910945/)
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
    public ListNode removeElements(ListNode head, int val) {
        ListNode newHead = head;
        while (newHead != null && newHead.val == val) {
            newHead = newHead.next;
        }
        if (newHead == null) {
            return null;
        }
        ListNode current = newHead.next;
        ListNode prev = newHead;
        while (current != null) {
            if (current.val == val) {
                current = current.next;
                prev.next = current;
            } else {
                prev = prev.next;
                current = current.next;
            }
        }
        return newHead;
    }
}
```
