```java
public class Solution {
    public ArrayList<ArrayList<Integer>> generateMatrix(int A) {
        int ans[][]=new int[A][A];

        int top=0, bottom=A-1, left=0, right=A-1, val=1;
        while(val<=A*A){
            for(int i=left;i<=right;i++){
                ans[top][i]=val++;
            }
            top++;

            for(int i=top;i<=bottom;i++){
                ans[i][right]=val++;
            }
            right--;

            for(int i=right;i>=left;i--){
                ans[bottom][i]=val++;
            }
            bottom--;

            for(int i=bottom;i>=top;i--){
                ans[i][left]=val++;
            }
            left++;
        }

        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        for(int i=0;i<A;i++){
            res.add(new ArrayList<Integer>());
            for(int j=0;j<A;j++){
                res.get(i).add(ans[i][j]);
            }
        }

        return res;
    }
}
```
