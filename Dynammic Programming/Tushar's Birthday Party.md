```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int solve(final List<Integer> A, final List<Integer> B, final List<Integer> C) {
        int max=Integer.MIN_VALUE;
        for(int i: A){
            max=Math.max(max,i);
        }

        //using knapsack approach
        int dp[]=new int[max+1];
        Arrays.fill(dp,Integer.MAX_VALUE);
        dp[0]=0;
        
        for(int i=1;i<=max;i++){
            for(int j=0;j<B.size();j++){
                //filling cap should be less than or equal to eating capacity
                if(i>=B.get(j)){
                    dp[i]=Math.min(dp[i],C.get(j)+dp[i-B.get(j)]);
                }
            }
        }

        //adding ans only for capacity of all friends
        int ans=0;
        for(int i: A){
            ans+=dp[i];
        }

        return ans;
    }
}

```
