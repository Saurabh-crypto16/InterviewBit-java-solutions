```java
/*
whenever we encounter /.. -> pop
whenever we encounter /name -> push
whenever we encounter /. -> do nothing
*/

public class Solution {
    public String simplifyPath(String A) {
        Stack<String> s=new Stack<>();
        StringBuilder res=new StringBuilder();
        String[] p=A.split("/");

        for(String str: p){
            if(!s.isEmpty() && str.equals(".."))    s.pop();
            else if(!str.equals("") && !str.equals(".") && !str.equals(".."))   
                s.push(str);
        }

        if(s.isEmpty()) return "/";
        while(!s.isEmpty()){
            res.insert(0,s.pop()).insert(0,'/');
        }
        return res.toString();
    }
}
```
