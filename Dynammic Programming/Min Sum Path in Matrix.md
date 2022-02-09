```java
public class Solution {
    public int minPathSum(ArrayList<ArrayList<Integer>> A) {
        if(A==null || A.size()==0 || A.get(0).size()==0)
            return 0;

        Map<String,Integer> dp=new HashMap<>();
        return minHP(0,0,A,dp);
    }
    public int minHP(int i,int j,ArrayList<ArrayList<Integer>> A,Map<String,Integer> dp){
        if(i>=A.size() || j>=A.get(0).size()){
            return Integer.MAX_VALUE;
        }

        if(i==A.size()-1 && j==A.get(0).size()-1){
            return A.get(i).get(j);
        }

        String key=i+"$"+j;
        if(dp.containsKey(key)){
            return dp.get(key);
        }

        int res=A.get(i).get(j)+Math.min(minHP(i+1,j,A,dp),minHP(i,j+1,A,dp));

        dp.put(key,res);
        return res;
    }
}

```
