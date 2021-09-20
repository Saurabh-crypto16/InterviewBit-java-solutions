```java
public class Solution {
	public int searchInsert(ArrayList<Integer> A, int B) {
		int left=0, right=A.size()-1;
		int ans=A.size();
		while(left<=right){
            int mid=(left+right)/2;
            if(A.get(mid)>=B)    {
				right=mid-1;
				ans=mid;
			}
            else left=mid+1;
        }
		return ans;
	}
}

//or

public class Solution {
    public int searchInsert(ArrayList<Integer> a, int b) {
        
        int low =0, high=a.size()-1;
        
        while(low<=high){
            int mid= low + (high-low)/2;
            
            if(a.get(mid)==b){
                return mid;
            }else if(a.get(mid) > b){
                high=mid-1;
            }else{
                low =mid+1;
            }
        }
        
        return high+1;
    }
}


```
