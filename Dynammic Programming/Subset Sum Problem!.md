```java
public class Solution {
    public int solve(ArrayList<Integer> A, int k) {
        int n=A.size();
        boolean dp[][]=new boolean[n][k+1];
        Collections.sort(A);

        for(int i=0;i<n;i++)    dp[i][0]=true;
        dp[0][A.get(0)]=true;

        //creating dp for target subset sum existence
        for(int ind=1;ind<n;ind++){
            for(int target=1;target<=k;target++){
                boolean notTake=dp[ind-1][target];
                boolean take=false;
                if(A.get(ind)<=target){
                    take=dp[ind-1][target-A.get(ind)];
                }
                dp[ind][target]=take|notTake;
            }
        }

        return dp[A.size()-1][k] ? 1 : 0;
    }
}
```
