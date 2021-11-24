```java
public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        PriorityQueue<Integer> pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i: A){
            pq.add(i);
        }

        int ans=0;
        while(B-->0){
            int rem=pq.remove();
            ans+=rem;
            if(rem>0){
                pq.add(rem-1);
            }
        }

        return ans;
    }
}
```
