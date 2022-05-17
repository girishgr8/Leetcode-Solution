---
tags:
    - Linked List
    - Two Pointers
    - Stack
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/](https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/){:target="\_blank"}

**Approach 1 : Two pointers Approach :slight_smile:**

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
    class Solution {
        public int pairSum(ListNode head) {
            Stack<Integer> stack = new Stack<Integer>();
            ListNode slow = head, fast = head;
            while(fast != null && fast.next != null){
                stack.push(slow.val);
                slow = slow.next;
                fast = fast.next.next;
            }
            int max = 0;
            while(slow != null){
                int n1 = stack.pop();
                int n2 = slow.val;
                max = Math.max(max,(n1+n2));
                slow = slow.next;
            }
            return max;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the number of nodes in linked list

-   [x] **Space Complexity :** O(1)
