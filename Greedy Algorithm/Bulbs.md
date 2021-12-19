```java
public class Solution {
    public int bulbs(ArrayList<Integer> A) {
        int[] arr = A.stream().mapToInt(i -> i).toArray();
        int switch_pressed=0;

        for(int i=0;i<A.size();i++){
            //if switch_pressed is odd then flip the curr element
            //1 -> 0 or 0 -> 1
            if(switch_pressed%2!=0){
                arr[i]=1-arr[i];
            }

            //if flipped val is 1 then continue else increment switch_pressed
            if(arr[i]==1)
                continue;
            else
                switch_pressed++;
        }

        return switch_pressed;
    }
}

```
