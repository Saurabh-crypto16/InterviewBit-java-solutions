```java
/**
 * Definition for an interval.
 * public class Interval {
 *     int start;
 *     int end;
 *     Interval() { start = 0; end = 0; }
 *     Interval(int s, int e) { start = s; end = e; }
 * }
 */
public class Solution {
  public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {
    ArrayList<Interval> result = new ArrayList<>();
    for (int i = 0; i < intervals.size(); i++) {
      Interval interval = intervals.get(i);
      if (interval.end < newInterval.start) {
        result.add(interval);
      } else if (newInterval.end < interval.start) {
        result.add(newInterval);
        result.addAll(intervals.subList(i, intervals.size()));
        return result;
      } else {
        int start = Math.min(newInterval.start, interval.start);
        int end = Math.max(newInterval.end, interval.end);
        newInterval.start = start;
        newInterval.end = end;
      }
    }

    result.add(newInterval);

    return result;
  }
}

//OR

public class Solution{

Comparator<Interval> inRangeCompA = (a, b) -> {
    return (a.end < b.start ) ? -1 : ((a.start > b.end) ? 1 : 0); 
};

public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {
    Interval newStart = new Interval(newInterval.start, newInterval.start);
    int i = Collections.binarySearch(intervals, newStart, inRangeCompA);
    if(i < 0){
        i = -(i+1);
        intervals.add(i, newStart);
    }
    Interval newEnd = new Interval(newInterval.end, newInterval.end);
    int j = Collections.binarySearch(intervals, newEnd, inRangeCompA);
    if(j < 0){
        j = -(j+1);
        intervals.add(j, newEnd);
    } 
    if(i != j){
        Interval v = intervals.get(i);
        v.end = intervals.get(j).end;
        intervals.set(i, v);
        intervals.subList(i+1, j+1).clear();
    }
    return intervals;
}
}

```
