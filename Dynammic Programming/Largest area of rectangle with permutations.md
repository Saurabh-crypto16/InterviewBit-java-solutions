```java
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        /*
        1 0 0 0
        1 1 0 0
        1 1 1 0
        1 1 1 1
        */
        //finding height of column
        for(int i=0;i<A.size();i++){
            for(int j=0;j<A.get(0).size();j++){
                if(i!=0 && A.get(i).get(j)!=0){
                    A.get(i).set(j,A.get(i).get(j)+A.get(i-1).get(j));
                }
            }
        }
        /*
        1 0 0 0
        2 1 0 0
        3 2 1 0
        4 3 2 1
        */

        //sorting the height calculated rows
        for(int i=0;i<A.size();i++){
            Collections.sort(A.get(i));
        }
        /*
        0 0 0 1
        0 0 1 2
        0 1 2 3
        1 2 3 4
        */

        //calculating area
        int maxArea=0,area=0;
        for(int i=0;i<A.size();i++){
            int width=1;
            for(int j=A.get(0).size()-1;j>=0;j--){
                //calculating area of independent rows
                area=width*A.get(i).get(j);
                width++;
                maxArea=Math.max(maxArea,area);
            }
        }

        return maxArea;
    }
}

```
