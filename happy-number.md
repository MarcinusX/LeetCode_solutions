# [Happy Number](https://leetcode.com/problems/happy-number/description/) [Easy]

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example: 
```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

## [Java solution](https://leetcode.com/submissions/detail/152771872/)
```
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> numbers = new HashSet<>();
        return isHappy(n, numbers);
    }
    
    private boolean isHappy(int n, Set<Integer> numbers) {
        if (numbers.contains(n)) {
            return false;
        }
        if (n == 1) {
            return true;
        }
        numbers.add(n);
        int newNumber = 0;
        while (n > 0) {
            int digit = n % 10;
            newNumber += (digit * digit);
            n /= 10;
        }
        return isHappy(newNumber, numbers);
    }
}
```
