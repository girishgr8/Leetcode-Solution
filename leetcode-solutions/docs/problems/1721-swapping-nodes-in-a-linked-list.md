---
tags:
    - Linked List
    - Two Pointers
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/swapping-nodes-in-a-linked-list/](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/){:target="\_blank"}

**Approach 1 : Simple & Intuitive approach :slight_smile:**

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
        public ListNode swapNodes(ListNode head, int k) {
            int n = 0, curr = 0;
            ListNode ptr = head;
            ListNode begin = head, end = head;
            while(ptr != null){
                ptr = ptr.next;
                n++;
            }
            ptr = head;
            while(ptr != null){
                if(n-curr == k) end = ptr;
                curr++;
                if(curr == k) begin = ptr;
                ptr = ptr.next;
            }
            int temp = begin.val;
            begin.val = end.val;
            end.val = temp;
            return head;
        }
    }
    ```

=== "C++"

    ```c++
    ```

-   [x] **Time Complexity :** O(n) where _n_ = number of nodes in linked list

-   [x] **Space Complexity :** O(1)

<hr>

**Approach 2 : Slow - Fast Pointers :smiley:**

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
        public ListNode swapNodes(ListNode head, int k) {
            ListNode dummy = new ListNode(0, head);
            ListNode fast = dummy, slow = dummy;
            ListNode tempNode = null;
            while (k-- > 0)
                fast = fast.next;
            tempNode = fast;
            while (fast != null) {
                fast = fast.next;
                slow = slow.next;
            }
            int temp = slow.val;
            slow.val = tempNode.val;
            tempNode.val = temp;
            return dummy.next;
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
        ListNode* swapNodes(ListNode* head, int k) {
            ListNode *dummy = new ListNode(0, head);
            ListNode *fast = dummy, *slow = dummy;
            ListNode* tempNode = NULL;
            while (k-- > 0)
                fast = fast->next;
            tempNode = fast;
            while (fast != NULL) {
                fast = fast->next;
                slow = slow->next;
            }
            int temp = slow->val;
            slow->val = tempNode->val;
            tempNode->val = temp;
            return dummy->next;
        }
    };
    ```

-   [x] **Time Complexity :** O(n) where _n_ = number of nodes in linked list

-   [x] **Space Complexity :** O(1)
