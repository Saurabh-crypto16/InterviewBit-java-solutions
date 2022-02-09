```java
public class Solution {
    public int uniquePathsWithObstacles(ArrayList<ArrayList<Integer>> A) {
        int m=A.size(),n=A.get(0).size();
        int dp[][]=new int[m][n];
        for(int d[]: dp){
            Arrays.fill(d,-1);
        }

        return paths(0,0,m-1,n-1,A,dp);
    }
    public int paths(int i,int j,int m,int n,ArrayList<ArrayList<Integer>> A,int[][] dp){
        if(i>m || j>n || A.get(i).get(j)==1)  return 0;
        if(i==m && j==n)    return 1;

        if(dp[i][j]!=-1)    return dp[i][j];
        return paths(i+1,j,m,n,A,dp)+paths(i,j+1,m,n,A,dp);
    }
}

```
