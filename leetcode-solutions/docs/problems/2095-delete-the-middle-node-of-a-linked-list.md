---
tags:
    - Linked List
    - Two pointers
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/){:target="\_blank"}

**Approach 1 : Naive Approach(Two pass solution) :slight_smile:**

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
        public ListNode deleteMiddle(ListNode head) {
            if(head == null || head.next == null)
                return null;
            int count = 0;
            ListNode ptr = head, prev = null;
            while(ptr != null){
                ptr = ptr.next;
                count++;
            }
            int mid = count/2;
            ptr = head;
            while(mid-- > 0){
                prev = ptr;
                ptr = ptr.next;
            }
            prev.next = ptr.next;
            return head;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of linked list

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Two Pointers Approach(One pass solution) :smiley:**

=== "Java"

    ``` java
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
        public ListNode deleteMiddle(ListNode head) {
            if(head == null || head.next == null)
                return null;

            ListNode slow = head, fast = head, prev = null;
            while(fast != null && fast.next != null){
                fast = fast.next.next;
                prev = slow;
                slow = slow.next;
            }
            prev.next = slow.next;
            return head;
        }
    }
    ```

=== "Python"

    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
            if(head == None or head.next == None):
                return None

            slow, fast, prev = head, head, None
            while(fast != None and fast.next != None):
                fast = fast.next.next
                prev = slow
                slow = slow.next

            prev.next = slow.next
            return head
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of linked list

-   [x] **Space Complexity :** O(1)
