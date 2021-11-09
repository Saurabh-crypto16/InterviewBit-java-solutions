```java
public class Solution {
    ArrayList<ArrayList<Integer>> res;
    public ArrayList<ArrayList<Integer>> subsetsWithDup(ArrayList<Integer> A) {
        res=new ArrayList<>();
        Collections.sort(A);
        bt(0,new ArrayList<>(),A);
        return res;
    }
    public void bt(int idx,ArrayList<Integer> list,ArrayList<Integer> A){
        res.add(new ArrayList<>(list));

        for(int i=idx;i<A.size();i++){
            //special condition
            if (i > idx && A.get(i).equals(A.get(i - 1))) {
                continue;
            }

            list.add(A.get(i));
            bt(i+1,list,A);
            list.remove(list.size()-1);
        }
    }
}

```
