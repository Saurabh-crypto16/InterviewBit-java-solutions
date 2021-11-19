```java
public class Solution {
    public int solve(String A) {
        Set<Character> set=new HashSet<>();

        for(char c: A.toCharArray()){
            if(set.contains(c)){
                set.remove(c);
            }else{
                set.add(c);
            }
        }

        return (set.size()==0 || set.size()==1) ? 1 : 0;
    }
}
```
