```java

public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        int left=0,right=A.size()-1, ans=0;
        if(A.get(right)<=B) return A.size();
        while(left<=right){
            int mid=left+(right-left)/2;
            if(A.get(mid)>B)    right=mid-1;
            else{
                ans=mid+1;
                left=mid+1;
            }
        }
        return ans;
    }
}
```
