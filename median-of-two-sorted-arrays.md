# [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/description/) [Hard]
 
There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

**Example 1:**
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```
**Example 2:**
```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

## [Java Solution](https://leetcode.com/submissions/detail/139200290/)
```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int totalLength = nums1.length+nums2.length;
        int center = totalLength/2 + 1;
        boolean isEven = totalLength % 2 == 0;
        
        int numberBeforeCenter = 0;
        int index1 = 0;
        int index2 = 0;
        int currentNumber = 0;
        
        for (int i=0; i<center; i++) {
            //get numbers from arrays
            Integer num1 = null;
            if (index1 < nums1.length) {
                num1 = nums1[index1];
            }
            Integer num2 = null;
            if (index2 < nums2.length) {
                num2 = nums2[index2];
            }
            
            //determine smaller number
            if (num2 == null || (num1 != null && num1 < num2)) {
                currentNumber = num1;
                index1++;
            } else {
                currentNumber = num2;
                index2++;
            }
            
            //save number before center for Even scenario
            if (isEven && i == center-2) {
                numberBeforeCenter = currentNumber;
            }
        }
        
        if (isEven) {
            return (numberBeforeCenter+currentNumber)/2.0;
        } else {
            return currentNumber;
        }
        
    }
}
```
