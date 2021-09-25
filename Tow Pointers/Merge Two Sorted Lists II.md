```java
public class Solution {
	public void merge(ArrayList<Integer> A, ArrayList<Integer> B) {
		int a_pointer=0,b_pointer=0;
		while(b_pointer<B.size()){
			if(a_pointer==A.size()){
				while(b_pointer<B.size()){
					A.add(B.get(b_pointer));
					b_pointer++;
				}
			}
			else if(A.get(a_pointer)>B.get(b_pointer)){
				A.add(a_pointer,B.get(b_pointer));
				b_pointer++;
			}else{
				a_pointer++;
			}
		}
	}
}

```
