```java
public class Solution {
    ArrayList<ArrayList<Integer>> res;
    public ArrayList<ArrayList<Integer>> permute(ArrayList<Integer> A) {
        res=new ArrayList<>();
        bt(new ArrayList<Integer>(),A);
        return res;
    }
    public void bt(ArrayList<Integer> list,ArrayList<Integer> A){
        if(list.size()==A.size()){
            res.add(new ArrayList<>(list));
            return;
        }

        for(int i: A){
            if(!list.contains(i)){
                list.add(i);
                bt(list,A);
                list.remove(list.size()-1);
            }
        }
    }
}
```
