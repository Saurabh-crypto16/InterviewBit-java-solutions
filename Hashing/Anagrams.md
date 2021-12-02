```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<ArrayList<Integer>> anagrams(final List<String> A) {
        HashMap<HashMap<Character,Integer>,ArrayList<Integer>> map=new HashMap<>();

        int num=1;
        for(String s: A){
            HashMap<Character,Integer> str_map=new HashMap<>();
            for(char c: s.toCharArray()){
                str_map.put(c,str_map.getOrDefault(c,0)+1);
            }

            ArrayList<Integer> al=map.getOrDefault(str_map,new ArrayList<Integer>());
            al.add(num);
            num++;
            map.put(str_map,al);
        }

        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
        for(Map.Entry<HashMap<Character,Integer>,ArrayList<Integer>> entry : map.entrySet()){
            ans.add(entry.getValue());
        }

        return ans;
    }
}
```
