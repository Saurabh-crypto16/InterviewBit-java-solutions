```java
/*
take a ans_pointer at start of array and loop through the elements and whenever we get number not equal to b 
wap it with ans_pointer and increment ans_pointer 
*/

public class Solution {
	public int removeElement(ArrayList<Integer> a, int b) {
        if(a.size()==0) return 0;
        int ans=0, n=a.size();
        for(int i=0;i<n;i++){
            if(a.get(i)!=b){
                Collections.swap(a,ans,i);
                ans++;
            }
        }
        return ans;
	}
}

```
