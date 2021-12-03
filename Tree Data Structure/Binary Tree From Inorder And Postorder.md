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
public class Solution {
    public TreeNode buildTree(ArrayList<Integer> in, ArrayList<Integer> post) {
        Map<Integer,Integer> inMap=new HashMap<>();
        for(int i=0;i<in.size();i++){
            inMap.put(in.get(i),i);
        }

        TreeNode root=build(in,0,in.size()-1,post,0,post.size()-1,inMap);
        return root;
    }
    public TreeNode build(ArrayList<Integer> in,int is,int ie,ArrayList<Integer> post,
        int ps,int pe,Map<Integer,Integer> inMap){
        if(ps>pe || is>ie){
            return null;
        }

        TreeNode root=new TreeNode(post.get(pe));
        int inRoot=inMap.get(post.get(pe));
        int numsLeft=inRoot-is;

        root.left=build(in,is,inRoot-1,post,ps,ps+numsLeft-1,inMap);
        root.right=build(in,inRoot+1,ie,post,ps+numsLeft,pe-1,inMap);

        return root;
    }
}
```
