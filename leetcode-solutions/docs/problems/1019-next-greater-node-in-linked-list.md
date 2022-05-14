---
tags:
    - Array
    - Linked List
    - Stack
    - Monotonic Stack
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/next-greater-node-in-linked-list/](https://leetcode.com/problems/next-greater-node-in-linked-list/){:target="\_blank"}

**Approach : Stack :smile:**

=== "Java"

    ```java
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    *     int val;
    *     ListNode next;
    *     ListNode() {}
    *     ListNode(int val) { this.val = val; }
    *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    * }
    */

    class Pair{
        int i;
        int val;
        public Pair(int i, int val){
            this.i = i;
            this.val = val;
        }
    }

    class Solution {
        public int[] nextLargerNodes(ListNode head) {
            int n = 0, i = 0;
            int[] result = new int[n];
            Stack<Pair> stack = new Stack<Pair>();
            ListNode ptr = head;

            while(ptr != null){
                n++;
                ptr = ptr.next;
            }

            ptr = head;
            while(ptr != null){
                while(!stack.isEmpty() && ptr.val > stack.peek().val)
                    result[stack.pop().i] = ptr.val;

                stack.push(new Pair(i++, ptr.val));
                ptr = ptr.next;
            }
            return result;
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :** O(n) where n = number of nodes in linked list

-   [x] **Space Complexity :** O(n) where n = number of nodes in linked list
