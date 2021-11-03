```java
public class Solution {
    public ArrayList<ArrayList<Integer>> solve(int A) {
        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        ArrayList<Integer> row,pre=null;
        for(int i=0;i<A;i++){
            row=new ArrayList<Integer>();
            for(int j=0;j<=i;j++){
                if(j==0 || j==i)    row.add(1);
                else    row.add(pre.get(j-1)+pre.get(j));
            }
            pre=row;
            res.add(row);
        }
        return res;
    }
}

```
