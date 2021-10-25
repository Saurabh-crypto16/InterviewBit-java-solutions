```java
/*
Insert 1st char in queue and maintain count of each char
while inserting into ans check if freq of head of queue is >1 
if so keep removing queue elements
*/

public class Solution {
  public String solve(String A) {
    Queue<Character> queue = new LinkedList<>();
    StringBuilder sb = new StringBuilder();
    Map<Character, Integer> map = new HashMap<>();
    for (char c : A.toCharArray()) {
      queue.add(c);
      map.put(c, map.getOrDefault(c, 0) + 1);
      while (!queue.isEmpty() && map.get(queue.peek()) > 1) {
        queue.remove();
      }
      sb.append(queue.isEmpty() ? '#' : queue.peek());
    }
    return sb.toString();
  }
}

```
