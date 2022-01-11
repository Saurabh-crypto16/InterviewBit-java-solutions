```java
public class Solution {
    public int jump(ArrayList<Integer> A) {
        int maxR=A.get(0);  //max reachability from current i
        int steps=A.get(0);  //number of allowed steps
        int jump=1; //number of jumps till now

        if(A.size()==1) return 0;
        if(A.get(0)==0) return -1;

        for(int i=1;i<A.size();i++){
            //reached last index
            if(i==A.size()-1){
                return jump;
            }

            //if we didnt reach end of array 1 steps will be decremented
            maxR=Math.max(maxR,i+A.get(i));
            steps--;

            //if we can't take any more stepss
            if(steps==0){
                jump++;
                if(i>=maxR){
                    return -1;
                }
                steps=maxR-i;
            }
        }

        return -1;
    }
}

```
