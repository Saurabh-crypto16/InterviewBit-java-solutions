```java
public class Solution {
    public String getPermutation(int n, int k) {
        ArrayList<Integer> list = new ArrayList<>();
        for(int i=1;i<=n;i++){
            list.add(i);
        }

        ArrayList<Integer> fact =  new ArrayList<Integer>();
        fact.add(1);
        int kl = 1;
        
        for(int j=1;j<=11;j++){
            kl*=j;
            fact.add(kl);
        }

        for(int j = 12;j<=n;j++){
            fact.add(Integer.MAX_VALUE);
        }
        if(k>fact.get(n)) return "";
        
        return getPermutation(list,k-1,fact);
    }
    public String getPermutation(ArrayList<Integer> list,int k,ArrayList<Integer> fact){
        int n=list.size();
        if(n==0) return "";
        
        int fact_n=fact.get(n-1);
        int index=k/fact_n;
        int num=list.get(index);
        list.remove(index);
        k%=fact_n;
        return num+getPermutation(list,k,fact);
    }
}
```
