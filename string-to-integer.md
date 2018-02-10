# [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/description/) [Medium]

Implement atoi to convert a string to an integer.

**Hint:** Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes:** It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

**Requirements for atoi:**

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.

## [Java solution](https://leetcode.com/submissions/detail/140261538/)
```
class Solution {
    public int myAtoi(String str) {
        long result = 0;
        boolean isNegative = false;
        int index = 0;
        
        while (index < str.length() && str.charAt(index) == ' ') {
            index++;
        }
        
        if (index == str.length()) {
            return 0;
        }
        
        if (str.charAt(index) == '-') {
            isNegative = true;
            index++;
        } else if (str.charAt(index) == '+') {
            index++;
        }
        
        if (index == str.length()) {
            return 0;
        }
        
        while (index < str.length() && isDigit(str.charAt(index)) && result <= 2147483647) {
            result *= 10;
            result += str.charAt(index) - '0';
            index++;
        }
        
        if (isNegative) {
            result = -result;
        }
        
        if (result > 2147483647) {
            result = 2147483647;
        } else if (result < -2147483648) {
            result = -2147483648;
        }
        
        return (int) result;
        
    }
    
    // or  c > '0' && c < '9'
    private boolean isDigit(char c) {
        switch (c) {
            case '0':
            case '1':
            case '2':
            case '3':
            case '4':
            case '5':
            case '6':
            case '7':
            case '8':
            case '9':
                return true;
            default: return false;
        }
    }
}
```
