```java
/*
Same intution as ugly number 
*/

public class Solution {
    public ArrayList<Integer> solve(int A, int B, int C, int D) {
        int i=0,j=0,k=0;
        ArrayList<Integer> al=new ArrayList<>();
        al.add(1);

        while(al.size()<=D){
            int min=Math.min(A*al.get(i),Math.min(al.get(j)*B,al.get(k)*C));
            al.add(min);

            if(min==al.get(i)*A){
                i++;
            }
            if(min==al.get(j)*B){
                j++;
            }
            if(min==al.get(k)*C){
                k++;
            }
        }

        al.remove(0);
        return al;
    }
}
```
