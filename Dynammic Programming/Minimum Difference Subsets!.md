```java
public class Solution {
    public int solve(ArrayList<Integer> A) {
        int n=A.size();
        int k=0;
        for(int a: A)   k+=a;
        boolean dp[][]=new boolean[n][k+1];

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

        //checking for each subset sum difference
        int min=Integer.MAX_VALUE;
        for(int i=0;i<=k;i++){
            if(dp[n-1][i]){
                int s1=i;
                int s2=k-i;
                min=Math.min(min,Math.abs(s2-s1));
            }
        }

        return min;
    }
}

```
