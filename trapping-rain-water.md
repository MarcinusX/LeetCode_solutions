# [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/description/) [Hard]

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

For example,   
Given `[0,1,0,2,1,0,1,3,2,1,2,1]`, return 6.  
![img](https://leetcode.com/static/images/problemset/rainwatertrap.png)

The above elevation map is represented by array `[0,1,0,2,1,0,1,3,2,1,2,1]`.  
In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!

## [Java solution](https://leetcode.com/submissions/detail/146218704/)
```
class Solution {
    public int trap(int[] height) {
        if (height.length == 0 || height.length == 1 || height.length == 2) {
            return 0;
        }
        int left = 0;
        int right = height.length-1;
        int total = 0;
        int currentHeight = Math.min(height[left], height[right]);
        while (left < right) {
            if (height[left] < height[right]) {
                left++;
                if (height[left] < currentHeight) {
                    total += currentHeight - height[left];
                } else {
                    currentHeight = Math.min(height[left], height[right]);
                }
            } else {
                right--;
                if (height[right] < currentHeight) {
                    total+= currentHeight - height[right];
                } else {
                    currentHeight = Math.min(height[left], height[right]);
                }
            }
        }
        return total;
    }
}
```
