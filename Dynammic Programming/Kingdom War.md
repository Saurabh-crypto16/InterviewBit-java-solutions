```java
/*
Start from bottom right cell
at each cell dp(i,j) = A(i,j)+dp(i+1,j)+dp(i,j+1)-dp(i+1,j+1)
find max of all dp cells
*/

public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int n=A.size(),m=A.get(0).size();
        
        int dp[][]=new int[n+1][m+1];
        int ans=Integer.MIN_VALUE;

        for(int i=n;i>=0;i--){
            for(int j=m;j>=0;j--){
                if(i==n || j==m){
                    continue;
                }
                dp[i][j]=A.get(i).get(j)+dp[i+1][j]+dp[i][j+1]-dp[i+1][j+1];
                ans=Math.max(ans,dp[i][j]);
            }
        }

        return ans;
    }
}

```
