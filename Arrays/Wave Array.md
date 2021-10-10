```java
public class Solution {
    public ArrayList<Integer> wave(ArrayList<Integer> A) {
        Collections.sort(A);
        for(int i=0;i<A.size();i+=2){
            if(i==A.size()-1)   break;
            Collections.swap(A,i,i+1);
        }
        return A;
    }
}
```
