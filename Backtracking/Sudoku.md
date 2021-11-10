```java
public class Solution {
	public void solveSudoku(ArrayList<ArrayList<Character>> a) {
        if(a==null || a.size()==0)
            return;

        solve(a);
	}
    public boolean solve(ArrayList<ArrayList<Character>> a){        
        int n = a.size();
        
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                
                if(a.get(i).get(j) == '.'){
                    for(char c='1'; c<='9'; c++){
                        if(isValid(a, i, j, c)){
                            a.get(i).set(j, c);
                            
                            if(solve(a))
                            return true;
                            else
                            a.get(i).set(j, '.'); 
                        }
                    }
                    
                    return false;
                }
            }
        }
        
        return true;
    }

    public boolean isValid(ArrayList<ArrayList<Character>> a, int row, int col, char c){
        int regionRow = 3 * (row/3);
        int regionCol = 3 * (col/3);
        
        for (int i = 0; i < 9; i++) {
            if (a.get(i).get(col) == c) return false; 
            if (a.get(row).get(i) == c) return false; 
            if (a.get(regionRow + i/3).get(regionCol + i%3) == c) return false; 
        }
        return true;        
        
    }
}
```
