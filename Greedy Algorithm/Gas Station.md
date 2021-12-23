```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int canCompleteCircuit(final List<Integer> A, final List<Integer> B) {
        int S=B.size();
        int total_surplus=0,surplus=0,start_idx=0;

        //an answer always exists so we just need to find the start idx
        for(int i=0;i<A.size();i++){
            total_surplus+=(A.get(i)-B.get(i));
            surplus+=(A.get(i)-B.get(i));

            //the idx where gas[i] > cost[i] will be answer
            if(surplus<0){
                start_idx=i+1;
                surplus=0;
            }
        }

        return (total_surplus<0) ? -1 : start_idx;
    }
}

```
