```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int maxProfit(final List<Integer> A) {
        int maxProfit=0;
        
        if(A.size()<=1){
            return maxProfit;
        }

        int min_price=A.get(0);
        for(int i=1;i<A.size();i++){
            if(min_price<A.get(i)){
                maxProfit=Math.max(maxProfit,A.get(i)-min_price);
            }
            min_price=Math.min(min_price,A.get(i));
        }

        return maxProfit;
    }
}

```
