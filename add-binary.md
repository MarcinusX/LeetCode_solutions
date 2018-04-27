# [Add Binary](https://leetcode.com/problems/add-binary/description/) [Easy]
Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.

Example 1:
```
Input: a = "11", b = "1"
Output: "100"
```
Example 2:
```
Input: a = "1010", b = "1011"
Output: "10101"
```

## [Java solution](https://leetcode.com/submissions/detail/151829754/)
```class Solution {
    public String addBinary(String a, String b) {
        String longer = a;
        String shorter = b;
        if (longer.length() < shorter.length()) {
            longer = b;
            shorter = a;
        }
        
        char[] array = new char[longer.length()];
        boolean carry = false;
        
        for (int i = 0; i < longer.length(); i++) {
            int index = longer.length()-1-i;
            
            char c1 = longer.charAt(index);
            char c2 = '0';
            if (i < shorter.length()) {
                c2 = shorter.charAt(shorter.length()-1-i);
            }
            
            if (c1 != c2) {
                array[index] = carry ? '0' : '1';
            } else if (c1 == '1') {
                if (carry) {
                    array[index] = '1';
                } else {
                    array[index] = '0';
                    carry = true;
                }
            } else {
                array[index] = carry ? '1':'0';
                carry = false;
            }  
        }
        String start = carry ? "1" : "";
        return new StringBuilder(start).append(array).toString();
    }
}
```
