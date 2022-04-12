---
tags:
    - Recursion
    - Linked List
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/){:target="\_blank"}

**Approach 1 : Recursive approach :smiley:**

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
        public ListNode reverseList(ListNode head) {
            if (head == null || head.next == null) {
                return head;
            }
            ListNode node = reverseList(head.next);
            head.next.next = head;
            head.next = null;
            return node;
        }
    }
    ```

-   [x] **Time Complexity :** O(n) where _n_ is number of nodes in linked list

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Iterative approach :slight_smile:**

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
        public ListNode reverseList(ListNode head) {

            ListNode prev = null, curr = head, next = null;

            while(curr != null){
                next = curr.next;
                curr.next = prev;
                prev = curr;
                curr = next;
            }

            return prev;
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
        ListNode* reverseList(ListNode* head) {

            ListNode *next, *prev = NULL;

            while(head != NULL) {
                next = head->next;
                head->next = prev;
                prev = head;
                head = next;
            }

            return prev;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ is number of nodes in linked list

-   [x] **Space Complexity :** O(1)
