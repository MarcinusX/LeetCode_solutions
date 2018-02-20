# [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/) [Medium]

Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given `1->2->3->4`, you should return the list as `2->1->4->3`.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

## [Java solution](https://leetcode.com/submissions/detail/141604871/)
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
    public ListNode swapPairs(ListNode head) {
        if (head == null) {
            return null;
        }
        if (head.next == null) {
            return head;
        }
        ListNode node1 = head;
        ListNode node2 = head.next;
        node1.next = node2.next;
        node2.next = node1;
        ListNode newHead = node2;
        ListNode node0 = node1;
        while (node0.next != null && node0.next.next != null) {
            node1 = node0.next;
            node2 = node1.next;
            node1.next = node2.next;
            node2.next = node1;
            node0.next = node2;
            node0 = node1;
        }
        return newHead;
    }
}
```
