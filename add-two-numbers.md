# [Add two numbers](https://leetcode.com/problems/add-two-numbers/description/) [Medium]

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example**
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

## [Java solution](https://leetcode.com/submissions/detail/138952278/)
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode node1 = l1;
        ListNode node2 = l2;
        ListNode result = null;
        ListNode current = null;
        boolean isCarrying = false;
        while (node1 != null || node2 != null) {
            //sum
            int number1 = node1 == null ? 0 : node1.val;
            int number2 = node2 == null ? 0 : node2.val;
            int sum = number1 + number2;
            if (isCarrying) {
                sum++;
            }
            if (sum >= 10) {
                sum = sum % 10;
                isCarrying = true;
            } else {
                isCarrying = false;
            }
            
            //add result
            if (result == null) {
                result = new ListNode(sum);
                current = result;
            } else {
                current.next = new ListNode(sum);
                current = current.next;
            }
            
            //iterate
            if (node1 != null) {
                node1 = node1.next;
            }
            if (node2 != null) {
                node2 = node2.next;
            }
        }
        if (isCarrying) {
            current.next = new ListNode(1);
        }
        return result;
    }
}
```
