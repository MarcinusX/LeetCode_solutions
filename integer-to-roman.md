# [Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/) [Medium]

Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.


## [Java Solution](https://leetcode.com/submissions/detail/140023310/)
```
class Solution {
    static String digit1[] = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};
    static String digit2[] = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
    static String digit3[] = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
    static String digit4[] = {"", "M", "MM", "MMM"};
    
    public String intToRoman(int num) {    
        StringBuilder builder = new StringBuilder(digit4[num/1000]);
        num = num % 1000;
        builder.append(digit3[num/100]);
        num = num % 100;
        builder.append(digit2[num/10]);
        num = num % 10;
        builder.append(digit1[num]);
        
        return builder.toString();
    }
}
```
