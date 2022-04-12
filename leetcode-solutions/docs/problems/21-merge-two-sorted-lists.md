---
tags:
    - Recursion
    - Linked List
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/){:target="\_blank"}

**Approach 1: Recursive approach :smiley:**

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
        public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
            // if list1 is empty return list2
            if(list1 == null)
                return list2;

            // if list2 is empty return list1
            if(list2 == null)
                return list1;

            if(list1.val < list2.val){
                list1.next = mergeTwoLists(list1.next, list2);
                return list1;
            }

            else{
                list2.next = mergeTwoLists(list1, list2.next);
                return list2;
            }
        }
    }
    ```

-   [x] **Time Complexity :** O(m+n) where _m_ and _n_ are the length of the two lists respectively

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2: Iterative approach :slight_smile:**

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
        public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
            ListNode dummy = new ListNode();
            ListNode ptr = dummy;

            while(list1 != null && list2 != null){
                if(list1.val < list2.val){
                    ptr.next = list1;
                    list1 = list1.next;
                }
                else{
                    ptr.next = list2;
                    list2 = list2.next;
                }
                ptr = ptr.next;
            }

            if(list1 == null) ptr.next = list2;
            if(list2 == null) ptr.next = list1;

            return dummy.next;
        }
    }
    ```

-   [x] **Time Complexity :** O(m+n) where _m_ and _n_ are the length of the two lists respectively

-   [x] **Space Complexity :** O(1)
