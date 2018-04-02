# [Merge Intervals](https://leetcode.com/problems/merge-intervals/description/) [Medium]

Given a collection of intervals, merge all overlapping intervals.

For example,  
Given `[1,3],[2,6],[8,10],[15,18]`,  
return `[1,6],[8,10],[15,18]`.

## [Java solution](https://leetcode.com/submissions/detail/148138114/)
```
/**
 * Definition for an interval.
 * public class Interval {
 *     int start;
 *     int end;
 *     Interval() { start = 0; end = 0; }
 *     Interval(int s, int e) { start = s; end = e; }
 * }
 */
class Solution {
    public List<Interval> merge(List<Interval> intervals) {
        if (intervals == null || intervals.isEmpty() || intervals.size() == 1) {
            return intervals;
        }
        int[] starts = new int[intervals.size()];
        int[] ends = new int[intervals.size()];
        for (int i = 0; i < intervals.size(); i++) {
            starts[i] = intervals.get(i).start;
            ends[i] = intervals.get(i).end;
        }
        
        Arrays.sort(starts);
        Arrays.sort(ends);
        
        int start = starts[0];
        
        List<Interval> results = new ArrayList<>();
        
        for (int i = 1; i < starts.length; i++) {
            if (starts[i] > ends[i-1]) {
                results.add(new Interval(start, ends[i-1]));
                start = starts[i];
            }
        }
        results.add(new Interval(start, ends[ends.length-1]));
        return results;
    }
}
```
