```java
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
 
 //Solution 1 
public class Solution {
    int sum;
    public int sumNumbers(TreeNode A) {
        if(A==null)     return 0;
        sum=0;
        findSum(A,0);
        return sum%1003;
    }
    public void findSum(TreeNode node,int val){
        int curr=(val*10)%1003+node.val;

        if(node.left==null && node.right==null){
            sum+=(curr%1003);
            sum%=1003;
            return;
        }

        if(node.left!=null)     findSum(node.left,curr);
        if(node.right!=null)     findSum(node.right,curr);
    }
}

 
 //Solution 2 - using extra space
public class Solution {
    public int sumNumbers(TreeNode root) {
        if(root==null)  return 0;
        if(root.left==null && root.right==null) return root.val;
        
        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        path(root,new ArrayList<Integer>(),res);
        
        int sum=0;
        for(ArrayList<Integer> a: res){
            int curr_num=0;
            for(int i: a){
                //System.out.print(i+" ");
                curr_num=(curr_num*10)%1003+i;
            }
            //System.out.println();
            sum+=(curr_num%1003);
        }
        
        return sum%1003;
    }
    public void path(TreeNode node,ArrayList<Integer> num, ArrayList<ArrayList<Integer>> res){
        num.add(node.val);
        
        if(node.left==null && node.right==null){
            res.add(new ArrayList<>(num));
            return;
        }
        
        if(node.left!=null){
            path(node.left,num,res);
            num.remove(num.size()-1);
        }
        if(node.right!=null){
            path(node.right,num,res);
            num.remove(num.size()-1);   
        }
    }
}
 ```
