# [Container With Most Water](https://leetcode.com/problems/container-with-most-water/description/) [Medium]

Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

## [Java Solution](https://leetcode.com/submissions/detail/141311408/)
```
class Solution {
    public int maxArea(int[] heights) {
        int maxArea = 0;
        int start = 0;
        int end = heights.length-1;
        while (start < end) {          
            int area = (end-start) * Math.min(heights[start], heights[end]);
            if (area > maxArea) {
                maxArea = area;
            }
            if (heights[start] > heights[end]) {
                end--;
            } else {
                start++;
            }
        }
        return maxArea;
    }
}
```
