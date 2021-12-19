```java
public class Solution {
    public int maxp3(ArrayList<Integer> A) {
        int max1=Integer.MIN_VALUE,max2=max1,max3=max1;
        int min1=Integer.MAX_VALUE,min2=min1;

        for(int i: A){
            if(i>max1){
                max3=max2;
                max2=max1;
                max1=i;
            }else if(i>max2){
                max3=max2;
                max2=i;
            }else if(i>max3){
                max3=i;
            }
            
            if(i<min1){
                min2=min1;
                min1=i;
            }else if(i<min2){
                min2=i;
            }
        }

        return Math.max(min1*min2*max1,max1*max2*max3);
    }
}

```
