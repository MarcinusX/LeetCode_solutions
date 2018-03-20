# [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/description/) [Easy]

Write a program to find the node at which the intersection of two singly linked lists begins.

```
For example, the following two linked lists:

A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
begin to intersect at node c1.
```

Notes:

* If the two linked lists have no intersection at all, return null.  
* The linked lists must retain their original structure after the function returns.  
* You may assume there are no cycles anywhere in the entire linked structure.  
* Your code should preferably run in O(n) time and use only O(1) memory.  

## [Java solution](https://leetcode.com/submissions/detail/146062796/)
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        
        int lengthA = length(headA);
        int lengthB = length(headB);
        
        int diff = lengthA - lengthB;
        ListNode shorter;
        ListNode longer;
        
        if (diff > 0) {
            longer = headA;
            shorter = headB;
            for (int i = 0; i < diff; i++) {
                longer = longer.next;
            }
        } else {
            longer = headB;
            shorter = headA;
            for (int i = 0; i < -diff; i++) {
                longer = longer.next;
            }
        }
        
        while (shorter!=null && longer != null) {
            if (shorter == longer) {
                return shorter;
            }
            shorter = shorter.next;
            longer = longer.next;
        }
        return null;
    }
    
    int length(ListNode node) {
        int i=0;
        while(node != null) {
            i++;
            node = node.next;
        }
        return i;
    }
}
```
