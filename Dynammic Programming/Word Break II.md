```java
public class Solution {
    public ArrayList<String> wordBreak(String A, ArrayList<String> B) {
        ArrayList<String> list = new ArrayList<>();
        Set<String> set = new HashSet<>(B);
        wordBreak(list, new ArrayList<>(), 0, set,A);
        return list;
    }
    private void wordBreak(ArrayList<String> list, ArrayList<String> temp, int index, 
                           Set<String> set, String s) {
        if(index==s.length()) { //  reached at the end of string
            StringBuilder sb = new StringBuilder();
            for(int i=0; i<temp.size()-1; i++) {
                sb.append(temp.get(i)).append(" ");
            }
            sb.append(temp.get(temp.size()-1));
            list.add(sb.toString());
            return;
        }
        
        for(int i=index; i<s.length(); i++) {
            String str = s.substring(index, i+1);
            if(!set.contains(str)) continue;
            temp.add(str); // add to the temporary list
            wordBreak(list, temp, i+1, set,s); // recurse to check every word from next index
            temp.remove(temp.size()-1); //backtrack
        }
    }
}

```
