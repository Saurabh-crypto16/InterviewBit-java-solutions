```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int solve(final List<Integer> A) {
        int sum = 0;
        for (Integer e : A ) {
            sum += e;
        }
        
        int n = A.size();
        sum = sum/2;
        int dp[][] = new int[n+1][sum + 1];
        
        for (int i=1; i<=sum; i++)
            dp[0][i] = Integer.MAX_VALUE;
            
        for (int i=1; i<=n; i++) {
           for (int j=0; j<=sum; j++) {
                dp[i][j] = dp[i-1][j];
                int val = A.get(i-1);
                if (j >= val && dp[i-1][j-val] != Integer.MAX_VALUE) {
                    dp[i][j] = Math.min(dp[i][j], 1 + dp[i-1][j-val]);
                }
           }
        }

        while (dp[n][sum] == Integer.MAX_VALUE) {
           sum--;
        }

        return dp[n][sum];
    }
}
```
