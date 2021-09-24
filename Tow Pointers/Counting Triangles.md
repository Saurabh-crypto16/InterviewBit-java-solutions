```java
/*
Following property should satisfy:
1.a+b>c
2.b+c>a
3.c+a>b

Sort the array then start i with max value and put two pointers at right=i-1 and left=0 and 
if A[left]+A[right]>A[i] then for all (right-left) indices the property will hold.
*/

public class Solution {
    public int nTriang(ArrayList<Integer> A) {
        Collections.sort(A);
        long ans=0;
        int mod = 1000000007;
        for(int k=A.size()-1;k>=2;k--){
            int left=0,right=k-1;
            while(left<right){
                if(A.get(left)+A.get(right)>A.get(k)){
                    ans=(ans%mod+(right-left)%mod)%mod;
                    right--;
                }else{
                    left++;
                }
            }
        }
        return (int)ans%mod;
    }
}

```
