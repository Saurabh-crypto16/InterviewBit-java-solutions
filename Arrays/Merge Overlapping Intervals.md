```java
//Using STACK - O(N) space
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
    public ArrayList<Interval> merge(ArrayList<Interval> intervals) {
        Collections.sort(intervals,(p1,p2) -> Integer.compare(p1.start,p2.start));
        
        Stack<Interval> st=new Stack<>();
        for(Interval i: intervals){
            if(st.isEmpty())    st.push(i);
            else{
                if(st.peek().end>=i.start){
                    Interval top=st.pop();
                    top.end=Math.max(i.end,top.end);
                    st.push(top);
                }else{
                    st.push(i);
                }
            }
        }

        ArrayList<Interval> ans=new ArrayList<>();
        while(!st.isEmpty())    ans.add(0,st.pop());
        return ans;
    }
}

public class Solution {
    public ArrayList<Interval> merge(ArrayList<Interval> intervals) {
        //ascending sort based on start
        Collections.sort(intervals,new Comparator<Interval>(){
            @Override
            public int compare(Interval a, Interval b)
            {
                return a.start-b.start;
            }
        });
      
        ArrayList<Interval> res = new ArrayList<Interval>();
        int start=intervals.get(0).start;
        int end=intervals.get(0).end;
        for(int i=1;i<intervals.size();i++)
        {
            if(intervals.get(i).start<=end)
            {
                end=Math.max(intervals.get(i).end,end);
            }
            else
            {
                res.add(new Interval(start,end));
                start=intervals.get(i).start;
                end=intervals.get(i).end;
            }
        }
        res.add(new Interval(start,end));
        
        return res;
    }
}
```
