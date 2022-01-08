```java
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int n = A.size(), mo = Integer.MIN_VALUE;
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        
        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (A.get(i).get(0) > A.get(j).get(1)) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
                mo = Math.max(mo, dp[i]);
            }
        }
        
        return mo;
    }
}

```
