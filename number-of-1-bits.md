# [Number of 1 bits](https://leetcode.com/problems/number-of-1-bits/description/) [Easy]
Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

Example 1:
```
Input: 11
Output: 3
Explanation: Integer 11 has binary representation 00000000000000000000000000001011
```
Example 2:
```
Input: 128
Output: 1
Explanation: Integer 128 has binary representation 00000000000000000000000010000000
```

## [Java solution](https://leetcode.com/submissions/detail/153027718/)
```
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int weight = 0;
    	while (n != 0) {
    		weight += (n & 1);
    		n = n>>>1;
    	}
    	return weight;

    }
}
```
