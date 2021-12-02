```java
public class Solution {
    public int solve(int[] A, int B) {
        HashMap<Integer,Integer> map=new HashMap<>();
        for(int i=0;i<A.length;i++){
            map.put(A[i],i);
        }

        int ans=0;
        for(int i=0;i<A.length;i++){
            if(map.containsKey(A[i]^B) && i!=map.get(A[i]^B)){
                ans++;
            }
        }
        return ans/2;
    }
}

```
