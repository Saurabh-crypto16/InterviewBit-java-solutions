```java
public class Solution {
    public ArrayList<Integer> solve(ArrayList<Integer> A, int B) {
        PriorityQueue<Integer> pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i: A){
            pq.add(i);
        }

        ArrayList<Integer> ans=new ArrayList<>();
        while(B>0){
            ans.add(pq.remove());
            B--;
        }

        return ans;
    }
}
```
