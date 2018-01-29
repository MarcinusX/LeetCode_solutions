# [Reverse Integer](https://leetcode.com/problems/reverse-integer/description/) [Easy]

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**
```
Input: 123
Output:  321
```
**Example 2:**
```
Input: -123
Output: -321
```
**Example 3:**
```
Input: 120
Output: 21
```
**Note:**

Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## [Java solution](https://leetcode.com/submissions/detail/138084682/)
```
class Solution {
    public int reverse(int x) {
        boolean isNegative = x < 0;
        if (isNegative) {
            x=-x;
        }
        int result = x%10;
        x= x/10;
        while (x != 0) {
            long test = (long) 10*result+x%10;
            if (test > Integer.MAX_VALUE || test<Integer.MIN_VALUE) {
                return 0;
            } else {
                result = (int) test;
            }
            x=x/10;
        }
        if (isNegative) {
            result = -result;
        }
        return result;
    }
}
```
