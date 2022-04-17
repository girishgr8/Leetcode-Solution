---
tags:
    - Stack
    - Tree
    - Depth-First Search
    - Binary Search Tree
    - Binary Tree
---

**Leetcode Problem Link :**

[https://leetcode.com/problems/increasing-order-search-tree/](https://leetcode.com/problems/increasing-order-search-tree/){:target="\_blank"}

**Approach : Recursion :smile:**

=== "Java"

    ```java
    /**
    * Definition for a binary tree node.
    * public class TreeNode {
    *     int val;
    *     TreeNode left;
    *     TreeNode right;
    *     TreeNode(int x) { val = x; }
    * }
    */
    class Solution {
        TreeNode head = null;
        public TreeNode increasingBST(TreeNode root) {
            inorder(root);
            return head;
        }
        public void inorder(TreeNode root){
            if(root==null)
                return;
            inorder(root.left);
            if(head==null){
                head = new TreeNode(root.val);
                head.left = null; head.right = null;
            }
            else{
                TreeNode ptr = head;
                while(ptr.right!=null)
                    ptr = ptr.right;
                TreeNode node = new TreeNode(root.val);
                node.left = null; node.right = null;
                ptr.right = node;
            }
            inorder(root.right);
        }
    }
    ```

=== "C++"

    ``` c++

    ```

-   [x] **Time Complexity :**

-   [x] **Space Complexity :**
