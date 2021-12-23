```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int majorityElement(final List<Integer> A) {
        int majority=0;
        int count=0;

        for(int i: A){
            if(majority==i){
                count++;
            }else{
                count--;
            }

            if(count<=0){
                majority=i;
                count=1;
            }
        }

        return majority;
    }
}

```
