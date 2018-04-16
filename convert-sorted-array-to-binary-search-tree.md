# [Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/) [Easy]

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.


Example:

Given the sorted array: [-10,-3,0,5,9],
```
One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
 ```
 
 ## [Java solution](https://leetcode.com/submissions/detail/150308511/)
 ```
 /**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if (nums.length == 0) {
            return null;
        }
        
        return helper(nums, 0, nums.length-1);
    }
    
    public TreeNode helper(int[] nums, int left, int right) {
        TreeNode node;
        if (right == left) {
            node = new TreeNode(nums[left]);
        } else if (right - left == 1) {
            node = new TreeNode(nums[left]);
            node.right = new TreeNode(nums[right]);
        } else {
            int mid = (right + left) / 2;
            node = new TreeNode(nums[mid]);
            node.left = helper(nums, left, mid-1);
            node.right = helper(nums, mid+1, right);
        }
        return node;
    }
}
 ```
