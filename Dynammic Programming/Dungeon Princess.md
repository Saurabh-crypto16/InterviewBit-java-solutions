```java
/*
Formula is from any (i,j) we find min of (i+1,j) and (i,j+1) and substract
curr (i,j) value from min and that will be the min value for (i,j)
If (n-1,m-1) is +ve the it will have value of 1 else we need just 1+value of (n-1,m-1) at it
*/
public class Solution {
    public int calculateMinimumHP(ArrayList<ArrayList<Integer>> A) {
        if(A==null || A.size()==0 || A.get(0).size()==0)
            return 0;

        Map<String,Integer> dp=new HashMap<>();
        return minHP(0,0,A,dp);
    }
    public int minHP(int i,int j,ArrayList<ArrayList<Integer>> A,Map<String,Integer> dp){
        if(i>=A.size() || j>=A.get(0).size()){
            return Integer.MAX_VALUE;
        }

        String key=i+"$"+j;
        if(dp.containsKey(key)){
            return dp.get(key);
        }

        int next=Math.min(minHP(i+1,j,A,dp),minHP(i,j+1,A,dp));
        if(next==Integer.MAX_VALUE){
            //if both (i+1,j) and (i,j+1) give Integer.MAX_VALUE then its (n-1,m-1)
            next=1; 
        }

        int res=Math.max(next-A.get(i).get(j),1);
        dp.put(key,res);
        return res;
    }
}

```
