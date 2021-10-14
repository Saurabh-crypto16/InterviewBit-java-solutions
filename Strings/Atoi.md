```java
public class Solution {
    public static int atoi(final String A) {
        if (A.isEmpty()) return 0;
        String[] strs = A.split("\\s+");
        boolean signFlag = true;
        if (!strs[0].isEmpty() && strs[0].charAt(0) == '-') {
            signFlag = false;
        }

        char[] nums = strs[0].toCharArray();
        StringBuilder sb = new StringBuilder("");
        int firstChar = 0;
        
        for (char num : nums) {
            if (Character.isDigit(num)) {
                firstChar = 1;
                sb.append(num);
            }
            else if (firstChar == 0 && (num == '+' || num == '-')) {
                firstChar = 1;
                continue;
            }
            else {
                break;
            }
        }

        if (sb.length() == 0) return 0;
        int ans = 0;
        try {
            ans = Integer.parseInt(sb.toString());
            ans *= signFlag == true ? 1 : -1;
        } catch (Exception e) {
            if (signFlag) {
                ans = Integer.MAX_VALUE;
            }
            else {
                ans = Integer.MIN_VALUE;
            }
        }

        return ans;
    }
}

//Other solution
public static int atoi(final String A) {
        char ch[]=A.toCharArray();
        int i=0;
        boolean neg_flag=false;

        while(i<ch.length && i==' ')    i++;
        int start=i;
        if(ch[start]=='-'){
            neg_flag=true;
            start++;
            i++;
        }
        if(ch[start]=='+'){
            start++;
            i++;
        }

        while(i<ch.length){
            if(!Character.isDigit(ch[i]))   break;
            i++;
        }
        
        double ans;
        if(start<i) ans=Double.parseDouble(A.substring(start,i));
        else    {
            if(Character.isDigit(ch[i])){
                if(neg_flag)    return -(int)ch[i];
                else    return (int)ch[i];
            }else{
                return 0;
            }
        }
        if(ans>Integer.MAX_VALUE)   return Integer.MAX_VALUE;
        else if(ans<Integer.MIN_VALUE)  return Integer.MIN_VALUE;
        else if(i<=ch.length){
            if(neg_flag)    return  -((int)ans);
            else    return (int)ans; 
        }else{
            return 0;
        }
    }
```
