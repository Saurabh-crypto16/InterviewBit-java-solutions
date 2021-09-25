```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<Integer> intersect(final List<Integer> A, final List<Integer> B) {
        ArrayList<Integer> ans=new ArrayList<>();
        int a_pointer=0,b_pointer=0;
        
        while(a_pointer<A.size() && b_pointer<B.size()){
            if(A.get(a_pointer).equals(B.get(b_pointer))){
                ans.add(A.get(a_pointer));
                a_pointer++;
                b_pointer++;
            }else if(A.get(a_pointer)>B.get(b_pointer)){
                b_pointer++;
            }else{
                a_pointer++;
            }
        }
        return ans;
    }
}

```
