```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int maxProfit(final List<Integer> A) {
        int maxProfit=0;
        for(int i=1;i<A.size();i++){
            if(A.get(i)>A.get(i-1)){
                maxProfit+=(A.get(i)-A.get(i-1));
            }
        }
        return maxProfit;
    }
}

```
