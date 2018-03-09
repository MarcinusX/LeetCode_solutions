# [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/description/) [Medium]

A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null.

Return a deep copy of the list.

## [Java solution](https://leetcode.com/submissions/detail/144204324/)
```
/**
 * Definition for singly-linked list with a random pointer.
 * class RandomListNode {
 *     int label;
 *     RandomListNode next, random;
 *     RandomListNode(int x) { this.label = x; }
 * };
 */
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        if (head == null) {
            return null;
        }
        Map<RandomListNode, RandomListNode> map = new HashMap<>(); //original, copy
        RandomListNode node = new RandomListNode(head.label);
        copy(head, node, map);
        return map.get(head);
        
    }
    
    private void copy(RandomListNode orgList, RandomListNode copyNode, Map<RandomListNode, RandomListNode> map) {
        map.put(orgList, copyNode);
        
        if (orgList.next == null) {
            copyNode.next = null;
        } else if (map.containsKey(orgList.next)) {
            copyNode.next = map.get(orgList.next);       
        } else {
            RandomListNode newNode = new RandomListNode(orgList.next.label);
            copyNode.next = newNode;
            copy(orgList.next, newNode, map);
        }
        
        if (orgList.random == null) {
            copyNode.random = null;
        } else if (map.containsKey(orgList.random)) {
            copyNode.random = map.get(orgList.random);       
        } else {
            RandomListNode newNode = new RandomListNode(orgList.random.label);
            copyNode.random = newNode;
            copy(orgList.random, newNode, map);
        }
        
    }
}
```
