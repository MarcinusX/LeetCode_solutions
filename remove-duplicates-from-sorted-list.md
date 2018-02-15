# [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/) [Easy]

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,

Given `1->1->2`, return `1->2`.

Given `1->1->2->3->3`, return `1->2->3`.

## [Java solution](https://leetcode.com/submissions/detail/140993554/)
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
    public ListNode deleteDuplicates(ListNode head) {
        if (head  == null || head.next == null) {
            return head;
        }
        
        ListNode prev = head;
        ListNode current = head.next;
        while (current != null) {
            if (current.val == prev.val) {
                current = current.next;
                prev.next = current;
            } else {
                current = current.next;
                prev = prev.next;
            }
        }
        
        return head;
    }
}
```
