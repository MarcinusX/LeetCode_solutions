# [Partition Labels](https://leetcode.com/problems/partition-labels/description/) [Medium]

A string `S` of lowercase letters is given. We want to partition this string into as many parts as possible so that each letter appears in at most one part, and return a list of integers representing the size of these parts.

Example 1:
```
Input: S = "ababcbacadefegdehijhklij"
Output: [9,7,8]
Explanation:
The partition is "ababcbaca", "defegde", "hijhklij".
This is a partition so that each letter appears in at most one part.
A partition like "ababcbacadefegde", "hijhklij" is incorrect, because it splits S into less parts.
```
Note:

`S` will have length in range `[1, 500]`.  
`S` will consist of lowercase letters (`'a'` to `'z'`) only.

## [Java solution](https://leetcode.com/submissions/detail/146531200/)
```
class Solution {
    public List<Integer> partitionLabels(String S) {
        if (S.isEmpty()) {
            return new ArrayList<>();
        }
        int[][] boundries = new int[26][2];
        for (int i = 0; i < 26; i++) {
            boundries[i][0] = -1;
            boundries[i][1] = -1;
        }
        
        for (int i = 0; i < S.length(); i++) {
            int letterIndex = S.charAt(i) - 'a';
            if (boundries[letterIndex][0] == -1) {
                boundries[letterIndex][0] = i;
            }
            boundries[letterIndex][1] = i;
        }
        
        List<Integer> result = new ArrayList<>();
        int min = 0;
        int max = boundries[S.charAt(0) - 'a'][1];
        for (int i = 0; i < S.length(); i++) {
            if (boundries[S.charAt(i) - 'a'][1] > max) {
                max = boundries[S.charAt(i) - 'a'][1];
            }
            if (i == max) {
                result.add(max-min+1);
                min = i+1;
            }
        }
        return result;
        
    }
}
```
