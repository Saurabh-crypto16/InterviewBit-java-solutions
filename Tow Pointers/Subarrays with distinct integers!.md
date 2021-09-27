```java
public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        return lessThanEqualToK(A,B)-lessThanEqualToK(A,B-1);
    }
    public int lessThanEqualToK(ArrayList<Integer> A, int B){
        int ans=0,start=0,end=0,n=A.size();
        Map<Integer,Integer> map=new HashMap<>();
        while(end<n){
            //if a unique element is added
            if(map.getOrDefault(A.get(end),0)==0)   B--;
            map.put(A.get(end),map.getOrDefault(A.get(end),0)+1);

            //removing elements if more than k and sliding start to start+1
            while (B < 0) {
                map.put(A.get(start), map.getOrDefault(A.get(start), 0) - 1);
                if (map.get(A.get(start)) == 0) {
                    B++;
                }
                start++;
            }

            //counting ans
            ans += (end - start + 1);
            end++;
        }
        return ans; 
    }
}

```
