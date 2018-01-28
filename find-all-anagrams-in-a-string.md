# [Find All Anagrams in a String](https://leetcode.com/problems/palindrome-number/description/) [Easy]

Given a string **s** and a **non-empty** string **p**, find all the start indices of **p**'s anagrams in **s**.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 20,100.

The order of output does not matter.

**Example 1:**
```
Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```
**Example 2:**
```
Input:
s: "abab" p: "ab"

Output:
[0, 1, 2]

Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```
## [Java solution](https://leetcode.com/submissions/detail/134602941/)
```
import java.util.*;

class Solution {
    public List<Integer> findAnagrams(String s, String p) {
       List<Integer> wynik = new ArrayList<>();
            HashMap<Character, Integer> map = new HashMap<>();
            for (char c : p.toCharArray()) {
                map.put(c, map.get(c) == null ? 1 : map.get(c)+1);
            }
            int ileZnakow = p.length();
            int ilePasuje = 0;
            int ujemnych = 0;
            for (int i=0; i<s.length(); i++) {
                char c = s.charAt(i);
                Integer val = map.get(c);
                if (val != null) {
                    ilePasuje++;
                    map.put(c, val-1);
                    if (map.get(c) < 0) {
                        ujemnych++;
                    }
                }
                if (i > ileZnakow-1) {
                    char c2 = s.charAt(i-ileZnakow);
                    Integer val2 =map.get(c2);
                    if (val2 != null) {
                        ilePasuje--;
                        map.put(c2, val2+1);
                        if (map.get(c2) <= 0) {
                            ujemnych--;
                        }
                    }
                }
                if (ilePasuje == ileZnakow && ujemnych==0) {
                    wynik.add(i-ileZnakow+1);
                }
            }
            return wynik;
    }
}
```
