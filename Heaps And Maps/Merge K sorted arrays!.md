```java
public class Solution {
    public ArrayList<Integer> solve(ArrayList<ArrayList<Integer>> A) {
        PriorityQueue<Integer> pq=new PriorityQueue<>();
        for(ArrayList<Integer> al: A){
            for(int i: al){
                pq.add(i);
            }
        }

        ArrayList<Integer> ans=new ArrayList<>();
        while(!pq.isEmpty()){
            ans.add(pq.remove());
        }

        return ans;
    }
}

```
