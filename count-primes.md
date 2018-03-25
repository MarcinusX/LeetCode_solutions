# [Count Primes](https://leetcode.com/problems/count-primes/description/) [Easy]

Count the number of prime numbers less than a non-negative number, **n**.

## [Java solution](https://leetcode.com/submissions/detail/146782689/)
```
class Solution {
    
    public int countPrimes(int n) {
        if (n == 0 || n == 1 || n == 2) {
            return 0;
        }
        
        int counter = 0;
        boolean[] sieve = new boolean[n];
        int sqrt = (int)Math.sqrt(n)+1;
        for (long i = 2L; i < n; i++) {
            if (!sieve[(int)i]) {
                counter++;
                for (long j = i*i; j < n; j += i) {
                    sieve[(int)j] = true;
                }
            }
        }
        
        return counter;
        
    }
}
```
