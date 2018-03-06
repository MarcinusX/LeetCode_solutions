# [Pascal's Triangle ||](https://leetcode.com/problems/pascals-triangle-ii/description/) [Easy]

Given an index k, return the kth row of the Pascal's triangle.

For example, given `k = 3`,  
Return `[1,3,3,1]`.

**Note:**  
Could you optimize your algorithm to use only O(k) extra space?

## [Java solution](https://leetcode.com/submissions/detail/143684865/)
```
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        res.add(1);

        if (rowIndex == 0) {
            return res;
        }
        
        for (int row = 1; row < rowIndex; row++) {
            res.add(0, 1);
            for (int i = 0; i < res.size()-1; i++) {
                res.set(i, res.get(i) + res.get(i+1));
            }
        }
        
        res.add(0,1);
        return res;
    }
}
```
