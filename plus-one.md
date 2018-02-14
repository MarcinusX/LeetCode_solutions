# [Plus One](https://leetcode.com/problems/plus-one/description/) [Easy]

Given a non-negative integer represented as a **non-empty** array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.

## [Java Solution](https://leetcode.com/submissions/detail/140892314/)

```
class Solution {
    public int[] plusOne(int[] digits) {
        int index = digits.length - 1;
        while (index >= 0) {
            if (digits[index] == 9) {
                digits[index] = 0;
                index--;
            } else {
                digits[index] = digits[index]+1;
                return digits;
            }
        }
        
        if (digits[0] == 0) {
            int[] result = new int[digits.length+1];
            result[0]=1;
            return result;
        } else {
            return digits;
        }
        
    }
}
```
