# [Roman to Integer](https://leetcode.com/problems/roman-to-integer/description/) [Easy]

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

## [Java solution](https://leetcode.com/submissions/detail/138295128/)

```
class Solution {
    public int romanToInt(String s) {
        int total=0;
        int lastNumber = calc(s.charAt(0));
        for (int i=1; i<s.length(); i++) {
            int currentDigit = calc(s.charAt(i));
            if (currentDigit > lastNumber) {
                total -= lastNumber;
            } else {
                total += lastNumber;
            }
            lastNumber = currentDigit;
        }
        total += lastNumber;
        return total;
    }
    
    private int calc(char c) {
        switch(c) {
            case 'I':
                return 1;
            case 'V':
                return 5;
            case 'X':
                return 10;
            case 'L':
                return 50;
            case 'C':
                return 100;
            case 'D':
                return 500;
            default:
                return 1000;
        }
    }
}
```
