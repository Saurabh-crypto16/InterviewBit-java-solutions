```java
public class Solution {
    public int solve(ArrayList<Integer> A) {
        HashMap<Integer,Integer> map=new HashMap<>();
        int ans=-1,ans_pos=Integer.MAX_VALUE;
        for(int i=0;i<A.size();i++){
            if(map.containsKey(A.get(i))){
                if(map.get(A.get(i))<ans_pos){
                    ans=A.get(i);
                    ans_pos=map.get(A.get(i));
                }
            }
            map.put(A.get(i),i);
        }

        return ans_pos==Integer.MAX_VALUE ? -1 : ans;
    }
}
```
