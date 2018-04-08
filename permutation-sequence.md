# [Permutation Sequence](https://leetcode.com/problems/permutation-sequence/description/) [Medium]

The set `[1,2,3,…,n]` contains a total of n! unique permutations.

By listing and labeling all of the permutations in order,  
We get the following sequence (ie, for n = 3):
```
"123"
"132"
"213"
"231"
"312"
"321"
```
Given n and k, return the kth permutation sequence.

Note: Given n will be between 1 and 9 inclusive.

## [Java solution](https://leetcode.com/submissions/detail/149026862/)
```
class Solution {
    int[] factorial = new int[]{1, 2, 6, 24, 120, 720, 5040, 40320, 362880};
    public String getPermutation(int n, int k) {
        StringBuilder builder = new StringBuilder(n);
        k--;
        
        List<Integer> availableDigits = new ArrayList<>();
        for (int i = 1; i < 10; i++) {
            availableDigits.add(i);
        }
        while (n > 1) {
            int numberIndex = k / factorial[n-2];
            int number = availableDigits.remove(numberIndex);
            builder.append(Integer.toString(number));
            k = k % factorial[n-2];
            n--;
        }
        
        builder.append(Integer.toString(availableDigits.get(0)));
        return builder.toString();
    }
}
```
