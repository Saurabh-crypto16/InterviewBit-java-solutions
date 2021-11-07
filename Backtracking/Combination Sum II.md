```java
public class Solution {
    ArrayList<ArrayList<Integer>> res;
	public ArrayList<ArrayList<Integer>> combinationSum(ArrayList<Integer> A, int B) {
        Collections.sort(A);
        res=new ArrayList<>();
        bt(0,0,A,new ArrayList<Integer>(),B);
        return res;
	}
    public void bt(int curr_idx,int curr_sum,ArrayList<Integer> A,ArrayList<Integer> list,int B){
        if(curr_sum==B && !res.contains(list)){
            res.add(new ArrayList<>(list));
        }

        for(int i=curr_idx;i<A.size();i++){
            if(curr_sum+A.get(i)<=B){
                list.add(A.get(i));
                bt(i+1,curr_sum+A.get(i),A,list,B);
                list.remove(list.size()-1);
            }
        }
    }
}
```
