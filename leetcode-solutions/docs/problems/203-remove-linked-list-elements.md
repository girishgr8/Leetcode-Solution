---
tags:
    - Linked List
    - Recursion
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/){:target="\_blank"}

**Approach 1 : Recursive Approach :smiley:**

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
        public ListNode removeElements(ListNode head, int val) {
            // Base case
            if(head == null) return head;

            // Recursively remove nodes with value 'val' from the list
            ListNode node = removeElements(head.next, val);

            // if the head's val == val, then return the other part of the list
            if(head.val == val) return node;

            // otherwise, head.next will point to list returned after solving recursively for rest part
            head.next = node;
            return head;
        }
    }
    ```

=== "C++"

    ```c++
    /**
    * Definition for singly-linked list.
    * struct ListNode {
    *     int val;
    *     ListNode *next;
    *     ListNode() : val(0), next(nullptr) {}
    *     ListNode(int x) : val(x), next(nullptr) {}
    *     ListNode(int x, ListNode *next) : val(x), next(next) {}
    * };
    */
    class Solution {
    public:
        ListNode* removeElements(ListNode* head, int val) {
            // Base case
            if(!head) return head;

            // Recursively remove nodes with value 'val' from the list
            ListNode* node = removeElements(head->next, val);

            // if the head's val == val, then return the other part of the list
            if(head->val == val) return node;

            // otherwise, head.next will point to list returned after solving recursively for rest part
            head->next = node;
            return head;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of linked list

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Iterative Approach :slight_smile:**

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
        public ListNode removeElements(ListNode head, int val) {
            if(head == null) return head;
            ListNode prev = null, curr = head;
            while(curr != null){
                if(curr.val == val){
                    if(prev == null)  head = curr.next;
                    else  prev.next = curr.next;
                }
                else
                    prev = curr;
                curr = curr.next;
            }
            return head;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is the length of linked list

-   [x] **Space Complexity :** O(1)
