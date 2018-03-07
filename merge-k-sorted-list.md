# [Merge k sorted lists](https://leetcode.com/problems/merge-k-sorted-lists/description/) [hard]

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

## [Java solution](https://leetcode.com/submissions/detail/143900722/)
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
    
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists.length == 0) {
            return null;
        }
        if (lists.length == 1) {
            return lists[0];
        }
        
        Queue<Integer> indexes = new PriorityQueue<>(lists.length, (index1, index2) -> lists[index1].val - lists[index2].val);
        for (int i = 0; i < lists.length; i++) {
            if (lists[i] != null) {
                indexes.add(i);
            }
        }
        
        if (indexes.size() == 0) {
            return null;
        }
        
        ListNode result;
        
        int index = indexes.poll();
        result = lists[index];
        lists[index] = lists[index].next;
        if (lists[index] != null) {
            indexes.add(index);
        }
        ListNode current = result;
        
        while (indexes.size() != 0) {
            index = indexes.poll();
            current.next = lists[index];
            current = lists[index];
            lists[index] = lists[index].next;
            if (lists[index]!= null) {
                indexes.add(index);
            }
        }
        
        return result;
    }
    
}
```
Complexity should be O(mklog(k)) where m is average size of list
