```java
/*
No of unique paths if there is no obstacle is (m+n-2)C(m-1) or (m+n-2)C(n-1)

int N=m+n-2,R=m-1;
double res=1;
for(int i=1;i<=R;i++){
    res*=((N-R+i)/i);
}
return (int)res;
*/
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
