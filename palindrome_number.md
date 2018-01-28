# [Palindrome Number](https://leetcode.com/problems/palindrome-number/description/) [Easy]

Determine whether an integer is a palindrome. Do this without extra space.

## [Java solution](https://leetcode.com/submissions/detail/138088462/)
```
class Solution {
    public boolean isPalindrome(int x) {
        if (x<0) {
            return false;
        }
        List<Integer> digits = new ArrayList<>();
        while (x != 0) {
            digits.add(x%10);
            x/=10;
        }
        int end=digits.size()-1;
        int start=0;
        while (end>start) {
            if (digits.get(end)!=digits.get(start)) {
                return false;
            } else {
                end--;
                start++;
            }
        }
        return true;
    }
}
```
