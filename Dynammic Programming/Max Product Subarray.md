```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int maxProduct(final List<Integer> arr) {
        int A[]=new int[arr.size()];
        for(int i=0;i<A.length;i++){
            A[i]=arr.get(i);
        }
        int n = A.length, ans = A[0], pmax = A[0], pmin = A[0];
        for (int i = 1; i < n; i++) {
            int cmax = Math.max(A[i], Math.max(pmax * A[i], pmin * A[i]));
            int cmin = Math.min(A[i], Math.min(pmax * A[i], pmin * A[i]));
            ans = Math.max(ans, cmax);
            pmax = cmax;
            pmin = cmin;
        }
        return ans;
    }
}
```
