---
tags:
    - Linked List
    - Math
    - Recursion
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/){:target="\_blank"}

**Approach : Simple Intuition :sweat_smile:**

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
    	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    		ListNode dummy = new ListNode(0);
    		ListNode curr = dummy;
    		int sum = 0;

    		while(l1 != null || l2 != null || sum > 0){
    			if(l1 != null){
    				sum += l1.val;
    				l1 = l1.next;
    			}
    			if(l2 != null){
    				sum += l2.val;
    				l2 = l2.next;
    			}
    			curr.next = new ListNode(sum % 10);
    			sum /= 10;
    			curr = curr.next;
    		}

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
    		ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    		ListNode dummy(0);
    		ListNode* curr = &dummy;
    		int sum = 0;

    		while (l1 || l2 || sum) {
    			if (l1) {
    				sum += l1->val;
    				l1 = l1->next;
    		    }
    			if (l2) {
    				sum += l2->val;
    				l2 = l2->next;
    			}
    			curr->next = new ListNode(sum % 10);
    			sum /= 10;
    			curr = curr->next;
    		}
    		return dummy.next;
    	}
    };
    ```

-   [x] **Time Complexity :** O(m + n) where m and n are number of nodes in linked list `l1` and `l2`

-   [x] **Space Complexity :** O(m + n) where m and n are number of nodes in linked list `l1` and `l2`

<hr>
