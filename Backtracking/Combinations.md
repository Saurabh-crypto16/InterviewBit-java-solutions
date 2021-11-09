```java
public class Solution {
    ArrayList<ArrayList<Integer>> res;
    public ArrayList<ArrayList<Integer>> combine(int A, int B) {
        res=new ArrayList<>();
        bt(1,new ArrayList<>(),A,B);
        return res;
    }
    public void bt(int idx,ArrayList<Integer> list,int A,int B){
        if(list.size()==B){
            res.add(new ArrayList<>(list));
            return;
        }

        for(int i=idx;i<=A;i++){
            list.add(i);
            bt(i+1,list,A,B);
            list.remove(list.size()-1);
        }
    }
}

```
