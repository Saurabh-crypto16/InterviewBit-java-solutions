```java
public class Solution {
	public int minimumTotal(ArrayList<ArrayList<Integer>> a) {
        ArrayList<Integer> dp=new ArrayList<>();
        int n=a.size();
        //copy last row in dp
        for(int i=0;i<a.get(n-1).size();i++){
            dp.add(a.get(n-1).get(i));
        }

        //start from second last row in triangle
        for(int i=n-2;i>=0;i--){
            for(int j=0;j<=i;j++){
                dp.set(j,Math.min(dp.get(j),dp.get(j+1))+a.get(i).get(j));
            }
        }

        return dp.get(0);
	}
}

```
