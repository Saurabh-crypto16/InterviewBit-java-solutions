```java
public class Solution {
    ArrayList<ArrayList<Integer>> res;
    public ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A) {
        res=new ArrayList<>();
        Collections.sort(A);
        bt(0,new ArrayList<Integer>(),A);
        return res;
    }
    public void bt(int j,ArrayList<Integer> list,ArrayList<Integer> A){
        res.add(new ArrayList<>(list));

        for(int i=j;i<A.size();i++){
            list.add(A.get(i));
            bt(i+1,list,A);
            list.remove(list.size()-1);
        }
    }
}

```
