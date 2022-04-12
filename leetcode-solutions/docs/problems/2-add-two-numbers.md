=== "C++"

    ```c++
    class Solution {
    	public:
    		ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    		ListNode dummy(0);
    		ListNode* curr = &dummy;
    		int carry = 0;

    		while (l1 || l2 || carry) {
    			if (l1) {
    			carry += l1->val;
    			l1 = l1->next;
    		}
    		if (l2) {
    			carry += l2->val;
    			l2 = l2->next;
    		}
    			curr->next = new ListNode(carry % 10);
    			carry /= 10;
    			curr = curr->next;
    		}
    		return dummy.next;
    	}
    };
    ```

=== "Java"

    ```java
    class Solution {
    	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    		if(l1==null) 
				return l2;
    		if(l2==null) 
				return l1;
    		
			ListNode head = l1, prev = null;
    		int carry = 0;
    		
			while(l1!=null && l2!=null){
    			int sum = l1.val + l2.val + carry;
    			carry = sum/10;
    			l1.val = sum%10;
    			prev = l1;
    			l1 = l1.next;
    			l2 = l2.next;
    		}
    		while(l1!=null){
    			int sum = l1.val + carry;
    			carry = sum/10;
    			l1.val = sum%10;
    			prev = l1;
    			l1 = l1.next;
    		}
    		while(l2!=null){
    			int sum = l2.val + carry;
    			carry = sum/10;
    			ListNode newnode = new ListNode(sum%10);
    			prev.next = newnode;
    			prev = newnode;
    			l2 = l2.next;
    		}
    		if(carry>0){
    			ListNode newnode = new ListNode(carry);
    			newnode.next = null;
    			prev.next = newnode;
    		}
    		return head;
    	}
    }
    ```
