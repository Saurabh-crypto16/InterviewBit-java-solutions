```java
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int n=A.size(),m=A.get(0).size();
        int dp[][]=new int[n][m];
        int ans=0;

        for(int i=n-1;i>=0;i--){
            for(int j=m-1;j>=0;j--){
                if(i==n-1 || j==m-1){
                    dp[i][j]=A.get(i).get(j);
                }else{
                    if(A.get(i).get(j)==0){
                        dp[i][j]=0;
                    }else{
                        dp[i][j]=Math.min(dp[i+1][j+1],Math.min(dp[i][j+1],dp[i+1][j]))+1;
                    }
                }
                ans=Math.max(ans,dp[i][j]);
            }
        }

        return ans*ans;
    }
}

```
