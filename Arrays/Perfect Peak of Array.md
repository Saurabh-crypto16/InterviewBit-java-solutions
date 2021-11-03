```java
public class Solution {
    public int perfectPeak(ArrayList<Integer> A) {
        int n=A.size();
        int l_max[]=new int[n];
        int r_min[]=new int[n];
        l_max[0]=-1;
        r_min[n-1]=-1;

        int max=A.get(0);
        for(int i=1;i<n;i++){
            max=Math.max(max,A.get(i-1));
            l_max[i]=max;
        }
        int min=A.get(n-1);
        for(int i=n-2;i>=0;i--){
            min=Math.min(min,A.get(i+1));
            r_min[i]=min;
        }

        for(int i=1;i<n-1;i++){
            if(A.get(i)>l_max[i] && A.get(i)<r_min[i])  return 1;
        }
        return 0;
    }
}

```
