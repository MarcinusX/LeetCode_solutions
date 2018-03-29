# [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/description/) [Easy]

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

**Note:**  
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

## [Java solution](https://leetcode.com/submissions/detail/147566340/)
```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        if (nums1.length == 0 || n == 0) {
            return;
        }
        int index1 = m-1;
        int index2 = n-1;
        for (int i = nums1.length-1; i >=0; i--) {
            if (index1 >= 0 && (index2 < 0 || nums1[index1] > nums2[index2]))  {
                nums1[i] = nums1[index1];
                index1--;
            } else {
                nums1[i] = nums2[index2];
                index2--;
            } 
            
        }
    }
}
```
