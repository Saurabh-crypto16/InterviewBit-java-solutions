```java
public class Solution {
    public ArrayList<Integer> solve(int A, ArrayList<Integer> B) {
        ArrayList<Integer> resp = new ArrayList<>();
        int min = Collections.min(B);
        int available = A % min;

        int i = 0;
        while (resp.size() < A / min) {
            if (B.get(i) - min <= available) {
                available -= B.get(i) - min;
                resp.add(i);
            } else {
                i++;
            }
        }
        
        return resp;
    }
}
```
