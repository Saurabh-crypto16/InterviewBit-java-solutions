```java
//Solution 1
//Bottom up approach
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int m = A.size(),n =A.get(0).size(); 
        int dp[][] = new int[m][n];
        for (int i = m - 1; i >= 0; i--) {
            for (int j = n - 1; j >= 0; j--) {
                if (i == m - 1 && j == n - 1) {
                    //max limit
                    dp[i][j] = 1;
                } else if (i == m - 1) {
                    //in last row
                    if (A.get(i).get(j) < A.get(i).get(j+1) && dp[i][j + 1] != 0) {
                        dp[i][j] = 1 + dp[i][j + 1];
                    }
                } else if (j == n - 1) {
                    //in last column
                    if (A.get(i).get(j) < A.get(i+1).get(j) && dp[i + 1][j] != 0) {
                        dp[i][j] = 1 + dp[i + 1][j];
                    }
                } else {
                    if (A.get(i).get(j) < A.get(i).get(j+1) && dp[i][j + 1] != 0) {
                        dp[i][j] = Math.max(dp[i][j], 1 + dp[i][j + 1]);
                    }
                    if (A.get(i).get(j) < A.get(i+1).get(j) && dp[i + 1][j] != 0) {
                        dp[i][j] = Math.max(dp[i][j], 1 + dp[i + 1][j]);
                    }
                }
            }
        }

        if (dp[0][0] == 0) {
            return -1;
        } else {
            return dp[0][0];
        }
    }
}

//Solution 2
//Top down approach
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int n = A.size();
        int m = A.get(0).size();
        int dp[][] = new int[n][m];
        dp[0][0] = 1;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(dp[i][j] == 0)
                    continue;
                if(i==n-1 && j==m-1)
                    break;
                if(j==m-1){
                    if(A.get(i).get(j) < A.get(i+1).get(j)){
                        dp[i+1][j] = Math.max(dp[i+1][j],dp[i][j] + 1);
                    }
                } else if(i==n-1){
                    if(A.get(i).get(j) < A.get(i).get(j+1)){
                        dp[i][j+1] = Math.max(dp[i][j+1],dp[i][j] + 1);
                    }
                } else{
                    if(A.get(i).get(j) < A.get(i+1).get(j)){
                        dp[i+1][j] = Math.max(dp[i+1][j],dp[i][j] + 1);
                    }
                    if(A.get(i).get(j) < A.get(i).get(j+1)){
                        dp[i][j+1] = Math.max(dp[i][j+1],dp[i][j] + 1);
                    }
                }
            }
        }
        return dp[n-1][m-1]==0?-1:dp[n-1][m-1];
    }
}
```
