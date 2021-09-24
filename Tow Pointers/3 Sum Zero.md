```java
public class Solution {
    public ArrayList<ArrayList<Integer>> threeSum(ArrayList<Integer> arr) {
        int n=arr.size();
        Collections.sort(arr);
        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
        for(int i=0;i<n-2;i++)
        {
            if(i==0||(i>0 && (long)arr.get(i)!=(long)arr.get(i-1)))
            {
                int low=i+1;
                int high=n-1;
                long negate=0-(long)arr.get(i);

                while(low<high)
                {
                    long sum=(long)arr.get(low)+(long)arr.get(high);
                    if(sum==negate)
                    {
                        ArrayList<Integer> temp=new ArrayList<>();
                        temp.add(arr.get(i));
                        temp.add(arr.get(low));
                        temp.add(arr.get(high));
                        ans.add(temp);

                        while(low<high&&(long)arr.get(low)==(long)arr.get(low+1))
                        low++;
                        while(low<high&&(long)arr.get(high)==(long)arr.get(high-1))
                        high--;

                        low++;
                        high--;
                    }
                    else if(sum<negate)
                    low++;
                    else
                    high--;
                }
            }
        }
        return ans;
    }
}

```
