```java
/*
Brute force : at any index i amount of water stored =
        Min(Max_height(0,i-1),Max_height(i+1,n))-h[i]
        
In efficient way we use 2 pointer to use the same formula
at any index left we fill water on it only if we make sure there is height>=h[left] and vice versa
for right
*/

public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int trap(final List<Integer> A) {
        if(A.size()<=0) return 0;
        int left=0, right=A.size()-1, leftmax=0, rightmax=0, ans=0;

        while(left<=right){
            if(A.get(left)<=A.get(right)){
                if(A.get(left)>=leftmax)  leftmax=A.get(left);
                else    ans+=(leftmax-A.get(left));
                left++;
            }else{
                if(A.get(right)>=rightmax)  rightmax=A.get(right);
                else    ans+=(rightmax-A.get(right));
                right--;
            }
        }

        return ans;
    }
}
```
