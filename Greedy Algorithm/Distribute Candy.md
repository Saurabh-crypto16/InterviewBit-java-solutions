```java
public class Solution {
    public int candy(ArrayList<Integer> A) {
        int left[]=new int[A.size()];
        int right[]=new int[A.size()];
        Arrays.fill(left,1);
        Arrays.fill(right,1);

        /*left[i] will containe min no of candies to satisfy the condition from left*/
        for(int i=1;i<A.size();i++){
            if(A.get(i)>A.get(i-1)){
                left[i]=(left[i-1]+1);
            }
        }

        /*right[i] will containe min no of candies to satisfy the condition from right*/
        for(int i=A.size()-2;i>=0;i--){
            if(A.get(i)>A.get(i+1)){
                right[i]=(right[i+1]+1);
            }
        }

        //max of left[i] and right[i] contains the optimal val at i
        for(int i=0;i<left.length;i++){
            left[i]=Math.max(left[i],right[i]);
        }
        
        int ans=0;
        for(int i: left)    ans+=i;
        return ans;
    }
}

```
