```java
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int m = A.size();
        int n = A.get(0).size();
        int[][] dp = new int[m][n];
        
        //copying last row of matrix
        for (int i = 0; i < n; i++) {
            dp[m - 1][i] = A.get(m - 1).get(i);
        }
        
        for (int i = m - 2; i >= 0; i--) {
            for (int j = 0; j <= i; j++) {
                dp[i][j] = A.get(i).get(j) + Math.max(dp[i + 1][j], dp[i + 1][j + 1]);
            }
        }
        
        return dp[0][0];
    }
}

```
