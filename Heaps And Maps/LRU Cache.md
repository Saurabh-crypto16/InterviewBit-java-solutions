```java
//DLL := head -> MRU -> node -> node -> LRU -> tail
public class Solution {
    
    public class Node{
        Node prev,next;
        int key,val;
        Node(int key,int val){
            this.key=key;
            this.val=val;
        }
    }

    Node head=new Node(0,0),tail=new Node(0,0);
    int capacity;
    HashMap<Integer,Node> map=new HashMap<>();

    public Solution(int capacity) {
        this.capacity=capacity;
        //initial config
        //MRU node will be just after head in DLL
        //LRU will be just before tail
        head.next=tail;
        tail.prev=head;
    }
    
    public int get(int key) {
        if(map.containsKey(key)){
            Node node=map.get(key);
            remove(node);
            insert(node);
            return node.val;
        }else{
            return -1;
        }
    }
    
    public void set(int key, int value) {
        if(map.containsKey(key)){
            remove(map.get(key));
        }
        if(map.size()==capacity){
            remove(tail.prev);
        }

        insert(new Node(key,value));
    }

    public void insert(Node node){
        map.put(node.key,node);
        node.next=head.next;
        node.prev=head;
        head.next.prev=node;
        head.next=node;
    }

    public void remove(Node node){
        map.remove(node.key);
        node.prev.next=node.next;
        node.next.prev=node.prev;
    }
}

```
