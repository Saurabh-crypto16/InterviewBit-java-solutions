```java
//SOLUTION 1
public class Solution {
    public String minWindow(String A, String B) {
        Map<Character, Integer> map = new HashMap<>();
        for (char c : B.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }

        int count = map.size();
        int idx = 0;
        int start = 0;
        int minLen = Integer.MAX_VALUE;
        int startIdx = -1;
        int endIdx = -1;

        while (idx < A.length()) {
            if (map.containsKey(A.charAt(idx))) {
                map.put(A.charAt(idx), map.get(A.charAt(idx)) - 1);
                if (map.get(A.charAt(idx)) == 0) {
                    count--;
                }
            }

            while (start < A.length() && count == 0) {
                if (minLen > idx - start + 1) {
                    startIdx = start;
                    endIdx = idx + 1;
                    minLen = idx - start + 1;
                }
                if (map.containsKey(A.charAt(start))) {
                    map.put(A.charAt(start), map.get(A.charAt(start)) + 1);
                    if (map.get(A.charAt(start)) == 1) {
                        count++;
                    }
                }

                start++;
            }

            idx++;
        }

        return minLen == Integer.MAX_VALUE ? "" : A.substring(startIdx, endIdx);
    }
}


//SOLUTION 2
public class Solution {
    public String minWindow(String A, String B) {
        String ans="";
        if(B.length()==0)   return ans;

        HashMap<Character,Integer> map2=new HashMap<>();
        for(char c:B.toCharArray()){
            map2.put(c,map2.getOrDefault(c,0)+1);
        }

        int mct=0;  //match count
        int dmct=B.length();  //desired match count

        HashMap<Character,Integer> map1=new HashMap<>();
        int i=-1,j=-1;        

        while(true){
            boolean flag1=false,flag2=false;

            //acquiring
            while(i<A.length()-1 && mct<dmct){
                i++;
                char ch=A.charAt(i);
                map1.put(ch,map1.getOrDefault(ch,0)+1);

                //increase mct only if valid char is acquired
                if(map1.getOrDefault(ch,0)<=map2.getOrDefault(ch,0)){
                    mct++;
                }

                flag1=true;
            }

            //releasing to get least size
            while(j<i && mct==dmct){
                String pans=A.substring(j+1,i+1);   //probable ans
                if(ans.length()==0 || pans.length()<ans.length()){
                    ans=pans;
                }

                j++;
                char ch=A.charAt(j);
                if(map1.get(ch)==1){
                    map1.remove(ch);
                }else{
                    map1.put(ch,map1.get(ch)-1);
                }

                if(map1.getOrDefault(ch,0)<map2.getOrDefault(ch,0)){
                    mct--;
                }

                flag2=true;
            }

            if(flag1==false && flag2==false){
                break;
            }
        }

        return ans;
    }
}
```
