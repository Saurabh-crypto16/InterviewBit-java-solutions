```java
/*
A =[ 3,    6,       9,           12     ]
dp=[[:], [3:1], [6:1,3:2], [9:1,6:1,3:2]]
*/
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int solve(final List<Integer> A) {
        if(A.size()==1) return 1;
        
        HashMap<Integer,Integer>[] dp=new HashMap[A.size()];
        int ans=1;

        for(int i=0;i<A.size();i++){
            int currEle=A.get(i);
            dp[i]=new HashMap<>();
            HashMap<Integer,Integer> currMap=dp[i];
            
            for(int j=0;j<i;j++){
                int diff=currEle-A.get(j);
                HashMap<Integer,Integer> prevMap=dp[j];
                //finding similar diff sequence length in previous array
                int newVal=prevMap.getOrDefault(diff,0)+1;
                
                currMap.put(diff,newVal);
                dp[i]=currMap;
                
                ans=Math.max(ans,currMap.get(diff));
            }
        }

        return ans+1;
    }
}

```
