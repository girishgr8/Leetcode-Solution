---
tags:
    - Linked List
    - Two pointers
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/middle-of-the-linked-list/](https://leetcode.com/problems/middle-of-the-linked-list/){:target="\_blank"}

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
        public ListNode middleNode(ListNode head) {
            ListNode slow = head, fast = head;
            while(fast != null && fast.next != null){
                fast = fast.next.next;
                slow = slow.next;
            }
            return slow;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the number of nodes in linked list

-   [x] **Space Complexity :** O(1)
