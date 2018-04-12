# [Multiply Strings](https://leetcode.com/problems/multiply-strings/description/) [Medium]
Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`.

Note:

The length of both `num1` and `num2` is < `110`.  
Both `num1` and `num2` contains only digits `0-9`.  
Both `num1` and `num2` does not contain any leading zero.  
**You must not use any built-in BigInteger library or convert the inputs to integer directly.**

## [Java solution](https://leetcode.com/submissions/detail/149691130/)
```
class Solution {
    
    public String multiply(String num1, String num2) {
        if (num1.equals("0") || num2.equals("0")) {
            return "0";
        }
        
        int n = num1.length();
        int m = num2.length();
        int length = n+m-1;
        int[] result = new int[length];
        
        for (int i = 0; i < n; i++) {
            for(int j =0; j < m; j++) {
                result[i+j] += (num1.charAt(n-i-1)-'0') * (num2.charAt(m-j-1)-'0');
            }
        }
        
        for(int i=0; i< length-1; i++) {
            result[i+1] += result[i]/10;
            result[i] = result[i] % 10;
        }
        int carry = result[length-1]/10;
        result[length-1] = result[length-1] % 10;
        
        StringBuilder sb = new StringBuilder();
        if (carry != 0) {
            sb.append(carry);
        }
        for (int i = result.length-1; i>-1; i--) {
            sb.append(result[i]);
        }
        return sb.toString();
    }
}
```
