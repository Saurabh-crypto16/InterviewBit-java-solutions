```java
public class Solution {
	ArrayList<ArrayList<String>> res;
	public ArrayList<ArrayList<String>> partition(String s) {
		res=new ArrayList<>();
		bt(0,new ArrayList<>(),s);
		return res;
	}
	public void bt(int idx,ArrayList<String> path,String s){
		if(idx==s.length()){
			res.add(new ArrayList<>(path));
			return;
		}

		for(int i=idx;i<s.length();i++){
			if(isPalin(s.substring(idx,i+1))){
				path.add(s.substring(idx,i+1));
				bt(i+1,path,s);
				path.remove(path.size()-1);
			}
		}
	}
	public boolean isPalin(String s){
		int start=0,end=s.length()-1;
		while(start<=end){
			if(s.charAt(start)!=s.charAt(end))
				return false;
			
			start++;
			end--;
		}
		return true;
	}
}

```
